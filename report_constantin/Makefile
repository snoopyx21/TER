# Modify the following lines:
NAME=ter
BIBER=YES

# Should stay the same
CFLAGS=
ifeq ($(BIBER), NO)
	override CFLAGS := -bibtex-
endif

.PHONY: all clean $(NAME).pdf 

all: $(NAME)

%.tex: %.raw
	./raw2tex $< > $@
#
%.tex: %.dat
	./dat2tex $< > $@
#
$(NAME): $(NAME).tex
	latexmk $(CFLAGS) -pdf -jobname="$@" -use-make $<
	latexmk -c
#
clean:
	latexmk -C
	@rm -f *run *glo *tdo *blx.bib *bbl *nav *run.xml *snm *synctex.gz *tex.bak *bcf *fdb_latexmk *aux *fls *log *out *ist $(NAME).gl*
#
