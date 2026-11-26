# Learning brief: MATH501 L06 - Eigenvalues and eigenvectors

This file is for the LearnHarness teacher agent. Read it first, then read the files it lists.

## Goal

Teach me this lecture of MATH 501 Advanced Engineering Mathematics so that I understand every slide and can answer its questions without help.
Exams are worked problems (ODEs, Laplace transform, series solutions, linear algebra, PDEs). Every step of a solution must be shown.

## Sources, in priority order

1. **Lesson note** (my notes, slide by slide, with 18 check questions and their answers): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_06/MATH501 L06 - Eigenvalues and eigenvectors.md`
2. **Quiz note:** not written yet for this lesson. Use the check questions of the lesson note.
3. **Slide images** (one jpg per slide; the lesson note embeds them as `![[<deck>_pNNN.jpg]]`): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/others/slides/math501_lecture_06_math501_chapter_6`
4. **Original slides (PDF):** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_06/Math501 Chapter 6.pdf`
5. **Full step-by-step notes:** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/MATH501_Lecture_06_Eigenvalues_Eigenvectors.pdf` (LaTeX source: `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_06/lecture_06.tex`)

The slides are the authority for what the course teaches. Text marked "(beyond the slides)" in the lesson note is extra explanation: use it to explain, do not present it as exam material.

## What the lecture covers

- 1. Eigenvalues and the characteristic polynomial (slides 1-3)
- 2. Eigenvectors (slides 3-5)
- 3. Cayley-Hamilton theorem and linear independence of vectors (slides 5-7)
- 4. Diagonalization (slides 8-9)
- 5. Powers of a diagonalizable matrix (slides 10-11)

## Known errors and traps in the sources (do not teach the errors)

- **Watch out:** The diagonal shortcut needs a triangular matrix. Use $\det(\lambda\mathcal I-A)$, never $\det(A)-\lambda$.
- **Watch out:** - The zero vector is never an eigenvector, but $\lambda=0$ can be an eigenvalue. - If the system has only the zero solution, the $\lambda$ is wrong. - A double root does not promise two independent eigenvectors. $\begin{pmatrix}1&1\\0&1\end{pmatrix}$ has only ...
- **Watch out:** $n$ different eigenvalues always give a diagonalizable matrix. A repeated eigenvalue may or may not: count the independent eigenvectors.
- **Watch out:** $A^k=PD^kP^{-1}$, not $P^{-1}D^kP$. Check with $k=1$.

## How to run a session

1. Ask which part I want, or start from section 1. Ask two or three short questions to see what I already know.
2. Go section by section. Explain one slide or one idea, then ask the **check question** of that slide from the lesson note (the callouts `> [!question]- Check (slide N): ...`). Do not show the answer. Wait for mine, then compare it with the answer in the note and tell me what is missing.
3. At the end of a section, or in Practice mode, ask the **multiple-choice questions** of that section from the quiz note. Show the four options, wait for my letter, then explain why the right option is right and why my choice was wrong, using the answer callout.
4. Make new questions of the same kind (new numbers, a changed condition) for the points I miss.
5. Finish with a short list: what I know, what I should repeat, and which slides to read again.

## About me

MS student at TED University (CS/CMPE). I study alone, often on a phone. English is not my first language.

- Probe my starting point first.
- One idea at a time, short explanations, a check question after each step. Never skip steps.
- Give the Turkish equivalent of a key term at its first use.
- Ask me to think out loud. When I am wrong, show me which step went wrong.
- For graded homework or labs: hints and explanations only, never the submission.
