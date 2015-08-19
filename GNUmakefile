.PHONY:	monop
all:	monop

include monop/Makefrag
monop/%.o:	monop/%.c
	$(CC) $(CFLAGS) $(monop_CFLAGS) $(monop_DEFS) $(BASE_INCS) -Imonop $(monop_INCS) -c $< -o $@
monop/%.i:	monop/%.c
	$(CC) $(CFLAGS) $(monop_CFLAGS) $(monop_DEFS) $(BASE_INCS) -Imonop $(monop_INCS) -E $< -o $@
monop/%.s:	monop/%.c
	$(CC) $(CFLAGS) $(monop_CFLAGS) $(monop_DEFS) $(BASE_INCS) -Imonop $(monop_INCS) -S -fverbose-asm $< -o $@
monop/%.d:	monop/%.c
	./mkdep $< $@ $(CC) $(CFLAGS) $(monop_CFLAGS) $(monop_DEFS) $(BASE_INCS) -Imonop $(monop_INCS)
include  monop/cards.d monop/execute.d monop/getinp.d monop/houses.d monop/jail.d monop/misc.d monop/monop.d monop/morg.d monop/print.d monop/prop.d monop/rent.d monop/roll.d monop/spec.d monop/trade.d
monop/monop:	 monop/cards.o monop/execute.o monop/getinp.o monop/houses.o monop/jail.o monop/misc.o monop/monop.o monop/morg.o monop/print.o monop/prop.o monop/rent.o monop/roll.o monop/spec.o monop/trade.o
include  monop/initdeck.d
monop/initdeck:	 monop/initdeck.o
.PHONY:	monop_clean
monop_clean:
	cd monop && rm -f -- a.out core *.o *.d *.i *.s *.d.tmp  monop initdeck $(monop_CLEANFILES)
.PHONY:	monop_install monop_install-strip monop_installdirs
monop_install:	monop_installdirs
monop_install-strip:
	$(MAKE) monop_install $(DEFS_TO_PASS_STRIP)
monop_installdirs:
	set -e; for d in $(monop_DIRS) /; do mkdir -p $(INSTALL_PREFIX)$$d; done

clean:	monop_clean
