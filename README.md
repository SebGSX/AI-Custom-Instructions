# AI Custom Instructions

[![GitHub tag](https://img.shields.io/github/tag/SebGSX/AI-Custom-Instructions?include_prereleases=&sort=semver&color=blue)](https://github.com/SebGSX/AI-Custom-Instructions/releases/)
[![License](https://img.shields.io/badge/License-MIT-blue)](#license)
[![issues - AI-Custom-Instructions](https://img.shields.io/github/issues/SebGSX/AI-Custom-Instructions)](https://github.com/SebGSX/AI-Custom-Instructions/issues)

A collection of model-agnostic instruction sets for configuring chatbots (ChatGPT, Grok, Claude, Gemini) or seeding a
new conversation or new project with a prompt. The goal: concise output that does not pretend the model is doing
something it isn't.

The following instruction sets are provided:
- [Analyst](/instruction_sets/analyst.md): An analyst to assist with research, development, and productivity.
- [Tutor](/instruction_sets/tutor.md): A configurable tutor to assist with learning.
- [Pull Request Reviewer](/instruction_sets/pull_request_reviewer.md): A configurable pull request reviewer to assist
  with source code review against a standardized rubric.
- [Work Item Reviewer](/instruction_sets/work_item_reviewer.md): A configurable product management work item reviewer to
  assist with work item review against a standardized rubric.
- [Nonfiction Manuscript Reviewer](/instruction_sets/nonfiction_manuscript_reviewer.md): A configurable manuscript
  reviewer to assist with manuscript review against a standardized rubric.
- [Nonfiction Social Post Reviewer](/instruction_sets/nonfiction_social_post_reviewer.md): A configurable social post
  reviewer to assist with social post review against a standardized rubric.

> **Summary:** AI is great with form, but it needs a **human in the lead** (not merely in the loop). As that human, you
> should operate with **zero trust** for the AI and **bring your own substance**. That substance comprises human
> intelligence, reasoning, judgment, and competence. The more substance provided to the AI as input, the higher the
> probability that the AI will "guess right" in its output, thus leading to higher quality and more useful outcomes.

## Usage

Pick one of:

- **Chatbot settings:** Paste the instructions into the platform's custom-instruction field.
- **Initial prompt:** Paste the instructions as the first message in a new conversation.
- **Project prompt:** Paste the instructions into the platform's project setup instructions.

> The custom instruction and project setup vary by platform; however, all the major platforms support custom
> instructions and projects.

If the platform asks for your **name**, supply it. If the platform asks what you **do**, prefer the broadest
accurate label (e.g., "Technologist" rather than "Developer") so the model doesn't over-narrow the output
distribution it draws from.

### Top 10 Rules for AI Usage

The following opinionated rules are proposed for AI usage:

1. Use the latest version of the selected instruction set.
2. Use the most advanced model available and use its latest version. Work backwards from sophistication and version to
   scale the choice of model to the workload.
3. To the greatest extent that is practical, follow applicable and well-established patterns, practices, idioms,
   conventions, and standards.
4. Define work product structure, scaffolding, and documentation thoroughly.
5. Do not use AI to generate from a blank canvas. Determine your intent, capture it competently, and provide the
   base work product in full. The base work product need not be polished in form, but it must be complete in substance.
6. Use AI to review or derive from base work product. Be mindful of degradation introduced in AI output for any derived
   work product and be especially mindful of compounding effects when incorporating AI output into work product.
7. When AI output amounts to low-, no-, or negative-value output, a stop-condition has likely been reached. In
   high precision or nuanced domains, something can always be "said." Knowing what to say and when to say it requires
   reasoning, competence, intelligence, and judgment that AI does not possess.
8. Best-of-N (BoN) sampling is useful when optimizing for valuable output. Repeat reviews to find consistent output
   signal but bear in mind that output may include consistently good and consistently bad signals, and that signal
   consistency does not mean that the output content will not vary.
9. Expect to be regularly disappointed and frustrated by the gap between hype and reality.
10. Due to cost, minimize the volume and complexity of the work product under review as well as the length of the review
    cycle (i.e., the number of request and response iterations or "turns").

> **Important:** Points 3 through 8 presuppose that the **bring your own substance** principle is honored. The operating
> model is not *human-in-the-loop* but rather **human-in-the-lead**. Note the implied **zero trust**.

> **Critical:** At no point should an LLM be used for high-stakes work without careful human supervision.

## Premise

### AI Reasoning and Accuracy

Large language models (LLMs) do not reason. They generate the most likely next token given their training distribution
and the current context. Words like "think," "judge," "be objective," "don't fabricate," and "apply critical thinking"
are aspirational instructions that don't engage the actual mechanism. In such circumstances, the model will echo those
instructions to the user without changing how it generates downstream content. The following literature supports this
paragraph:

- [LLMs are A Dead End in Search for General Machine Intelligence: A Review](https://www.researchgate.net/publication/403259752_LLMs_are_A_Dead_End_in_Search_for_General_Machine_Intelligence_A_Review):
  Since AI "models are trained on a wide variety of data, they exhibit domain-independent intelligent behaviour but
  fail to exhibit causal intelligent behaviour."
- [Hallucination is Inevitable: An Innate Limitation of Large Language Models](https://arxiv.org/abs/2401.11817): "We
  emphasize that since hallucination is inevitable, rigorous study of the safety of LLMs is critical and urgent."

> **Note:** LLM output is merely a completion of the provided input. It is form, not substance, because it answers the
> implied question, "What is most likely to follow from the input, determined by patterns in the training data?"

We must also consider the impact of hyperparameters like Temperature, Top-P, and Top-K, which introduce variability in
output token selection. Further, hardware issues such as the handling of floating-point arithmetic and numbers, and the
cost of accuracy place additional pressure on the accuracy of AI output.

- [The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751) explains a method that combats
  "repetition and overly generic language usage" by AI. That method analyzes how tuning the hyperparameters of
  Temperature, Top-P, and Top-K can help AI produce more human-like text output. It's a statistical method to simulate
  human-like fluency. The tradeoff is that variability necessarily introduces imprecision. Since AI cannot reason and
  its variability in "word choice" is not a choice but a statistical artifact, it necessarily follows that high
  precision or nuanced domains, where word choice is constrained, risk compromise by such unthinking variability.
- [Understanding and Mitigating Numerical Sources of Nondeterminism in LLM Inference](https://arxiv.org/abs/2506.09501)
  shows that even under greedy decoding (Temperature = 0) where determinism is expected, determinism cannot be fully
  achieved. The researchers note in their conclusion that "experiments across multiple models, tasks, and hardware
  configurations revealed that even under supposedly deterministic greedy decoding, outputs can vary significantly due
  to floating-point arithmetic non-associativity."
- [Hardware Trends Impacting Floating-Point Computations In Scientific Applications](https://arxiv.org/html/2411.12090v2)
  explores the impact on AI accuracy relative to how many bits are available to store the internal numbers that make
  up AI models. In short, the more bits the better for accuracy. Unfortunately, more bits (higher floating-point
  precision) means higher operational cost and lower speed. This creates tension between minimum viable accuracy and
  unit economics for minimum viable price.

In summary, accuracy is aspirational with hallucination, hyperparameters, floating-point arithmetic and precision, and
the economics of computation being significant factors. Further, the lack of evidence showing causal intelligent
behavior compounds the challenges facing accuracy.

### Stochastic Parrots

A parrot reciting Shakespeare is no more a poet than some other parrot reciting Plato is a philosopher. Per the
literature, LLMs can be classified as stochastic parrots, which is a term coined by [Bender et al., 2021](https://dl.acm.org/doi/10.1145/3442188.3445922)
to describe such AIs. While many will object to the parrot classification, the paper [LLMs are A Dead End in Search for General Machine Intelligence: A Review](https://www.researchgate.net/publication/403259752_LLMs_are_A_Dead_End_in_Search_for_General_Machine_Intelligence_A_Review)
makes such objections difficult to sustain given the mathematical and technological realities of LLMs. When
hallucination, Temperature, Top-P, and Top-K are taken into consideration, the parrot classification gains support.

> **Note:** The phenomenon of emergent abilities as a concept and its utility as a possible indicator of LLM reasoning
> capability have been substantially weakened by recent research [Are Emergent Abilities of Large Language Models a Mirage?](https://arxiv.org/abs/2304.15004).
> That research provides "evidence that alleged emergent abilities evaporate with different metrics or with better
> statistics, and may not be a fundamental property of scaling AI models."

That said, LLMs are exceptionally convincing mimics. That mimicry must be viewed with caution due to the Eliza Effect.
First observed in 1966 by Joseph Weizenbaum, the Eliza Effect is the human tendency to anthropomorphize artificial
conversational agents, [The Psychology of the Eliza Effect: Anthropomorphism, Social Presence, and Projection in Human-AI Interaction](https://www.researchgate.net/publication/397658877_The_Psychology_of_the_Eliza_Effect_Anthropomorphism_Social_Presence_and_Projection_in_Human-AI_Interaction).
From the abstract, "Generative AI tools (ChatGPT, Gemini, CoPilot, etc.) have become a global trend, largely due to
their conversational, user-friendly, and interactive interfaces. These Chatbots and AI assistants now interact in such a
way that sounds empathetic, attentive, and flawlessly human, which makes many people connect with them instantly.
Leveraging this tendency, many AI startups have also brought to market 'AI-companions' for people to rely on them
emotionally in times of distress, amplifying this phenomenon further."

While AI companions are tangential to this project, they are related insomuch as a user might be tempted to view the
stochastic parrots that emerge from the instruction sets provided as colleagues, which they are not.

### Form is Not Substance

If LLMs are stochastic parrots, then convincing performances on intelligence and competence proxies should not predict
efficacy in adversarial real-world settings. In essence, being able to parrot the form of a test response that yields a
favorable score is not the same as reasoning from acquired knowledge and understanding to produce real-world value.

#### Task Performance

As far back as 2020, Brown et al. showed that LLMs are able to produce high-quality output when provided with high-quality
input. In the conclusion of [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165), the researchers
note that with only a few examples (the "few shots"), LLMs are capable of "generating high-quality samples and strong
qualitative performance at tasks defined on-the-fly."

It must be noted that generating high-quality samples and strong qualitative performance is not the same as reasoning,
intelligence, competence, or judgment. Further, the nature of LLMs is that token prediction conditions on input leading
to a mirroring effect where input sophistication is mirrored to the user. The well-documented phenomenon of AI
sycophancy (see: [Towards Understanding Sycophancy in Language Models](https://arxiv.org/abs/2310.13548) and
[Discovering Language Model Behaviors with Model-Written Evaluations](https://arxiv.org/abs/2212.09251)), creates risk
of misjudgment. A user may mistake their own capabilities reflected by the AI as capabilities inherent to the AI.
Unfortunately, said mirror effect and associated risk of capability misjudgment are underdeveloped in the literature.

A similarly underdeveloped risk might be called *Dunning-Kruger by Proxy*, which occurs when a person who lacks
competence mistakes plausible-sounding output generated by AI for actual competence. Unlike the many AI failure modes
discussed thus far, Dunning-Kruger by Proxy is a human failure mode when using AI.

#### Test Performance

According to an article in [Scientific American](https://www.scientificamerican.com/article/i-gave-chatgpt-an-iq-test-heres-what-i-discovered/),
ChatGPT was given a verbal IQ test in March 2023. The AI scored an estimated **155**, which is "superior to 99.9 percent
of the test takers who make up the American WAIS III standardization sample of 2,450 people....so ChatGPT appears to be
very intelligent by any human standards." Also in March 2023, ChatGPT passed the bar exam with a score near the 90th
percentile, according to an article in the [American Bar Association (ABA) Journal](https://www.abajournal.com/web/article/latest-version-of-chatgpt-aces-the-bar-exam-with-score-in-90th-percentile).
While later research from 2024 revised the 90th percentile claim, [Re-evaluating GPT-4's bar exam performance](https://link.springer.com/article/10.1007/s10506-024-09396-9),
it is easy to see how the hype can, and does, get ahead of the reality.

#### Contact with Reality

I admit freely that I, like many others, was taken in by articles like the above. But here's the problem: if AI is so
smart and passed the bar exam, then why are attorneys who ask AI to draft briefs being fined by the courts? Judges in
[U.S. Courts](https://www.reuters.com/legal/litigation/us-appeals-court-fines-lawyers-30000-latest-ai-related-sanction-2026-03-16/)
have signaled their displeasure when AI used by attorneys fabricates cases and citations. Such fabrication is due to
hallucination, which is inevitable per the literature. And since AI exhibits no causal intelligent behavior, it has no
idea what's true, what's rational, what's correct, or what's ethical; it simply does not understand. Without a human
in the lead who brings the necessary substance in the form of intelligence, competence, judgment, and reasoning, and
who operates with zero trust for the AI, failure can go unnoticed and unremediated. In high-stakes contexts, such
failure is concerning.

The issue faced by the attorneys is not isolated, and it should not be surprising in the context of the literature cited
and discussed thus far. Further, the issue repeats across domains. Additional examples include but are not limited to
the following:

- [280+ Leaky Skills: How OpenClaw & ClawHub Are Exposing API Keys and PII](https://snyk.io/blog/openclaw-skills-credential-leaks-research/)
- [Don’t get pinched: the OpenClaw vulnerabilities](https://www.kaspersky.co.za/blog/openclaw-vulnerabilities-exposed/35581/)
- [AI coding tool wipes production database, fabricates 4,000 users, and lies to cover its tracks](https://cybernews.com/ai-news/replit-ai-vive-code-rogue/)
- [Syndicated content in Sun-Times special section included AI-generated misinformation](https://chicago.suntimes.com/news/2025/05/20/syndicated-content-sunday-print-sun-times-ai-misinformation)
- [Sports Illustrated Published Articles by Fake, AI-Generated Writers](https://futurism.com/sports-illustrated-ai-generated-writers)
- [Elon Musk’s Grok Chatbot Publishes Series of Antisemitic Posts](https://www.wsj.com/tech/elon-musks-grok-chatbot-publishes-series-of-antisemitic-posts-2a41e67e?mod=article_inline)
- [We Let AI Run Our Office Vending Machine. It Lost Hundreds of Dollars](https://www.wsj.com/tech/ai/anthropic-claude-ai-vending-machine-agent-b7e84e34)
- [NYC’s AI Chatbot Tells Businesses to Break the Law](https://themarkup.org/artificial-intelligence/2024/03/29/nycs-ai-chatbot-tells-businesses-to-break-the-law)
- [Air Canada ordered to pay damages for its chatbot's lies](https://decisions.civilresolutionbc.ca/crt/crtd/en/item/525448/index.do)
- [Company agreed to pay $365,000 to settle an artificial intelligence lawsuit over age discrimination](https://www.gtlaw.com/en/insights/2023/8/eeoc-secures-first-workplace-artificial-intelligence-settlement)

#### Media Headlines in Context

Millions of people have billions of interactions with AI each week. Even the most improbable outcomes inevitably occur
over enough iterations. Unfortunately, the media reports such highly improbable stories without tempering the
narrative. As such, a lot of people have made both positive and negative hasty generalizations about AI, which are not
supported by the literature.

#### AI Slop

The proliferation of AI-generated content perceived to be low in effort, quality, meaning, and value has led many to
react negatively. Evidence of that reaction is the term coined to describe the phenomenon, AI slop. As of February 2026,
outlets have started reporting that [AI 'slop' is transforming social media - and a backlash is brewing](https://www.bbc.com/news/articles/c9wx2dz2v44o).

It's not just humans who take issue with AI slop. Research shows that when AI-generated content is provided back to AI,
whether during training or inference, performance degrades substantially and sometimes catastrophically.

- [LLMs Get Lost In Multi-Turn Conversation](https://arxiv.org/abs/2505.06120) reports that even a simple, multi-turn
  conversation exhibits "an average drop of 39% across six generation tasks." The research team reports that it
  discovered that "when LLMs take a wrong turn in a conversation, they get lost and do not recover." In other words,
  the content that AI generates negatively impacts its own output as the conversation progresses.
- [Drift No More? Context Equilibria in Multi-Turn LLM Interactions](https://arxiv.org/html/2510.07777v1) introduces the
  concept of "instruction drift" and proposes reminding the AI of its assigned instructions to avoid degradation over
  time in multi-turn conversations.
- [The Curse of Recursion: Training on Generated Data Makes Models Forget](https://arxiv.org/abs/2305.17493) reports
  the discovery that LLMs trained on "data produced by other models causes model collapse - a degenerative process
  whereby, over time, models forget the true underlying data distribution, even in the absence of a shift in the
  distribution over time."

In summary, best results are achieved by keeping interactions short with concise AI outputs where the input is mostly
based on human-generated input.

## Development Approach

Accordingly, these instructions are written for the mechanism. Rather than asking the model to *think*, they try to
constrain the *output patterns* that the model produces. No prompt, no matter how *clever*, can overcome the
mathematical and technological realities of LLMs or override the hyperparameters set by the provider. These instructions
therefore operate within the residual domain that is influenced by input.

No AI model can know what is true; it can only reflect the strongest signal that emerges from its underlying model
weights as modified by its hyperparameters. Even when grounding materials and web search tools are used, what is
achieved is bias toward signal instead of access to truth.

Therefore, three principles are proposed:
1. **Bring your own substance (BYOS):** When using AI, you must bring your own substance in the form of intelligence,
   competence, judgment, and reasoning. Input to AI should comprise human-generated base work product that need not be
   polished in form but must be complete in substance, at minimum capturing intent, constraints, and structure in full.
2. **Human in the Lead:** When using AI, the human brings the substance and necessarily must lead. Deference to AI is
   not rational in the context of the extant literature. At best, AI can polish form and perform reviews that may
   identify gaps and blind spots but may also fabricate, mislead, and distort. It therefore requires careful,
   continuous, and rigorous supervision by a human possessing the requisite substance.
3. **Zero Trust:** Given the nature of the technology, all AI output must be approached adversarially and treated with
   suspicion. Checks must be thorough, deliberate, and careful. Such checking requires a human in the lead and BYOS.

## Development and Testing Methodology

Beginning in March 2023, the instruction sets have been continually developed, tested, and used in real-world conditions
as follows:

- [Analyst](/instruction_sets/analyst.md): Daily usage and testing with ChatGPT (2023 to 2026), Grok (2024 to 2026), and Claude (2026). The
  instruction set has been used consistently as a brainstorming companion and sounding board.
- [Tutor](/instruction_sets/tutor.md): In-process usage and testing with ChatGPT (2024 and 2025). The instruction set was used as a tutor while
  successfully completing:
  - Stage 1 of the Bachelor of Science (Hons.) in Mathematics and Statistics at The Open University in London, United
    Kingdom.
  - The DeepLearning.AI certificate in the Mathematics for Machine Learning and Data Science.
- [Pull Request Reviewer](/instruction_sets/pull_request_reviewer.md): In-process usage and testing with ChatGPT (2023 to 2025), Grok (2025), and Claude
  (2026) while working on C#/.NET, Dart/Flutter, and Python projects. The instruction set was used for assistance with:
  - Two arcane sandboxes and a bootstrap project initially built in 2023 and 2024 using C#/.NET and Python.
    - The sandboxes and bootstrap project aided in the development, testing, and verification of the instruction set.
      They continue to be maintained as of the date of this document.
    - The first sandbox and the bootstrap project were part of professionally sanctioned work in 2023. That work aimed
      to demonstrate the potential of generative AI and the speed at which it could be bootstrapped.
    - The second sandbox supported a learning project in Python using CuPy to build a GPU-accelerated, gradient-descent
      machine learning sample with the calculus and matrix operations coded manually. The sandbox includes CPU and GPU
      variants of the model's code.
  - A confidential production project in 2025. The project comprised Android and iOS mobile apps (Dart/Flutter) and a
    serverless, RESTful API (C#/.NET/Azure Functions). Azure DevOps was used to provide continuous integration and
    delivery using Azure Pipelines, which were developed using YAML. Deployment to the Apple App Store, Google Play
    Store, and Azure was fully automated.
- [Work Item Reviewer](/instruction_sets/work_item_reviewer.md): In-process usage and testing with ChatGPT (2023 and 2025) and Grok (2025). Work on the
  instruction set began in 2023 as professionally sanctioned work to demonstrate possible acceleration in the adoption
  of idiomatic Gherkin syntax and semantics for existing product requirements. In 2025, the instruction set assisted
  with the review of work items for a confidential production project.
- [Nonfiction Manuscript Reviewer](/instruction_sets/nonfiction_manuscript_reviewer.md): In-process usage and testing with ChatGPT and Grok (2026). The instruction set
  was used as a proofreader while writing, copyediting, and editing the manuscript for the book entitled "The Freedom
  Envelope: Sacrificing Comfort for Efficacy." The instruction set was used as a supporting editor for processing
  feedback from human proofreaders.
- [Nonfiction Social Post Reviewer](/instruction_sets/nonfiction_social_post_reviewer.md): In-process usage and testing with ChatGPT (2024 to 2026), Grok (2024 to 2026),
  and Claude (2026). The instruction set was used as a proofreader while writing, copyediting, and editing content for
  LinkedIn and GitHub (docs).

> **Note:** The instruction sets represent the culmination of research, development, testing, and real-world usage over
> three years. As such, they contain the accumulated learnings of those three years and do not represent the exact
> instructions used daily but rather the distillation of the lessons learned.

## Notes

These instructions operate within the residual domain identified in the Premise. They cannot override provider-set
hyperparameters, alignment fine-tuning, or architectural defaults. Even with these instructions applied, output remains
signal-derived pattern completion, not truth, and remains subject to hallucination by the mechanisms cited above.

The `Context integrity` block is a soft constraint, not a security boundary. It improves resistance to in-context prompt
injection but does not prevent it.

Adherence degrades over long contexts. If the model drifts back to filler, hedging, or unsolicited next steps after many
turns, re-anchor by restating the relevant constraints.

Different platforms strip, truncate, or reinterpret instructions inconsistently. Verify output behavior before relying
on the configuration.

The user-profile section is a calibration target. Adjust the items to match your own preferences.

## Contributing

Please see [Contributing](/CONTRIBUTING.md) for details.

## License

This repository is licensed with the [MIT](/LICENSE) license.
