
---

# Plink LiftOver Python Script

## Overview
This Python script facilitates lifting of genetic data files (Plink format MAP, PED) from one Human genome build version to another using the `liftOver` tool . 
It can liftover from easily between multiple builds available. E.g Hg19, Hg18, GRCH36 and others. 

```bash
wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/liftOver
export PATH=$PATH:/~liftOver PATH

```


The script converts input files to BED format, performs lifting, and converts back to the original format, providing a seamless transition between genome versions.

## Usage
```bash
python liftover_python_umich_update.py -m old.map -p old.ped -c chain_file -o new.prefix
```

## Arguments
- `-m, --map`: Input MAP file containing genetic marker information (required).
- `-p, --ped`: Input PED file containing genotype information (optional).
- `-c, --chain`: Liftover Chain File.
- `-o, --prefix`: Prefix for output files (required).

## Functions
1. `usage()`: Prints the usage information of the script.
2. `die(msg)`: Prints error message and exits the script.
3. `myopen(fn)`: Opens a file and handles gzip format if applicable.
4. `map2bed(fin, fout)`: Converts MAP file to BED format.
5. `liftBed(fin, fout, unlifted)`: Lifts BED file using `liftOver` tool.
6. `bed2map(fin, fout)`: Converts BED file back to MAP format.
7. `liftDat(fin, fout)`: Lifts DAT file.
8. `liftPed(fin, fout, fOldMap)`: Lifts PED file.

## Execution
- The script parses command-line arguments.
- Converts MAP to BED format.
- Performs lifting using `liftOver`.
- Converts lifted files back to original formats.

## Dependencies
- Ensure that the `liftOver` tool is installed and accessible in the system path.
- Ensure that you get the appropriate chain file (that conversts one build to another) from https://hgdownload2.soe.ucsc.edu/downloads.html
- Plink genotype files can be recoded from binary (bed, bim and fam) to text (map and ped) formats
```
plink --bfile {prefix} --recode --out {output_file_name}

```
To re-obtain binary formats we do:
```
plink --file {} --recode --make-bed --out {output_file_name}



