# ICP Blockchain Project

This project is built using **ICP (Internet Computer Protocol) and Motoko Blockchain**.

## Prerequisites

To run this project, you must install:

- **Ubuntu (WSL for Windows users)**
- **DFX (Dfinity SDK)**
- **Node.js**

## Steps to Run the Project

### 1. Open a WSL window in VS Code
### 2. Install dependencies
`npm i`

## Split the terminal into three sections and run the following:

### First Terminal: Start the local ICP replica
`dfx start`

### Second Terminal: Deploy the canisters and start the frontend
`dfx deploy`
`npm start`

### Third Terminal: Charge the Canister

# Check canister ID
`dfx canister id token`

# Save canister ID into a command line variable
`CANISTER_PUBLIC_KEY="principal \"$(dfx canister id token)\""`

# Verify canister ID is saved
`echo $CANISTER_PUBLIC_KEY`

# Transfer half a billion tokens to the canister
`dfx canister call token transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"`

### Access the Application
## Once the above steps are completed, you can open your browser and go to:
`http://localhost:8080`
