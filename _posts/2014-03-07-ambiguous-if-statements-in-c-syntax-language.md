---
layout: post
title: "Ambiguous 'if' Statements in C-syntax Language"
categories: article
tags: context free language, teaching
---

Yesterday when I was preparing slides for the recitation, I found a very
interesting usecase for knowing context-free grammar, c.f. Theory of Computation
, Sipser 2013.

<p>$STMT\rightarrow ASSIGN|IF-THEN|IF-THEN-ELSE$</p>
<p>$IF-THEN\rightarrow\mbox{ if condition then }STMT$</p>
<p>$IF-THEN-ELSE\rightarrow\mbox{ if condition then }STMT\mbox{ else }STMT$</p>
<p>$ASSIGN\rightarrow\mbox{ a:=1 }$</p>
<p>$\Sigma=\{\mbox{ if, condition, then, else, a:=1 }\}$</p>
<p>$V=\{STMT, IF-THEN, IF-THEN-ELSE, ASSIGN\}$</p>

It turns out that this grammar is ambiguous. A very quick fix is to eliminate
the ambiguity is to add brackets, by introducing the order of evaluation.
However, we all know that C syntax allows the pair of brackets ommitted. What
if there is ambiguouty when brackets not showing up? This is known as the
[dangling-else problem](http://en.wikipedia.org/wiki/Dangling_else) and most of
C compilers solve it by associating the "else" with the nearest "if".
