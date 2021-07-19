DEVICE		= esp8266:esp8266
BOARD		:= thingdev
CC		:= /home/denzuko/.local/bin/arduino-cli
CFLAGS		:= --fqbn $(DEVICE):$(BOARD)
TARGET		:= help
COM1		:= /dev/ttyUSB0
DRIVERS		:= https://arduino.esp8266.com/stable/package_esp8266com_index.json
.PHONY: all help $(TARGET)

deps:
	@-$(CC) config init
	@-$(CC) core update-index  --additional-urls $(DRIVERS)
	@-$(CC) core install --additional-urls $(DRIVERS) $(DEVICE)

all: deps upload

help:
	@$(CC) $@

upload: $(TARGET)
	@sudo $(CC) upload -p $(COM1) $(CFLAGS) $(TARGET)

SDAPServer:
	@$(CC) compile $(CFLAGS) $@

SDAPServerCaptive:
	@$(CC) compile $(CFLAGS) $@
