# Differential Privacy (DP) Notes

# What is the Purpose of Differential Privacy?

## Main Purpose
Enable useful analysis of sensitive data for reasearch, policy and market analysis while ensuring an adversary can't determine whether any single individual data influenced the output

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

## Why Simpler Approaches Fail

**Approach 1 — Encryption:**
Blocks access entirely, but data must be decrypted before analysis can happen, 
which reintroduces privacy risks at the point of use.

**Approach 2 — Anonymization:**
Removing names and identifiers is not enough. Quasi-identifiers like ZIP code, 
birth date, and sex can be cross-referenced with public datasets to re-identify 
individuals.

- **Sweeney (1997):** Linked anonymized medical records with public voter rolls 
using ZIP, birth date and sex — successfully re-identifying individuals.
- **Netflix Prize (2006):** Anonymized movie ratings were matched against public 
IMDb reviews, deanonymizing users and leading to cancellation of the second 
Netflix prize.

**Approach 3 — Mediated Access:**
A curator filters queries on behalf of analysts. Still insufficient because exact 
aggregate answers, returned repeatedly, can leak individual information through 
careful query construction — which leads directly to what DP solves.

---

## Goals of Differential Privacy
DP aims to:
- Protect individual privacy
- Prevent re-identification attacks
- Allow safe statistical analysis
- Enable data sharing securely

---

## Main idea of designing Differential Privacy schemes
The core principle is to add carefully calibrated random noise to the output so that the presence of absence of any single record can't be detected

---

## How it works
Instead of returning the exact answer to a query, small amount of random noise is added to the result

Random enough to hide any single data contributed to the answer, but small enough that the result is still statistically useful

Amount of noise is calibrated based on sensitivity of the query

---

## Consequences of returning answer wihout noise
Adversary can issue series of slightly different queries and compare the results.

They can query the dataset and if the answers are different, they can infer the data

Overly accurate estimates across many queries is "non-private" due to cumulative effect of exact answers letting an attacker reconstruct what individual records contain