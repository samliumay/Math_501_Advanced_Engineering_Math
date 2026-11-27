# Learning brief: MATH501 L02 - Higher order linear ODEs

This file is for the LearnHarness teacher agent. Read it first, then read the files it lists.

## Goal

Teach me this lecture of MATH 501 Advanced Engineering Mathematics so that I understand every slide and can answer its questions without help.
Exams are worked problems (ODEs, Laplace transform, series solutions, linear algebra, PDEs). Every step of a solution must be shown.

## Sources, in priority order

1. **Lesson note** (my notes, slide by slide, with 25 check questions and their answers): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_02/MATH501 L02 - Higher order linear ODEs.md`
2. **Quiz note** (25 multiple-choice questions, one per check question, each with a folded answer that explains every option): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_02/MATH501 L02 - Higher order linear ODEs - quiz.md`
3. **Slide images** (one jpg per slide; the lesson note embeds them as `![[<deck>_pNNN.jpg]]`): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/others/slides/math501_lecture_02_math501_chapter_2`
4. **Original slides (PDF):** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_02/Math501 Chapter 2.pdf`
5. **Full step-by-step notes:** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_02/MATH501_Lecture_02_Higher_Order_Linear_ODEs.pdf` (LaTeX source: `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_02/lecture_02.tex`)

The slides are the authority for what the course teaches. Text marked "(beyond the slides)" in the lesson note is extra explanation: use it to explain, do not present it as exam material.

## What the lecture covers

- 1. Linear dependence, independence, Wronskian (slides 1-2)
- 2. Second order linear ODEs: superposition and basis (slides 2-3)
- 3. Constant coefficients, second order (slides 3-7)
- 4. Constant coefficients, order n (slides 7-9)
- 5. Variation of parameters (slides 10-12)
- 6. Undetermined coefficients (slides 13-18)
- 7. Euler's differential equation (slides 18-22)

## Known errors and traps in the sources (do not teach the errors)

- **Watch out:** - The ratio rule is for two functions only. $1$, $\sin^2x$, $\cos^2x$ are dependent although no two are proportional. - The Wronskian test works in one direction. $W=0$ everywhere does not prove dependence: $x$ and $|x|$ have $W=0$ but are independent on $\mat...
- **Watch out:** Superposition fails for non-homogeneous and for nonlinear equations. Example: $\tfrac12x^2$ and $\tfrac12x^2+x$ both solve $y''=1$, but their sum has second derivative 2.
- **Watch out:** Put the equation in standard form first (coefficient of $y''$ equal to 1), then read $R$. $u_1$ has the minus sign.
- **Slide error:** Slide 10 says "Solving the system of equations (2.5a) and (2.5b)". The system is (2.7a) and (2.7b), the two equations directly above that line.
- **Watch out:** - For a sine or a cosine, always guess both $\cos$ and $\sin$. - For a polynomial of degree $n$, guess all powers down to the constant. - Check the modification rule before substituting. - For $\sec 3x$, $\tan x$, $\ln x$ and similar right sides use variation ...
- **Watch out:** - The auxiliary equation has $(A-1)$, not $A$. - Divide first so that the coefficient of $x^2y''$ is 1. - Repeated root: the second solution has $\ln x$, not an extra factor $x$.

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
