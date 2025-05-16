
SOURCES:=u212.pld u213.pld u701.pld u714.pld u901.pld u902.pld

SRC := $(SOURCES:%.pld=source/%.pld)
JED := $(SOURCES:%.pld=jedec/%.jed)
CUPL = LIBCUPL=C:\\Wincupl\\Shared\\cupl.dl WINEDEBUG=-all wine c:Wincupl/Shared/cupl.exe
#OPT  = m1

all: $(JED)

jedec/%.jed: source/%.pld Makefile util/jedcrc
	$(CUPL) -j$(OPT) $(LIBCUPL) $<
	mv $(<:source/u%.pld=source/U%.jed) $(<:source/%.pld=jedec/%.jed)
	util/fixup_jed.sh $< $(<:source/%.pld=jedec/%.jed)

util/jedcrc : util/jedcrc.c

clean:
	rm -f util/jedcrc
distclean: clean
	rm -f $(JED)

