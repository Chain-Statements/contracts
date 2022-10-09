# ETH Bogota - Chain Statement - Smart Contract

We are builidng our smart contract on top of [Semaphore](https://semaphore.appliedzkp.org/).

## What is Semaphore

Semaphore is a zero-knowledge protocol that allows you to cast a signal (for example, a vote or endorsement) as a provable group member without revealing your identity. Additionally, it provides a simple mechanism to prevent double-signaling. Use cases include private voting, whistleblowing, anonymous DAOs and mixers.

## Smart contract overview

We are refering to [Semaphore boilerplate](https://github.com/semaphore-protocol/boilerplate).

Smart Contracts:

1. ChainStatement.sol: Main logic of the code, includes adding user to group, verify proof, and set Relayer address.
2. BalanceGiver.sol: Mint tokens for users. (Testing purpose)
3. DummyToken.sol: General ERC20 Token. (Testing purpose)
4. Greeter.sol: Simple execution sample of using semaphore.

### Key functionalities:

1. Add User To Group: ` function addNewUser(uint256 identityCommitment, address userAddr) external onlyRelayer`
2. Create Proof that prove user exists in the group: `generateProof(users[0].identity, group, BigInt(groupId), greeting, {wasmFilePath,zkeyFilePath })`
3. Verify User is in the group: `semaphore.verifyProof(groupId, merkleTreeRoot, signal, nullifierHash, groupId, proof)`
