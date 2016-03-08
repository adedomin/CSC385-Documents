DOC=pandoc
DOCFLAGS=--toc --css style/buttondown.css --self-contained
DOCNAME=group4-SRS
DOCOBJ=sections/**/*.md

all: pdf
	
pdf:
	$(DOC) $(DOCFLAGS) $(DOCOBJ) -o $(DOCNAME).pdf

html:
	$(DOC) $(DOCFLAGS) $(DOCOBJ) -o $(DOCNAME).html

remove_docs:
	rm $(DOCNAME).*
