# DigitalGuard: Secure ZK-Proof Verification Across Decentralized Oracles

DigitalGuard is a decentralized crypto-economic API built with Typescript and orchestrated through Rust-based microservices. It provides a secure and verifiable mechanism for verifying zero-knowledge proofs (ZKPs) across multiple blockchain oracles. This enables trustless data validation and computation, bridging the gap between off-chain computation and on-chain verification, thus unlocking a new wave of privacy-preserving decentralized applications.

The core purpose of DigitalGuard is to address the limitations of current decentralized systems where data integrity and computational integrity are often compromised due to the lack of secure and verifiable methods for integrating off-chain computations. DigitalGuard achieves this by employing a network of Rust-based microservices that handle the complex process of ZKP verification. These microservices interact with various blockchain oracles, retrieving necessary data and verifying the submitted proofs against cryptographic commitments. The system leverages a crypto-economic model to incentivize honest participation and penalize malicious behavior, ensuring the integrity and reliability of the verification process.

DigitalGuard's design prioritizes modularity, scalability, and security. The microservice architecture allows for easy expansion and maintenance, enabling the integration of new ZKP systems and blockchain oracles. The system is designed to be resistant to common attacks such as Sybil attacks and data manipulation attacks through its robust crypto-economic incentives and cryptographic security measures. Ultimately, DigitalGuard provides a crucial infrastructure component for building trustless and privacy-preserving decentralized applications that rely on verifiable off-chain computations.

## Key Features

*   **Decentralized ZKP Verification:** Verifies zero-knowledge proofs across a distributed network of nodes, eliminating single points of failure. The microservices are designed to operate independently, increasing system resilience.
*   **Multi-Oracle Support:** Supports integration with various blockchain oracles (e.g., Chainlink, Band Protocol, API3), allowing for access to diverse data sources. Implementation utilizes abstract interfaces for easy addition of new oracles.
*   **Rust-Based Microservices:** Core verification logic is implemented in Rust for performance and security. Rust's memory safety guarantees and performance characteristics are ideal for this application.
*   **Crypto-Economic Incentives:** Uses a staking and reward mechanism to incentivize honest verification and penalize malicious behavior. Implemented via smart contracts on a supported blockchain.
*   **Typescript API:** Provides a Typescript API for seamless integration with existing Javascript/Typescript projects. The API handles proof submission, verification status monitoring, and interaction with the underlying blockchain components.
*   **ZK-Snarks and ZK-Starks Support:** Currently supports verification of both ZK-Snarks and ZK-Starks proofs, with extensibility for future ZKP systems. The system is designed to handle the different verification algorithms and parameter configurations required by each proof system.
*   **Fault Tolerance:** System is designed to be fault-tolerant, ensuring verification continues even if some nodes are offline or malicious. Implemented through redundancy and consensus mechanisms.

## Technology Stack

*   **Typescript:** Used for building the API and client-side applications. Its static typing and rich tooling enhance code quality and maintainability.
*   **Rust:** Used for implementing the core verification logic within microservices. Its performance, memory safety, and strong type system ensure security and efficiency.
*   **Actix-web (Rust):** A lightweight Rust framework for building web applications and microservices. Used for creating the REST APIs within the verification microservices.
*   **Axios (Typescript):** A promise-based HTTP client for making requests to the verification microservices.
*   **Web3.js or Ethers.js (Typescript):** Used for interacting with blockchain oracles and smart contracts.
*   **Docker:** Used for containerizing and deploying the microservices. Ensures consistent execution across different environments.
*   **Kubernetes (Optional):** Can be used for orchestrating the microservices in a production environment. Provides scalability and fault tolerance.

## Installation

1.  **Clone the Repository:**
    git clone https://github.com/jjfhwang/DigitalGuard.git
    cd DigitalGuard

2.  **Install Dependencies (Typescript):**
    cd api
    npm install

3.  **Install Rust and Cargo:** Follow the instructions on the official Rust website (https://www.rust-lang.org/tools/install). Ensure you have a stable Rust version installed.

4.  **Build Rust Microservices:**
    cd ../verifier
    cargo build --release

5.  **Install Docker:** Follow the instructions on the official Docker website (https://docs.docker.com/get-docker/).

6.  **Build Docker Images:**
    cd ../docker
    docker-compose build

## Configuration

The application relies on several environment variables for configuration. Create a `.env` file in the root directory with the following structure:

NODE_ENV=development
API_PORT=3000
VERIFIER_PORT=8080
ORACLE_URL=https://some-oracle-url.com
PRIVATE_KEY=0x...
CONTRACT_ADDRESS=0x...

*   `NODE_ENV`:  Environment (development or production).
*   `API_PORT`: Port for the Typescript API.
*   `VERIFIER_PORT`: Port for the Rust verifier microservice.
*   `ORACLE_URL`: URL of the blockchain oracle.
*   `PRIVATE_KEY`: Ethereum private key for interacting with the blockchain.
*   `CONTRACT_ADDRESS`: Address of the verification smart contract.

## Usage

1.  **Start the Services:**
    cd docker
    docker-compose up

This will start the API and the Rust verifier microservice.

2.  **API Documentation:** The API provides endpoints for submitting proofs and querying verification status.

    *   `POST /submit`: Submits a ZKP for verification.  Expects a JSON payload containing the proof, public inputs, and the type of ZKP system used.

    Example request:

    curl -X POST -H "Content-Type: application/json" -d '{"proof": "...", "publicInputs": ["1", "2"], "zkpSystem": "zk-snarks"}' http://localhost:3000/submit

    *   `GET /status/{verificationId}`: Retrieves the verification status of a specific proof.

    Example request:

    curl http://localhost:3000/status/12345

## Contributing

We welcome contributions to DigitalGuard. Please follow these guidelines:

*   Fork the repository and create a branch for your feature or bug fix.
*   Write clear and concise commit messages.
*   Submit a pull request with a detailed description of your changes.
*   Ensure your code adheres to the project's coding style.
*   Include unit tests for any new functionality.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/DigitalGuard/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the Rust and Typescript communities for providing excellent tools and libraries. We also appreciate the contributions of the open-source ZKP community for their invaluable research and development.