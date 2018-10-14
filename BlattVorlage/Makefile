# Rundum-Sorglos Paket für Übungszettel
# 2017, Philip Bleicker
all: build/blatt.pdf clean

############################################################
# Anpassbare Optionen:
#
# Präfix der PDF-Dokumente. Struktur ist: Präfix_BlattXY.pdf
Prefix = TP1_WS1819
############################################################

# Automatisch ermittelter Name
Filename = $(addprefix $(Prefix)_, $(addsuffix .pdf,$(notdir $(CURDIR))))
# LaTeX-Optionen, um unnötiges Generve auszuschalten
TeXOptions = --interaction=nonstopmode \
			 --halt-on-error \
			 --output-directory=build

build/blatt.pdf: uebung.sty blatt.tex Contents/*.tex | build
	# Optionaler doppelter Aufruf verhindert Darstellungsfehler
	#pdflatex $(TeXOptions) blatt.tex;
	pdflatex $(TeXOptions) blatt.tex

build:
	mkdir -p build/

clean:
	mv build/blatt.pdf $(Filename) # PDF bewegen und umbenennen
	rm -f *log # Globales Log löschen
	rm -rf build # Build
ifeq ($(OS),Windows_NT) # PDF anzeigen
	start $(Filename)
else
ifeq ($(shell uname -s),Linux)
	xdg-open $(Filename)
endif
ifeq ($(shell uname -s),Darwin)
	open $(Filename)
endif
endif
