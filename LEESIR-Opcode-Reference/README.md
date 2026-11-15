# LEESIR Opcode Reference

This repository is the complete opcode reference accompanying the dissertation **A Unified Multi-System Emulator (LEESIR)**.

The dissertation includes 20 representative Game Boy instructions and 20 representative NES instructions to explain the fetch-decode-execute process and how processor instructions were translated into C#. This repository provides the complete tables used by the project.

## Opcode tables

- [Game Boy base opcodes](opcode-tables/gameboy-base-opcodes.md) - all 256 base opcode byte positions. LEESIR supports 243 base instructions, dispatches `0xCB` to the CB table, recognises `STOP`, and treats 11 invalid Game Boy opcode values as invalid by design.
- [Game Boy CB-prefixed opcodes](opcode-tables/gameboy-cb-opcodes.md) - all 256 CB-prefixed operations implemented by LEESIR.
- [NES official opcodes](opcode-tables/nes-opcodes.md) - all 151 official 6502/NES opcode encodings implemented by LEESIR.

CSV versions are included in the same folder for filtering and machine-readable review.

## How this relates to the C# code

The Game Boy implementation is located in `LEESIR.Cores.Gameboy/GameBoyCpu.cs`. It uses a combination of grouped bit-pattern decoding and explicit cases. Repeated instruction families are decoded by masking and shifting bits from the opcode, for example selecting a register or register pair before calling shared helpers.

The NES implementation is located in `LEESIR.Cores.Nes/NesCpu.cs`. It uses a more direct opcode `switch`, with shared helper methods for addressing modes, arithmetic, branches, stack operations, flags and memory access.

The tables identify the representative C# implementation path for each opcode so that an examiner can trace the machine-code byte to the emulator behaviour.

## Scope

This reference documents the CPU opcode support implemented for the submitted LEESIR project. It does not claim complete hardware compatibility. Cartridge mappers, graphics, audio, timing, DMA, interrupts and other hardware subsystems are documented separately in the dissertation.

## Technical references

- GBDev Pan Docs: https://gbdev.io/pandocs/
- RGBDS Game Boy CPU instruction reference: https://rgbds.gbdev.io/docs/master/gbz80.7
- Patrick Diskin, *Nintendo Entertainment System Documentation* (2004): https://www.nesdev.org/NESDoc.pdf

## Project

LEESIR is an independently developed C#/.NET multi-system emulator prototype supporting original Game Boy and selected NES cartridge configurations through a shared host and WinForms interface.