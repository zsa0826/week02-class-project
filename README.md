# Terminal Calculator — Ohm's Law

## Purpose
This program reads a voltage (V) and a resistance (R), then calculates and prints
the current using Ohm's Law: I = V / R.

## Input Format
Two numbers entered via standard input, separated by a space or newline:
<voltage> <resistance>
Example: 12 4

## Build Commands
mkdir -p build
g++ -std=c++17 -Wall -Wextra -pedantic src/main.cpp -o build/app

## Run Commands
./build/app
Then type the two numbers when prompted.

## Example Output
Input: 12 4
Output: Current: 3 A

Input: 12 0
Output: Invalid input

## Automated Testing
Run all acceptance tests at once with: bash test.sh
This compiles the program, runs it against each test case in tests/, and compares
the output to the expected result using diff. GitHub Actions also runs this
automatically on every push and pull request.

## Limitations
- Does not handle non-numeric input gracefully beyond printing "Invalid input" -
  it does not tell the user why the input was invalid.
- Only supports two space/newline-separated numeric inputs; does not validate
  units or extra input provided after the two expected numbers.
- Resistance of exactly 0 or any negative value is rejected, but there is no
  upper bound check on unreasonably large values.

## Debugging Reflection
While setting this project up, the main challenge was GitHub authentication -
pushing over HTTPS initially failed with a 403 permission error due to a stale
cached credential. Switching to SSH authentication (generating a new key with
ssh-keygen and adding it to GitHub) resolved this permanently. A second lesson
was how strict YAML indentation is in the GitHub Actions workflow file - a
two-space indentation error under jobs: and steps: silently broke the
workflow structure until corrected.
