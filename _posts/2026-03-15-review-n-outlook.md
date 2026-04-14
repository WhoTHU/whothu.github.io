---
layout: post
title:  My Research Journey Part 2 - Lessons of The Curse of Goodhart’s Law and the Duality
date:   2026-03-15 16:37:00
description: 
tags: random research
categories: sample-posts
---

I've learned and realized two important lessons from my research journey, which I think are crucial for the future research. The first one is from **brain-inspired research**, which is that we need to find the right research paradigm and the right research questions, rather than just trying different methods. The second one is from **adversarial examples research**, which is that we need to be careful about the "Goodhart's Law" when we are trying to solve a problem, and we need to distinguish between "research questions" and "engineering targets". I'll majorly talk about the second one in this post.

### 1. Review: The Curse of Goodhart’s Law and the Duality

<!-- As I reflect on my research journey thus far, I see a path defined by two distinct yet unified routes. One involves challenging the most fundamental **Machine Learning Theories**, while the other builds upon existing frameworks to address the critical issue of **Robustness**.  -->

In my view, robustness is not merely a sub-discipline; it is the "litmus test" for a theorey or paradigm. If they cannot account for the inherent brittleness of the resulting models, it is a sign that our fundamental understanding is still incomplete. However, I believe that much of the research in this area has been misaligned due to a manifestation of **Goodhart’s Law**:
<div style="text-align: center; font-style: italic; margin-bottom: 20px;">
  "When a measure becomes a target, it ceases to be a good measure."
</div>

#### The curse of Goodhart’s Law in Adversarial Examples Research

<!-- Looking back at the last decade of research, the field of **Adversarial Examples**—where microscopic, intentional perturbations (noise) cause a model to fail—has been a primary focus. However, I believe much of this collective effort has been "misaligned." -->

One interpretation of the cause of adversarial examples is that deep learning models are "overfitting" to the training goal (e.g., minimizing cross-entropy loss on the training data), and thus they learn "spurious features" that are not robust. Under this perspective, adversarial examples are actually **emerging because of Goodhart’s Law**: we are optimizing for a specific training objective, and the model finds "shortcuts" that work well on the training data.

<!-- Adversarial examples both **emerge because of Goodhart’s Law** and **remain trapped within it**. -->

The curse is that when we try to fix adversarial examples, we actually fall into the same trap again. We created a new metric—**Adversarial Robustness** (performance under worst-case small perturbations)—and began optimizing for that specifically. By treating a symptom as the ultimate goal, we **fell into the same cycle**. The robustness metric itself is not the destination; its true value lies in revealing the structural flaws of how deep learning algorithms perceive the world. Among all the defense methods proposed in the past decade, the most effective (and the only effective) one is **Adversarial Training**, which directly optimizes the robustness metric bruteforcely. However, it brings limited insights to solving slightly different problems, such as other types of perturbations, or larger perturbations, or the general out-of-distribution generalization problem, or the robustness of other domains such as LLMs.

#### The Duality: Research Questions vs. Engineering Targets

During my research, I have found it essential to distinguish between two types of objectives. Both are necessary, but they serve different roles in the research ecosystem:

* **Research Questions :** Why do these robustness issues arise in the first place? How do we propose a general algorithm that avoids these issues by design? This is about long-term impact and seeking fundamental truths.
* **Engineering Targets :** How do we optimize a specific model to meet the requirements for immediate deployment? This is about scale, efficiency, and reliability in the present.

For adversarial examples, I would argue that the Research Question should be much more important than the Engineering Target. It was originally proposed as a phenomenon that revealed a fundamental vulnerability of deep learning models, while its real-world impact is limited. While almost all the research efforts have been focused on the Engineering Target of "optimizing the robustness metric", it has been off the track at the first place. It is somewhat useful, as it does provide some insights to the problem, and is potentially useful for other similar problems that has more real-world impact, such as the security issues of LLMs.

For LLMs, the situation is different. The real-world impact of security issues is much more significant, and thus the Engineering Target to this specific problem is more urgent. It is understandable that this field has been heavily skewed toward Engineering Targets, given the immediate pressures of real-world deployment. But without a parallel focus on "Research Questions," we risk perpetually patching symptoms without ever addressing the underlying causes.

---

### 2. Outlook: The Unified Frontier of Safety, Hallucination, and World Models

As we look toward the future, the rise of Large Language Models (LLMs) and the pursuit of **World Models** have turned robustness from a theoretical puzzle into a high-stakes reality. A key insight in my current outlook is that **generalized hallucination and safety/security issues are fundamentally unified.** They are two sides of the same coin: a failure of the model to align its internal representation with the causal structure of reality. Whether a model is misled by a malicious prompt (Security) or spontaneously generates false information (Hallucination), the root cause is a "brittle" World Model. The model relies on spurious statistical correlations rather than an invariant understanding of the world.


#### The Engineering Outlook (Immediate Impact)
Current efforts to secure these models:
* **Reinforcement Learning & Alignment:** Training models to follow safety/robust guidelines or pursue "truthfulness" by using human feedback, reward models, or adversarial training to directly optimize for relevent metrics.
* **Safety Guardrails:** Proactively stress-testing models with adversarial prompts to build external filtering layers, using detection or reasoning modules to catch and mitigate harmful outputs.
* **Agentic Design:** Refining workflow and system architecture to minimize attack surfaces.

#### The Research Outlook (Foundational Shift)
Potential directions to solve these problems:
* **Robust World Models:** Building systems that internalize the underlying rules and causal structures of reality, making them naturally resistant to both noise and logic collapses.
* **Causal Inference & Invariant Learning:** Moving beyond "statistical correlation" to ensure models ignore "shortcuts" that lead to both hallucinations and adversarial vulnerabilities.
* **Mechanistic Interpretability:** Peering into the "black box" to understand how internal circuits represent "truth" versus "statistical noise." This might give us insights into how to design models that are inherently more robust.

---

### 3. A Call for a Holistic View of the Field

By sharing this review and outlook, I hope to encourage a more holistic view of the field. While the immediate pressures of deployment will always drive a focus on "Engineering Targets," we must not lose sight of the "Research Questions" that will ultimately lead us to a reliable and beneficial AGI. 

---
I used LLMs for the help in refining the expression and structure of this post.