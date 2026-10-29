# Libtycoin

Libtycoin is a peer-to-peer electronic cash system: payments sent directly from
one person to another, with no bank and no intermediary.

This is a guide to running it.

## 1. Build

Libtycoin builds with CMake. From the source directory:

    cmake -B build
    cmake --build build

This produces the programs in `build/bin`:

- `libtycoind` — the node
- `libtycoin-cli` — command-line control
- `libtycoin-wallet` — wallet management

See the `doc/` folder for the packages your system needs first.

## 2. Run a node

    libtycoind -daemon

The node connects to the network and synchronises the chain. Check its state:

    libtycoin-cli getblockchaininfo

To help the network, open the peer port on your firewall so others can connect
to you.

## 3. Make a wallet

    libtycoin-cli createwallet "main"
    libtycoin-cli getnewaddress

The second command returns an address — this is where you receive coins.

## 4. Mine

While the network is young, an ordinary computer can still find blocks. Mine to
your address:

    libtycoin-cli generatetoaddress 1 YOUR_ADDRESS 100000000000

Use the address from step 3. Each block found pays its reward to that address.

## 5. Send and receive

To receive, give the sender your address (step 3). To send:

    libtycoin-cli sendtoaddress THEIR_ADDRESS AMOUNT

## Verify this release

Every release is signed with PGP. Signing key:

    A69F A35A 4BA7 EC16 CFDD  EED4 A7B9 CE90 6BCC 4ED6


— Tobin Wyler
