---
layout: post
title: "Why Upstream-First Development Matters"
date: 2026-09-06
categories: [Linux Graphics, Open Source, Engineering Leadership]
tags: [Linux, Upstream, DRM, KMS, GPU, Display Graphics, CI, Simulation, AI, Semiconductor Software]
---

# Why Upstream-First Development Matters

Over the years, working across semiconductor software, Linux platforms and Display Graphics has changed the way I think about product development.

One lesson has become increasingly clear to me:

> **The earlier we develop with upstream Linux in mind, the easier it becomes to scale technology across products.**

For me, upstream-first is not simply a contribution model or a way of getting patches into the Linux kernel. It is increasingly a **product-development strategy**.

It changes where we find problems, when we validate them, how we reuse engineering investment, and ultimately how quickly a platform can move from silicon to products.

## From Product-Specific Development to Platform Development

A traditional product-development approach often looks like this:

**Silicon → Product → Customized software → Integration → Validation → Fixes**

When several products are built on related hardware, this model can create multiple branches of essentially the same software problem.

A display issue discovered in one product may result in a local fix. Another product may encounter the same issue and develop a different solution. Over time, these differences accumulate.

The result is familiar to anyone who has worked on large software platforms:

- Multiple downstream branches
- Duplicated fixes
- Difficult backports
- Increasing validation effort
- Divergence from upstream
- Higher maintenance cost with every new product generation

An upstream-first approach changes the model:

**Silicon → Linux upstream → Common platform → Multiple products**

The objective is to solve the problem once at the platform level and make that solution reusable across products.

For a company developing multiple products, that creates a powerful multiplier.

## What My Display Graphics Experience Taught Me

Working in Linux Display Graphics has reinforced this idea for me.

Modern graphics is not an isolated driver problem. It is a complete software stack involving:

**Hardware → Firmware → Kernel/DRM → Display/GPU drivers → Mesa → Wayland/Compositor → Applications**

A change at one layer can influence many products and many use cases.

In my experience, graphics development becomes significantly more effective when architecture, interfaces, validation and upstream integration are considered together rather than treated as separate activities.

This makes upstream development particularly valuable.

When a graphics capability, architectural improvement or bug fix becomes part of the upstream stack, the investment is no longer tied to one product.

It becomes a **platform capability**.

That is the difference between:

**"We fixed this product."**

and

**"We improved the platform."**

That distinction becomes increasingly important as organizations support multiple products, platforms and generations.

## Scaling Across Multiple Products

Imagine an organization developing five products using the same graphics architecture.

With a heavily downstream approach:

```text
Product A ── local graphics changes
Product B ── local graphics changes
---
layout: post
title: "Why Upstream-First Development Matters"
date: 2026-09-06
categories: [Linux Graphics, Open Source, Engineering Leadership]
tags: [Linux, Upstream, DRM, KMS, GPU, Display Graphics, CI, Simulation, AI, Semiconductor Software]
---

# Why Upstream-First Development Matters

Over the years, working across semiconductor software, Linux platforms and Display Graphics has changed the way I think about product development.

One lesson has become increasingly clear to me:

> **The earlier we develop with upstream Linux in mind, the easier it becomes to scale technology across products.**

For me, upstream-first is not simply a contribution model or a way of getting patches into the Linux kernel. It is increasingly a **product-development strategy**.

It changes where we find problems, when we validate them, how we reuse engineering investment, and ultimately how quickly a platform can move from silicon to products.

## From Product-Specific Development to Platform Development

A traditional product-development approach often looks like this:

**Silicon → Product → Customized software → Integration → Validation → Fixes**

When several products are built on related hardware, this model can create multiple branches of essentially the same software problem.

A display issue discovered in one product may result in a local fix. Another product may encounter the same issue and develop a different solution. Over time, these differences accumulate.

The result is familiar to anyone who has worked on large software platforms:

- Multiple downstream branches
- Duplicated fixes
- Difficult backports
- Increasing validation effort
- Divergence from upstream
- Higher maintenance cost with every new product generation

An upstream-first approach changes the model:

**Silicon → Linux upstream → Common platform → Multiple products**

The objective is to solve the problem once at the platform level and make that solution reusable across products.

For a company developing multiple products, that creates a powerful multiplier.

## What My Display Graphics Experience Taught Me

Working in Linux Display Graphics has reinforced this idea for me.

Modern graphics is not an isolated driver problem. It is a complete software stack involving:

**Hardware → Firmware → Kernel/DRM → Display/GPU drivers → Mesa → Wayland/Compositor → Applications**

A change at one layer can influence many products and many use cases.

In my experience, graphics development becomes significantly more effective when architecture, interfaces, validation and upstream integration are considered together rather than treated as separate activities.

This makes upstream development particularly valuable.

When a graphics capability, architectural improvement or bug fix becomes part of the upstream stack, the investment is no longer tied to one product.

It becomes a **platform capability**.

That is the difference between:

**"We fixed this product."**

and

**"We improved the platform."**

That distinction becomes increasingly important as organizations support multiple products, platforms and generations.

## Scaling Across Multiple Products

Imagine an organization developing five products using the same graphics architecture.

With a heavily downstream approach:

```text
Product A ── local graphics changes
Product B ── local graphics changes
Product C ── local graphics changes
Product D ── local graphics changes
Product E ── local graphics changes
The engineering organization effectively maintains five variations.

With an upstream-first strategy:

                 Linux Upstream
                       │
             Common Graphics Platform
                       │
        ┌──────────────┼──────────────┐
        │              │              │
     Product A      Product B      Product C
        │              │              │
     Product D      Product E      Future Products

The architecture, interfaces, fixes and validation become increasingly reusable.

This doesn't mean every product becomes identical. Product-specific differentiation will always exist.

The important point is that the common technology moves upward into the shared platform instead of being repeatedly recreated downstream.

That is where the scalability comes from.

Upstream-First Enables a Better Left Shift

There is another benefit that I consider even more important: left-shifting validation and integration.

In many traditional product organizations, hardware availability determines when serious software validation can begin.

That creates a late integration problem.

A simplified model is:

Silicon available
      ↓
Driver integration
      ↓
System integration
      ↓
Validation
      ↓
Bug discovery
      ↓
Debug
      ↓
Fix
      ↓
Re-test

The later a problem is discovered, the more expensive it becomes to fix.

With an upstream-first approach, much more of the software architecture can be developed, reviewed and tested before the final product integration phase.

The objective is to move validation closer to development rather than waiting for complete product integration.

That changes the engineering question from:

"Does this work when the product is almost ready?"

to:

"Can we continuously prove that this change works as we develop it?"

That is a much healthier development model.
Simulation: The Next Opportunity for Linux Platform Development

I believe there is an even bigger opportunity ahead.

Linux gives us an excellent environment for increasing the amount of platform development that can happen before complete physical hardware is available.

Not everything can be simulated.

Graphics performance, power behavior, display timing and many hardware-specific interactions ultimately require real silicon.

But a significant amount of software engineering can be exercised earlier.

We can validate:

Driver architecture
Interfaces
Error handling
Userspace interactions
Command submission paths
Memory-management behavior
Display-stack integration
API behavior
Regression tests
System configuration
Automation
Portions of workload execution

The important idea is not that simulation replaces hardware.

It is that simulation expands the amount of software validation we can perform before hardware-dependent validation becomes available.

That can significantly change the product-development timeline.

Upstream + CI + Simulation = A Stronger Development Loop

I see these three technologies working together:

              UPSTREAM-FIRST
                    │
                    ↓
          Common platform architecture
                    │
                    ↓
             CI / Automation
                    │
                    ↓
          Continuous validation
                    │
                    ↓
              Simulation
                    │
                    ↓
       Earlier software validation
                    │
                    ↓
          Real hardware validation
                    │
                    ↓
              Production
Instead of waiting for hardware and then discovering problems, we progressively eliminate classes of problems throughout the development cycle.

This is what I mean by left-shifting product development.

The earlier we can find a problem, the easier it generally is to fix.

Upstream Is Also an Engineering Quality Mechanism

One aspect of upstream development that is sometimes underestimated is technical review.

When code remains inside a product organization, local assumptions and shortcuts can sometimes survive for a long time.

Upstream development exposes those decisions to a broader engineering community.

That creates pressure to improve:

Architecture
Interfaces
Maintainability
Documentation
Testing
Error handling
Long-term compatibility

From my perspective, this is one of the hidden benefits of upstream-first development.

The upstream community becomes part of the engineering feedback loop.

Upstream-First Does Not Mean Upstream-Only

There is an important distinction here.

I don't believe every piece of product software needs to be upstream.

There will always be:

Product-specific functionality
Proprietary algorithms
Confidential technology
Customer-specific requirements
Temporary integration code
Hardware bring-up code
Product differentiation

The objective is not to eliminate downstream development.

The objective is to ask a different question:

"Should this capability really belong only to this product?"

If the answer is no, upstream should be considered from the beginning.

This mindset can prevent years of accumulated downstream maintenance.

The Organizational Impact

Upstream-first development also changes how engineering organizations scale.

If every new product requires a new team to understand and maintain a large downstream software stack, engineering capacity grows with product count.

But if common platform capabilities are developed upstream and continuously validated, the organization can increasingly reuse its engineering investment.

That means the organization can spend more time on:

Innovation rather than integration.

For engineering leaders, I see this as one of the most important benefits.

The goal is not simply to increase the number of engineers.

The goal is to increase the engineering leverage per engineer.

A well-designed upstream platform can provide exactly that leverage.

Looking Ahead

My experience in Display Graphics has convinced me that the future of Linux platform development will increasingly depend on three principles:

1. Upstream early

Develop the architecture with upstream acceptance and long-term maintainability in mind from the beginning.

2. Validate continuously

Use CI, automated regression testing and real hardware validation to move validation closer to every change.

3. Simulate wherever practical

Use simulation and virtualized environments to validate software behavior before complete hardware availability.

Together, these principles create a much more scalable development model.

My View

After working across different generations of technology — from DSP and embedded systems to semiconductor multimedia platforms and Linux Display Graphics — I increasingly see upstream development as more than an open-source philosophy.

I see it as a way of engineering platforms.

The real opportunity is to move from:

Product → Fork → Fix → Validate → Repeat

toward:

Upstream → Automate → Simulate → Validate → Reuse → Scale

For organizations building multiple products on common silicon and software foundations, this can become a significant competitive advantage.

The biggest shift, in my view, is not simply getting code upstream.

It is changing the question from:

"How do we make this product work?"

to:

"How do we build the platform so that the next five products start from a much stronger position?"

That is why I believe upstream-first development matters.

And I believe Linux, combined with automated CI, simulation and increasingly AI-assisted engineering, gives us an opportunity to push that philosophy much further than we have today.
