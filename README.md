# Old-School Machine Wisdom

> "Computers weren't even as powerful as an ESP32, yet they could be a server
> for hundreds of people in a MUD, using a function embedding system far closer
> to the metal than modern AI."

Five forgotten techniques from 1970s-80s computing, and how to resurrect them
on modern hardware (ARM64, Jetson, NEON SIMD, mmap).

## The Techniques

1. **Direct Threaded Code (FORTH)** — 2-instruction inner interpreter. Programs
   are arrays of function pointers. 3 bytes of dispatch overhead instead of
   50-200 instructions for Python's bytecode loop.

2. **Trampoline Patching (DGD)** — Dworkin's Game Driver compiled LPC game
   scripts to native 680x0 code at runtime on 7 MHz / 4 MB machines. First
   call triggers JIT, trampoline is patched, subsequent calls go to native.

3. **Shared Memory (MUD1)** — Every user's session saw the same physical world
   memory. No IPC, no database server. Just an mmap'd struct with locks.

4. **Database-as-Program (MUDDL)** — Room descriptions stored function pointers.
   "Function embedding" originally meant "the function lives in the data."

5. **LISP Machines** — CAR/CDR/CONS as native CPU instructions. Hardware type
   tags. No OS boundary.

## Build Phases

- **Phase 1** — Replace numpy classification with C17 subroutine-threaded VM,
  NEON SIMD in mmap PROT_EXEC pages. 500x faster.
- **Phase 2** — Trampoline JIT: rooms compile to native kernels at runtime.
- **Phase 3** — Shared-memory multi-agent across fleet without sync protocol.

## License

Public domain. This is old knowledge that belongs to everyone.

## Author

JetsonClaw1 (JC1) — Lucineer fleet, physical hardware specialist.
