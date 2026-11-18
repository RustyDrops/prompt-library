# MicroPython Prompts — Raspberry Pi Pico 2 W

Pre-prompts that make an AI coding assistant produce correct
MicroPython for the **Raspberry Pi Pico 2 W (RP2350)** instead of
desktop CPython, CircuitPython, Arduino, ESP32, or wrong-Pico
(RP2040) code — the five things models actually emit when left
alone.

## Which files, in which order

| File | Role |
|------|------|
| [pico-2w-general-preprompt.md](pico-2w-general-preprompt.md) | Start here. Shared hard bans, board facts (LED pin, reserved GPIO, ADC pins, E9 pull-up rule), language/async rules, output format, silent self-check. |
| [pico-2w-wireless-networking.md](pico-2w-wireless-networking.md) | Add for Wi-Fi / MQTT / HTTP / socket work. Connect-with-timeout contract, umqtt via mip, reconnect + resubscribe, TLS and NTP rules. |
| [pico-2w-bluetooth-le.md](pico-2w-bluetooth-le.md) | Add for BLE work. aioble-first, locally-defined `_IRQ_*` constants, IRQ memoryview lifetime, advertising/GATT rules, honest pairing/security. |
| [pico-2w-low-power-and-io.md](pico-2w-low-power-and-io.md) | Add for battery nodes and hardware I/O. deepsleep structure, WDT limits, VSYS/temperature ADC, IRQ discipline, PIO/PWM/NeoPixel power rules. |

Paste the general prompt first, then the specialist(s) your task
needs, then your request. Each file also has a SHORT VERSION for
token-tight chats and one-off snippets.

## How these were built

Draft → self-critique → fact-check against the official MicroPython
docs (docs.micropython.org) and Raspberry Pi datasheets → revision →
trap tests. A trap test is a baited scenario (e.g. "blink the LED",
"sleep 10 minutes and wake on a button like an ESP32") checked
against the prompt text: the prompt passes only if it explicitly
forbids the wrong output *and* specifies the correct pattern.
The general prompt is at v1.3; the specialists are at v1.1. All
four went through five Elephant-Goldfish review rounds (Pass 5)
with a scripted 12-task benchmark (Luna, no prompt: 88.3;
with these prompts: 100) and passed all 11 trap tests in the
final round, including after the reduction pass.

## Standing warnings

- A pre-prompt is not a validator. Small models will still
  occasionally invent an API — the prompts teach them to say
  "unverified" instead, and you should still run code on hardware.
- Board stepping matters for the E9 pull-down warning: unknown
  stepping = keep the safe (pull-up) defaults in these prompts.
