DIR_INC = ./inc/
DIR_SRC = ./src
DIR_LIB = ./lib
DIR_OBJ = ./obj
DIR_BIN = ./bin

SRC = $(wildcard ${DIR_SRC}/*.c ${DIR_LIB}/*.c)  
OBJ = $(patsubst %.c,${DIR_OBJ}/%.o,$(notdir ${SRC})) 
TARGET = main

BIN_TARGET = ${DIR_BIN}/${TARGET}

#CC =arm-none-linux-gnueabi-gcc -lrt
#CC =gcc -lrt
CC = arm-linux-gcc -lrt
#CFLAGS = -Wall -Wno-pointer-sign -Wunused-value -g -I /rootfs/include/libxml2  ${DIR_INC}   

CFLAGS = -g -Wno-pointer-sign -Wunused-value -I /rootfs/include/libxml2 ${DIR_INC}   

#CFLAGS = -g -I ${DIR_INC}   


${BIN_TARGET}:${OBJ}
	$(CC) $(OBJ)  -o $@ -lpthread -L /rootfs/lib/ -lm 

${DIR_OBJ}/%.o:${DIR_SRC}/%.c
	$(CC) $(CFLAGS) -c  $< -o $@  

${DIR_OBJ}/%.o:${DIR_LIB}/%.c
	$(CC) $(CFLAGS) -c  $< -o $@  

.PHONY:clean
clean:
	cd obj; rm -rf *.o;cd ../bin; rm *


