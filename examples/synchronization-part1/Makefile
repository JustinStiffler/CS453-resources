

# Recognize files with .class and .java extensions
.SUFFIXES: .class .java
.java.class:
	javac $(JFLAGS) $<

JFLAGS=

CC=gcc
#CFLAGS=-I. -g -Wall
CFLAGS=-I. -O  -Wall
LDFLAGS=-lpthread

PROGS= threads-hello-synchronized mycp threads-sem-cp threads-dbl-buf threads-cp checkpoint counting\
		threads-barrier threads-id bad-bank-balance safe-bank-balance java-progs randomqueues-test\
	    tdbc tsc mergesort-progs

all: $(PROGS)


threads-hello-synchronized: threads-hello-synchronized.o 
	$(CC) $(CFLAGS) threads-hello-synchronized.o -o $@ $(LDFLAGS)

mycp: mycp.o
	gcc mycp.o -o mycp

counting: counting.o
	$(CC) counting.o -o counting

threads-barrier: $(OBJS) threads-barrier.o
	$(CC) $(CFLAGS)  $(OBJS)  $< -o $@ $(LDFLAGS)

threads-cp: $(OBJS) threads-cp.o
	$(CC) $(CFLAGS)  $(OBJS)  threads-cp.o -o $@ $(LDFLAGS)

threads-sem-cp:  threads-sem-cp.o
	$(CC) $(CFLAGS)  threads-sem-cp.o -o tsc $(LDFLAGS)

threads-dbl-buf: $(OBJS) threads-dbl-buf.o
	$(CC) $(CFLAGS)  $(OBJS) threads-dbl-buf.o -o tdbc $(LDFLAGS)


threads-id:	threads-id.o
	$(CC) $(CFLAGS)  threads-id.o -o $@ $(LDFLAGS)

randomqueues-test: randomqueues-test.o
	$(CC) $(CFLAGS)  -o $@ $< $(LDFLAGS)

bad-bank-balance: bad-bank-balance.o
	$(CC) $(CFLAGS)  -o $@ $< $(LDFLAGS)

safe-bank-balance: safe-bank-balance.o
	$(CC) $(CFLAGS)  -o $@ $< $(LDFLAGS)

checkpoint: checkpoint.o 
	$(CC) $(CFLAGS) checkpoint.o  -o $@ $(LDFLAGS)

java-progs: 
	cd java; make

mergesort-progs: 
	cd mergesort/; make

clean:
	/bin/rm -f *.o $(PROGS)
	cd java; make clean
	cd mergesort/; make clean
