# 8051 Square and Cube of a Number

# 1. 8051 Square Program

## AIM
To write and execute an Assembly language program for finding the square of a given data using the 8051 microcontroller in Keil software.

## APPARATUS REQUIRED
- Personal computer
- Keil µVision IDE

## ALGORITHM
1. Enter the Assembly language program.
2. Configure Port 0 (P0) as the input port.
3. Read the input number from P0.
4. Move the input number into registers A and B.
5. Multiply A and B using the `MUL AB` instruction.
6. Store the lower byte of the result in Port 2 (P2).

## PROGRAM

```asm
ORG 0000H

START:
    MOV P0, #0FFH       ; Configure P0 as input
    MOV A, P0           ; Read input number
    MOV B, A            ; Copy input to B
    MUL AB              ; Multiply A and B

    MOV P2, A           ; Store result in P2

HERE:
    SJMP HERE           ; Stop execution

END
```

## OUTPUT

**Sample Input:**

- P0 = 05H (Decimal 5)

**Calculation:**

- Square = 5 × 5 = 25
- Hexadecimal result = 19H

**Expected Output:**

```text
P0 = 05H
P2 = 19H
```

| Input (P0) | Square | Output (P2) |
|---|---:|---|
| 02H | 4 | 04H |
| 03H | 9 | 09H |
| 05H | 25 | 19H |
| 0AH | 100 | 64H |
| 0FH | 225 | E1H |

## RESULT

Thus, the square of the given data was calculated using the 8051 microcontroller in Keil µVision.

---

# 2. 8051 Cube Program

## AIM
To write and execute an Assembly language program for finding the cube of a given data using the 8051 microcontroller in Keil software.

## APPARATUS REQUIRED
- Personal computer
- Keil µVision IDE

## ALGORITHM
1. Enter the Assembly language program.
2. Configure Port 0 (P0) as the input port.
3. Read the input number from P0 and store it in register R1.
4. Multiply the input number by itself to calculate the square.
5. Store the square in register R0.
6. Multiply the square by the original input number.
7. Store the lower byte of the cube in Port 2 (P2).

## PROGRAM

```asm
ORG 0000H

START:
    MOV P0, #0FFH       ; Configure P0 as input
    MOV R1, P0          ; Read and store input

    MOV A, R1           ; Load input into A
    MOV B, R1           ; Load input into B
    MUL AB              ; Calculate square

    MOV R0, A           ; Store lower byte of square

    MOV A, R0           ; Load square into A
    MOV B, R1           ; Load original input into B
    MUL AB              ; Calculate cube

    MOV P2, A           ; Store result in P2

HERE:
    SJMP HERE           ; Stop execution

END
```

## OUTPUT

**Sample Input:**

- P0 = 05H (Decimal 5)

**Calculation:**

- Square = 5 × 5 = 25
- Cube = 25 × 5 = 125
- Hexadecimal result = 7DH

**Expected Output:**

```text
P0 = 05H
P2 = 7DH
```

| Input (P0) | Cube | Output (P2) |
|---|---:|---|
| 01H | 1 | 01H |
| 02H | 8 | 08H |
| 03H | 27 | 1BH |
| 04H | 64 | 40H |
| 05H | 125 | 7DH |
| 06H | 216 | D8H |

## RESULT

Thus, the cube of the given data was calculated using the 8051 microcontroller in Keil µVision.

---

## NOTE
- The `MUL AB` instruction performs 8-bit multiplication and produces a 16-bit result.
- The lower byte is stored in register A, while the higher byte is stored in register B.
- Since only the lower byte is sent to P2, the square program uses inputs from 00H to 0FH and the cube program uses inputs from 00H to 06H.
- For hardware implementation, Port 0 requires external pull-up resistors.
