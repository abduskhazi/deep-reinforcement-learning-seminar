# Configuration
MASTERTEX = master.tex
SIDETEX = content.tex preamble.tex
BIB = literature.bib

TEXOPTS="--synctex=1"

# Preparation
ALLTEX=$(MASTERTEX) $(SIDETEX)

# Rules
all:$(MASTERTEX:.tex=).pdf

%.pdf:	%.tex $(ALLTEX) $(BIB)
	pdflatex $(TEXOPTS) $<
	bibtex $*.aux	
	pdflatex $(TEXOPTS) $<
	pdflatex $(TEXOPTS) $<

clean:
	rm -f $(ALLTEX:.tex=.aux) $(ALLTEX:.tex=.pdf) $(ALLTEX:.tex=.log) $(ALLTEX:.tex=.blg) $(ALLTEX:.tex=.bbl) $(ALLTEX:.tex=.out) $(ALLTEX:.tex=.toc) $(ALLTEX:.tex=.synctex.gz) $(BIB).bak


