all: compile execute run_gprof

compile:
	g++ example.cpp -o example -pg

execute:
	./example 

run_gprof:
	gprof example > example.txt


clean:
	rm example gmon.out