EXEC_NAME     = rfctl
SRCS          = rfctl.c cul443.c nexa.c ikea.c impulse.c sartano.c
CROSS_COMPILE = 
CC            = $(CROSS_COMPILE)gcc
CFLAGS        = -O2 -W -Wall -Wextra -Wno-unused-parameter -DVERSION=\"0.9\"
LDFLAGS       = 
LIBS          =
OBJS          = $(SRCS:.c=.o)
TARGET_ROOT   =
INSTALL_DIR   = $(TARGET_ROOT)/usr/local/bin

all: $(EXEC_NAME)

OBJS: $(SRCS:.c=.o)
	$(CC) $(CFLAGS) -c $<

$(OBJS): common.h protocol.h

$(EXEC_NAME): $(OBJS)
	$(CC) -o $(EXEC_NAME) $(OBJS) $(LDFLAGS) $(LIBS)

# Install will require root privilegies or sudo
install: $(EXEC_NAME)
	cp $(EXEC_NAME) $(INSTALL_DIR) 	

clean:
	rm -f *.o $(EXEC_NAME) core

distclean:
	rm -f *~
	rm -f *.o $(EXEC_NAME) core

