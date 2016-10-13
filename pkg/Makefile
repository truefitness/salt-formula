SHELL:=/bin/bash -s extglob
APP=salt
FORMULANAME=true-$(APP)-formula
SRC=src
REPO=$(SRC)/$(APP)-formula
DEST=$(shell pwd)/build/srv/formulas
BUILD=build
QUEUE=queue


all: clone update
	@echo "make clone - clone git repo  into $(REPO)"
	@echo "make update - pull latest from git $(repo)"
	@echo "make install - Install into $(DEST)"

clone:
	(cd $(SRC); git clone https://github.com/truefitness/salt-formula.git )

update:
	( cd $(REPO); git fetch ; git pull )

srcdir:
	-@mkdir -p $(REPO)
	$(shell tar xf - -c --exclude-vcs --exclude='*pkg*' | ( cd ${REPO} && tar xbf -) )
pkg:
	cd $(SRC) ;\
	dpkg-buildpackage -uc -us -tc
	-@mkdir -p $(QUEUE)
	mv $(FORMULANAME)_* $(QUEUE)

clean:
	[ ! -d $(REPO) ] || rm -rf $(REPO)
	rm -rf $(QUEUE)
