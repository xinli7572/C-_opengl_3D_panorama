


CC = gcc
CXX = g++ -std=c++11 -lstdc++
LD = g++ -std=c++11  -lstdc++
INC =
LIB =



CFLAGS =  -Wall

INCLUDE= $(INC) -I/usr/src/so/include -I/usr/src/so/include/opencv4 -I/usr/src/so/include/opencv4/opencv2 -I/usr/include/GL -I/usr/src/so/include/opengl -I/usr/local/include/soil2 -I/usr/src/so/include/learnopengl

LIB_PATH = /usr/src/so/lib
LIB_SO =  -lglfw -ldl -lSOIL -lGLEW -lGL -lGLU -lglut -lopencv_core -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_videoio -lavcodec -lavformat -lavutil -lswscale

LO = main.o glad.o


gv: $(LO)
	$(LD) -o gv $(LO) -L$(LIB_PATH) $(LIB_SO)  -Wl,--copy-dt-needed-entries -Wl,-rpath=$(LIB_PATH) -lm -lpthread  /usr/lib/x86_64-linux-gnu/libpthread.a


glad.o: glad.c glad.h
	$(CXX) $(CFLAGS) $(INCLUDE) -c glad.c -o glad.o

main.o: main.cpp
	$(CXX) $(CFLAGS) $(INCLUDE) -c main.cpp -o main.o




clean:
	rm gv *.o
