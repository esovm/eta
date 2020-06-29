#
# $Id: Makefile,v 1.4-hacked 1999/09/29 13:27:55 harveyt Exp harveyt $
#
CFLAGS	= -O
LDFLAGS	= -s
ETA	= ./eta

DISTFILES	= Makefile eta.c hello.eta hello2.eta pip.eta pip2.eta \
		  fact.eta bottles.eta crlf.eta \
		  test-OUTPUT

eta: eta.o
	$(CC) $(LDFLAGS) -o eta eta.o

tar:
	gtar -zcvf eta.tar.gz $(DISTFILES)

uu: tar
	uuencode eta.tar.gz eta.tar.gz > eta.uu

test: $(ETA)
	rm -f OUTPUT
	$(ETA) ../pit/hello.eta >> OUTPUT
	$(ETA) ../pit/hello2.eta >> OUTPUT
	$(ETA) ../pit/pip.eta < OUTPUT >> OUTPUT
	$(ETA) ../pit/pip2.eta < OUTPUT >> OUTPUT
	echo "8" | $(ETA) ../pit/fact.eta >> OUTPUT
	$(ETA) ../pit/bottles.eta >> OUTPUT
	$(ETA) ../pit/crlf.eta >> OUTPUT
	cmp -s OUTPUT test-OUTPUT

clean:
	rm -rf eta.uu eta.tar.gz OUTPUT eta *.[ao]
