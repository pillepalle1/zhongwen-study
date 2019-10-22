.PHONY: clean all pages text

all: preview.pdf slides.pdf review.pdf handouts.pdf pages text

text: pages
	find .pdf-pages/ -name "*.pdf" -exec pdftotext {} \;
	mv .pdf-pages/*.txt .text-pages/

pages: preview.pdf slides.pdf review.pdf
	pdfseparate preview.pdf .pdf-pages/preview-%04d.pdf
	pdfseparate slides.pdf .pdf-pages/slides-%04d.pdf
	pdfseparate review.pdf .pdf-pages/review-%04d.pdf
	pdfseparate handouts.pdf .pdf-pages/handouts-%04d.pdf

preview.pdf: preview
	pdfunite preview/*.pdf preview.pdf

slides.pdf: slides
	pdfunite slides/*.pdf slides.pdf

review.pdf: review
	pdfunite review/*.pdf review.pdf

handouts.pdf: handouts
	pdfunite handouts/*.pdf handouts.pdf

clean:
	rm -f .pdf-pages/*
	rm -f .text-pages/*
	rm -f preview.pdf
	rm -f slides.pdf
	rm -f review.pdf
	rm -f handouts.pdf
