SOURCES=greeter.cpp person.cpp
OBJECTS=$(patsubst %.cpp, %.o, $(SOURCES))


greeter: $(OBJECTS) main.o
	g++ -std=c++17 $^ -o $@

$(OBJECTS): %.o : %.cpp %.hpp   
	g++ -std=c++17 -Wall -Werror -Wextra -pedantic -c $< -o $@

main.o: main.cpp   
	g++ -std=c++17 -Wall -Werror -Wextra -pedantic -c  $< -o $@

.PHONY: clean

clean: 
	rm greater *.o

run:
	./greater

