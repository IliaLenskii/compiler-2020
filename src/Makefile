SHELL := /bin/bash

FILES=$(wildcard *.lama)
ALL=$(sort $(FILES:.lama=.o))
LAMAC=lamac

all: Parser.o Lexer.o X86.o Stmt.o SM.o Manifest.o
	$(LAMAC) -I . -o lama-impl Driver.lama

Parser.o: Lexer.o

Expr.o: State.o

Stmt.o: State.o Expr.o World.o

SM.o: State.o World.o Util.o Expr.o

X86.o: SM.o Manifest.o

%.o: %.lama
	$(LAMAC) -I . -c $<

variate:
	../variate -leave '\(\* Assignment' -remove '\(\* Implementation' -ending 'End \*\)' *.lama

clean:
	rm -Rf *.s *.o *.i *~ *.html *.sm lama-impl

