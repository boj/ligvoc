# Linux Game Voice Control (LiGVoC)

Inspired by wanting to make strategem commands in Helldivers 2 work with voice.

## Requirements

- Rhasspy: https://github.com/rhasspy/rhasspy - Offline Voice Assistant
- jq: Parses Rhasspy JSON "intents"
- ydotool: Send input to anything
- socat: Easy way to make sockets

## Installation

A `docker-compose.yml` configured to pass pulseaudio input is included in this repo, borrowed from the Rhasspy examples.

Follow the Rhasspy install docs and configure entire setup. Copy relevant `sentences.ini` to `$HONE/.config/rhasspy/profiles/en` and train Rhasspy.

Copy game scripts into profiles location. They generate a shared `command.pipe` FIFO that docker can write to via the `command` script. Run listener script on host, i.e. `bin/helldivers` - this will then handle Rhasspy intents and send relevant input using `ydotool`.
