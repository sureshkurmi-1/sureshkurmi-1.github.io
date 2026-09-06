---
layout: post
date: 2026-09-06
permalink: /2026/09/06/why-upstream-first-development-matters/
categories: [Linux Graphics, Open Source, Engineering Leadership]
tags: [Linux, Upstream, DRM, KMS, GPU, Display Graphics, CI, Simulation, AI, Semiconductor Software]
---

# Why Upstream-First Development Matters

Over the years, working across semiconductor software, embedded systems, Linux platforms and Display Graphics has changed the way I think about product development.

One principle has become increasingly clear to me:

**Upstream development is not just an open-source practice. It is a product engineering strategy.**

In the Linux graphics world, where kernel, firmware, drivers, Mesa, display frameworks and applications continuously evolve together, developing with the upstream ecosystem in mind can fundamentally change how products are designed, validated and scaled.

For me, upstream-first development is about bringing the product engineering lifecycle closer to the real ecosystem in which the software will ultimately live.

---

## From Product-Specific Development to Platform Thinking

In traditional product development, it is natural to optimize for the immediate product.

A feature is developed for a particular platform, validated against a particular hardware configuration and integrated into a product branch. This can work well for a single product.

The challenge appears when the same technology needs to support multiple products, multiple hardware generations and multiple software configurations.

The complexity starts multiplying.

A driver change may need to be maintained across several branches. A workaround developed for one product may become a dependency for another. Interfaces can diverge. Validation becomes increasingly expensive.

Over time, engineering teams can spend a significant amount of effort maintaining differences instead of building new capabilities.

My experience with Linux Display Graphics has reinforced for me that this is where an upstream-first mindset becomes particularly valuable.

Instead of asking:

> "How do we make this work for this product?"

I increasingly prefer asking:

> **"How do we solve this in a way that can become part of the common platform?"**

That is a very different engineering question.

---

## Why Graphics Makes This Especially Important

Linux graphics is a good example of a highly interconnected software ecosystem.

A modern graphics feature rarely belongs to a single component.

It can involve:

- GPU hardware
- Firmware
- Linux kernel driver
- DRM
- KMS
- Memory management
- Display pipelines
- Mesa
- Wayland or other compositors
- User-space applications
- Validation and CI infrastructure

The interfaces between these components matter as much as the individual implementation.

The Linux DRM architecture itself provides common infrastructure for memory management, command submission, synchronization, framebuffer handling, modesetting and other graphics functions. :contentReference[oaicite:0]{index=0}

This means that a locally optimized solution can easily become a system-level problem if it does not fit the architecture of the broader ecosystem.

The upstream community forces us to think about those interfaces early.

That is a feature, not a limitation.

---

## Upstream Is an Engineering Feedback Loop

One of the biggest benefits I see in upstream-first development is the feedback loop.

When development happens close to upstream, engineers get feedback from people working on adjacent parts of the stack.

A kernel change may expose a user-space requirement.

A Mesa change may expose a kernel interface problem.

A display feature may reveal a synchronization or memory-management issue.

A validation failure may identify an architectural assumption that was wrong.

This creates an engineering loop:

**Design → Implementation → Upstream Review → Integration → CI → Feedback → Refinement**

That loop is extremely valuable.

It moves some of the discovery of architectural problems earlier in the development lifecycle.

The Linux DRM development process also explicitly encourages design discussion and RFCs for complex work, particularly when new user-space interfaces are involved. :contentReference[oaicite:1]{index=1}

From my perspective, this is essentially **left-shifting system-level validation**.

---

## Left Shift: Validate the Architecture Earlier

"Shift left" is often discussed in the context of testing.

I believe the same concept should apply to architecture.

If an interface is going to be difficult to upstream six months from now, it is much better to discover that during the design phase.

If a proposed uAPI does not fit the Linux graphics model, finding that during upstream review is much cheaper than discovering it after several products have already integrated it.

The DRM community has deliberately developed strong expectations around graphics uAPI. New kernel interfaces are expected to have corresponding open-source user-space implementations and appropriate review and validation. :contentReference[oaicite:2]{index=2}

That process can sometimes feel slower initially.

But I see it differently.

**The objective is not to move slower. The objective is to avoid moving quickly in the wrong direction.**

---

## Scaling Across Multiple Products

This becomes even more important when an organization has multiple products.

Imagine three product teams independently implementing the same capability.

Without a common upstream strategy, the organization may eventually have:

- Three implementations
- Three validation strategies
- Three maintenance branches
- Three sets of workarounds
- Multiple integration points

The engineering organization has effectively multiplied the cost of the same feature.

An upstream-first approach tries to reverse that equation.

The goal becomes:

**One architectural solution → shared upstream implementation → multiple product integrations**

The products still have differentiation.

But the foundational software becomes increasingly common.

This is one of the most powerful aspects of open-source platform engineering.

---

## Upstream Can Become a Scaling Mechanism

I see upstream not simply as a destination for patches, but as a mechanism for organizational scaling.

When common functionality moves into upstream projects, product teams do not need to independently own every piece of the technology stack.

Instead, engineering investment can move toward:

- Product differentiation
- Hardware optimization
- Performance
- Power efficiency
- User experience
- Platform integration
- New capabilities

while common infrastructure continues to evolve in the upstream ecosystem.

This is particularly relevant for semiconductor companies supporting multiple silicon generations.

The more products an organization has, the more expensive duplicated software becomes.

**Upstream can turn duplicated product engineering into shared platform engineering.**

---

## The Cost of Carrying Private Code

There is another side to this discussion.

Every private patch has a maintenance cost.

It has to be:

- Rebasing against newer kernels
- Revalidated
- Debugged
- Integrated with other changes
- Maintained across product branches
- Understood by future engineers

Graphics software makes this particularly challenging because the interfaces between kernel and user space evolve continuously.

The Linux graphics ecosystem also has explicit expectations around maintaining compatibility and avoiding regressions, while recognizing the close coupling between kernel and open-source user space. :contentReference[oaicite:3]{index=3}

That means the cost of staying outside upstream can increase over time.

The real cost is therefore not just the engineering effort required to create a private patch.

It is the **lifetime cost of owning the divergence**.

---

## Simulation Can Change the Equation

One area where I see significant potential is simulation.

Linux provides an unusually rich environment for experimenting with system software without always requiring the final hardware to be available.

For graphics, this opens interesting possibilities.

We can think about validating parts of the software stack using:

- Virtual devices
- Software-rendered environments
- Kernel virtualisation
- Automated CI systems
- Hardware models
- Emulation
- Synthetic workloads
- Fault injection
- Performance models

The goal is not to replace real hardware validation.

The goal is to **move more validation earlier**.

If a significant portion of the software architecture can be exercised before silicon availability, the development cycle can become much more parallel.

That can have a major impact on semiconductor product schedules.

---

## Linux as a Simulation and Validation Platform

I see Linux itself becoming increasingly important as a platform for this kind of engineering.

A software stack can be exercised at different levels:

**Application**

↓

**Compositor / User Space**

↓

**Mesa / Graphics Libraries**

↓

**DRM / Kernel**

↓

**Virtual or Simulated Hardware**

↓

**Real Hardware**

This creates opportunities to validate interfaces and system behaviour progressively.

For example, the Linux graphics ecosystem already uses CI infrastructure to continuously test interactions between kernel and graphics user space. Mesa's CI documentation describes kernel updates, platform configurations and full-pipeline testing as part of maintaining graphics CI. :contentReference[oaicite:4]{index=4}

I believe this model can be extended much further.

---

## From Continuous Integration to Continuous System Validation

The next evolution is not simply more CI jobs.

It is **continuous system validation**.

Instead of validating only after a feature is implemented, the system could continuously evaluate:

- API compatibility
- Driver behaviour
- Performance
- Power characteristics
- Regression risk
- Kernel/user-space interaction
- Hardware capability assumptions
- Cross-platform behaviour

AI can potentially help here as well.

Large amounts of engineering data already exist across commits, CI results, bug databases, traces, logs and performance measurements.

The opportunity is to connect these signals.

For example:

**Patch → Build → Test → Regression Analysis → Root Cause → Recommendation**

could increasingly become an automated engineering workflow.

---

## Upstream-First and AI-Driven Engineering

I also see an interesting connection between upstream development and AI.

AI is becoming very effective at helping engineers navigate large codebases, analyze logs, identify patterns and accelerate implementation.

But the quality of AI-assisted engineering depends heavily on the quality of the engineering ecosystem around it.

An upstream-first environment provides:

- Consistent interfaces
- Public code
- Review history
- Test infrastructure
- Documentation
- CI results
- Design discussions
- Clear ownership

This creates a much richer context for AI-assisted engineering.

Instead of AI simply generating code, it can potentially help answer higher-level questions:

**Has this problem already been solved?**

**Is there an existing upstream interface?**

**Which subsystem should own this functionality?**

**What regressions could this change introduce?**

**Which tests should be added?**

**Does this design fit existing architecture?**

That is where I believe AI can become much more valuable to engineering organizations.

---

## Upstream Review as Architecture Review

One of the most interesting lessons from the Linux graphics ecosystem is that upstream review is not merely code review.

At its best, it is architecture review.

A patch may trigger questions such as:

- Is this the correct abstraction?
- Should this functionality belong in the kernel?
- Should this be handled in user space?
- Is a new interface really required?
- Can an existing helper be extended?
- Does the design scale to future hardware?
- Will this create long-term compatibility problems?

Those questions are valuable even before the code is written.

For engineering leaders, this changes the role of upstream participation.

It becomes part of **technology strategy**, not simply contribution management.

---

## What This Means for Engineering Organizations

For organizations building semiconductor platforms, I believe upstream-first development requires a cultural shift.

Teams need to think beyond their immediate product boundary.

Instead of measuring only:

**"Did we deliver the feature?"**

we should also ask:

**"Did we build it in a way that scales?"**

That includes measuring:

- Percentage of functionality aligned with upstream
- Number of long-lived private patches
- Time required to upstream new features
- Regression rates
- Cross-product reuse
- Automated validation coverage
- Time from design to upstream acceptance
- Engineering effort spent maintaining divergence

These measurements provide a different view of engineering health.

---

## My Experience With Display Graphics

Working in Display Graphics has made this perspective particularly clear to me.

Graphics is not an isolated driver problem.

A display feature can cross hardware, firmware, kernel, user space, compositor and application layers.

A change that looks small at one layer can have consequences several layers away.

That is why I increasingly see the value of designing with the complete ecosystem in mind.

The Linux graphics community is continuously working through exactly these types of interactions across DRM, i915, Xe, Mesa, display components, CI and user-space interfaces. The public development traffic reflects an ongoing cycle of patches, reviews, testing and refinement. :contentReference[oaicite:5]{index=5}

For me, that is one of the strongest arguments for upstream-first engineering.

---

## The Bigger Vision

I believe the future semiconductor software organization will look increasingly different from the traditional product software organization.

Instead of every product maintaining its own software island, we can move toward a model like:

**Common upstream platform**

↓

**Shared validation and simulation**

↓

**Common kernel and user-space infrastructure**

↓

**Product-specific differentiation**

↓

**Automated continuous validation**

↓

**AI-assisted engineering**

This model can improve both engineering efficiency and product scalability.

The objective is not to eliminate product-specific engineering.

It is to make sure product-specific engineering is focused on the areas that actually differentiate the product.

---

## Upstream-First Is About Long-Term Engineering Economics

For me, upstream-first development ultimately comes down to engineering economics.

Every duplicated implementation has a cost.

Every private interface has a cost.

Every long-lived downstream patch has a cost.

Every manual validation step has a cost.

Every branch that diverges from the ecosystem creates future maintenance work.

Upstream development does not eliminate those costs.

But it can significantly reduce duplication and move more of the engineering effort toward a shared platform.

That is especially powerful when the same software architecture needs to support multiple products and multiple generations of hardware.

---

## Closing Thoughts

I don't see upstream-first development as simply:

**"Contribute code to Linux."**

I see it as a way of designing software organizations.

It encourages engineers to think about:

- Architecture before implementation
- Interfaces before integration
- Validation before product release
- Reuse before duplication
- Simulation before hardware availability
- Automation before manual execution
- Ecosystems before individual products

And most importantly, it encourages us to build software that can survive beyond a single product cycle.

For Linux Graphics and Display engineering, I believe this becomes increasingly important as hardware complexity grows and software stacks become more interconnected.

The opportunity is to combine **upstream-first engineering, simulation, continuous validation and AI-assisted development** into a new engineering model.

One where we don't simply develop software faster.

**We develop software that scales better across products, teams and generations of technology.**

That, to me, is the real value of upstream-first development.

---

*My views are based on my experience working across semiconductor software, Linux platforms and Display Graphics engineering. The objective is not to prescribe one development model for every organization, but to explore how upstream engineering can contribute to scalable platform development.*
