include definitions.mk

all: ucode.bin flashpatches.c

ucode.bin: $(RAM_FILE) definitions.mk
	@printf "\033[0;31m  EXTRACTING UCODE\033[0m\n"
	$(Q)$(NEXMON_ROOT)/buildtools/ucode_extractor/ucodeext -r $< -b $(UCODESTART) -l $(UCODESIZE) -o $@

flashpatches.c: $(RAM_FILE) definitions.mk
	@printf "\033[0;31m  EXTRACTING FLASHPATCHES\033[0m\n"
	$(Q)printf "#include <patcher.h>\n\n" > flashpatches.c
	$(Q)$(NEXMON_ROOT)/buildtools/flash_patch_extractor/fpext -r $< -s $(RAMSTART) -b $(FP_CONFIG_ORIGBASE) -e $(FP_CONFIG_ORIGEND) >> $@

clean:
	@printf "\033[0;31m  CLEANING\033[0m\n"
	$(Q)rm -f ucode.bin flashpatches.c
