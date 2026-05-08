# Mastermind

I built a small project that combines my interest in game design and smart contracts: a **Mastermind Game dApp** built on the [Agoric](https://agoric.com/) blockchain.
This project gave me a hands-on way to learn more about Agoric’s smart contract platform, experiment with wallet integrations, and improve my frontend engineering skills. It also reminded me how fun it can be to bring a classic logic game to life in a decentralized environment.

**Project Repo:** [Jorge-Lopes/mastermind](https://github.com/Jorge-Lopes/mastermind.git)

### Why Mastermind?

For those unfamiliar, **Mastermind** is a classic code-breaking game where one player (the code maker) sets a hidden sequence of colored pegs, and the other (the code breaker) tries to guess it in as few attempts as possible.

In my version, the **smart contract** takes the role of the code maker. It generates a **secret code** — four colors out of a possible six — and keeps it hidden on-chain. As the player, you connect your wallet, make guesses, and receive feedback after each one:

* **Black** = correct color in the correct position
* **Red** = correct color, wrong position

The game continues until you either crack the code or run out of ten attempts.

### Pseudorandom Number Generator

I used the [Mersenne-Twister](https://www.npmjs.com/package/mersenne-twister) pseudorandom number generator to create the secret code each time a new game starts.

Each sequence is generated based on a timestamp-derived seed — which means the same seed will always produce the same random sequence. While this approach makes testing easier, it also highlights one of the current limitations: the seed could be predictable if extracted from chain logs. In the future, I plan to integrate a more secure randomness source like [Nois](https://nois.network/).


### Lessons Learned

* **Smart contracts for games require careful randomness design.** Predictable seeds can break fairness, so secure randomness sources are key.
* **Frontend integration with blockchain wallets** can be tricky at first, but once you understand the flow — connection, signing, querying — it becomes intuitive.
* **Agoric’s JavaScript-first approach** makes it accessible for web developers transitioning into blockchain development.
