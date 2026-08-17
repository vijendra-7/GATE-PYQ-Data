
When a processor stores a multi-byte data type (like a 32-bit integer) in memory, it must decide the sequence of those bytes. This specific ordering is known as **Endianness**.

Let's visualize storing the decimal number **`439041101`**. In hexadecimal, this 32-bit (4-byte) number is:

$$ 0x1A2B3C4D $$

> [!NOTE] 
> In the hex number `0x1A2B3C4D`:
> 
> - **Most Significant Byte (MSB)** is ==`1A`==
> - **Least Significant Byte (LSB)** is ==`4D`==

---

## 📊 Memory Layout Visual Comparison

![Big Endian vs Little Endian](https://assets.bytebytego.com/diagrams/0084-big-endian-vs-little-endian.png)

Here is how the exact same value maps into memory differently depending on the architecture. 

| 📍 Memory Address | 🐘 Big Endian | 🤏 Little Endian |
| :--- | :---: | :---: |
| **`0x0000`** *(Lowest)* | ==`1A`== *(MSB)* | ==`4D`== *(LSB)* |
| **`0x0001`** | `2B` | `3C` |
| **`0x0002`** | `3C` | `2B` |
| **`0x0003`** *(Highest)*| ==`4D`== *(LSB)* | ==`1A`== *(MSB)* |

### 1. Big-Endian 🐘
Notice in the **Big Endian** column how the memory visually reads downwards as `1A 2B 3C 4D` — exactly how we write the number! The **Most Significant Byte** (`1A`) goes to the lowest address (`0x0000`).

> [!TIP]
> **Who uses it?** Network protocols (like TCP/IP) universally use Big-Endian formatting, often referred to as **Network Byte Order**.

### 2. Little-Endian 🤏
Notice in the **Little Endian** column how the lowest byte (`4D`) is placed at the top at address `0x0000`. The **Least Significant Byte** always goes first.

> [!IMPORTANT]
> **Who uses it?** Intel (x86/x64) processors use Little-Endian. This means your personal laptop is likely a Little-Endian machine!

---

## 🧮 A Mathematical Perspective

> [!FORMULA]
> **Value Calculation in Big-Endian**
> If a variable spans from byte $B_0$ to $B_{n-1}$ (where $B_0$ is the MSB), its total integer value is computed as:
> $$ Value = \sum_{i=0}^{n-1} B_i \times 256^{(n-1-i)} $$

Understanding endianness is a fundamental concept in **Computer Organization & Architecture (COA)**, critical for networking, file parsing, and low-level C programming.

---

<!-- PRACTICE -->
<MCQ>
In a Little-Endian machine, what byte will be stored at address `0x2000` if the 32-bit integer `0xAABBCCDD` is stored starting at address `0x2000`?
- 0xAA
- 0xBB
- 0xCC
- 0xDD
<ANS>
3
<EXP>
In Little-Endian, the **Least Significant Byte (LSB)** is stored at the lowest address. 
The LSB of `0xAABBCCDD` is `DD`. 
Therefore, `DD` is stored at the starting address `0x2000`.
</EXP>

<MCQ>
Which of the following generally utilizes **Big-Endian** byte ordering?
- Intel x86 processors
- TCP/IP Network Protocols
- ARM processors in default little-endian mode
- Windows Operating System core
<ANS>
1
<EXP>
Network protocols like **TCP/IP** use Big-Endian byte ordering, which is often referred to as "Network Byte Order". Intel processors primarily use Little-Endian.
</EXP>

<NAT>
If the 16-bit value `0x4F52` is stored at memory location `0x4000` using Big-Endian format, what is the exact hexadecimal byte (in hex, no prefix) stored at address `0x4001`?
<ANS>
52
<EXP>
In Big-Endian, the **Most Significant Byte (MSB)** goes to the lowest address. 
- Address `0x4000` gets `4F`.
- Address `0x4001` gets the LSB, which is `52`.
</EXP>
