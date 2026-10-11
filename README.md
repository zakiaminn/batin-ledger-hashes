# Batin ledger hashes

One line per trading day: the date and the SHA-256 hash of that day's entry in a private research
ledger. Nothing else is published here.

## What the ledger is

A paper-tracking record for one research rule about option order flow before company earnings.
The rule passed one pre-registered out-of-sample test on 2022 to 2024 data, by a thin margin, and
is being tracked on new data from 2026-10-12 to see whether it holds. No money is traded. Nothing
here is a prediction, a trading signal or advice.

Every trading evening, before the next market open, the day's readings are written to the ledger
as one entry. Each entry contains the hash of the entry before it. Days that could not be logged in
time are recorded as late or missed, and they get a line here too.

## What a line proves

- The entry for that day existed, with exactly that content, when its line was pushed here.
- Because entries are chained, one line also fixes every earlier entry.
- Only a ledger whose entry hashes match `hashes.txt` counts as the record. That rules out keeping
  several versions and choosing one later.

Each entry is also time-stamped by three independent RFC 3161 timestamp authorities. Those signed
replies are kept with the ledger.

## What is not here

The entries themselves. The underlying market data is licensed for individual use and is not
redistributed, so only hashes are public.

## Format

`hashes.txt`, append-only, one line per entry:

```
YYYY-MM-DD <sha256 of the entry>
checkpoint-YYYYQn <sha256 of the quarterly checkpoint record>
```

The rules for the tracking were fixed before the first entry. Each entry records the SHA-256 of
the rules file it was written under, so the rules are covered by the same hashes.
