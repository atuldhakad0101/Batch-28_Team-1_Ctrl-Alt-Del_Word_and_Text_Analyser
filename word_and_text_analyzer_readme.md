# Word and Text Analyzer (Problem Statement 9)

A C programming mini-hackathon project that analyzes a user-entered word or sentence to generate a complete text statistics report and verify whether the input is a palindrome.

---

## Project Details

* **Project Title:** Word and Text Analyzer
* **Problem Statement:** Problem 9 – Word and Text Analyzer
* **Team Name:** Team 1 (`Ctrl+alt+del`)
* **Batch:** `[Enter Your Batch, e.g., Batch 01]`
* **Course:** C Programming Lab – Mini Hackathon
* **Problem Description:** Develop a text analysis tool that processes a sentence entered by the user to count characters, words, vowels, and consonants, identify the longest word, check whether the word or sentence is a palindrome (ignoring spaces and letter case), and handle empty or space-only inputs properly.

---

## Team Members

| S. No. | Student Name | SAP ID |
| :--- | :--- | :--- |
| **1** | **Atul Dhakad** | `590037030` |
| **2** | **Khushi Kumari Anil** | `590042559` |
| **3** | **Tanishq Paliwal** | `590042436` |

---

## Project Objectives

* To apply fundamental C programming concepts—such as character arrays, strings, loops, conditional statements, and standard library functions—to solve a practical text-processing problem.
* To build a reliable command-line text analysis tool capable of safely reading multi-word sentences and computing accurate character and word statistics in a single pass.
* To implement an efficient, memory-friendly two-pointer algorithm for case-insensitive palindrome detection that ignores spaces and punctuation.
* To ensure robust input validation by gracefully handling empty inputs and whitespace-only strings.

---

## Project Features

* **Safe Multi-Word Input:** Reads full sentences (up to `999` characters) including spaces using `fgets()` and strips the trailing newline (`\n`) character.
* **Character Counting:** Calculates both **Total Characters (with spaces)** and **Total Characters (without spaces)**.
* **Vowel & Consonant Analysis:** Identifies alphabetic characters using `isalpha()` and classifies them into **Vowels** (`a, e, i, o, u`) and **Consonants** regardless of letter case.
* **Accurate Word Detection & Longest Word:** Detects word boundaries across spaces and punctuation using `isalnum()`, counts total words, and extracts the **Longest Word** in the sentence.
* **In-Place Palindrome Check:** Uses a two-pointer approach (`left` and `right`) to check if the text is a palindrome while skipping spaces/punctuation and ignoring uppercase/lowercase differences.
* **Empty & Whitespace Validation:** Detects empty inputs (`Enter` key only) or inputs containing only spaces and displays a clear error message instead of invalid statistics.

---

## Algorithm

* **Step 1:** Start.
* **Step 2:** Declare a character array `text` of size `MAX_LEN` (`1000`).
* **Step 3:** Display the prompt message: `"enter a word or sentence to analyze : "`.
* **Step 4:** Read the input text using `fgets()`.
* **Step 5:** If input cannot be read (`NULL`), display `"error reading input."` and terminate the program.
* **Step 6:** Calculate the length of the input text using `strlen()`.
* **Step 7:** If the last character is a newline (`\n`), replace it with `'\0'` and decrease `len` by `1`.
* **Step 8:** Initialize the tracking variables:
  * `total_chars = len`
  * `chars_no_spaces = 0`, `words = 0`, `vowels = 0`, `consonants = 0`
  * `curr_word_len = 0`, `max_word_len = 0`
  * `longest_word = ""`, `current_word = ""`
* **Step 9:** Traverse the text from index `i = 0` to `len`. For each character `ch`:
  1. If `i < len` and `ch` is not whitespace (`!isspace(ch)`), increment `chars_no_spaces`.
  2. If `i < len` and `ch` is an alphabet (`isalpha(ch)`):
     * Convert it to lowercase using `tolower(ch)`.
     * If it is `'a'`, `'e'`, `'i'`, `'o'`, or `'u'`, increment `vowels`; otherwise, increment `consonants`.
  3. If `i < len` and `ch` is alphanumeric (`isalnum(ch)`):
     * Append `ch` to `current_word` and increment `curr_word_len`.
  4. Otherwise (delimiter or end of string reached):
     * If `curr_word_len > 0`:
       * Increment `words`.
       * If `curr_word_len > max_word_len`, update `max_word_len` and copy `current_word` into `longest_word`.
       * Reset `curr_word_len = 0`.
* **Step 10:** If `total_chars == 0` or `chars_no_spaces == 0`, display `"Error: Input is empty or contains only spaces. Please enter valid text."` and terminate the program.
* **Step 11:** Initialize the palindrome checking variables:
  * `is_palindrome = 0`
  * `left = 0`
  * `right = total_chars - 1`
* **Step 12:** Repeat while `left <= right`:
  1. If `text[left]` is not alphanumeric, increment `left`.
  2. Else if `text[right]` is not alphanumeric, decrement `right`.
  3. Otherwise:
     * Set `is_palindrome = 1`.
     * Convert both `text[left]` and `text[right]` to lowercase. If they are not equal, set `is_palindrome = 0` and exit the loop (`break`).
     * Increment `left` and decrement `right`.
* **Step 13:** Display the **Text Statistics Report** containing total characters (with and without spaces), total words, vowels, consonants, longest word, and palindrome status (`Yes` or `No`).
* **Step 14:** Stop.

*(Note: A visual flowchart created in Flowgorithm is also included in this repository as `flowchart.png` / `flowchart.fprg`.)*

---

## C Programming Concepts Used

* **Standard Libraries (`<stdio.h>`, `<string.h>`, `<ctype.h>`):**
  * `<stdio.h>` for console I/O (`printf`, `fgets`).
  * `<string.h>` for string length calculation (`strlen`) and string copying (`strcpy`).
  * `<ctype.h>` for safe character classification and case conversion (`isspace`, `isalpha`, `isalnum`, `tolower`).
* **Preprocessor Directives (`#include`, `#define`):** Used to include header files and define the `MAX_LEN` constant (`1000`).
* **Arrays & Null-Terminated Strings:** Using `char` arrays (`text`, `current_word`, `longest_word`) with explicit `'\0'` termination.
* **Loops (`for` and `while`):** A single-pass `for` loop (`0` to `len`) for counting statistics and detecting words, and a `while` loop for two-pointer palindrome checking.
* **Conditional Statements & Control Flow (`if`, `else if`, `else`, `break`, `return`):** Used for character classification, input validation, and early termination on palindrome mismatch.
* **Ternary Operator (`? :`):** Used in `printf()` to cleanly format `"N/A"` when no words exist and `"Yes"` / `"No"` for the palindrome result.

---

## How to Compile and Run

### Prerequisites
* A C compiler such as **GCC** (MinGW on Windows, or built-in GCC/Clang on Linux/macOS).

### Compilation & Execution Steps

1. **Clone or download the repository** and open a terminal/command prompt inside the project folder.
2. **Compile the C source code:**
   ```bash
   gcc team_1_Code.c -o team1.out
   ```
3. **Run the compiled executable:**
   * **On Windows (CMD / PowerShell):**
     ```bash
     .\team1.out
     ```
   * **On Linux / macOS / Git Bash:**
     ```bash
     ./team1.out
     ```

---

## Sample Test Cases

| Test Case ID | Scenario | Sample Input | Expected Output |
| :--- | :--- | :--- | :--- |
| **TC-01** | Standard multi-word sentence | `FRI Mesuem In Dehradun` | Chars (with spaces): `22`, Chars (without spaces): `19`, Words: `4`, Vowels: `8`, Consonants: `11`, Longest Word: `Dehradun`, Palindrome: `No` |
| **TC-02** | Single-word palindrome (mixed case) | `Madam` | Chars (with spaces): `5`, Chars (without spaces): `5`, Words: `1`, Vowels: `2`, Consonants: `3`, Longest Word: `Madam`, Palindrome: `Yes` |
| **TC-03** | Sentence palindrome with punctuation | `Madam, I'm Adam!` | Chars (with spaces): `16`, Chars (without spaces): `14`, Words: `4`, Vowels: `5`, Consonants: `6`, Longest Word: `Madam`, Palindrome: `Yes` |
| **TC-04** | Empty input (Enter pressed immediately) | `""` | `Error: Input is empty or contains only spaces. Please enter valid text.` |
| **TC-05** | Spaces-only input | `"     "` | `Error: Input is empty or contains only spaces. Please enter valid text.` |

---

## Testing Results

All test cases were executed and verified on the local GCC environment.

### Test Case 1: Multi-Word Sentence (`FRI Mesuem In Dehradun`)
```text
C:\Users\Atul\Desktop\c-language\lab_hackathon>team1.out
enter a word or sentence to analyze : FRI Mesuem In Dehradun

-------- Text Statistics Report --------
Total Characters (with spaces)    : 22
Total Characters (without spaces) : 19
Total Words                       : 4
Vowels                            : 8
Consonants                        : 11
Longest Word                      : Dehradun
Is Palindrome?                    : No
-------------------------------------------
```
* **Status:** **PASS** – Accurately counted spaces, words, vowels, consonants, identified `Dehradun` as the longest word, and returned `No` for palindrome.

### Test Case 2: Mixed-Case Palindrome (`Madam`)
```text
C:\Users\Atul\Desktop\c-language\lab_hackathon>team1.out
enter a word or sentence to analyze : Madam

-------- Text Statistics Report --------
Total Characters (with spaces)    : 5
Total Characters (without spaces) : 5
Total Words                       : 1
Vowels                            : 2
Consonants                        : 3
Longest Word                      : Madam
Is Palindrome?                    : Yes
-------------------------------------------
```
* **Status:** **PASS** – Correctly ignored uppercase `'M'` vs. lowercase `'m'` and returned `Yes`.

### Test Case 3: Empty / Whitespace-Only Input (`"     "`)
```text
C:\Users\Atul\Desktop\c-language\lab_hackathon>team1.out
enter a word or sentence to analyze :      

Error: Input is empty or contains only spaces. Please enter valid text.
```
* **Status:** **PASS** – Handled space-only input gracefully without division errors or false palindrome results.

---

## Repository Structure

```text
BatchXX_Team01_WordTextAnalyzer/
├── README.md
├── team_1_Code.c
├── presentation.pptx
├── flowchart.png
└── screenshots/
    ├── test_sentence.png
    └── test_palindrome.png
```