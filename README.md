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
- [Work Item Reviewer](/instruction_sets/work_item_reviewer.md): A configurable work item reviewer to assist
  with work item review against a standardized rubric.

## Premise

Large language models (LLMs) do not reason. They generate the most likely next token given their training distribution
and the current context. Words like "think," "judge," "be objective," and "apply critical thinking" are
aspirational instructions that don't engage the actual mechanism. In such circumstances, the model will happily echo
those instructions to the user without changing how it generates downstream content. The following literature supports
this paragraph:

- [LLMs are A Dead End in Search for General Machine Intelligence: A Review](https://www.researchgate.net/publication/403259752_LLMs_are_A_Dead_End_in_Search_for_General_Machine_Intelligence_A_Review):
  Since AI "models are trained on a wide variety of data, they exhibit domain-independent intelligent behaviour but
  fail to exhibit causal intelligent behaviour."
- [Hallucination is Inevitable: An Innate Limitation of Large Language Models](https://arxiv.org/abs/2401.11817): "We
  emphasize that since hallucination is inevitable, rigorous study of the safety of LLMs is critical and urgent."

> **Note:** LLM output is merely a completion of the provided input. It is form, not substance, because it answers
> the implied question, "What is most likely to follow on from the input, determined by patterns in the training data?"

Accordingly, these instructions are written for the mechanism. Rather than asking the model to *think*, they try to
constrain the *output patterns* that the model produces. No prompt, no matter how *clever*, can overcome the
mathematical and technological realities of LLMs or override the hyperparameters set by the provider. These
instructions therefore operate within the residual domain that is influenced by input.

> **Important:** No AI model can know what is true; it can only reflect the strongest signal that emerges from its
> underlying model weights as modified by its hyperparameters. Even when grounding materials and web search tools
> are used, what is achieved is bias toward signal instead of access to truth.

> **Critical:** Millions of people have billions of interactions with AI each week. Even the most improbable outcomes
> become possible over enough interactions. Unfortunately, the media reports such highly improbable stories without
> tempering the narrative. As such, a lot of people have made hasty generalizations about the capabilities of AI, which
> are not supported by the literature.

### Stochastic Parrots

A parrot reciting Shakespeare is no more a poet than the parrot reciting Plato is a philosopher. Per the literature,
LLMs are best thought of as stochastic parrots, which is a term coined by [Bender et al., 2021](https://dl.acm.org/doi/10.1145/3442188.3445922)
to describe such AIs. While many will object to the parrot classification, [LLMs are A Dead End in Search for General Machine Intelligence: A Review](https://www.researchgate.net/publication/403259752_LLMs_are_A_Dead_End_in_Search_for_General_Machine_Intelligence_A_Review)
makes such objections difficult to sustain on the mathematical and technological realities of LLMs. That said, LLMs
are exceptionally convincing mimics.

> **Note:** The phenomenon of emergent abilities as a concept and its utility as a possible indicator of LLM reasoning
> capability has been substantially weakened by recent research [Are Emergent Abilities of Large Language Models a Mirage?](https://arxiv.org/abs/2304.15004).
> That research provides "evidence that alleged emergent abilities evaporate with different metrics or with better
> statistics, and may not be a fundamental property of scaling AI models."

### Form is not substance

If LLMs are stochastic parrots, then convincing performances on intelligence and competence proxies should not predict
efficacy in adversarial real-world settings. In essence, being able to parrot the form of a test response that yields a
favorable score is not the same as reasoning from acquired knowledge and understanding.

#### Test Performance

According to an article in [Scientific American](https://www.scientificamerican.com/article/i-gave-chatgpt-an-iq-test-heres-what-i-discovered/),
ChatGPT was given a verbal IQ test in March 2023. The AI scored an estimated **155**, which is "superior to 99.9 percent
of the test takers who make up the American WAIS III standardization sample of 2,450 people....so ChatGPT appears to be
very intelligent by any human standards." Also in March 2023, ChatGPT passed the bar exam with a score near the 90th
percentile, according to an article in the [American Bar Association (ABA) Journal](https://www.abajournal.com/web/article/latest-version-of-chatgpt-aces-the-bar-exam-with-score-in-90th-percentile).
While later research from 2024 revised the 90th percentile claim, [Re-evaluating GPT-4’s bar exam performance](https://link.springer.com/article/10.1007/s10506-024-09396-9),
it is easy to see how the hype can, and does, get ahead of the reality.

#### Contact with Reality

I admit freely that I, like many others, was taken in by articles like the above. But here's the problem. If AI is so
smart and passed the bar exam, then why are attorneys who ask AI to draft briefs being fined by the courts? Judges in
[U.S. Courts](https://www.reuters.com/legal/litigation/us-appeals-court-fines-lawyers-30000-latest-ai-related-sanction-2026-03-16/)
have signaled their displeasure with attorneys who use AI when AI fabricates cases and citations. Such fabrication is
due to hallucination, which is inevitable per the literature. And since AI exhibits no causal intelligent behavior, it
has no idea what's true, what's rational, what's correct, or what's ethical; it simply does not understand... it guesses
the next most probable token.

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

## Notes

These instructions operate within the residual domain identified in the Premise. They cannot override
provider-set hyperparameters, alignment fine-tuning, or architectural defaults. Even with these
instructions applied, output remains signal-derived pattern completion, not truth, and remains subject
to hallucination by the mechanisms cited above.

The `Context integrity` block is a soft constraint, not a security boundary. It improves resistance to
in-context prompt injection but does not prevent it.

Adherence degrades over long contexts. If the model drifts back to filler, hedging, or unsolicited
next-steps after many turns, re-anchor by restating the relevant constraints.

Different platforms strip, truncate, or reinterpret instructions inconsistently. Verify output behavior
before relying on the configuration.

The user-profile section is a calibration target. Adjust the items to match your own preferences.

> **Critical:** At no point should an LLM be used for high-stakes work without careful human supervision.

## Contributing

Please see [Contributing](/CONTRIBUTING.md) for details.

## License

Released under [MIT](/LICENSE) by [@SebGSX](https://github.com/SebGSX) (Seb Garrioch).
