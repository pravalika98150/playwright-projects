# 📚 LearnPlaywright3x — JavaScript Fundamentals & IQ Notes Library

A progressive JavaScript learning repository from first principles, plus an **IQ_Notes** reference library for interview-style concept breakdowns (source code vs bytecode, identifiers, operators, etc.).

---

## Table of Contents

- [Repo Structure](#repo-structure)
- [00 — GenAI / RICE Prompting](#00--genai--rice-prompting)
- [01 — Hello World](#01--hello-world)
- [02 — `let` & Scope](#02--let--scope)
- [03 — Identifiers & Comments](#03--identifiers--comments)
- [04 — Literals & Numbers](#04--literals--numbers)
- [05 — Operators](#05--operators)
- [IQ_Notes — Reference Library](#iq_notes--reference-library)

---

## 📂 FOLDER STRUCTURE

```
LearnPlaywright3x/
├── 00_chaptet_GENAI/
│   └── RICEPOT_SeleniumFramworkCreation.md    # LLM prompt for Selenium framework
├── chapter_01_Basics/
│   └── HelloWorld.js                          # console.log fundamentals
├── chapter_02_JS_Concepts/
│   └── 02_let_concept.js                      # let, block scope, hoisting
├── 03_chapter_Identifier/
│   ├── 03_Identifer_Rules.js                  # valid/invalid identifier chars
│   ├── 04_Identifer_Rues_Part2.js             # naming conventions
│   ├── 05_Comments.js                         # // /* */ /** */ syntax
│   └── 06_Identifer_IQ.js                     # Unicode, keywords, edge cases
├── 04_chapter_Literal/
│   ├── 07_Literal.js                          # literal types, typeof
│   ├── 08_null_undefined.js                   # null vs undefined
│   ├── 09_Null_IQ.js                          # null quirk (typeof null)
│   ├── 10_Literal.js                          # number formats (hex, octal)
│   ├── 11_Number.js                           # binary, hex, exponent literals
│   └── 12_Number_Part2.js                     # BigInt, Infinity, NaN
├── 05_chapter_Operator/
│   ├── 13_DataType.js                         # 7 primitives + objects
│   ├── 14_Assignment_Operator.js              # =, +=, -=, *=, /=, %=
│   ├── 15_Arithmetic_Opeartor.js              # + - * / %, **, odd/even
│   ├── 16_Comparsion_Operator.js              # ==, ===, !=, !==, >, <
│   ├── 17_Logical_Operators.js                # &&, ||, ! gates
│   ├── 18_Confusing_Comparsion.js             # "" == 0, type coercion traps
│   └── 18_Confusing_Comparsion_P2.js          # null/undefined coercion edge cases
└── IQ_Notes/
    ├── README.md                              # This repo overview
    ├── README_1.md                            # This repo overview (alternate version)
    ├── Source_Code_ByteCODE_Binary_IQ.md       # Source → Bytecode → Binary code
    └── [Other IQ notes]
```

---

## 🎯 CHAPTER BREAKDOWN

### Chapter 01 — Hello World

| Concept | Details |
|---------|---------|
| **What** | Smallest JS program: `console.log("Hello...")` |
| **Why** | Confirm Node.js + V8 engine pipeline works |
| **Run** | `node chapter_01_Basics/HelloWorld.js` |
| **Output** | Text to stdout via console binding |

```javascript
console.log("Hello The Testing Academy!");
```

---

### Chapter 02 — `let` & Block Scope

| Concept | Details |
|---------|---------|
| **What** | Block-scoped variables + hoisting |
| **vs `var`** | `var` is function-scoped (leaks past blocks) |
| **Hoisting** | Function declarations hoist fully (name + body) |
| **Key Rule** | Always use `let` in loops/conditionals |

```javascript
let a = 10;

for (let i = 0; i < 5; i++) {
    console.log(i);  // 0, 1, 2, 3, 4
}
// i is NOT accessible here (block-scoped) ✅

function myFn() {
    console.log("I run even if called before declaration");
}
myFn();  // Works — function hoisting
```

---

### Chapter 03 — Identifiers & Comments

| Rule | Valid? | Example |
|------|:------:|---------|
| **Start with letter** | ✅ | `let name` |
| **Start with `_`** | ✅ | `let _private` |
| **Start with `$`** | ✅ | `let $element` |
| **Start with digit** | ❌ | `let 1st` → SyntaxError |
| **Unicode letters** | ✅ | `let café` |
| **Reserved keywords** | ❌ | `let class` → SyntaxError |

**Comment Types:**

```javascript
// Single-line comment

/* Multi-line comment */

/**
 *  JSDoc comment (for documentation tools)
 *  @param {string} name - user name
 *  @returns {string} greeting
 */
```

---

### Chapter 04 — Literals & Numbers

**A literal** = fixed value written directly in code (`42`, `"text"`, `true`, `null`).

| Number Format | Example | Decimal Value |
|---------------|---------|---------------|
| Decimal | `42` | 42 |
| Binary | `0b1010` | 10 |
| Octal | `0o52` | 42 |
| Hex | `0x2A` | 42 |
| Exponent | `1.5e3` | 1500 |
| Separator | `1_000_000` | 1000000 |
| BigInt | `123n` | 123 (arbitrary precision) |

**The `null` vs `undefined` Gotcha:**

| Type | Set By | Meaning |
|------|--------|---------|
| `undefined` | JS engine | "Not assigned yet" |
| `null` | Developer | "Intentionally empty" |
| `typeof null` | ❌ Returns "object" | Long-standing bug kept for compatibility |

```javascript
let user;                    // undefined
let profile = null;          // intentionally empty

console.log(typeof user);    // "undefined"
console.log(typeof profile); // "object" 😬 (quirk)
```

---

### Chapter 05 — Operators

**Three main types:**

| Type | Operators | Purpose |
|------|-----------|---------|
| **Assignment** | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | Assign/modify values |
| **Arithmetic** | `+`, `-`, `*`, `/`, `%`, `**` | Math operations |
| **Comparison** | `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=` | Compare values |
| **Logical** | `&&`, `||`, `!` | Boolean gates |

**CRITICAL: `==` vs `===`**

```javascript
5 == "5"      // true  ← == coerces "5" to 5 ⚠️
5 === "5"     // false ← === checks value AND type ✅

"" == 0       // true  ← TRAP: "" coerces to 0 😬
null == 0     // false ← null is special, doesn't coerce
null >= 0     // true  ← >= uses different coercion rules 🤯

// Always use ===
```

**Rule:** Use `===` by default. Use `==` only for the intentional `x == null` check.

---

## 🔄 LEARNING PIPELINE

```
┏━━━━━━━━━━━━┓
┃ Chapter 1  ┃  → Learn console.log (output)
┃ HelloWorld ┃
┗━━━━━━━━━━━━┛
       ↓
┏━━━━━━━━━━━━┓
┃ Chapter 2  ┃  → Learn let & block scope
┃ let/Scope  ┃
┗━━━━━━━━━━━━┛
       ↓
┏━━━━━━━━━━━━┓
┃ Chapter 3  ┃  → Learn naming rules & comments
┃ Identifiers┃
┗━━━━━━━━━━━━┛
       ↓
┏━━━━━━━━━━━━┓
┃ Chapter 4  ┃  → Learn data types & quirks
┃ Literals   ┃
┗━━━━━━━━━━━━┛
       ↓
┏━━━━━━━━━━━━┓
┃ Chapter 5  ┃  → Learn operators & coercion
┃ Operators  ┃
┗━━━━━━━━━━━━┛
       ↓
   Master: Control flow, functions, objects
```

---

## 📖 IQ_NOTES REFERENCE LIBRARY

**Standalone concept explainers** with tables, code walkthroughs, diagrams, and TL;DR.

| File | Topic | Key Takeaway |
|------|-------|--------------|
| [`Source_Code_ByteCODE_Binary_IQ.md`](Source_Code_ByteCODE_Binary_IQ.md) | Source → Bytecode → Binary | V8 compiles JS → bytecode → native code |
| `01_Identifier_Rules.md` | Legal identifier names | Start with letter, `_`, or `$`; Unicode OK |
| `02_Keyword_Notes.md` | Reserved keywords | Keywords can't be used as identifiers |
| `03_commands_mac.md` | VS Code shortcuts (macOS) | `Cmd+/`, `Cmd+Shift+P`, etc. |
| `03_commands_win.md` | VS Code shortcuts (Windows) | `Ctrl+/`, `Ctrl+Shift+P`, etc. |

**How to use:** Pick a topic from the IQ_Notes library for interview prep or quick reference.

---

## 🎓 TL;DR

```
CHAPTER FLOW:
  1️⃣ console.log("Hello")          → Output to terminal
  2️⃣ let x; for loops             → Variables & scope
  3️⃣ Identifier naming rules        → Valid variable names
  4️⃣ Literals & typeof             → Data types
  5️⃣ Operators & ===               → Comparisons & logic

KEY RULES:
  ✅ Always use ===, not ==
  ✅ Use let, not var
  ✅ Identifiers: start with letter, _, or $
  ✅ null vs undefined are different
  ✅ typeof null === "object" is a quirk

NEXT STEPS:
  → IQ_Notes/ for interview prep
  → Run each file: node chapter_XX/file.js
  → Understand coercion traps before building tests
```

---

**Last Updated:** 2026-07-14 | **Author:** Pravalika Mailaram | **Repo:** [playwright-projects](https://github.com/pravalika98150/playwright-projects)
