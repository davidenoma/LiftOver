
---

# Plink LiftOver Python Script

## Overview
This Python script facilitates lifting of genetic data files (MAP, PED, and DAT formats) from one genome version to another using the `liftOver` tool . 
```bash
wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/liftOver
export PATH=$PATH:/~liftOver PATH

```


The script converts input files to BED format, performs lifting, and converts back to the original format, providing a seamless transition between genome versions.

## Usage
```bash
python liftover_python_umich_update.py -m old.map -p old.ped -d old.dat -o new.prefix
```

## Arguments
- `-m, --map`: Input MAP file containing genetic marker information (required).
- `-p, --ped`: Input PED file containing genotype information (optional).
- `-d, --dat`: Input DAT file containing additional data (optional).
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

## Example
```bash
python liftover_python_umich_update.py -m old.map -p old.ped -d old.dat -o new.prefix
```


