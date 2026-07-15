---
layout: post
title: "How Does a Computer Work? From Transistors Up"
date: 2026-07-14 22:00:00 +0900
categories: [hardware, cpu, semiconductors]
type: Article
excerpt: "Building up from a single transistor to a running program — MOSFETs, logic gates, adders, flip-flops, and the fetch-decode-execute cycle."
---

I gave a science talk on a question that sounds simple but goes surprisingly deep: **how does a computer actually work?** The trick is to start from the smallest possible part — a single transistor — and keep combining until you reach a running program. Here's the whole chain.

## The pieces of a computer

Before the CPU, the cast of characters:

- **CPU (Central Processing Unit)** — interprets instructions and performs calculations.
- **GPU (Graphics Processing Unit)** — handles display output and massively parallel computation.
- **RAM (main memory)** — temporarily holds running programs and data (lost when powered off).
- **Storage** — SSDs, HDDs; permanently stores files and programs.
- **Motherboard** — the board that connects every part and lets them exchange data.

## The core part: the CPU

The CPU is the brain — it reads program instructions one at a time, decodes them, and executes them. Everything from addition to a game's physics ultimately reduces to a combination of the CPU's very simple operations.

So how can it "calculate" at all? We'll follow this ladder:

> transistor → logic gate → arithmetic / memory circuits → CPU → running program

Inside, a CPU is made of parts like the **ALU** (arithmetic-logic unit), the **accumulator (ACC)**, **temporary and general-purpose registers**, an **opcode buffer**, the **control unit**, and the **MAR** (memory address register).

## The "part of a part": the transistor (MOSFET)

Each of those CPU components is itself built from **MOSFETs** (Metal-Oxide-Semiconductor Field-Effect Transistors).

A MOSFET is a tiny switch you flip with an electrical signal:

- **On = 1 (true), off = 0 (false)** — this is *why* computers use binary.
- It has four terminals: **gate** (the "handle" — a voltage here opens a channel between source and drain), **source**, **drain**, and **bulk** (the body).
- **NMOS** turns on when the gate is `1`; **PMOS** is the opposite, turning on when the gate is `0`.

A single modern CPU packs *tens of billions* of these. (Real chips today use even more efficient variants — FinFET, GAAFET, MBCFET — but the MOSFET is the mental model.)

## Building logic gates from MOSFETs

Wire transistors together and you get **logic gates**, the real heart of the CPU:

- **AND** — output is true only when *both* inputs are true. Wire the transistors **in series**: both must be on for current to pass.
- **OR** — output is true if *either* input is true. Wire them **in parallel**: one being on is enough.
- And from there: **NOT, XOR, NAND, NOR**, and the rest.

## A simple half adder

Combine an **XOR** and an **AND** gate and you get a **half adder** — a circuit that adds two bits:

- **Sum = A XOR B** — `1` when the inputs differ
- **Carry = A AND B** — `1` only when both are `1`

For example `1 + 1 = binary 10`, so `Sum = 0, Carry = 1`. Chain two half adders with an OR gate and you get a **full adder** that also accepts a carry-in. Stack and combine these arithmetic circuits and you've built the CPU's **ALU**.

## Remembering with flip-flops

Logic gates alone forget everything the instant the input disappears. To *store* a value you need feedback.

A **flip-flop** feeds a gate's output back into its own input to hold a single bit. In an SR flip-flop:

- **S (Set) = 1** → store `1` in output Q
- **R (Reset) = 1** → clear Q to `0`
- **S = R = 0** → hold the previous value — *memory!*
- **S = R = 1** → forbidden input

Gate everything with a **clock (CK)** signal so values only change on the beat, and the whole CPU stays in sync. Combine flip-flops and you get **registers**.

## Actually running a program

Put it all together and you can run real code. A tiny program that computes `5 + 3` and prints it runs on exactly these parts — ALU, registers, memory. The CPU processes every instruction in three steps:

1. **Fetch** — the control unit uses the address in the MAR to pull an instruction from RAM into the opcode buffer.
2. **Decode** — the control unit works out which parts (ALU, registers, …) the instruction needs.
3. **Execute** — the ALU performs the operation and writes the result to a register or memory.

Repeat this cycle *billions of times per second* (a few GHz) and you have a running program.

## Summary

- **Transistor (MOSFET)** — a tiny electrical on/off switch
- **Logic gates** — AND, OR, XOR built by wiring transistors
- **Half / full adders** — "calculating" circuits built from gates → the **ALU**
- **Flip-flops** — "remembering" circuits built by feeding gates back → **registers**
- **CPU** — ALU + registers + control unit
- **Programs** — run by repeating **fetch → decode → execute**

In the end, a computer is nothing more than *on and off* — the simplest switch imaginable — combined tens of billions of times over.
