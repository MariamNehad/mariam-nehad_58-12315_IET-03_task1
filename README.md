# Task 1 — Inconsistencies and duplicates

Name: Mariam Nehad
ID: 58-12315

## What I did

The faculty, club and city columns spelled the same value many ways: different capitals, extra spaces, full names, short forms ("Alex", "Pharma", "El Giza") and synonyms ("Soccer", "Debating", "Chess Club"). I first normalised every value (trimmed, lower-cased and collapsed inner spaces), then mapped what was left to the canonical values with an explicit dictionary, and asserted that only canonical values remain. In names I removed all extra spaces and used Title Case; I trimmed emails and lower-cased them. I mapped nine different spellings of `fee_paid` to a boolean column. `signed_up_at` mixed two formats: 25 rows were `YYYY-MM-DD` and 14 were `NN/NN/YYYY`. In the second format the first part went up to 18, so it had to be the day, and I parsed it as `%d/%m/%Y`. I started with 39 rows. Removing exact duplicates took out 3 (36 left). Keeping one row per student and club took out 4 more (32 left). I kept the latest submission, because students came back to mark the fee as paid. In all four pairs the later row says paid, so keeping the first would wrongly show them as unpaid. I fixed the spellings before removing duplicates. If I had done it the other way round, only 2 of the 4 repeated sign-ups would have been found, because "Music"/"music" and "Debate"/"debate club" would not match. Two different students are both called Mohamed Adel, and they even share an email. I matched people only by `student_id`, never by name or email, so they stayed separate.
