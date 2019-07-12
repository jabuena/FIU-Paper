GRAFFLE_EXPORT = osascript ../.build/graffle2pdf.scr
PPTX_EXPORT = osascript ../.build/pptx-to-pdf.scr
DOCX_EXPORT = osascript ../.build/docx-to-pdf.scr
# To install drawio tool, run the following command (requires nodejs)
#     npm install --global draw.io-export
DRAWIO_EXPORT = drawio
PDFCROP = pdfcrop

.PHONY: images

IMAGE_FILES_GRAFFLE=$(shell find . -name '*.graffle')
IMAGE_FILES_PPTX=$(shell find . -name '*.pptx')
IMAGE_FILES_DOCX=$(shell find . -name '*.docx')
IMAGE_FILES_DRAWIO=$(shell find . -name '*.drawio')

images: $(IMAGE_FILES_GRAFFLE:graffle=pdf) $(IMAGE_FILES_PPTX:pptx=pdf) $(IMAGE_FILES_DOCX:docx=pdf) $(IMAGE_FILES_DRAWIO:drawio=pdf)

%.pdf: %.graffle
	${GRAFFLE_EXPORT} $< $@
	${PDFCROP} $@ $@

%.pdf: %.pptx
	${PPTX_EXPORT} $< $@
	${PDFCROP} $@ $@

%.pdf: %.docx
	${DOCX_EXPORT} $< $@
	${PDFCROP} $@ $@

%.pdf: %.drawio
	${DRAWIO_EXPORT} $< -o $@

clean:
	rm -f $(IMAGE_FILES:graffle=pdf) $(IMAGE_FILES_PPTX:pptx=pdf) $(IMAGE_FILES_DOCX:docx=pdf) $(IMAGE_FILES_DRAWIO:drawio=pdf)
