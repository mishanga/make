# Синтетический мейкфайл с примерами для семинара про GNU make

simple = a.txt b.txt c.txt d.txt

# Дефолтная цель (пустая)
.PHONY: all
all: $(simple)
	$(info Всё готово!)


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
	$(info ==> Всё чисто!)


# Примеры переменных
var1 := $(shell ls *.txt) # немедленное вычисление
var2 = $(shell ls *.txt) # отложенное вычисление, в момент первого вызова
var3 ?= val3    val2    val1 # условное вычисление
var4 = $(foreach val,$(var3),$(val))
var4 += $(sort $(var3)) # добавление

.PHONY: vars var2
vars: $(simple)
	$(info ==> Переменные)
	$(info var1: $(var1))
	$(info var1 массив: $(foreach val,$(var1),"$(val)"))
	$(info var2: $(var2))
	$(info var3: $(var3))
	$(info var4: $(var4))


# Пример автоваров — контекстных переменных
.PHONY: autovars
autovars: $(foreach file,$(simple),$(shell pwd)/$(file))
	$(info ==> Автовары)
	$(info Цель: $@)
	$(info Пререквизиты: $^)
	$(info Первый пререквизит: $<)
	$(info Директория: $(<D))
	$(info Имена файлов: $(^F))


# Функции
full_path = $(shell pwd)/$(1) # возвращает полный путь до файла

.PHONY: func
func: $(simple)
	$(info ==> Вызов функции)
	$(foreach file,$^,$(info $(file): $(call full_path,$(file))))


# Хитрые переменные
comma := ,
empty :=
space := $(empty) $(empty)
foo := a b c
bar := $(subst $(space),$(comma),$(foo))

.PHONY: hacks
hacks:
	$(info ==> Хитрые переменные)
	$(info comma: '$(comma)')
	$(info empty: '$(empty)')
	$(info space: '$(space)')
	$(info bar: '$(bar)')
