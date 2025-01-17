# OpticNerveHead_DBiT
Processing for 25um DBiT data on optic nerve head samples from open angle glaucoma and control samples


```
OpticNerveHead_DBiT
|	README.md
|	.gitignore
|
|_______Analysis
|	|	Environment.txt
|	|	spatial_barcodes_index.txt
|	|
|	|_______Python
|	|	| fastq_process.py
|	|
|	|_______R
|	|	| (Code goes here)
|	|
|	|_______Scripts
|	|	| BuildSTARreference.sh
|	|	| CellRangerAlign.sh  
|	|	| converttoname_mmd.sh
|	|	| GetDataFromArchive.s
|	|	| SendDataToArchive.sh
|	|	| stpipeline_submit.sh
|	|
|	|_______Results
|		| (Output goes here)
|	
|_______Docs
	|	
	|	InfoAboutProject.txt

```

Complete the directory setup with:

```
mkdir data
mkdir data/raw
mkdir data/processed
mkdir ReferenceFiles
```


- To run from raw data you need to get [st_pipeline](https://github.com/jfnavarro/st_pipeline) installed.  See [Analysis/Environment.txt](Analysis/Environment.txt).

     - [st_pipeline usage manual](https://htmlpreview.github.io/?https://raw.githubusercontent.com/jfnavarro/st_pipeline/master/docs/manual.html)

- Then you need to build a reference for [STAR aligner](https://github.com/alexdobin/STAR). See [Analysis/Scripts/BuildSTARreference.sh](Analysis/Scripts/BuildSTARreference.sh).

- Put your raw ``*.fastq.gz`` files in ``data/raw``.  

- Read 2 from the DBiT experiments needs to be preprocessed with ``Analysis/Python/fastq_process.py``:

    ```
    python Analysis/Python/fastq_process.py -i data/raw/MyFastqFile_R2.fastq.gz
    ```

- Run st_pipeline with

   ```
   sbatch Analysis/Scripts/stpipeline_submit.sh
   ```

