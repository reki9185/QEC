gurobi_path = /opt/gurobi952/linux64
# gurobi_path = /home/student11/gurobi903/linux64 # on server

all: a.out

a.out: main.cpp Network/Node/Node.o Network/Channel/Channel.o Path/Path.o Network/Graph/Graph.o Algorithm/AlgorithmBase/AlgorithmBase.o Algorithm/Greedy/Greedy.o Algorithm/QCAST/QCAST.o Request/Request.o config.o Algorithm/REPS/REPS.o
	g++ -fopenmp -g -Wall -Wextra main.cpp Network/Node/Node.o Network/Channel/Channel.o Path/Path.o Network/Graph/Graph.o Algorithm/AlgorithmBase/AlgorithmBase.o Algorithm/Greedy/Greedy.o Algorithm/QCAST/QCAST.o Request/Request.o config.o Algorithm/REPS/REPS.o -I$(gurobi_path)/include/ -L$(gurobi_path)/lib -lgurobi_c++ -lgurobi95 -lm 
	
# qcast.out: Network/Node/Node.o Network/Channel/Channel.o Path/Path.o Network/Graph/Graph.o Algorithm/AlgorithmBase/AlgorithmBase.o
Network/Node/Node.o: Network/Node/Node.cpp Network/Node/Node.h config.h
	g++ -c -g -Wall -Wextra Network/Node/Node.cpp Network/Node/Node.h config.h
	mv Node.o Network/Node/Node.o

Network/Channel/Channel.o: Network/Channel/Channel.h Network/Channel/Channel.cpp config.h
	g++ -c -g -Wall -Wextra Network/Channel/Channel.h Network/Channel/Channel.cpp config.h
	mv Channel.o Network/Channel/Channel.o 

Path/Path.o: Path/Path.cpp Path/Path.h config.h
	g++ -c -g -Wall -Wextra Path/Path.cpp Path/Path.h config.h
	mv Path.o Path/Path.o

Network/Graph/Graph.o: Network/Graph/Graph.cpp Network/Graph/Graph.h config.h
	g++ -c -g -Wall -Wextra Network/Graph/Graph.cpp Network/Graph/Graph.h config.h
	mv Graph.o Network/Graph/Graph.o

Request/Request.o: Request/Request.cpp Request/Request.h config.h
	g++ -c -g -Wall -Wextra Request/Request.cpp Request/Request.h config.h
	mv Request.o Request/Request.o

Algorithm/AlgorithmBase/AlgorithmBase.o: Algorithm/AlgorithmBase/AlgorithmBase.h Algorithm/AlgorithmBase/AlgorithmBase.cpp config.h
	g++ -c -g -Wall -Wextra Algorithm/AlgorithmBase/AlgorithmBase.h Algorithm/AlgorithmBase/AlgorithmBase.cpp config.h
	mv AlgorithmBase.o Algorithm/AlgorithmBase/AlgorithmBase.o

Algorithm/Greedy/Greedy.o: Algorithm/Greedy/Greedy.h Algorithm/Greedy/Greedy.cpp config.h
	g++ -c -g -Wall -Wextra Algorithm/Greedy/Greedy.h Algorithm/Greedy/Greedy.cpp config.h
	mv Greedy.o Algorithm/Greedy/Greedy.o

Algorithm/QCAST/QCAST.o: Algorithm/QCAST/QCAST.h Algorithm/QCAST/QCAST.cpp config.h
	g++ -c -g -Wall -Wextra Algorithm/QCAST/QCAST.h Algorithm/QCAST/QCAST.cpp config.h
	mv QCAST.o Algorithm/QCAST/QCAST.o

Algorithm/REPS/REPS.o: Algorithm/REPS/REPS.h Algorithm/REPS/REPS.cpp config.h
	g++ -c -g -Wall -Wextra Algorithm/REPS/REPS.h Algorithm/REPS/REPS.cpp config.h -m64 -I$(gurobi_path)/include/  -L$(gurobi_path)/lib -lgurobi_c++ -lgurobi95 -lm 2>warning.txt
	grep -e opt/gurobi952/linux64/include/gurobi_c++.h -e GRB  -e addConstr -v warning.txt
	mv REPS.o Algorithm/REPS/REPS.o

config.o:	config.h config.cpp
	g++ -c -g config.h config.cpp
check_node: Node/Node.o Node/Node_test.cpp
	g++ -g -Wall -Wextra Node/Node_test.cpp Node/Node.o -o node_check.out

check_channel: Node/Node.o Channel/Channel.o Channel/Channel_test.cpp
	g++ -g -Wall -Wextra Node/Node.o Channel/Channel.o Channel/Channel_test.cpp -o channel_check.out


clean:
	rm -f a.out check_node.out channel_check.out
	rm -f Network/Node/Node.o Network/Node/Node.h.gch
	rm -f Network/Channel/Channel.o Network/Channel/Channel.h.gch
	rm -f Path/Path.o Path/Path.h.gch
	rm -f Network/Graph/Graph.o Network/Graph/Graph.h.gch
	rm -f Request/Request.o Request/Request.h.gch