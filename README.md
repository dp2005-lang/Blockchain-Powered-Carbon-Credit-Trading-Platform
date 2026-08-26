# Blockchain-Powered-Carbon-Credit-Trading-Platform
Blockchain-based carbon credit trading platform for secure issuance, ownership tracking, marketplace trading, and irreversible retirement, built in Python and Google Colab with transaction hashing, security validation, and visual analytics.
# Blockchain-Powered Carbon Credit Trading Platform

## Overview

The **Blockchain-Powered Carbon Credit Trading Platform** is an educational blockchain simulation that demonstrates how blockchain technology can be used to model the lifecycle of carbon credits — from issuance and ownership to marketplace trading and permanent retirement.

The project is designed as a **student-friendly, industry-oriented proof-of-work project**. It simulates blockchain wallets, authorized issuers, carbon-credit issuance, marketplace transactions, ownership transfers, retirement, transaction hashes, blockchain events, security validation, and live supply metrics.

> **Important:** This project uses **simulated carbon-credit data and simulated wallets**. It does **not** create, verify, certify, or represent legally recognized carbon credits.

---

## Project Objective

The objective is to build a transparent and traceable simulation of a carbon-credit marketplace where simulated credits can be:

* Issued by an authorized issuer
* Assigned to an owner wallet
* Listed for sale
* Purchased using simulated test ETH
* Transferred between wallets
* Permanently retired
* Recorded through blockchain-style transaction hashes and events

The project follows the lifecycle:

```text
Simulated Carbon Project
        ↓
Credit Issuance
        ↓
Tokenized Carbon Credit
        ↓
Owner Wallet
        ↓
Marketplace Listing
        ↓
Buyer Purchase
        ↓
Ownership Transfer
        ↓
Credit Retirement
        ↓
Immutable Retirement Record
```

---

## Key Features

### 1. Issuer Registration

Only authorized issuer wallets can create carbon credits.

```text
ADMIN
  ↓
Register Issuer
  ↓
AUTHORIZED ISSUER
```

### 2. Carbon Credit Issuance

The platform creates a simulated carbon credit containing:

* Credit ID
* Project name
* Project type
* Country
* Vintage year
* CO₂e quantity
* Issuer address
* Owner address
* Metadata hash
* Status
* Creation timestamp

### 3. Marketplace

The current owner can list an active credit for sale.

The simulated marketplace records:

* Seller
* Credit ID
* Price
* Listing status
* Listing timestamp

### 4. Credit Purchase

A buyer can purchase a listed credit using simulated test ETH.

After purchase:

```text
Seller
  ↓
Marketplace Purchase
  ↓
Buyer
```

Ownership is automatically updated.

### 5. Ownership Transfer

The project supports direct ownership transfer between simulated wallets.

### 6. Credit Retirement

A credit can be permanently retired by its current owner.

Once retired:

```text
RETIRED
   ↓
Cannot Transfer
   ↓
Cannot Sell
   ↓
Cannot Retire Again
```

### 7. Blockchain-Style Transaction Hashes

Every major operation generates a simulated transaction hash using SHA-256 hashing.

Examples:

```text
REGISTER_ISSUER
ISSUE_CREDIT
LIST_CREDIT
BUY_CREDIT
TRANSFER_CREDIT
RETIRE_CREDIT
```

### 8. Event Logging

The platform records blockchain-style events such as:

```text
IssuerRegistered
CreditIssued
CreditListed
CreditPurchased
CreditTransferred
CreditRetired
```

### 9. Security Validation

The simulation tests important rules including:

* Unauthorized issuance
* Zero-tonne credit creation
* Transfer of retired credit
* Listing of retired credit

### 10. Visual Dashboard

The project automatically generates a PNG dashboard containing:

* Carbon-credit supply metrics
* Credit lifecycle
* Security-test results
* Project execution status
* Final ownership
* Retirement status
* Transaction count
* Event count

---

## Technology Stack

| Technology        | Purpose                      |
| ----------------- | ---------------------------- |
| Python            | Blockchain simulation        |
| Google Colab      | Execution environment        |
| SHA-256           | Transaction/metadata hashing |
| Pandas            | Data processing and tables   |
| Matplotlib        | Visualization                |
| JSON              | Metadata representation      |
| Simulated Wallets | Blockchain participants      |

---

## Simulated Wallets

The project uses four simulated blockchain accounts:

| Actor  | Wallet        |
| ------ | ------------- |
| Admin  | `0xADMIN001`  |
| Issuer | `0xISSUER002` |
| Seller | `0xSELLER003` |
| Buyer  | `0xBUYER004`  |

These are **not real blockchain addresses**.

---

## Sample Carbon Credit

The demonstration creates the following simulated credit:

```text
Credit ID       : CC-2026-001
Project         : Solar Energy Project
Project Type    : Renewable Energy
Country         : India
Vintage Year    : 2026
CO2e            : 10 tonnes
Issuer          : 0xISSUER002
Initial Owner   : 0xSELLER003
Final Owner     : 0xBUYER004
Final Status    : RETIRED
Verification    : SIMULATED
```

---

## Carbon Credit Data Model

Each credit is represented as a Python dictionary similar to a Solidity `struct`.

```python
{
    "credit_id": "CC-2026-001",
    "project_name": "Solar Energy Project",
    "project_type": "Renewable Energy",
    "country": "India",
    "vintage_year": 2026,
    "tonnes_co2e": 10,
    "issuer": "0xISSUER002",
    "owner": "0xSELLER003",
    "metadata_hash": "...",
    "status": "ACTIVE",
    "created_at": "...",
    "retired_at": None,
    "retirement_reason": None
}
```

---

## Credit Status Lifecycle

The project uses the following states:

```text
ACTIVE
  ↓
LISTED
  ↓
TRANSFERRED
  ↓
RETIRED
```

### ACTIVE

The credit has been issued and is available to its owner.

### LISTED

The owner has placed the credit on the marketplace.

### TRANSFERRED

Ownership has changed.

### RETIRED

The credit has permanently left circulation.

---

## Project Architecture

```text
┌─────────────────────────────────────────────┐
│              USER / SIMULATION              │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│          CARBON CREDIT BLOCKCHAIN            │
│                                             │
│  ┌──────────────┐   ┌───────────────────┐  │
│  │ Issuer       │   │ Carbon Credit     │  │
│  │ Management   │   │ Registry          │  │
│  └──────────────┘   └───────────────────┘  │
│                                             │
│  ┌──────────────┐   ┌───────────────────┐  │
│  │ Marketplace  │   │ Retirement        │  │
│  │              │   │ Registry          │  │
│  └──────────────┘   └───────────────────┘  │
│                                             │
│  ┌────────────────────────────────────────┐ │
│  │ Transaction & Event Audit Log           │ │
│  └────────────────────────────────────────┘ │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│             ANALYTICS DASHBOARD             │
│                                             │
│ Supply │ Lifecycle │ Security │ Status      │
└─────────────────────────────────────────────┘
```

---

## Complete Workflow

### Step 1 — Register Issuer

The admin registers the issuer wallet.

```text
ADMIN
 ↓
register_issuer()
 ↓
ISSUER AUTHORIZED
```

### Step 2 — Issue Carbon Credit

The authorized issuer creates:

```text
CC-2026-001
10 tonnes CO2e
Solar Energy Project
```

### Step 3 — Assign Ownership

The initial owner becomes:

```text
0xSELLER003
```

### Step 4 — Marketplace Listing

The seller lists the credit for:

```text
0.05 TEST ETH
```

### Step 5 — Purchase

The buyer purchases the credit.

```text
0xSELLER003
      ↓
  Marketplace
      ↓
0xBUYER004
```

### Step 6 — Ownership Verification

The system confirms:

```text
Current Owner = 0xBUYER004
```

### Step 7 — Retirement

The buyer retires the credit for:

```text
Corporate Net-Zero Demonstration
```

### Step 8 — Security Testing

The system attempts to:

* Transfer the retired credit
* List the retired credit
* Issue a credit from an unauthorized wallet
* Issue a zero-tonne credit

These operations should be rejected.

---

## Security Features

### Unauthorized Issuance Protection

Only registered issuers can create credits.

```python
if issuer not in self.authorized_issuers:
    raise Exception("Only authorized issuer can issue credits")
```

### Unique Credit IDs

A credit ID cannot be reused.

```python
if credit_id in self.credits:
    raise Exception("Credit ID already exists")
```

### Positive CO₂e Validation

Credits must contain more than zero tonnes.

```python
if tonnes <= 0:
    raise Exception("Tonnes CO2e must be greater than zero")
```

### Owner Validation

Only the current owner can list, transfer, or retire a credit.

### Retirement Protection

Retired credits cannot be transferred or listed again.

---

## Audit Trail

Every major operation generates a transaction hash.

Example:

```text
REGISTER_ISSUER
→ 0x...

ISSUE_CREDIT
→ 0x...

LIST_CREDIT
→ 0x...

BUY_CREDIT
→ 0x...

RETIRE_CREDIT
→ 0x...
```

The event log provides an additional audit trail.

```text
IssuerRegistered
CreditIssued
CreditListed
CreditPurchased
CreditTransferred
CreditRetired
```

---

## Supply Metrics

The dashboard calculates:

```text
Total Issued
Active
Listed
Traded
Retired
```

For the demonstration:

```text
Total Issued : 10 tCO2e
Retired      : 10 tCO2e
```

This demonstrates how blockchain-style records can be used to derive transparent supply information.

---

## Generated Output

Running the Colab cell produces a visual result:

```text
carbon_credit_blockchain_result.png
```

The image contains four major sections:

```text
┌───────────────────────────────────────────────┐
│ BLOCKCHAIN-POWERED CARBON CREDIT PLATFORM     │
├─────────────────────┬─────────────────────────┤
│ Supply Metrics      │ Credit Lifecycle         │
│                     │                         │
├─────────────────────┼─────────────────────────┤
│ Security Tests      │ Project Status           │
│                     │                         │
└─────────────────────┴─────────────────────────┘
```

This image can be used as a **project demonstration screenshot** for documentation, presentations, or a GitHub repository.

---

## How to Run in Google Colab

### 1. Open Google Colab

Create a new notebook in Google Colab.

### 2. Add One Code Cell

Copy the complete Python code into a single cell.

### 3. Run the Cell

Click:

```text
Runtime → Run all
```

or press:

```text
Shift + Enter
```

### 4. View Results

The notebook will display:

* Issuer registration
* Credit issuance
* Credit details
* Marketplace listing
* Purchase
* Ownership change
* Retirement
* Security tests
* Transaction history
* Event logs
* Supply metrics
* Final dashboard

### 5. Generated Image

The dashboard is saved as:

```text
/content/carbon_credit_blockchain_result.png
```

---

## Example Console Output

```text
===========================================================================
BLOCKCHAIN-POWERED CARBON CREDIT TRADING PLATFORM
Google Colab Blockchain Simulation
===========================================================================

[ISSUER REGISTRATION]
Issuer: 0xISSUER002
Status: AUTHORIZED

[CREDIT ISSUED]
Credit ID: CC-2026-001
Project: Solar Energy Project
CO2e: 10 tonnes
Owner: 0xSELLER003
Status: ACTIVE

[MARKETPLACE LISTING]
Credit: CC-2026-001
Seller: 0xSELLER003
Price: 0.05 TEST ETH
Status: LISTED

[CREDIT PURCHASED]
Credit: CC-2026-001
Seller: 0xSELLER003
Buyer: 0xBUYER004
New Owner: 0xBUYER004

[CREDIT RETIRED]
Credit: CC-2026-001
Owner: 0xBUYER004
Status: RETIRED
```

---

## Security Test Results

Expected result:

| Test                    | Expected |
| ----------------------- | -------- |
| Retired credit transfer | PASSED   |
| Retired credit listing  | PASSED   |
| Unauthorized issuance   | PASSED   |
| Zero-tonne validation   | PASSED   |

A `PASSED` result means the smart-contract-style validation correctly rejected an invalid operation.

---

## Repository Structure

A recommended GitHub structure is:

```text
Blockchain-Carbon-Credit-Trading-Platform/
│
├── README.md
│
├── carbon_credit_blockchain.py
│
├── carbon_credit_blockchain.ipynb
│
├── outputs/
│   └── carbon_credit_blockchain_result.png
│
├── screenshots/
│   ├── issuer_registration.png
│   ├── credit_issuance.png
│   ├── marketplace_listing.png
│   ├── purchase.png
│   ├── retirement.png
│   └── final_dashboard.png
│
├── sample_metadata/
│   └── project_001.json
│
└── docs/
    └── project_report.pdf
```

---

## GitHub Repository Description

> **Blockchain-based carbon credit trading prototype using Python to simulate credit issuance, marketplace trading, transparent ownership transfer, transaction auditing, security validation, and irreversible carbon-credit retirement.**

---

## Suggested GitHub Topics

```text
blockchain
python
carbon-credit
carbon-market
sustainability
climate-tech
ethereum
web3
smart-contract
ESG
carbon-trading
green-tech
google-colab
```

---

## Future Improvements

The current implementation is intentionally a Python simulation. A more advanced version could implement:

* Solidity smart contracts
* Hardhat
* Ethereum testnet
* MetaMask
* React frontend
* Ethers.js
* ERC-20/ERC-1155 carbon-credit tokens
* IPFS metadata
* Real blockchain transaction hashes
* Marketplace smart contract
* Retirement certificates
* Role-based access control
* Oracle integration
* Analytics dashboard
* Database/event indexing
* KYC/allowlist functionality
* Carbon-registry integration

The original project specification also proposes Solidity + Hardhat + Ethers.js + MetaMask + React as the recommended production-oriented architecture.

---

## Real-World Limitation

Blockchain can provide a transparent and tamper-resistant record of:

* Issuance
* Ownership
* Transfers
* Marketplace transactions
* Retirement

However, blockchain **cannot independently prove that a real-world project actually removed or avoided the claimed amount of CO₂**.

Real carbon-credit systems require processes such as:

* Measurement
* Reporting
* Verification
* Approved methodologies
* Project validation
* Registry integration
* Trusted verification organizations

Therefore, this project should be presented as a **blockchain carbon-credit trading prototype**, not as a real carbon-credit registry.

---

## Educational Value

This project demonstrates practical understanding of:

* Blockchain architecture
* Distributed-ledger concepts
* Wallets and addresses
* Tokenization
* Smart-contract logic
* Access control
* Ownership management
* Marketplace design
* Transaction hashing
* Event logging
* State transitions
* Retirement mechanisms
* Security validation
* Data visualization

---

## Interview Explanation

### "Explain your project."

> I developed a blockchain-inspired carbon-credit trading platform as an educational prototype. The system simulates authorized issuers creating carbon credits, assigning them to wallet addresses, listing them in a marketplace, transferring ownership through purchases, and permanently retiring credits. I implemented transaction hashing, event logging, supply metrics, and security validation to demonstrate blockchain concepts such as traceability, ownership, access control, and immutable retirement. The project uses simulated carbon-credit data rather than legally verified credits.

---

## Disclaimer

This project is intended **only for educational, demonstration, and portfolio purposes**.

The carbon credits, wallets, transactions, verification status, and marketplace payments are simulated.

**This project does not issue, certify, verify, trade, or represent legally recognized carbon credits or financial assets.**

---

## Author

**Debankita Panja**

B.Tech — Electronics & Communication Engineering

### Project

**Blockchain-Powered Carbon Credit Trading Platform**

### Built With

`Python` • `Google Colab` • `Pandas` • `Matplotlib` • `SHA-256` • `Blockchain Simulation`

---

## License

This project is available for educational and portfolio use. Add an appropriate open-source license such as **MIT License** if you intend to distribute the repository publicly.
