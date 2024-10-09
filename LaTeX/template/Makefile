# TODO: Replace with the actual project name
NAME = "PROJECT_NAME"
# TODO: Replace with the actual project root file
TARGET = main.tex

OUTPUT_DIR = "output"
AUX_DIR = ".aux"

LATEX_CMD = latexmk
LATEX_FLAGS = \
	--verbose \
	-Werror \
	-f \
	-file-line-error \
	-interaction=nonstopmode \
	-jobname=$(NAME) \
	-pdf \
	-output-directory=$(OUTPUT_DIR) \
	-synctex=1 \
	-time

ifeq ($(OS), Windows_NT)
	LATEX_FLAGS += -aux-directory=$(AUX_DIR)
# else
# 	LATEX_FLAGS += -emulate-aux-dir
endif

all: build

build:
	$(LATEX_CMD) $(LATEX_FLAGS) $(TARGET)

preview:
	$(LATEX_CMD) $(LATEX_FLAGS) -pvc -view=none $(TARGET)

clean:
	$(LATEX_CMD) $(LATEX_FLAGS) -c

clean-all:
	$(LATEX_CMD) $(LATEX_FLAGS) -C

.PHONY: all build preview clean clean-all
