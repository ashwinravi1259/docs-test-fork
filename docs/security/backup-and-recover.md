# Backup and Recovery

Staking $LITKEY provides the first level of resilience for the network, ensuring that should a node want to leave the network, they do so gracefully. For an additional layer of security, a backup and recovery process has been implemented to ensure that the network can be recovered even in the case that a threshold of the active node set goes permanently offline.

## Verifiable Backups

All keys (except the BLS encryption key) in the network are derived hierarchically from a set of root keys. These root keys are generated during each distributed key generation process (DKG) in which each Lit node generates and holds a share of each key. To ensure these key shares are safe and can be recovered as needed, they're encrypted and backed up regularly using a dedicated recovery party and verifiable encryption. The verifiable encryption process ensures that the ciphertext (in this case, each encrypted key share) meets certain properties which allow the protocol to confirm that all encrypted root key shares are genuine. Every time new root keys are produced, nodes update the backups they have stored with the new data.

The backups ensure that if the network were to ever fall below threshold it could be recovered by decrypting the backups (with the help of the recovery party) and importing them into a fresh set of nodes.  

## The Recovery Party

To assist with the recovery process, a designated set of Recovery Party members are responsible for facilitating the decryption of encrypted root key shares. For a successful recovery, more than two-thirds of these members must participate—enabling a threshold-based decryption process that ensures no single party can perform recovery unilaterally.

Each encrypted backup is further protected using a Blinder, a symmetric encryption key held by each node operator. This additional layer ensures that even if the Recovery Party is compromised, the backups cannot be decrypted without participation from the nodes themselves. During recovery, after the Recovery Party has met quorum and produced the necessary decryption shares, each node operator applies their Blinder to fully decrypt the backup.

This two-step safeguard ensures that:
• The Recovery Party alone cannot decrypt the root key shares.
• The Lit nodes alone cannot decrypt the backups without the Recovery Party’s participation.
• Only with cooperation from both groups—Recovery Party quorum and node-held Blinders—can the encrypted backups be fully decrypted.

This mechanism preserves the system’s threshold security guarantees, even in the context of sensitive operations like key recovery.

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
