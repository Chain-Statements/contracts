# ETH Bogota - Chain Statement - Smart Contract 📝

We are builidng our smart contract on top of [Semaphore](https://semaphore.appliedzkp.org/).

## What is Semaphore 🐉

Semaphore is a zero-knowledge protocol that allows you to cast a signal (for example, a vote or endorsement) as a provable group member without revealing your identity. Additionally, it provides a simple mechanism to prevent double-signaling. Use cases include private voting, whistleblowing, anonymous DAOs and mixers.

## Smart contract overview

We are refering to [Semaphore boilerplate](https://github.com/semaphore-protocol/boilerplate).

Smart Contracts:

1. ChainStatement.sol: Main logic of the code, includes adding user to group, verify proof, and set Relayer address.
2. BalanceGiver.sol: Mint tokens for users. (Testing purpose)
3. DummyToken.sol: General ERC20 Token. (Testing purpose)
4. Greeter.sol: Simple execution sample of using semaphore.

## Key functionalities:

1. Add User To Group: ` function addNewUser(uint256 identityCommitment, address userAddr) external onlyRelayer`
2. Create Proof that prove user exists in the group: `generateProof(users[0].identity, group, BigInt(groupId), greeting, {wasmFilePath,zkeyFilePath })`
3. Verify User is in the group: `semaphore.verifyProof(groupId, merkleTreeRoot, signal, nullifierHash, groupId, proof)`

## General Workflow

1. Users connect their wallet and create identity in the **Home** Page ➡️ User's identity is registered on our contract.
2. Users enter the same identity information and generate Chain Statements in the **Statements** Page ➡️ Generate proof based on identity commitment and call verifyProof function from semaphore protocol.
3. If verified succeessfully, user can download their Chain Statement PDF ➡️ Chain Statement PDF stored on IPFS is fetched to the Front End.

## Deployed Contract

### Polygon Mumbai

| Title                         | Address                                    |
| ----------------------------- | ------------------------------------------ |
| Verifier20                    | 0xbFA3E40AC6A75c1760130566E5b4DC5EB8890eaC |
| Poseidon library              | 0x56727656b869A48A4924596800020B9b500CB0fC |
| IncrementalBinaryTree library | 0xA2CfB62dA0071bb4d57b4Aa64Cf920a35CA99fDD |
| Semaphore                     | 0x206e2F907c54B49416CD4d26CFCdCa656E528dD2 |
| ChainStatment                 | 0x6f7cAf248770bA7dc49c6Fb13D1F10658758BED3 |

### Optimism Goerli

| Title                         | Address                                    |
| ----------------------------- | ------------------------------------------ |
| Verifier20                    | 0x2686540BE833cFB49F1D8BEa13F7c0E46767FC2D |
| Poseidon library              | 0xe9F49bE29195AFa0BDB483561D547C36f8be5045 |
| IncrementalBinaryTree library | 0x89168c3604B54EA33Ebf0477a36dA8766d5A5D98 |
| Semaphore                     | 0x08B2DB74922f00011F3404221cE3d9E6aAE1921D |
| ChainStatment                 | 0x396064e93017c170477626830DCe671909146981 |

## Start Building

1. Install packages: `yarn add`
2. Run the following commands sequentially in three separate tabs of the terminal:

```bash
yarn start:contracts
```

```bash
yarn start:web-app
```

```bash
yarn start:relay
```
