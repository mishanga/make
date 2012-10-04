# Синтетический мейкфайл с примерами для семинара про GNU make

# Дефолтная цель (пустая)
.PHONY: all
all:
	$(info All done!)


# Пример описания целей, пререквизитов и команд
a.txt b.txt: c.txt d.txt
	cp c.txt a.txt
	cp d.txt b.txt

c.txt d.txt:
	touch $@


# Пример цели clean
.PHONY: clean
clean::
	@rm -f *.txt
	$(info Cleaning is done!)
