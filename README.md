# AES Encryption and Decryption in Verilog

This repository contains Verilog implementations of AES (Advanced Encryption Standard) encryption and decryption modules. The modules include key expansion, round transformations, and operations for both encryption and decryption according to the AES standard.

## Project Overview

AES is a widely used symmetric encryption algorithm, essential for securing digital communications. This project provides a hardware implementation of AES, including modules for:
- Key Expansion
- AddRoundKey
- SubBytes
- ShiftRows
- MixColumns
- InvSubBytes, InvShiftRows, InvMixColumns (for decryption)

## File Structure

- `AES.v`: Top-level AES module integrating encryption and decryption processes.
- `AESEncrypt.v`: Module handling the AES encryption rounds.
- `AESDecrypt.v`: Module handling the AES decryption rounds.
- `KeyExpansion.v`: Module for expanding the encryption key for each AES round.
- `AddRoundKey.v`, `SubBytes.v`, `ShiftRows.v`, `MixColumns.v`: Core operations for encryption.
- `InvSubBytes.v`, `InvShiftRows.v`, `InvMixColumns.v`: Core operations for decryption.
- `SubTable.v`, `InvSubTable.v`: Lookup tables for substitution bytes in encryption and decryption.

## Installation

1. Clone this repository:
    ```bash
    git clone https://github.com/yourusername/aes-verilog.git
    ```
2. Open the project in your preferred Verilog simulator or FPGA design tool (e.g., Xilinx Vivado, ModelSim).
3. Compile the modules and run the provided testbenches to verify functionality.

## Usage

Each module is designed to be instantiated within an AES-based project. To perform encryption or decryption, load the `AES.v` module with the required key and plaintext or ciphertext input.

Example instantiation in a Verilog testbench:
```verilog
module AES_testbench;
    reg [127:0] plaintext;
    reg [127:0] key;
    wire [127:0] ciphertext;

    AES aes_instance (
        .plaintext(plaintext),
        .key(key),
        .ciphertext(ciphertext)
    );

    initial begin
        // Initialize inputs and simulate AES encryption
        plaintext = 128'h00112233445566778899aabbccddeeff;
        key = 128'h000102030405060708090a0b0c0d0e0f;
        #10; // Wait for encryption process
    end
endmodule
