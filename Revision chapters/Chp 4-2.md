# Differential Privacy (DP) Notes

# What is the Purpose of Differential Privacy?

## Main Purpose
Differential Privacy (DP) is designed to allow useful analysis of datasets while protecting the privacy of individuals inside the dataset.

---

## Problem DP Tries to Solve

Organizations often collect sensitive data such as:
- Health records
- Census information
- Social media activity
- Telecommunication data

The challenge is:

> How can we use the data for research, statistics, or business insights without exposing personal information?

---

## Goals of Differential Privacy
DP aims to:
- Protect individual privacy
- Prevent re-identification attacks
- Allow safe statistical analysis
- Enable data sharing securely

---

# Problems with Traditional Privacy Approaches

# 1. Encrypting the Data

## Idea
Encrypt the dataset so unauthorized users cannot access it.

## Problem
- Data still needs to be decrypted for analysis
- Once decrypted, privacy risks return
- Does not protect against insider misuse

---

# 2. Anonymizing the Data

## Idea
Remove identifiers such as:
- Name
- Address
- ID numbers

---

## Problem: Re-identification Attacks

Even anonymized datasets can sometimes be linked with public information to identify individuals.

---

## Example: Latanya Sweeney Attack (1997)

### Scenario
Anonymous medical records were linked with:
- Public voter records
- Birth dates
- ZIP codes
- Gender information

### Result
Individuals were successfully re-identified.

---

## Example: Netflix Prize Dataset

Netflix released anonymized movie rating data.

Researchers matched:
- Netflix ratings
- IMDb public reviews

### Result
Users were deanonymized.

---

# Main Idea of Designing Differential Privacy Schemes

## Core Idea
The effect of any single person's data should be hidden.

---

## Important Principle

An attacker should NOT be able to determine:
- Whether a person's data exists in the dataset
- Whether a specific individual's record changed the output

---

## Ideal Privacy Goal

The analysis result should remain almost the same:
- Whether a user is included
- Or replaced by another random person

---

# How Differential Privacy Works

# Key Technique: Add Random Noise

Instead of returning the exact answer to a query, DP adds carefully calibrated random noise.

---

# For Each Query: Return Answer with Noise

## Normal Query
```text
“How many users have diabetes?”

Instead of just 5000, it will return with 5003 or 4997

This noise hides individual contribution, makes re-identification harder and perserves overall statistical usefulness