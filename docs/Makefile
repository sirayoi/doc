BASE_DIR=..
DOC_ROOT=.

DEST_DIR=$(BASE_DIR)/dist
SRC_IMAGES_DIR=$(IMAGES_DIR)
DST_IMAGES_DIR=$(DEST_DIR)/$(IMAGES_DIR)

include $(DOC_ROOT)/asciidoc.mk

HTML_LIST=\
mkdir_and_copy \
$(DEST_DIR)/index.html \
$(DEST_DIR)/sample.html \
$(DEST_DIR)/study/01-00_dynamoDB.html \
$(DEST_DIR)/ff14/01-00_ff14.html \
$(DEST_DIR)/tutorial/01-00_tutorial.html \
$(DEST_DIR)/memo/01-00_devEnv.html \

.PHONY: adoc mkdir_and_copy

adoc: $(HTML_LIST)

mkdir_and_copy:
	mkdir -p $(DEST_DIR)
	-test ! -d $(SRC_IMAGES_DIR) || mkdir -p $(DST_IMAGES_DIR)
	-test ! -d $(SRC_IMAGES_DIR) || cp $(CP_OPTS) $(SRC_IMAGES_DIR)/* $(DST_IMAGES_DIR)/

	mkdir -p $(DEST_DIR)/study
	-test ! -d study/$(IMAGES_DIR) || mkdir -p $(DEST_DIR)/study/$(IMAGES_DIR)
	-test ! -d study/$(IMAGES_DIR) || cp $(CP_OPTS) study/$(IMAGES_DIR)/* $(DEST_DIR)/study/$(IMAGES_DIR)/

$(DEST_DIR)/%.html: %.adoc
	asciidoctor --trace $(AD_OPTS_HTML5_ROUGE) -o "$@" "$<"
  
