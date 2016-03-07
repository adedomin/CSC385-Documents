DOC=pandoc
DOCFLAGS=--toc
DOCNAME=group4-SRS.pdf
DOCOBJ=sections/**/*.md

all: doc
	
doc:
	$(DOC) $(DOCOBJ) -o $(DOCNAME) $(DOCFLAGS)

remove_doc:
	rm $(DOCNAME)
