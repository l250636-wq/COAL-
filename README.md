# COAL - Assembly Language Programs

**Name:** [Shabi Ul Hassan]
**Roll No:** [L250636]
**Section:** [Bcs-3H]
**Course:** COAL (EE2003), FAST NUCES Lahore, Fall 2026

## About this repository

This repository holds my COAL (Computer Organization and Assembly Language) programs. Each assignment is in its own folder.

## Assignment 3 - Text Viewport Manager

`Assignment3/q2.asm` is a 16-bit 8088 program that works directly on text-mode video memory (segment `0xB800`, 80x25). It does the following:

- `draw_window`: clears the screen and draws a double-line bordered window.
- `draw_banner`: draws a centered title banner inside the window.
- `stream_text`: copies a paragraph into the window line by line with `LODSB` / `STOSW`, staying inside the margins.
- `scroll_window_up`: scrolls only the text area of the window up (row by row with `MOVSW`, then blanks the freed rows with `STOSW`).
- `find_and_highlight`: searches the text area for a substring using `REPE CMPSB` and changes only the attribute bytes of every match.
- `printNum`: prints a number by dividing by 10, pushing the digits on the stack and popping them back in order. It is used for the status bar.

Every subroutine takes its parameters on the stack, uses a `BP` stack frame with local variables, preserves the registers it modifies with `push` / `pop`, and cleans up its own parameters with `ret n`.

## Tools used

- **NASM** - assembler
- **DOSBox** - to run the `.com` file

## How to assemble and run

1. Install NASM and DOSBox.
2. Put `q2.asm` and `nasm.exe` in one folder (for example `C:\COAL`).
3. Open DOSBox and type:

```
mount c c:\COAL
c:
nasm q2.asm -f bin -o q2.com
q2.com
```

## Folder structure

```
COAL/
|-- README.md
|-- Assignment3/
    |-- q2.asm
    |-- screenshots/
        |-- q2_output.png
```

## Output screenshot

<img width="327" height="218" alt="image" src="https://github.com/user-attachments/assets/2d773edb-5a47-49d6-bb4c-684e85d69fa0" />

