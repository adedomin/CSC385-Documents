DOC=pandoc
DOCFLAGS=--toc
DOCNAME=group4-SRS
DOCOBJ=sections/**/*.md

all: pdf
	
pdf:
	$(DOC) $(DOCOBJ) -o $(DOCNAME).pdf $(DOCFLAGS)

docx:
	$(DOC) $(DOCOBJ) -o $(DOCNAME).docx $(DOCFLAGS)

remove_doc:
	rm $(DOCNAME)
