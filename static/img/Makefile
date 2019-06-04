all: exegetic-logo-small.png exegetic-logo-tiny.png

exegetic-logo-small.png: exegetic-logo.png
	convert -antialias -background transparent -scale 10% $< $@

exegetic-logo-tiny.png: exegetic-logo.svg
	convert -antialias -background transparent -scale 5% $< $@
