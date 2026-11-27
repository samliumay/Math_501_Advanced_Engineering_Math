# Learning brief: MATH501 L07 - Linear systems of ODEs

This file is for the LearnHarness teacher agent. Read it first, then read the files it lists.

## Goal

Teach me this lecture of MATH 501 Advanced Engineering Mathematics so that I understand every slide and can answer its questions without help.
Exams are worked problems (ODEs, Laplace transform, series solutions, linear algebra, PDEs). Every step of a solution must be shown.

## Sources, in priority order

1. **Lesson note** (my notes, slide by slide, with 20 check questions and their answers): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_07/MATH501 L07 - Linear systems of ODEs.md`
2. **Quiz note** (20 multiple-choice questions, one per check question, each with a folded answer that explains every option): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_07/MATH501 L07 - Linear systems of ODEs - quiz.md`
3. **Slide images** (one jpg per slide; the lesson note embeds them as `![[<deck>_pNNN.jpg]]`): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/others/slides/math501_lecture_07_math501_chapter_7`
4. **Original slides (PDF):** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_07/Math501 Chapter 7.pdf`
5. **Full step-by-step notes:** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_07/MATH501_Lecture_07_Linear_Systems.pdf` (LaTeX source: `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_07/lecture_07.tex`)

The slides are the authority for what the course teaches. Text marked "(beyond the slides)" in the lesson note is extra explanation: use it to explain, do not present it as exam material.

## What the lecture covers

- 1. Linear systems, matrix form, initial value problems (slides 1-2)
- 2. Existence, superposition, Wronskian, fundamental matrix (slides 3-4)
- 3. Homogeneous systems with a constant matrix (slides 5-6)
- 4. Nonhomogeneous systems, variation of parameters (slides 7-10)

## Known errors and traps in the sources (do not teach the errors)

- **Watch out:** Superposition is for the homogeneous system only. The "one point is enough" rule needs the columns to be solutions of the same system.
- **Watch out:** This chapter treats only the case of distinct real eigenvalues. The rule says nothing about repeated or complex eigenvalues.
- **Watch out:** - Order of multiplication: $\Phi^{-1}$ before $F$, and $\Phi$ in front of the integral. - For an IVP with a forcing term, find $C$ after adding $X_p$. - The eigenvalue order must match the eigenvector order in $\Phi$.

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
