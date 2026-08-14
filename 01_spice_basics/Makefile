NGSPICE = ngspice_con.exe

CIRCUIT_DIR = circuits
LOG_DIR = logs

CKT_FILES := $(wildcard $(CIRCUIT_DIR)/*.ckt)
LOG_FILES := $(patsubst $(CIRCUIT_DIR)/%.ckt,$(LOG_DIR)/%.log,$(CKT_FILES))

.PHONY: all clean list

all: $(LOG_FILES)

$(LOG_DIR):
	mkdir $(LOG_DIR)

$(LOG_DIR)/%.log: $(CIRCUIT_DIR)/%.ckt | $(LOG_DIR)
	$(NGSPICE) -b $< > $@ 2>&1

list:
	@echo Circuits:
	@for %%f in ($(CKT_FILES)) do @echo %%f

clean:
	del /Q "$(LOG_DIR)\*.log"