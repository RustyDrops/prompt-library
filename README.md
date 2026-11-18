# Prompt Library

A small, growing collection of pre-prompts I actually use — each one
battle-tested against the mistakes AI coding assistants really make,
not just written and hoped for.

## What is a pre-prompt?

A pre-prompt is a block of instructions you paste into an AI chat
(as the system prompt, custom instructions, or the first message)
*before* asking for the thing you actually want. A good one does
three jobs:

1. **Ground truth** — states the facts the model most often gets
   wrong, in a form it can't argue with.
2. **Hard bans** — names the plausible-but-wrong outputs it must
   never produce, with the correct pattern beside each ban.
3. **A self-check** — a silent checklist the model runs on its own
   answer before sending it.

## How to use one

1. Open the prompt file and copy the **FULL VERSION** block.
2. Paste it into your AI tool before your request.
3. Add your request after it, plus any fill-ins the prompt asks for
   (board, firmware version, editor) if you know them.
4. If the model still emits banned code, most of these prompts
   include a one-line recovery phrase — send it and the model
   re-checks its last answer against the bans and rewrites.

Use the **SHORT VERSION** block when the chat is token-tight or the
task is a one-off snippet. It keeps the traps that break things and
drops the coaching.

Specialist prompts are designed to be stacked *after* their general
prompt: general first, specialist second, then your request.

## Index

| Area | Prompt | What it covers |
|------|--------|----------------|
| MicroPython | [Pico 2 W — General](micropython/pico-2w-general-preprompt.md) | MicroPython on the Raspberry Pi Pico 2 W (RP2350): bans, board facts, async, MQTT/BLE basics, output format, self-check |
| MicroPython | [Pico 2 W — Wireless Networking](micropython/pico-2w-wireless-networking.md) | Wi-Fi connect/reconnect, AP mode, MQTT via umqtt, HTTP, sockets, TLS, NTP/RTC |
| MicroPython | [Pico 2 W — Bluetooth LE](micropython/pico-2w-bluetooth-le.md) | aioble and raw `bluetooth`: advertising, IRQ data lifetime, GATT, pairing/security |
| MicroPython | [Pico 2 W — Low Power & Hardware I/O](micropython/pico-2w-low-power-and-io.md) | deepsleep/lightsleep, watchdog, ADC/VSYS, IRQs, timers, PIO, PWM, NeoPixel, E9 inputs |

More areas will be added as prompts earn their place here — a prompt
only lands in this library after it has passed trap tests: baited
requests designed to make a model produce the wrong code, checked
against the prompt's own rules.

## Notes

- These prompts reduce mistakes; they don't eliminate them. Always
  run generated code on real hardware before trusting it.
- Facts in the MicroPython prompts were checked against the official
  MicroPython documentation and Raspberry Pi datasheets.
