# Fuzzy-Logic
Clinical decision making using fuzzy discrete event system
Decision Making Using Fuzzy Discrete Event Systems
You can use a fuzzy discrete event system (FDES) for deciding between different outcomes in scenarios where discrete events can be modeled using a fuzzy transition matrix.

This example shows a sample FDES for clinical decision making in selecting medical treatments. A clinical decision-making system assists a medical practitioner in the diagnosis and treatment of a disease using relevant medical evidence. An FDES [1] allows continuous monitoring of the patient state to recommend a possible course of treatments for a disease [2]. This medical application in this example is for illustrative purposes and does not include real clinical data.

An FDES compactly and explicitly represents application-specific knowledge, even when the knowledge is imprecise or subjective. Also, an FDES model is not a black box. Rather, you can intuitively understand and validate the model structure and operational logic based on the event-transition matrices and related fuzzy state transfers. This model interpretability is important to many applications, especially those in medicine, as patient safety is paramount. Also, interpretability makes model design, development, refinement, and implementation easier, quicker, and more cost-effective.

This example performs decision making using single-event FDES models. You can also use multi-event FDES models for more complex treatment decision where each option consists of two or more different kinds of treatment.

FDES Basics
An FDES complements a conventional discrete event system (DES) by using fuzzy sets and fuzzy logic. A conventional automaton model, which defines a DES, is extended to a fuzzy automaton to define an FDES as follows:

G=(Q,Σ,φ,q
o
)

where:

Q is a 1-by-N vector that represents the overall system state using N fuzzy states. Each fuzzy state in Q can have membership values in the range [0, 1], as opposed to only 0 or 1 in conventional discrete event systems.

q
o
 is the initial fuzzy state vector.

Σ is a set of fuzzy events, each of which is represented by an N-by-N state-transition matrix. The elements of a fuzzy state-transition matrix can have values in the range [0, 1] rather than only 0 or 1. Therefore, the occurrence of a fuzzy event can produce a new overall system state Q with partial membership values for the individual fuzzy states. An FDES can consist of one or more fuzzy events, which can be defined by domain experts or learned from available domain-specific data.

φ:Q×Σ→Q represents state transitions. The state-transition mapping uses fuzzy reasoning, such as the max-product composition method.

A conventional automaton is a special case of a fuzzy automaton while a discrete event system is a special case of a fuzzy discrete event system.

FDES Model for Clinical Status
For this example, the treatment model uses an FDES for patients recently diagnosed with an aggressive, early-stage cancer.

The FDES represents the clinical status of the patient using four fuzzy states, each of which is defined by a fuzzy set.

Healthy — Fuzzy set with maximum membership or peak value at x
h
=4

Good — Fuzzy set with peak value at x
g
=3

Fair — Fuzzy set with peak value at x
f
=2

Poor — Fuzzy set with peak value at x
p
=1
