---
layout: post
title: Dequantized the Quantum Machine Learning
date: 2026-01-20 10:00:00
description: De-hype the quantum AI. 
tags: quantum ML
categories: posts
thumbnail:
---
This post is just a note for myself but I think it might be also interesting for others. So I put it online.

Amidst the current hype, quantum machine learning (QML) yet hardly provides any conclusive evidence for exponential speedup over classical machine learning. 

Today I ran into a concept of [Dequantizing the QML](https://doi.org/10.1038/s42254-022-00511-w) in Dr. Ewin Tang's article.  
According to the article, the quantum algorithm is ruled out for exponential speedup if it only polynomially outperforms the "dequantized" counterpart. This is usually the case for when the quantum algorithm has classical data as an input. In this case, the QML requires pre-processing of the data to make it suitable for quantum computation, a.k.a state preparation. By allowing the classical algorithm to access the similar pre-processing step, the speedup gap becomes smaller. However, the dequantize framework does not work for when the QML has quantum data, e.g. output from quantum circuits or when amplitudes are used, as an input. 

The key takeaway here is that when people are claiming for any quantum advantage of QML over classical ML, one should ask what is the input, and whether the classical ML can also perform the same task with the help of the same pre-processing step. Being pessimistic does not mean the quantum hype is not real, but rather narrows our focus on the real candidate.
