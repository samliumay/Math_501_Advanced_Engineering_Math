# Learning brief: MATH501 L03 - The Laplace transform

This file is for the LearnHarness teacher agent. Read it first, then read the files it lists.

## Goal

Teach me this lecture of MATH 501 Advanced Engineering Mathematics so that I understand every slide and can answer its questions without help.
Exams are worked problems (ODEs, Laplace transform, series solutions, linear algebra, PDEs). Every step of a solution must be shown.

## Sources, in priority order

1. **Lesson note** (my notes, slide by slide, with 35 check questions and their answers): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_03/MATH501 L03 - The Laplace transform.md`
2. **Quiz note** (35 multiple-choice questions, one per check question, each with a folded answer that explains every option): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_03/MATH501 L03 - The Laplace transform - quiz.md`
3. **Slide images** (one jpg per slide; the lesson note embeds them as `![[<deck>_pNNN.jpg]]`): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/others/slides/math501_lecture_03_math501_chapter_3`
4. **Original slides (PDF):** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_03/Math501 Chapter 3.pdf`
5. **Full step-by-step notes:** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_03/MATH501_Lecture_03_Laplace_Transform.pdf` (LaTeX source: `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_03/lecture_03.tex`)

The slides are the authority for what the course teaches. Text marked "(beyond the slides)" in the lesson note is extra explanation: use it to explain, do not present it as exam material.

## What the lecture covers

- 1. Definition and transforms from the definition (slides 1-3)
- 2. Existence, linearity, table, multiplying and dividing by t (slides 4-6)
- 3. The inverse Laplace transform (slide 7)
- 4. Solving initial value problems (slides 8-11)
- 5. First shifting theorem (slides 11-12)
- 6. Heaviside function and pulses (slides 12-13)
- 7. Second shifting theorem (slides 14-15)
- 8. Convolution (slides 16-18)
- 9. Dirac delta function (slides 18-20)
- 10. Systems of ODEs (slides 21-22)

## Known errors and traps in the sources (do not teach the errors)

- **Slide error (slide 2):** In the line "If $s>a$" the slide writes $-\dfrac1s e^{-(s-a)R}-\dfrac{1}{a-s}$. This is a misprint: the factor in front of the exponential must be $\dfrac{1}{a-s}$ instead of $-\dfrac1s$, as in the line above it, so the bracket should read $\dfrac{1}{a-s}e^{-(...
- **Watch out:** Do not drop the initial value terms. $\mathcal L[y'']$ contains $-sy(0)$ and $-y'(0)$. They vanish only when the initial values are zero.
- **Watch out:** - Shift the argument too: the inverse is $H(t-a)f(t-a)$, not $H(t-a)f(t)$. - The slide says "a real constant $a$". The proof needs $a\ge0$.
- **Watch out:** $\mathcal L[fg]\neq F\,G$. Example: $\mathcal L[1\cdot1]=\tfrac1s$, but $\tfrac1s\cdot\tfrac1s=\tfrac{1}{s^2}$.
- **Watch out:** $\mathcal L[\delta(t)]=1$ but $\mathcal L[1]=\tfrac1s$.

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
