# Foreword

If you encounter any problems while following these steps, however minor, please submit an issue report [here](https://github.com/nikothomas/FjordPhytoIssues/issues). It's greatly appreciated! Acknowledgements to the [Galaxy Project](https://galaxyproject.org),[q2galaxy](https://github.com/qiime2/q2galaxy), and [Allen Lab](https://allen.physics.ucsd.edu) for creating the tools to follow.

# Requirements and Installations

This process will require the terminal to be accessible as well as an internet connection.
We will be installing the following resources:

- [Miniconda](https://docs.anaconda.com/free/miniconda/index.html) 
- [Qiime2](https://qiime2.org) 
- [i5_demultiplexer](https://github.com/nikothomas/i5_index_demultiplex) 

And visiting this website:

- [Galaxy Website](http://138.128.245.9:8080)

# Install miniconda

1. If you already have miniconda installed you can skip this step. To check if it is already installed, open your terminal and run the following command:

	```
	conda init
	```

2. If your computer does not recognize the command click on the link for your operating system and chipset, open the downloaded file, and install the software.
	- [[#How do I check what chip I have on MacOS? | How do I check what chip I have?]]

<center>

| OperatingSystem   |        Link                                                                                                                  |
|--------------------|:--------------------------------------------------------------------------|
| Windows                  | [Miniconda3 Windows 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe)                         |
| MacOS Intel             | [Miniconda3 macOS Intel x86 64-bit pkg](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg)|
| MacOS M1                | [Miniconda3 macOS Apple M1 64-bit pkg](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.pkg)                           |
| Linux                          | [Miniconda3 Linux 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh)                                 |
| Linux                          | [Miniconda3 Linux-aarch64 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh)                                |
| Linux                          | [Miniconda3 Linux-s390x 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-s390x.sh)                                    |

</center>

# Qiime2 Setup

1. If you already have qiime2-2022.11 installed you can skip this step. To check if it is already installed, open your terminal and run the following command:

	```terminal
	conda env activate qiime2-2022.11
	```

	If it's already installed then qiime2-2022.11 should now show up next to your username, here is an example:

	```Example
	(qiime2-2022.11) nik@Nikolass-MBP my_folder % 
	```

2. Otherwise open your terminal and run the following command:

	```terminal
	conda install wget
	```

3. Find the list below that matches your operating system, and run the commands in your terminal.

	###### Mac Intel Chip ([How do I check what chip I have?](#Appendix))
	
		wget https://data.qiime2.org/distro/core/qiime2-2022.11-py38-osx-conda.yml

		conda env create -n qiime2-2022.11 --file qiime2-2022.11-py38-osx-conda.yml

		rm qiime2-2022.11-py38-osx-conda.yml
	
	###### Mac M1 Chip ([How do I check what chip I have?](#Appendix))
	
		wget https://data.qiime2.org/distro/core/qiime2-2022.11-py38-osx-conda.yml
		
		CONDA_SUBDIR=osx-64 conda env create -n qiime2-2022.11 --file qiime2-2022.11-py38-osx-conda.yml
		
		conda activate qiime2-2022.11
		
		conda config --env --set subdir osx-64
		
		rm qiime2-2022.11-py38-osx-conda.yml

	###### Windows
		
		wget https://data.qiime2.org/distro/core/qiime2-2022.11-py38-linux-conda.yml
		
		conda env create -n qiime2-2022.11 --file qiime2-2022.11-py38-linux-conda.yml
		
		rm qiime2-2022.11-py38-linux-conda.yml

	###### Linux
		
		wget https://data.qiime2.org/distro/core/qiime2-2022.11-py38-linux-conda.yml
		
		conda env create -n qiime2-2022.11 --file qiime2-2022.11-py38-linux-conda.yml
		
		rm qiime2-2022.11-py38-linux-conda.yml

# Download and Run the Demultiplexer

This demultiplexer is based heavily on the one on the Allen Lab github page. To see their repo click [here](https://github.com/allenlab/i5_index_demultiplex).

1. Click on this link to download the demultiplexer: [Demultiplexer](https://github.com/nikothomas/i5_index_demultiplex/archive/refs/tags/v0.0.2.zip) 
<br>
2. Then open the downloaded file. You will see a screen that looks like this:

![[Screenshot 2024-05-09 at 7.33.36 PM.png]]

3. Drag your barcode file in tsv format to the Metadata folder. Click [here](#Appendix) for a barcode file example.
<br>
4. Drag your i7 demultiplexed samples into the Raw Sequences folder, these should have a filename like *DNA_18SV9_Group_1_S1_L001_R1_001.fastq*.
<br>
5. Open your terminal and type in **but do not run the following command** (you need to type 'cd' then hit your spacebar).

	```
	cd 
	```

6. Drag the i5_index_demultiplex-0.0.2 folder that you downloaded, which now contains your metadata and the samples you want to demultiplex, into your terminal window. Your terminal should look something like this after you drag and drop it:

	```
	(base) nik@Nikolass-MBP ~ % cd /Users/nik/Downloads/i5_index_demultiplex-0.0.2
	```

7. Hit the enter/return button. You should see something like this now:

	```
	(base) nik@Nikolass-MBP i5_index_demultiplex-0.0.2 %
	```

8. Now run this command

	```
	cd ./i5_index_demultiplex
	```

9. Now run the demultiplexer with the following commands:

	```
	conda activate qiime2-2022.11
	```
	
	```
	python ./run_demultiplex.py
	```

10. You will now see a progress bar, once the program is complete you will find your demultiplexed samples in the Demultiplexed Sequences folder.

# Using FjordPhyto Galaxy

We have our own private Galaxy server, to find out more about the Galaxy project click [here](https://galaxyproject.org).
This server is running an instance of q2galaxy developed by the qiime2 team, see their repo [here](https://github.com/qiime2/q2galaxy)
1. To open the FjordPhyto Galaxy website follow this [link](http://138.128.245.9:8080).
<br>
2. Register a Galaxy account.
<br>
###### Secure Your Data 

Although the website is running on a private server, anyone with the link can access the site so it's important to set your data to private by default. You only need to do this once. [[#Make Private Datasets Private By Default | Video Tutorial]]

1. Click the **user** button on top of the website
<br>
2. Click on the **preferences** under the dropdown menu
<br>
3. Click **Make all data private** and accept
<br>
4. Select **Set Dataset Permissions for New Histories**
<br>
5. Set dataset access to yourself and then click **save permission**
<br>
###### Upload Your Data

1. Upload your dataset by clicking Upload Data .
 <br>
2. Select 'Collection' 
<br>
3. Open the Demultiplexed Samples folder which we created in [[# Download and Run the Demultiplexer | this]]  step. 
<br>
4. Select all of the files in this folder and drag them into the dropbox on the website.
<br>
5. Do not close the upload window while the files are uploading.
<br>
6. Once all of your files are uploaded, click 'Build' to make your collection.
<br>
###### Processing In Galaxy

Now you can use an already setup workflow to process your data, or if you're feeling brave you can explore Galaxy yourself!
###### 16S Workflow Instructions

1. In order to run the 16S workflow you'll also need to upload a Silva Sequence and Silva Taxonomy file (use the default upload files option) which can be found at these links:
	-  [Silva Sequence](https://data.qiime2.org/2022.8/common/silva-138-99-seqs.qza)
	-  [Silva Taxonomy](https://data.qiime2.org/2022.8/common/silva-138-99-tax.qza)
<br>
2. You can find the 16S workflow at this link: [16S workflow](http://138.128.245.9:8080/u/admin/w/16s-pipeline)
<br>
3. Click the run icon in the top right of the workflow page
<br>
4. Your jobs will initialize, this will take awhile so note that you don't need to stay on the galaxy website for the jobs to run, you can come back and check on their progress anytime.

5. In order to view any .qvz files generated by the workflow you currently need to download them from the website and drop them into this [vizualizer](https://view.qiime2.org).
<br>
###### 18S Workflow Instructions

1. None yet, but if you create your own please let me know!
<br>
###### Note for those who don't use the predefined workflows:

- I have adjusted the files to be named according to the Casava 1.8 standard so they can be easily imported into qiime2. If you decide to explore for yourself select the SampleData\[PairedEndSequencesWithQuality\] and 'Casava one eight single lane per sample' format options for your import into qiime2.


## Appendix:
###### How do I check what chip I have on MacOS?

- If you have a mac you can check what chip you have by clicking the  icon in the top left of your screen, and then clicking "about this mac". If your mac says M1 or M2 you have an M1 or M2 chip, otherwise you have an Intel chip.

###### Barcode File Example

```
name    file_name  idx1   seq1   idx2   seq2  
ManifestSample_001  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA501  ATCGTACG  
ManifestSample_002  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA502  ACTATCTG  
ManifestSample_003  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA503  TAGCGAGT  
ManifestSample_004  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA504  CTGCGTGT  
ManifestSample_005  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA505  TCATCGAG  
ManifestSample_006  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA506  CGTGAGTG  
ManifestSample_007  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA507  GGATATCT  
ManifestSample_008  DNA_18SV9_Group_1_S1_L001  SA701  CGAGAGTT   SA508  GACACCGT  
ManifestSample_009  DNA_18SV9_Group_2_S2_L001  SA702  GACATAGT   SA501  ATCGTACG  
ManifestSample_010  DNA_18SV9_Group_2_S2_L001  SA702  GACATAGT   SA502  ACTATCTG
```

###### Make Private Datasets Private By Default

![[new-hist-perm.gif]]

