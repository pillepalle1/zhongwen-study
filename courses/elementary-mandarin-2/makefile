.PHONY: clean all pages text

all: notes.org preview.pdf slides.pdf review.pdf pages text

text: pages
	find .pdf-pages/ -name "*.pdf" -exec pdftotext {} \;
	mv .pdf-pages/*.txt .text-pages/

pages: preview.pdf slides.pdf review.pdf
	pdfseparate preview.pdf .pdf-pages/preview-%04d.pdf
	pdfseparate slides.pdf .pdf-pages/slides-%04d.pdf
	pdfseparate review.pdf .pdf-pages/review-%04d.pdf

preview.pdf: preview
	pdfunite preview/*.pdf preview.pdf

slides.pdf: slides
	pdfunite slides/*.pdf slides.pdf

review.pdf: review
	pdfunite review/*.pdf review.pdf

notes.org: notes
	cat notes/*.org >> notes.org

clean:
	rm -f .pdf-pages/*
	rm -f .text-pages/*
	rm -f notes.org
	rm -f preview.pdf
	rm -f slides.pdf
	rm -f review.pdf
