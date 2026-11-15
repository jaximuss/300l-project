# Source Mapping

| Reference table | LEESIR source file | Decoder approach |
|---|---|---|
| Game Boy base opcodes | `LEESIR.Cores.Gameboy/GameBoyCpu.cs` | Grouped bit-pattern decoding plus explicit special cases |
| Game Boy CB-prefixed opcodes | `LEESIR.Cores.Gameboy/GameBoyCpu.cs` (`ExecuteCb`) | Bit fields select operation group, bit number/operation and register |
| NES official opcodes | `LEESIR.Cores.Nes/NesCpu.cs` | Direct opcode switch plus addressing/ALU/branch helpers |

The repository tables are documentation derived from the implemented LEESIR CPU decoders; they are not third-party emulator source code.