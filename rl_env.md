# Verifiable RL Environments Are Going to Zero  
*(Eventually)*  

## The Story of Proof-Based Mathematics for LLMs  

The original state of the art relies on human experts (mathematicians) operating within locally consistent systems (math), occasionally augmented by specialized tools like [Lean](https://leanprover.github.io/) or other theorem provers. Large language models (LLMs) enter this landscape by leveraging these tools as environments for both supervised fine-tuning and recursive self-improvement.  

**[GPT-f](https://arxiv.org/abs/2009.03393)** (2020), built on a GPT-3 architecture, was trained on a corpus of AMT proof steps and integrated into large-scale tree search. **[DeepSeek-Prover](https://arxiv.org/abs/2504.21801)** later eliminated tree search, introduced GRPO-based RL, and achieved minor recursive self-improvement by feeding *verified proofs* back into its training loop. **[AlphaProof](https://deepmind.google/discover/blog/ai-solves-imo-problems-at-silver-medal-level/)** reached IMO Silver Medal performance using analogous techniques. As models grow capable enough to supervise their *own* improvement, they eventually outgrow the need for external RL environments. OpenAI reportedly secured IMO Gold using a ["universal verifier"](https://x.com/alexwei_/status/1946477753194484181) for RL, untethered from formal proof systems entirely.  

## Eventually This Is Going to Happen to Everything  

Math’s suitability for this evolution stems from two key properties:  
- **Accretive**: Consuming more math (theorems, lemmas) safely expands the "toolkit" in a consistent system, assuming high recall accuracy.  
- **Locally verifiable**: Validity hinges on checking individual steps, not the entire proof.  

Yet nothing confines this playbook to mathematics. We’re already living **Step 1**: vast ecosystems of approximate recall tools exist across *all* fields—from legal research (Harvey) to programming (Cursor) to real-time news aggregation. While private or rapidly changing data sometimes requires lookup capabilities (e.g., Perplexity), this rarely degrades the core recall experience.  

**Step 2** is now unfolding: startups are building bespoke RL environments with domain-specific verifiers acting as "theorem provers" for law, medicine, finance, and beyond. But **Step 3** is accelerating faster than anticipated. As model capabilities surge, the need for bespoke *external* verifiers plummets.  

## Self-Verification Is Coming, "RL Environments" Are Going  

Progress in self-verification is flying under the radar. **[OpenAI](https://www.theinformation.com/articles/universal-verifiers-openais-secret-weapon)** is reportedly developing a universal verifier as a "secret weapon." Meanwhile, **[Moonshot (Kimi)](https://moonshotai.github.io/Kimi-K2/)**, **[ByteDance](https://arxiv.org/html/2504.13914v1)**, and **[Scale AI](https://arxiv.org/html/2507.17746)** have all published results demonstrating RL in *non-verifiable* domains using **self-critique RL with rubric rewards**.  

If self-verification becomes robustly practical—and evidence suggests it will—the entire industry of verifiable RL "data factories" will collapse like automated theorem provers did for frontier systems: rendered obsolete by the model’s own competence.  

## What This Might Look Like  

You hire a new coworker—Ana, a data analyst. First, you set up her workspace: tools, software access, and hardware. Next, you prepare a welcome package with company info, a first-day agenda, key contacts, a detailed job description, success metrics, and standard operating procedures (SOPs). You also set clear short-term (30-60-90 day) goals. Then, you watch Ana improve daily—answering questions, refining outputs, and exceeding expectations with no input other than answering questions and doing the occassional check in.

Did you hire a human analyst who naturally grows more skilled over time, or did you onboard **"Ana by TextQL (TM)"**—an agent honing itself through self-critique RL on its SOPs? And once the results are indistinguishable, does it even matter?
