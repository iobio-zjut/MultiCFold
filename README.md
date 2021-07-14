# MultiCFold
### Distance-guided protein folding based on generalized descent direction



**Developer:**   
                Minghua Hou  
                College of Information Engineering  
                Zhejiang University of Technology, Hangzhou 310023, China  
				Email:  hmh6218@163.com  

**Contact:**  
                Guijun Zhang, Prof  
                College of Information Engineering  
                Zhejiang University of Technology, Hangzhou 310023, China  
                Email: zgj@zjut.edu.cn  

## 1. INSTALLATION
Binaries for Linux 64 bit system has been included in the package. The Linux binary was compiled using GCC 5.4.0. Users need to have these versions of GCC compilers when using binaries.

Please Follow the below steps to install and configure MultiCFold:

- Download Rosetta3.10 source package from https://www.rosettacommons.org/software/.
(where `$ROSETTA3`=path-to-Rosetta)

- Copy and paste ``"ClassicAbinitio.cc"`` and ``"ClassicAbinitio.hh"`` from ``"src/"`` folder in MultiCFold package to ``"$ROSETTA3/main/source/src/protocols/abinitio/"`` folder in Rosetta.

- Copy and paste ``"mymethod.cc"`` and ``"mymethod.hh"`` and ``"readfile.cc"`` and ``"readfile.hh"`` from ``"src/"`` folder in MultiCFold package to ``"$ROSETTA3/main/source/src/protocols/abinitio/"`` folder in Rosetta.

- Compile MultiCFold source code using the following commands:

```
 $> cd $ROSETTA3/main/source/
 $> ./scons.py AbinitioRelax -j<NumOfJobs> mode=release bin
```

## 2. INPUT
MultiCFold requires five files to generate models:

	-fasta				: fasta file
	-PSIPRED.txt			: contact map file by DeepMetaPSICOV
	-RaptorX.txt			: contact map file by RaptorX
	-SpotContact.txt			: contact map file by SpotContact
	-TripletRes.txt			: contact map file by TripletRes
	-3mer_frag_set		: fragment library with fragment lenth 3
	-9mer_frag_set		: fragment library with fragment lenth 9
	-flags				: parameter of MultiCFold

## 3. RUN
Please follow the below steps to run MultiCFold:

- Go to the ``"example/"`` folder of MultiCFold.

- Run MultiCFold with the following command:

```
 $> $ROSETTA3/main/source/bin/AbinitioRelax.default.linuxgccrelease @flags
```

- Final model is generated in the current folder.

- ``"score.fsc"``, ``"S_00000001.pdb"`` and ``"default.out"`` can be deleted.

## 4. OUTPUT
Output file of MultiCFold is stored in the ``"example/"`` folder, including final predicted model.

	model_final.pdb


- ``"TMscore"`` in the ``"example/"`` folder can be used to calculate the accuracy of predicted models using the following commands:

```
 $> ./TMscore ./1FCA_A/model_final.pdb ./1FCA_A/input_files/native.pdb
```

## 5. DISCLAIMER
The executable software and the source code of MultiCFold is distributed free of charge 
as it is to any non-commercial users. The authors hold no liabilities to the performance 
of the program.
