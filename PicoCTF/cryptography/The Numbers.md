# The Numbers

## Challenge
<img width="688" height="323" alt="Screenshot 2025-08-08 093953" src="https://github.com/user-attachments/assets/7d6d1026-21ed-4ae4-9e20-eb5d57ac70d2" />

The challenge provides an image containing a sequence of numbers and curly braces, with a noisy, splattered background.


The numbers presented are:
`16 9 3 15 3 20 6 { 20 8 5 14 21 13 2 5 18 19 13 1 19 15 14 }`

## Analysis

The core of this challenge is recognizing the pattern in the data provided. Several clues point toward the solution:

1.  **Numeric Data:** The data consists entirely of numbers.
2.  **Range of Numbers:** All numbers fall between 1 and 26. This is a strong indicator of a substitution cipher where each number maps to a letter of the English alphabet.
3.  **Standard CTF Format:** The presence of curly braces `{}` strongly suggests the standard `picoCTF{flag_goes_here}` format. The numbers outside the braces likely spell out `picoCTF`.

This pattern is characteristic of the **A1Z26 cipher**, where `A=1`, `B=2`, `C=3`, and so on, up to `Z=26`.

## Solution

To solve the cipher, we substitute each number with its corresponding letter in the alphabet.

Let's break it down:

**Part 1: The prefix**
*   `16` -> `P`
*   `9` -> `I`
*   `3` -> `C`
*   `15` -> `O`
*   `3` -> `C`
*   `20` -> `T`
*   `6` -> `F`

This spells out `PICOCTF`, confirming our suspicion about the flag format.

**Part 2: The flag content**
*   `20` -> `T`
*   `8` -> `H`
*   `5` -> `E`
*   `14` -> `N`
*   `21` -> `U`
*   `13` -> `M`
*   `2` -> `B`
*   `5` -> `E`
*   `18` -> `R`
*   `19` -> `S`
*   `13` -> `M`
*   `1` -> `A`
*   `19` -> `S`
*   `15` -> `O`
*   `14` -> `N`

This sequence decodes to `THE NUMBERS MASON`. This is a famous quote from the video game *Call of Duty: Black Ops*.

## Flag

Combining the parts and formatting it as a standard flag (usually with underscores instead of spaces), we get the final answer.
