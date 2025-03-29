ICP and Motoko Blockchain Project
This project is built using Internet Computer Protocol (ICP) and the Motoko programming language for blockchain development.
Prerequisites
Before you begin, ensure you have the following installed:

Ubuntu (via WSL if on Windows)
DFX framework (Internet Computer SDK)
Node.js and npm

Installation and Setup

Clone this repository:
Copygit clone [repository URL]
cd [project directory]

Install project dependencies:
Copynpm i


Running the Project
You'll need to run three terminal processes simultaneously:
Terminal 1: Start the Local Internet Computer
Copydfx start
This starts a local instance of the Internet Computer blockchain.
Terminal 2: Deploy and Start Frontend
Copydfx deploy
After the deployment completes successfully:
Copynpm start
This deploys your canisters (smart contracts) and starts the frontend web server.
Terminal 3: Fund the Token Canister
Check your Balance

Find out your principal id:

Copydfx identity get-principal

Save it somewhere.
e.g. My principal id is: 4atzf-s3mn3-t3qjy-hd6k2-ahckb-424xt-oiddu-o7qq5-fny3v-pszgm-3ae
Format and store it in a command line variable:

CopyOWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""

Check that step 3 worked by printing it out:

Copyecho $OWNER_PUBLIC_KEY

Check the owner's balance:

Copydfx canister call token balanceOf "( $OWNER_PUBLIC_KEY )"
Charge the Canister

Check canister ID:

Copydfx canister id token

Save canister ID into a command line variable:

CopyCANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token )\""

Check canister ID has been successfully saved:

Copyecho $CANISTER_PUBLIC_KEY

Transfer half a billion tokens to the canister Principal ID:

Copydfx canister call token transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"
Accessing the Application
Once all the above steps are completed successfully, open your browser and navigate to:
Copyhttp://localhost:8080
You should now be able to interact with the application with the token canister fully funded.
Deploying to the Live IC Network
Deploy the Project to the Live IC Network

Create and deploy canisters:

Copydfx deploy --network ic

Check the live canister ID:

Copydfx canister --network ic id token

Save the live canister ID to a command line variable:

CopyLIVE_CANISTER_KEY="principal \"$( \dfx canister --network ic id token )\""

Check that it worked:

Copyecho $LIVE_CANISTER_KEY

Transfer some tokens to the live canister:

Copydfx canister --network ic call token transfer "($LIVE_CANISTER_KEY, 50_000_000)"

Get live canister front-end id:

Copydfx canister --network ic id token_assets

Copy the id from step 6 and add .raw.ic0.app to the end to form a URL.
e.g. zdv65-7qaaa-aaaai-qibdq-cai.raw.ic0.app

Project Structure

/src - Contains the source code for the canisters
/src/frontend - Frontend code
/src/backend - Backend canister code written in Motoko

Troubleshooting

If you encounter issues with dfx start, ensure no other instances are running using dfx stop
For deployment errors, check your canister configurations in dfx.json
Ensure your WSL environment has the correct permissions to run the required commands

License
[Specify your license here]
Contributors
[List contributors here]
