---
date: 2025-01-23
description: "How a radical 1980s experiment at Xerox PARC—eliminating classes from object-oriented programming—invented the optimization techniques that power today's JavaScript engines and Java virtual machines"
sections:
  - reports
title: "Self: The invisible language that powers modern computing"
---

Self may be the most influential programming language that most developers have never heard of. Designed between **1985 and 1986** by **David Ungar** and **Randall B. Smith** at Xerox PARC, this prototype-based language pioneered nearly every optimization technique used in today's JavaScript engines and Java virtual machines. Though Self never achieved mainstream adoption, its DNA runs through V8, HotSpot, SpiderMonkey, and JavaScript's object model—making it one of computing's most consequential "failures."

The language emerged from frustration with Smalltalk's complexity. Ungar, fresh from his award-winning Berkeley dissertation on Smalltalk performance, joined Smith at PARC to explore a radical simplification: what if object-oriented programming didn't need classes at all?

## The technical revolution: eliminating classes, inventing modern JIT

Self's core insight was that classes are unnecessary for object-oriented programming. Objects inherit directly from other objects through **prototype delegation**—when a message is sent, the system searches the receiver for a matching slot, then recursively searches parent objects. Creating new objects requires only **cloning** existing ones, not instantiating from abstract class descriptions.

This simplicity created severe performance challenges that drove groundbreaking innovations. The most important was **maps** (now called "hidden classes" in V8): an implementation-level structure that transparently groups objects with identical slot layouts. Since objects cloned from the same prototype typically share structure, maps enabled class-like optimization without language-level classes. [V8's documentation](https://v8.dev/blog/fast-properties) explicitly acknowledges: "This basic idea is not new—the prototype-based programming language Self used maps to do something similar."

**Polymorphic inline caches (PICs)**, introduced by Hölzle, Chambers, and Ungar in 1991, solved the problem of call sites that encounter multiple receiver types. Rather than falling back to slow dictionary lookups, PICs generate stub routines that test receiver types and branch directly to cached methods. This technique achieved **11% median speedup** on typical programs and became standard in all modern JavaScript engines.

The team's work on **adaptive optimization** proved equally transformative. Urs Hölzle's 1994 PhD thesis demonstrated that compilers could use runtime type information collected by PICs to guide aggressive speculative optimization, then safely **deoptimize** when assumptions failed. This approach—compile quickly at first, then recompile hot code with full optimization—became the foundation of Java's HotSpot VM and every major JavaScript engine.

## Why Self remained a research curiosity

Despite its technical brilliance, Self faced formidable adoption barriers. The system required approximately **32MB of RAM**—extraordinary when typical PCs had 8-16MB. Its image-based development model, where programs existed as "snapshots" of memory rather than source files, confused developers trained in file-based workflows. The GUI-intensive environment demanded substantial hardware and made text-based development awkward.

More fundamentally, prototype-based programming was simply unfamiliar. Industry and academia had converged on class-based object orientation, and Self's alternative paradigm required conceptual reorientation that few were willing to undertake. When Sun cancelled the project in favor of Java, Self lost its institutional champion. By the time hardware caught up with Self's requirements, JavaScript and Java had captured mindshare.

## Timeline

<div class="timeline">

<div class="timeline-year">
<div class="timeline-year-label">Predecessors</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1972</span>
<h3 class="timeline-header">Smalltalk created at Xerox PARC</h3>
<p class="timeline-description">Alan Kay, Dan Ingalls, and Adele Goldstein create Smalltalk at Xerox PARC.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1980</span>
<h3 class="timeline-header">Smalltalk-80 released</h3>
<p class="timeline-description">Smalltalk-80 released publicly; becomes dominant dynamic OO language.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1984</span>
<h3 class="timeline-header">Ungar completes Berkeley PhD</h3>
<p class="timeline-description">David Ungar completes Berkeley PhD on Smalltalk performance, introducing Generation Scavenging GC.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1986</span>
<h3 class="timeline-header">Alternate Reality Kit</h3>
<p class="timeline-description">Randall B. Smith creates Alternate Reality Kit at Xerox PARC—a prototype-based predecessor to Self.</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">The PARC Era (1985–1987)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1985</span>
<h3 class="timeline-header">Self design begins</h3>
<p class="timeline-description">Ungar joins Smith at Xerox PARC; they begin designing Self. Smith brings insights from his Alternate Reality Kit prototype system and Ungar contributes deep expertise in dynamic language implementation.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1986</span>
<h3 class="timeline-header">Self language design completed</h3>
<p class="timeline-description">Self language design completed at PARC, establishing the conceptual foundations for prototype-based programming.</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">The Stanford Era (1987–1991)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1987</span>
<h3 class="timeline-header">Implementation begins at Stanford</h3>
<p class="timeline-description">Ungar moves to Stanford as assistant professor; implementation begins with graduate students Craig Chambers and Urs Hölzle. First Self compiler completed.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1987</span>
<h3 class="timeline-header">"Self: The Power of Simplicity" published</h3>
<p class="timeline-description">The foundational paper published at OOPSLA—later named one of three most influential OOPSLA papers (1986–1996).</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1989</span>
<h3 class="timeline-header">"An Efficient Implementation of Self" published</h3>
<p class="timeline-description">Introduces maps (hidden classes)—the optimization technique that would later power V8 and other JavaScript engines.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1990</span>
<h3 class="timeline-header">Self publicly released</h3>
<p class="timeline-description">The team publicly releases Self, demonstrating that a prototype-based language could achieve remarkable performance.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1991</span>
<h3 class="timeline-header">"Polymorphic Inline Caches" paper published</h3>
<p class="timeline-description">Hölzle, Chambers, and Ungar publish the foundational PIC paper at ECOOP, introducing the technique that achieved 11% median speedup.</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">The Sun Microsystems Era (1991–1995)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1991</span>
<h3 class="timeline-header">Self moves to Sun Microsystems</h3>
<p class="timeline-description">Self project moves to Sun Microsystems Labs; Lars Bak and Mario Wolczko join the team.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1992</span>
<h3 class="timeline-header">Chambers completes PhD thesis</h3>
<p class="timeline-description">Craig Chambers completes PhD thesis on Self compiler—a deep dive into compilation strategies.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1993</span>
<h3 class="timeline-header">Morphic UI framework developed</h3>
<p class="timeline-description">John Maloney and Randall B. Smith develop Morphic UI framework—the direct-manipulation UI that influenced Squeak.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1994</span>
<h3 class="timeline-header">Hölzle completes PhD thesis</h3>
<p class="timeline-description">Urs Hölzle completes "Adaptive Optimization for Self"—foundational work on type feedback and deoptimization that became the basis for HotSpot and modern JavaScript engines.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1995</span>
<h3 class="timeline-header">Self 4.0 released; project ends</h3>
<p class="timeline-description">Self 4.0 released with redesigned programming environment. Java launched; Sun redirects resources. Self project officially ends at Sun.</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">Immediate Descendants (1993–1995)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1993</span>
<h3 class="timeline-header">NewtonScript created</h3>
<p class="timeline-description">NewtonScript created for Apple Newton PDA—adopts Self's prototype model, demonstrating that prototype-based programming could work on resource-constrained devices.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1993</span>
<h3 class="timeline-header">Lua 1.0 released</h3>
<p class="timeline-description">Lua 1.0 released—later adopts Self-style delegation via metatables.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1995</span>
<h3 class="timeline-header">JavaScript created</h3>
<p class="timeline-description">Brendan Eich creates JavaScript at Netscape—directly adopts Self's prototype-based inheritance. He later wrote: "I'm not proud, but I'm happy that I chose Scheme-ish first-class functions and Self-ish prototypes as the main ingredients."</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">The VM Legacy (1994–2008)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1994</span>
<h3 class="timeline-header">Animorphic Systems founded</h3>
<p class="timeline-description">Hölzle and Bak co-found Animorphic Systems; build Strongtalk VM using Self techniques.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1997</span>
<h3 class="timeline-header">Sun acquires Animorphic</h3>
<p class="timeline-description">Sun acquires Animorphic Systems, bringing Self's optimization techniques into the Java ecosystem.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">1999</span>
<h3 class="timeline-header">Java HotSpot VM released</h3>
<p class="timeline-description">Java HotSpot VM released—directly derived from Self/Strongtalk technology.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2002</span>
<h3 class="timeline-header">Io language created</h3>
<p class="timeline-description">Steve Dekorte creates Io language—explicitly inspired by Self.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2006</span>
<h3 class="timeline-header">Google hires Lars Bak</h3>
<p class="timeline-description">Google hires Lars Bak to build Chrome's JavaScript engine.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2008</span>
<h3 class="timeline-header">V8 JavaScript engine released</h3>
<p class="timeline-description">V8 released—implements Self's hidden classes, inline caches, and adaptive optimization. The techniques that make JavaScript fast enough to power modern web applications all originated in Self research.</p>
</div>

</div>

<div class="timeline-year">
<div class="timeline-year-label">Modern Era (2006–Present)</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2006</span>
<h3 class="timeline-header">Self 4.3 released</h3>
<p class="timeline-description">First release in 11 years.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2010</span>
<h3 class="timeline-header">Self 4.4 released</h3>
<p class="timeline-description">Community members release Self 4.4 with Linux support.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">2017</span>
<h3 class="timeline-header">Self 2017.1 released</h3>
<p class="timeline-description">New versioning scheme adopted.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">August 2024</span>
<h3 class="timeline-header">Self 2024.1 released</h3>
<p class="timeline-description">Released with FreeBSD and NetBSD support.</p>
</div>

<div class="timeline-entry">
<span class="timeline-marker"></span>
<span class="timeline-date">Present</span>
<h3 class="timeline-header">Self's legacy continues</h3>
<p class="timeline-description">Self maintained on GitHub; V8 and HotSpot continue to use Self's optimization techniques in billions of devices worldwide.</p>
</div>

</div>

</div>

## Key academic papers and resources

**Foundational Papers**

- [Self: The Power of Simplicity](https://bibliography.selflanguage.org/_static/self-power.pdf) — Ungar & Smith, OOPSLA 1987 (revised 1991). The original paper introducing prototype-based OOP.
- [An Efficient Implementation of Self](https://bibliography.selflanguage.org/_static/implementation.pdf) — Chambers, Ungar & Lee, OOPSLA 1989. Introduces maps (hidden classes).
- [Optimizing Dynamically-Typed Object-Oriented Languages With Polymorphic Inline Caches](https://bibliography.selflanguage.org/_static/pics.pdf) — Hölzle, Chambers & Ungar, ECOOP 1991. The foundational PIC paper.

**Theses & Extended Works**

- [Adaptive Optimization for Self: Reconciling High Performance with Exploratory Programming](https://bibliography.selflanguage.org/_static/urs-thesis.pdf) — Urs Hölzle, Stanford PhD Thesis, 1994. Comprehensive treatment of type feedback and deoptimization.
- [The Design and Implementation of the Self Compiler](https://bibliography.selflanguage.org/_static/craig-thesis.pdf) — Craig Chambers, Stanford PhD Thesis, 1992. Deep dive into compilation strategies.

**UI and Environment**

- [Self: The Video](https://www.youtube.com/watch?v=Ox5P7QyL774) — Stanford demonstration video showing the live programming environment.
- [Morphic: The Self User Interface Framework](https://bibliography.selflanguage.org/_static/morphic.pdf) — Maloney & Smith, 1995. The direct-manipulation UI that influenced Squeak.

**Official Resources**

- [Self Language Website](https://selflanguage.org/) — Downloads, documentation, and current releases.
- [Complete Self Bibliography](https://bibliography.selflanguage.org/) — Full collection of all Self papers with PDF links.
- [Self GitHub Repository](https://github.com/russellallen/self) — Current source code and development.

## Conclusion

Self represents a fascinating paradox: a language that "failed" commercially yet became foundational to modern computing. The techniques Ungar, Smith, Chambers, Hölzle, and Bak developed at PARC, Stanford, and Sun now execute every time JavaScript runs in a browser, Java runs on a server, or any JIT compiler optimizes hot code paths. Self's vision of "simplicity, uniformity, concreteness, and liveness" lives on not in Self programs but in the infrastructure that powers billions of devices daily.

The language also demonstrated that radical simplification can drive innovation. By eliminating classes, Self forced its implementers to invent new optimization strategies—strategies that proved more powerful and general than the class-based approaches they replaced. Self's lesson for language designers: constraints can catalyze creativity, and today's research curiosity may become tomorrow's invisible foundation.
