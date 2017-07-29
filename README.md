# makefile_Bash_generator
A Shell script that generate the makefile of a C program

In the case that you have all C files in a folder, you put this script in the directory and it generate a makefile with all dependances automated, with this pattern for example: 

===============================
.PHONY: clean
.SUFFIXES:

prog: calc.o main.o show.o
	gcc calc.o main.o show.o -o prog
calc.o: calc.c calc.h
	gcc -c calc.c
main.o: main.c show.h calc.h
	gcc -c main.c
show.o: show.c show.h calc.h
	gcc -c show.c
clean:
	rm -f *.o prog
  ===============================
  
  by default, the name of the final exec file is 'prog'
  If you want another name, you just do
  ./gen_makefile yourNameOfYourAwesomeProgram
