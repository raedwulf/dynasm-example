Q=@
E=$(Q)echo

CC=cc
LUA=lua
OUT=dynasm_test
CCOPTS=-Wall -Werror -std=c99 -I../
CCOPTS+=-g -O0 -DDEBUG
#CCOPTS+=-O2 -DNDEBUG

DASM_F = backend.h
OBJS   = main.o vm.o recorder.o compile.o


all: $(DASM_F) $(OBJS)
	$(E) "  " $(CC) $(OBJS) "->" $(OUT)
	$(Q)$(CC) $(CCOPTS) -o $(OUT) $(OBJS)

%.h: %.dasc
	$(E) "  DynASM" $<
	$(Q)$(LUA) ../dynasm/dynasm.lua -c $< > $@

%.o: %.c
	$(E) "  " $(CC) $< 
	$(Q)$(CC) $(CCOPTS) -c $< -o $@

clean:
	$(Q)rm -rf $(OUT) *.o *~ backend.h *.dSYM debug.out
