#SOURCES := $(wildcard *.md)
SOURCES := 1-python-numpy-tutorial.md
SOURCES += 1-colab-tour.md
SOURCES += 1-print-colab.md
SOURCES += 1-exploratory-data-analysis.md
SOURCES += 1-data-detective.md
SOURCES += 1-explore-hw.md

EXECS := 1-python-numpy-tutorial.md
EXECS += 1-exploratory-data-analysis.md

SOURCES += 2-compute-by-hand.md
SOURCES += 2-regression-r2.md
SOURCES += 2-linear-regression-deep-dive.md
SOURCES += 2-linear-regression-case-study.md
SOURCES += 2-advertising-hw.md

EXECS += 2-compute-by-hand.md
EXECS += 2-regression-r2.md
EXECS += 2-linear-regression-deep-dive.md
EXECS += 2-linear-regression-case-study.md
EXECS += 2-advertising-hw.md

SOURCES += 3-gradient-descent-deep-dive.md
SOURCES += 3-bias-variance-deep-dive.md

EXECS += 3-gradient-descent-deep-dive.md
EXECS += 3-bias-variance-deep-dive.md

SOURCES += 4-model-selection.md
SOURCES += 4-linear-regression-case-study-part-2.md
SOURCES += 4-regularization-deep-dive.md
SOURCES += 4-neural-model-selection-hw.md

EXECS += 4-model-selection.md
EXECS += 4-linear-regression-case-study-part-2.md
EXECS += 4-regularization-deep-dive.md

SOURCES += 5-logistic-regression-in-depth.md
SOURCES += 5-logistic-regression-digits.md
SOURCES += 5-compas-case-study.md
SOURCES += 5-hw-logistic-regression.md

EXECS += 5-logistic-regression-in-depth.md
EXECS += 5-logistic-regression-digits.md
EXECS += 5-compas-case-study.md

SOURCES += 6-k-nearest-neighbors-in-depth.md
SOURCES += 6-decision-trees.md
SOURCES += 6-knn-tree-bias-variance.md
SOURCES += 6-knn-voter-classification-hw.md
SOURCES += 6-knn-voter-classification-2020-hw.md

EXECS += 6-k-nearest-neighbors-in-depth.md
EXECS += 6-decision-trees.md
EXECS += 6-knn-tree-bias-variance.md
EXECS += 6-knn-voter-classification-hw.md

SOURCES += 7-trees-ensembles-in-depth.md
SOURCES += 7-demo-adaboost.md
SOURCES += 7-svm-pre-kernel.md
SOURCES += 7-knn-tree-bias-variance.md
SOURCES += 7-demo-digits-classifiers.md

EXECS += 7-trees-ensembles-in-depth.md
EXECS += 7-demo-adaboost.md
EXECS += 7-svm-pre-kernel.md

SOURCES += 8-svm-with-kernel.md
SOURCES += 8-svm-bias-variance.md
SOURCES += 8-hyperparameter.md

SOURCES += 8-demo-backprop.md
SOURCES += 8-neural-net-demo-draw.md
SOURCES += 8-neural-net-demo-draw-torch.md
SOURCES += 8-lab-neural-net-music-classification.md

EXECS += 8-svm-with-kernel.md
EXECS += 8-svm-bias-variance.md
EXECS += 8-demo-backprop.md

SOURCES += 9-slash-dataset.md
SOURCES += 9-convolutional-neural-networks.md
SOURCES += 9-fine-tune-rock-paper-scissors.md

EXECS += 9-slash-dataset.md
EXECS += 9-convolutional-neural-networks.md



# Convert the list of source files (Markdown files )
# into a list of output files
NBS := $(patsubst %.md,%.ipynb,$(SOURCES))


NBSEXEC := $(patsubst %.md,%.nbconvert.ipynb,$(EXECS))
PDFS := $(patsubst %.md,%.pdf,$(EXECS))

PANDOCFLAGS=--pdf-engine=xelatex\
         -V mainfont='Fira Sans' \
         -V geometry:margin=1in \
         --highlight-style pygments \
	 --listings --variable urlcolor=Maroon \
	 -H style/listings-setup.tex -H style/keystroke-setup.tex -H style/includes.tex

%.ipynb: %.md
	pandoc  --self-contained --wrap=none  $^ -o $@

%.nbconvert.ipynb: %.ipynb
	jupyter nbconvert --to notebook --execute --ExecutePreprocessor.store_widget_state=False --ExecutePreprocessor.allow_errors=True --ExecutePreprocessor.timeout=360 $^

%.pdf: %.nbconvert.ipynb
	pandoc $^ $(PANDOCFLAGS) -o $@

all: $(NBS)

notebooks: $(NBS) 

executed: $(NBSEXEC)

pdfs: $(PDFS)

clean: 
	rm -f *.ipynb

