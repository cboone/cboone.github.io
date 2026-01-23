---
date: 2025-01-23
description: "Self is a prototype-based programming language that pioneered optimization techniques now used in V8, HotSpot, and SpiderMonkey."
sections: []
title: "Self: The Invisible Language That Powers Modern Computing"
---

Self is a prototype-based programming language created in 1986 by David Ungar and Randall B. Smith at Xerox PARC. Though it never achieved mainstream adoption, Self profoundly influenced modern computing through innovations that power today's JavaScript engines and Java virtual machines.

## Key Technical Contributions

Self pioneered several breakthrough optimization techniques:

- **Maps (Hidden Classes)**: Structures that group objects with identical slot layouts, enabling class-like optimization without language-level classes. V8's documentation notes: "This basic idea is not new—the prototype-based programming language Self used maps to do something similar."

- **Polymorphic Inline Caches**: Introduced by Urs Hölzle, Craig Chambers, and Ungar, these eliminated slow dictionary lookups by generating stub routines for different receiver types, achieving significant performance improvements.

- **Adaptive Optimization**: Hölzle's research demonstrated how compilers could use runtime type information to guide speculative optimization and safely deoptimize when assumptions failed—a foundation for HotSpot and modern JavaScript engines.

## Why Self Failed Commercially

Despite technical brilliance, Self faced substantial barriers. It required approximately 32MB of RAM when typical PCs had 8-16MB. Its image-based development model and GUI-intensive environment confused developers accustomed to file-based workflows. Most importantly, prototype-based programming was unfamiliar to an industry committed to class-based object orientation.

## Lasting Legacy

Self's influence persists through JavaScript and Java. Brendan Eich explicitly adopted Self's prototype model when creating JavaScript in 1995. After Sun cancelled Self, Lars Bak transplanted Self's optimization techniques into Google's V8 engine, which powers modern web applications.
