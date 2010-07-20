FILE = elic10

all:
	pdflatex $(FILE)-1.tex
	#
	pdflatex $(FILE)-2.tex
	#
	pdflatex $(FILE)-3.tex

1:
	pdflatex $(FILE)-1.tex

2:
	pdflatex $(FILE)-2.tex

3:
	pdflatex $(FILE)-3.tex

1h:
	cp $(FILE)-1.tex x
	sed -e 's/\]{beamer}/t\,handout\]{beamer}/g' x > y.tex
	pdflatex y.tex
	pdfnup --nup 2x4 --frame true --delta ".5cm .5cm" --scale 0.9 y.pdf  --outfile $(FILE)-1-h.pdf
	rm x*
	rm y.*

2h:
	cp $(FILE)-2.tex x
	sed -e 's/\]{beamer}/t\,handout\]{beamer}/g' x > y.tex
	pdflatex y.tex
	pdfnup --nup 2x4 --frame true --delta ".5cm .5cm" --scale 0.9 y.pdf  --outfile $(FILE)-2-h.pdf
	rm x*
	rm y.*

3h:
	cp $(FILE)-3.tex x
	sed -e 's/\]{beamer}/t\,handout\]{beamer}/g' x > y.tex
	pdflatex y.tex
	pdfnup --nup 2x4 --frame true --delta ".5cm .5cm" --scale 0.9 y.pdf  --outfile $(FILE)-3-h.pdf
	rm x*
	rm y.*

allh:
	make 1h
	make 2h
	make 3h
	pdfjoin $(FILE)-1-h.pdf $(FILE)-2-h.pdf $(FILE)-3-h.pdf --outfile handout.pdf

clean:
	# the '-' before rm is to ignore errors
	-rm *.log *~ *.snm *.out *.nav *.aux *.toc *.vrb
	
pub:
	tar czf pub.tgz $(FILE)-*.pdf handout.pdf Tutorial/tutorial.pdf spill*.pdf *.html
	scp pub.tgz loria.loria.fr:
