iftOver Python Script Documentation
Overview
This Python script facilitates lifting of genetic data files (MAP, PED, and DAT formats) from one genome version to another using the liftOver tool. The script converts input files to BED format, performs lifting, and converts back to the original format, providing a seamless transition between genome versions.

Usage
bash
Copy code
python liftover_python_umich_update.py -m old.map -p old.ped -d old.dat -o new.prefix
Arguments
-m, --map: Input MAP file containing genetic marker information (required).
-p, --ped: Input PED file containing genotype information (optional).
-d, --dat: Input DAT file containing additional data (optional).
-o, --prefix: Prefix for output files (required).
Functions
usage(): Prints the usage information of the script.
die(msg): Prints error message and exits the script.
myopen(fn): Opens a file and handles gzip format if applicable.
map2bed(fin, fout): Converts MAP file to BED format.
liftBed(fin, fout, unlifted): Lifts BED file using liftOver tool.
bed2map(fin, fout): Converts BED file back to MAP format.
liftDat(fin, fout): Lifts DAT file.
liftPed(fin, fout, fOldMap): Lifts PED file.
Execution
The script parses command-line arguments.
Converts MAP to BED format.
Performs lifting using liftOver.
Converts lifted files back to original formats.
Dependencies
Ensure that the liftOver tool is installed and accessible in the system path.
Example
bash
Copy code
python liftover_python_umich_update.py -m old.map -p old.ped -d old.dat -o new.prefix
