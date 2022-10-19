# options
B25	= -DB25

ifdef B25
  B25_OBJS = B25Decoder.o
endif

CXX	= g++
CXXFLAGS = -O2 -march=native -std=c++17 -g -Wall -pthread -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 $(B25)
CC	= gcc
CFLAGS  = -O2 -march=native -g -Wall -pthread -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 $(B25)
OBJS	= fsusb2n.o usbops.o em2874-core.o ktv.o IoThread.o tssplitter_lite.o $(B25_OBJS)
LIBS	= -lpthread -lstdc++fs -laribb25
TARGET	= recfsusb2n

all: $(TARGET)

clean:
	rm -f $(OBJS) $(B25_OBJS_EXT) $(TARGET)

$(TARGET): $(OBJS) $(B25_OBJS_EXT)
	$(CXX) -o $(TARGET) $(OBJS) $(B25_OBJS_EXT) $(LIBS)

depend:
	$(CXX) -MM $(OBJS:.o=.cpp) > Makefile.dep

-include Makefile.dep

