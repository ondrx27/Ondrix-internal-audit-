# Security Audit Commands

Commands used for internal security audit. All paths relative to project root.

---

## Tool Versions

```bash
rustc 1.82.0
cargo 1.82.0
cargo-audit 0.20.0
cargo-clippy 0.1.82
solana-cli 2.0.25
slither 0.10.4
mythril 0.24.8
node 18.x
npm 10.x
```

---

## Solana Contracts

### SPL Token

```bash
cd SPL
cargo audit > spl-token-security-reports/cargo-audit.txt 2>&1
cargo clippy --all-targets --all-features > spl-token-security-reports/clippy-output.txt 2>&1
```

### Vesting Contract

```bash
cd vesting_ondrix/solana_vesting_ondrix_cont
cargo audit > security-reports/cargo-audit.txt 2>&1
cargo clippy --all-targets --all-features > security-reports/clippy-output.txt 2>&1
```

### Escrow Contract

```bash
cd escrow-ondrix/ondrix-escrow-solana
cargo audit > escrow-solana-security-reports/cargo-audit.txt 2>&1
cargo clippy --all-targets --all-features > escrow-solana-security-reports/clippy-output.txt 2>&1
```

---

## EVM Contracts

### Vesting Contract (BNB Chain)

```bash
cd vesting_ondrix/bnb_vesting_ondrix
slither contracts/TokenVesting.sol --json vesting-evm-security-reports/slither-report.json > vesting-evm-security-reports/slither-report.txt 2>&1
myth analyze contracts/TokenVesting.sol > vesting-evm-security-reports/mythril-report.txt 2>&1
```

### Escrow Contract (BNB Chain)

```bash
cd escrow-ondrix/ondrix-escrow-evm
slither contracts/OndrixEscrow.sol --json escrow-evm-security-reports/slither-report.json > escrow-evm-security-reports/slither-report.txt 2>&1
myth analyze contracts/OndrixEscrow.sol > escrow-evm-security-reports/mythril-report.txt 2>&1
```

---

## Prerequisites

### Rust Tools

```bash
cargo install cargo-audit
```

### Python Tools

```bash
pip3 install slither-analyzer mythril
```

### Solana (if needed)

```bash
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
```

---

## Reproduction

To reproduce results:

1. Install tools listed in Tool Versions
2. Navigate to respective contract directory
3. Run commands as shown above
4. Compare output with provided artifacts



