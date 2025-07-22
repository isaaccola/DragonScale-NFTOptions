# DragonScale NFT Options
  
**Language:** Clarity (Stacks Blockchain)  
**Theme:** Fantasy-themed derivatives trading contract

## 🐉 Overview

DragonScale NFT Options is a mystical derivatives trading smart contract that allows users to create and trade options contracts with a fantasy theme. The contract uses enchanted terminology where traders become "enchanters" and "seekers," and traditional financial instruments are reimagined as magical artifacts and spells.

## ✨ Key Features

- **Dragon Scale Token System**: Mint, burn, and transfer mystical dragon scales as the base currency
- **Mystical Options Contracts**: Create options contracts disguised as magical spells
- **Fire & Ice Enchantments**: Two types of option contracts (likely Call and Put equivalents)
- **Wizard Portfolio Tracking**: Track created and acquired options contracts
- **Oracle Integration**: Price feed system for contract settlement
- **Fantasy-themed Interface**: All operations use magical terminology

## 🏗️ Contract Architecture

### Constants

```clarity
ARCHMAGE                 // Contract deployer/admin
FIRE-BLESSING (u1)       // Option type 1
ICE-CURSE (u2)          // Option type 2
```

### Error Codes

| Error | Code | Description |
|-------|------|-------------|
| `ERR-SPELL-EXPIRED` | u1 | Option contract has expired |
| `ERR-INVALID-RUNES` | u2 | Invalid parameters provided |
| `ERR-FORBIDDEN-MAGIC` | u3 | Unauthorized operation |
| `ERR-ARTIFACT-MISSING` | u4 | Required data not found |
| `ERR-INSUFFICIENT-MANA` | u5 | Insufficient dragon scales |
| `ERR-RITUAL-COMPLETE` | u6 | Contract already executed |
| `ERR-CURSED-PRICE` | u7 | Invalid price data |
| `ERR-SPELL-DORMANT` | u8 | Contract not yet active |

### Data Structures

#### DragonHoard
Tracks dragon scale balances for each user:
```clarity
{ keeper: principal } -> { scales: uint }
```

#### MysticContracts
Stores options contract details:
```clarity
{ spell-id: uint } -> {
    enchanter: principal,        // Contract creator
    seeker: (optional principal), // Contract buyer
    magic-type: uint,           // FIRE-BLESSING or ICE-CURSE
    ritual-price: uint,         // Strike price
    offering: uint,             // Premium paid
    moon-phase: uint,           // Expiration time
    scale-count: uint,          // Contract size
    is-enchanted: bool,         // Contract active status
    is-completed: bool,         // Contract executed status
    creation-era: uint          // Creation timestamp
}
```

#### WizardScrolls
Tracks user's created and acquired contracts:
```clarity
{ mage: principal } -> {
    forged: (list 20 uint),    // Created contracts
    acquired: (list 20 uint)   // Purchased contracts
}
```

## 🔧 Core Functions

### Dragon Scale Management

#### `summon-scales(quantity: uint)`
**Public Function** - Mints dragon scales to caller's balance
- **Parameters:** `quantity` - Number of scales to create
- **Returns:** `(response bool uint)`
- **Usage:** Equivalent to minting tokens

#### `banish-scales(quantity: uint)`
**Public Function** - Burns dragon scales from caller's balance
- **Parameters:** `quantity` - Number of scales to destroy
- **Returns:** `(response bool uint)`
- **Errors:** `ERR-INSUFFICIENT-MANA` if insufficient balance

#### `teleport-scales(sender, receiver, quantity)`
**Private Function** - Transfers scales between accounts
- **Parameters:** 
  - `sender: principal` - Source account
  - `receiver: principal` - Destination account
  - `quantity: uint` - Amount to transfer
- **Returns:** `(response bool uint)`

### Contract Management

#### `update-wizard-scrolls(mage, spell-id, is-enchanter)`
**Private Function** - Updates user's contract portfolio
- **Parameters:**
  - `mage: principal` - User address
  - `spell-id: uint` - Contract identifier
  - `is-enchanter: bool` - True if user created the contract
- **Returns:** `(response bool uint)`

## 🎮 Usage Examples

### Creating Dragon Scales
```clarity
;; Summon 100 dragon scales
(contract-call? .dragonscale-nft-options summon-scales u100)
```

### Destroying Dragon Scales
```clarity
;; Banish 50 dragon scales
(contract-call? .dragonscale-nft-options banish-scales u50)
```

## 🔒 Security Features

- **Admin Controls**: Archmage (deployer) has special privileges
- **Balance Checks**: All transfers verify sufficient balance
- **List Limits**: Portfolio tracking limited to 20 contracts per user
- **Overflow Protection**: Uses safe arithmetic operations

## 🚀 Deployment

1. Deploy the contract to Stacks blockchain
2. The deployer becomes the `ARCHMAGE`
3. Users can start summoning dragon scales and creating mystical contracts

## 📝 Development Notes

This contract appears to be a work-in-progress implementation of an options trading system. Key functions for creating, executing, and settling options contracts are not yet implemented in the provided code.

### Missing Functionality
- Options contract creation
- Contract execution/settlement
- Oracle price updates
- Premium payment handling
- Expiration checking

## 🧙‍♂️ Fantasy Theme Mapping

| Traditional Finance | Fantasy Equivalent |
|-------------------|-------------------|
| Token Balance | Dragon Scales Hoard |
| Options Contract | Mystical Contract/Spell |
| Contract Creator | Enchanter |
| Contract Buyer | Seeker |
| Call Option | Fire Blessing |
| Put Option | Ice Curse |
| Strike Price | Ritual Price |
| Premium | Offering |
| Expiration | Moon Phase |
| Portfolio | Wizard Scrolls |
