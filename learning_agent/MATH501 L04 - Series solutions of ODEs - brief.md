# Learning brief: MATH501 L04 - Series solutions of ODEs

This file is for the LearnHarness teacher agent. Read it first, then read the files it lists.

## Goal

Teach me this lecture of MATH 501 Advanced Engineering Mathematics so that I understand every slide and can answer its questions without help.
Exams are worked problems (ODEs, Laplace transform, series solutions, linear algebra, PDEs). Every step of a solution must be shown.

## Sources, in priority order

1. **Lesson note** (my notes, slide by slide, with 19 check questions and their answers): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_04/MATH501 L04 - Series solutions of ODEs.md`
2. **Quiz note** (19 multiple-choice questions, one per check question, each with a folded answer that explains every option): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/lessons/lecture_04/MATH501 L04 - Series solutions of ODEs - quiz.md`
3. **Slide images** (one jpg per slide; the lesson note embeds them as `![[<deck>_pNNN.jpg]]`): `/home/umaysamli/Desktop/university/ms/semester_2/math_501/MATH_501_Advanced_Engineering_Math/others/slides/math501_lecture_04_math501_chapter_4`
4. **Original slides (PDF):** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lectures/lecture_04/Math501 Chapter 4.pdf`
5. **Full step-by-step notes:** `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_04/MATH501_Lecture_04_Series_Solutions.pdf` (LaTeX source: `/home/umaysamli/Desktop/university/ms/semester_2/math_501/lecture_notes/lecture_04/lecture_04.tex`)

The slides are the authority for what the course teaches. Text marked "(beyond the slides)" in the lesson note is extra explanation: use it to explain, do not present it as exam material.

## What the lecture covers

- 1. Power series, analytic functions, Maclaurin series (slides 1-2)
- 2. Ordinary points and the power series method (slides 2-3)
- 3. Second order examples and an IVP (slides 3-6)
- 4. Singular points, Frobenius' theorem, indicial equation (slides 7-9)
- 5. Frobenius example: roots not differing by an integer (slides 10-12)
- 6. Frobenius example: repeated root (slides 12-15)

## Known errors and traps in the sources (do not teach the errors)

- **Watch out:** Analytic is much stronger than continuous. $|x|$ is continuous at 0 but has no power series about 0.
- **Watch out:** When shifting an index, change both the power and the starting value: $\sum_{n\ge1}na_nx^{n-1}=\sum_{n\ge0}(n+1)a_{n+1}x^n$.
- **Watch out:** - The theorem promises one Frobenius series, not two. - $\ln x$ and $x^r$ with non-integer $r$ need $x>0$. - The top of slide 7 holds the exercise of the previous section.
- **Slide wording (slides 8 and 11):** Case (2.) on slide 8 says "if $r_1-r_2$ is not a positive integer". Read it as "if $r_1-r_2$ is not an integer" (not zero and not a positive integer). For $r_1-r_2=0$ both series would start with the same power $x^{r_1}$ and would be the same solution. That ca...
- **Errors on the slides:** - Slide 15 prints the last term as $\tfrac{137}{432000}x^2$. The power is $x^3$ ($a_5^*$ goes with $x^{5-2}$). - Slide 12 has a slip "$y'=y=\sum\dots$" at the start of this example. It should read $y'=\sum(n+r)a_nx^{n+r-1}$.

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
