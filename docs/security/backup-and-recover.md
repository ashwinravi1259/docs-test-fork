# Backup and Recovery

Staking $LITKEY provides the first level of resilience for the network, ensuring that should a node want to leave the network, they do so gracefully. For an additional layer of security, a backup and recovery process has been implemented to ensure that the network can be recovered even in the case that a threshold of the active node set goes permanently offline.

## Verifiable Backups

All keys (except the BLS encryption key) in the network are derived hierarchically from a set of root keys. These root keys are generated during each distributed key generation process (DKG) in which each Lit node generates and holds a share of each key. To ensure these key shares are safe and can be recovered as needed, they're encrypted and backed up regularly using a dedicated recovery party and verifiable encryption. The verifiable encryption process ensures that the ciphertext (in this case, each encrypted key share) meets certain properties which allow the protocol to confirm that all encrypted root key shares are genuine. Every time new root keys are produced, nodes update the backups they have stored with the new data.

The backups ensure that if the network were to ever fall below threshold it could be recovered by decrypting the backups (with the help of the recovery party) and importing them into a fresh set of nodes.  

## The Recovery Party
To assist with the recovery process, there is a designated set of recovery party members who facilitate the root key share decryption process. More than two-thirds of the members of the recovery party must participate to successfully decrypt the stored backups. Additionally, each backup is encrypted with a Blinder that is held by each node operator.

## Encrypting the Backups
The process for encrypting the root key backups involves:

1. Each member of the recovery party (RP) creates a public encryption key and the decryption key shares using Distributed Key Generation (DKG).
2. This public key is used for encrypting the root key backups.
3. Each Node creates a Blinder, which is used to additionally encrypt the backup.
4. The encrypted backups are stored securely by the Lit Protocol development company.

## Recovery Process
If the network needs to be restored:

1. Each RP member validates their identities with a Lit node and produces decryption shares for the required root key shares.
2. Node operators spin up a new node environment and input their Blinder and encrypted backup, reaching out to each RP member for their share of the decryption key. The decryption key shares are combined above the threshold, combined with the Blinder, to fully decrypt the ciphertext backups.  Recovery, therefore, requires participation of ⅔ of the Recovery Party, ⅔ of the node operators, and Lit Protocol to supply the encrypted backups.
3. With the decrypted root key shares in the new node environment, the network can be restored.
