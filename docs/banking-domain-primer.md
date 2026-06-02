# Banking Domain Primer
Notes for: Xander Le 
## Payment Rails

### RTP (Real-Time Payments)
- **What it is:** Real-Time Payments. A payment type that settles nearly instantly, typically used for B2B and B2C transactions.
- **Operator:** The Clearing House
- **Speed:** Seconds, 24/7/365
- **Irrevocable:** Yes. Once a payment completes there is no way to reverse it, so disputes have to be resolved through a separate process.

### Wire Transfer (Fedwire)
- **What it is:** An interbank wire transfer.
- **Speed:** Real-time, with same-day settlement during operating hours.
- **How it differs from RTP:** The two differ in their transaction limits, the operator, how quickly funds settle within real time, and overall volume.
- **Irrevocable:** Yes. Once funds settle there is no clear or easy path to reverse the transfer and recover the money if a mistake was made.

### Book Transfer
- **What it is:** An intra-bank account move that happens internally to the bank. These are generally instant, used for transfers between accounts at the same bank such as customer-to-customer.
- **When a bank uses it instead of an external rail:** When both accounts are held at the same bank, so no external rail is needed. The transfer is just a set of ledger entries.

## Digital Asset Services

### Custody
- **What it is:** The bank acts as custodian, holding the individual's private keys on their behalf. Custody can be managed via hot storage, cold storage, or Multi-Party Computation.
- **Regulatory permission:** OCC Letter 1170 (July 2020)

### Staking
- **What it is:** Proof-of-stake blockchains require validators to lock up a quantity of cryptocurrency as a bond. In exchange, they perform validation work and earn newly minted tokens.
- **How a bank earns yield:** A bank offering staking services pools client assets, stakes them on behalf of clients, and passes through the yield minus fees.
- **Open regulatory question:** The SEC has taken the position that staking-as-a-service may constitute a securities offering in some contexts.

## What I Would Ask an Engineer
- If RTP is irrevocable, what actually happens when a customer calls and says the money went to the wrong account? Who eats the loss, and what does the recovery process look like in practice?
- When a payment fails straight-through processing and lands in a manual review queue, what does that queue actually look like day to day, and what's the most common reason things end up there?
- For something as final as a Fedwire, what checks run before the send button is pressed, and how much of that is automated today versus a person eyeballing it?