DOC=pandoc
DOCFLAGS=--toc --css style/buttondown.css --self-contained
DOCNAME=group4-SDD
DOCOBJ=sections/*/*.md

all: pdf
	
pdf:
	$(DOC) $(DOCFLAGS) $(DOCOBJ) -o ../pdf-outputs/$(DOCNAME).pdf

html:
	$(DOC) $(DOCFLAGS) $(DOCOBJ) -o $(DOCNAME).html

remove_docs:
	rm $(DOCNAME).*
