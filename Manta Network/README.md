# Manta Trusted Setup

<p align="center">
  <img width="650" alt="github-banner" src="https://user-images.githubusercontent.com/98164067/154848582-58988e81-6a89-4c5f-bdae-ec83478e245c.png">
  </a>
</p>

The global private blockchain platform is called Manta. From the ground up, we are creating a scalable, modular, and private network. Developers may create interoperable, user-friendly, high-performance, auditable dapps with end-to-end privacy guarantees thanks to Manta's zero-knowledge cryptography. DeFi, NFTs, GameFi, DAOs, and countless more blockchain applications may all benefit from anonymity thanks to Manta.

[Twitter](https://twitter.com/MantaNetwork)

[Discord](https://discord.gg/PRDBTChSsF)

[Telegram Announcements](https://t.me/mantanetwork)

[Telegram](https://t.me/mantanetworkofficial)

[Website](https://manta.network/)

## What is Trusted Setup?

Your anonymity is safeguarded by the Manta Network using zero-knowledge proofs (ZKPs). We employ a ZK-SNARK called "Groth16" for Manta Pay, and it needs two pieces of public infrastructure: a prover key and a verifier key. A method for creating these keys in a secure manner is the trusted setup.

## What are this Keys?

Let's take a look at what's going on with the Manta Network using Manta Pay as an illustration. Users can transmit tokens to one another via Manta Pay without risking their anonymity. The way it operates is that users post a ZKP rather than sensitive information (address, token type, quantity) on-chain as they would on Bitcoin or Ethereum. This ZKP serves as evidence that "I am carrying out a legitimate transaction." (Of course, the true statement is a little more difficult)

Therefore, in this scenario, the Manta Pay user is proving the assertion that "I am making a valid transaction," and the Manta Network nodes are verifying it. An intricate mathematical puzzle has a solution in the proof itself. An honest prover (a user who submits a valid transaction) can answer this math problem without much difficulty, whereas an untruthful prover will have a difficult time (someone attempting to submit a fraudulent transaction). A verifier can swiftly determine whether a proposed answer to that mathematical problem is accurate. Importantly, the solution itself conceals any private data, including address, token type, and value. (For technical information, see Groth '16)

The math problem that provers and verifiers must solve and verify is expressed in terms of a set of open parameters that all sides concur to use. The so-called "keys" are these parameters. The prover key and verifier key are the parameters required to assert a mathematical solution and to validate that solution, respectively. Manta Pay users require the prover key to create a ZKP, and Manta Network nodes require the verifier key to validate that evidence. Of course, none of these keys are visible when using Manta Pay, but they are nonetheless involved in the operation of the system.

## How do I participate?

> Note: This is how to install on Linux, for MacOS and Windows you can see the Official Document [here](https://docs.manta.network/docs/guides/TrustedSetup)

### Update packages and install the Client

```
sudo apt update && sudo apt upgrade -y
```

```
curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/Manta-Network/manta-rs/main/tools/install.sh | sh
```

```
source ~/.profile
```

To confirm that the installation worked, enter the command

```
manta-trusted-setup register
```

![image](https://docs.manta.network/assets/images/ts_guide_register-d42125a1fd2371c7ea6ab14c62636229.png)

An email address and Twitter account are required. You will get output after providing them that resembles this.

- **Registration form:** proceed to the customized link created by the customer (in green above). Answer a few optional questions to complete the registration process. Keep in mind that the data you give the client is carried over in the link to the registration form. Use only a Twitter handle or email address that you feel confident sharing with us. (We don't divulge this info to anyone)

- **Keep your secret:** place your secret seed phrase (highlighted in red in the image above) on paper and keep it private.

## Contribution

```
manta-trusted-setup contribute
```

You will be required to input the secret phrase you saved from the registration process (see above) when you enter that command.

![images](https://docs.manta.network/assets/images/ts_guide_secret_prompt-a51b0113ad8b979fb1cf9f23d46cd42e.png)

You only need to input your secret; everything else will take care of itself. You will most likely be added to the contribution queue, which will like this.

![images](https://storage.googleapis.com/papyrus_images/c529b1ad7a80fdd41dd05cf44c517d3e.png)

You don't need to do anything at this time; simply wait with **CTRL+A+D** pressed in the background, and your contribution will be made when your turn arrives. Keep in mind that you will lose your spot in the queue if you close this assignment. Although you will be sent at the back of the line, you can still repeat the work later to participate.

Your contribution will start right away on the client once you are at the head of the line. The contribution procedure could take a short while. Once more, hold tight and don't do anything at this time. Your completed contribution will be forwarded to our server for validation. You'll observe that.

![images](https://storage.googleapis.com/papyrus_images/e803e0f5142d59e6d0052a3771141e72.png)

A confirmation message will be sent to you after the server has confirmed your contribution.

![images](https://storage.googleapis.com/papyrus_images/77d8c52a90e90a5a3a2fe9b87959bcb9.png)
