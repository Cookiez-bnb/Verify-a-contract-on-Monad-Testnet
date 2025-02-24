# Verify-a-contract-on-Monad-Testnet

we're gonna using Foundry method which is faster and easier

as a window user, you need WSL to run these code
more details to install WSL pls ask google or GPT, i'll keep this thread short

![image](https://github.com/user-attachments/assets/3baed163-3eb7-4631-9d5d-1f209c1e015e)

Okay, let's assume that you guys all have WSL ready. 
Now open CMD as adminstrator type WSL to enter WSL terminal

![image](https://github.com/user-attachments/assets/9f8a0b96-bcad-438e-a16e-31cee52e9e54)

Before you begin, you need to install the following tools:
🔴Rust
🔴Cargo
🔴Foundryup

first to install RUST type 

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

Follow the on-screen instructions:

During the installation, you will be prompted to choose an installation option. The default option should be suitable for most users.

Configure your environment:
After the installation is complete, you need to configure your environment. The installation script will provide instructions on how to do this. Typically, you need to add the Rust binaries to your PATH. You can do this by running the following command

setx PATH "%PATH%;%USERPROFILE%\.cargo\bin"

after that, verify to see if Rust is installed or not  
 
rustc --version  

This command should display the version of Rust that is installed on your system.

![image](https://github.com/user-attachments/assets/d9ccda1b-b68b-468c-b802-c489fd4c8447)

next step is to install cargo

Luckily, it's installed by default when you install Rust. 

you could check your cargo version by using

cargo --version

![image](https://github.com/user-attachments/assets/1577bdda-e3e1-4177-baae-9fe01c5e4fbb)

Now foundry is the last component you need
To install Foundryup, run the following command:

curl -L https://foundry.paradigm.xyz | bash

Next run this
 # clone the repository
git clone https://github.com/foundry-rs/foundry.git
cd foundry
# install Forge
cargo install --path ./crates/forge --profile release --force --locked
# install Cast
cargo install --path ./crates/cast --profile release --force --locked
# install Anvil
cargo install --path ./crates/anvil --profile release --force --locked
# install Chisel
cargo install --path ./crates/chisel --profile release --force --locked

This process may take a while depend on your CPU and DISK.

Now pay attention to this

direct your command to the foundry folder after successfully install, default is C/windows/system32/foundry

type this in console to move to the folder
cd /mnt/c/windows/system32/foundry

![image](https://github.com/user-attachments/assets/4aa307cb-4a24-46da-9002-b07826374010)

now type this to clone monad template on github. 

git clone https://github.com/monad-developers/foundry-monad

you could verify if this is official or not on this
https://github.com/monad-developers/foundry-monad?tab=readme-ov-file

after successfully cloning, there will be a folder named foundry-monad in the foundry folder that you could manually check on file explorer

![image](https://github.com/user-attachments/assets/6bece461-457d-4a6f-8084-154d7e6c68e3)

now move to that folder on your console using 

cd /mnt/c/windows/system32/foundry/foundry-monad

The command to verify your contract should be like this

forge verify-contract \
    <contract_address> \ ( your contract addrs )
    <contract_name> \ ( your contract name )
    --chain 10143 \
    --verifier sourcify \
    --verifier-url https://sourcify-api-monad.blockvision.org

    By default there will be a file name Counter.sol in Foundry-monad/src already so you could create and verify that contract w/o creating a new one ( which leading to more step )

  ![image](https://github.com/user-attachments/assets/2f7435bf-12c4-4420-b5b8-ec9d00325f2a)

  To broadcast that contract ( create/deploy ) type this

forge create --private-key <your_private_key> src/Counter.sol:Counter --broadcast

which <your_private_key> replace with your private key

If successfully deploy there will be smth like this appear on the terminal

Deployer: 0xAd346209612E1a381B976055925A3040318fc218
Deployed to: 0x05b92EdD3188874A2C8Af630a35f641857403c18
Transaction hash: 0xe37edae995b11deea58369341f4ab2ed09040c3aaf3ff57b2a7f4c25cf30479a

You could copy the hash and paste on explorer to see more details like image below

![image](https://github.com/user-attachments/assets/18c49290-ed12-4548-a2fa-39355eabe255)

As you can see, the contract haven't be verified yet. Now next step is to verify your newly created contract

![image](https://github.com/user-attachments/assets/2daadc05-3362-43fc-b3de-df94d7771f3b)

The code should look like this

forge verify-contract \
    <contract_address> \
    <contract_name> \
    --chain 10143 \
    --verifier sourcify \
    --verifier-url https://sourcify-api-monad.blockvision.org

<contract_address> replace with CA
<contract_name> replace with src/Counter.sol:Counter

successful attemp should be like this

![image](https://github.com/user-attachments/assets/bddc2967-299d-41f9-a3b5-4c2df245c4c2)

Final step: Flex with your friend that you are a developer 😎
And that's it, your contract is verified

![image](https://github.com/user-attachments/assets/16cc7f83-b2b9-45a7-9055-66f088dac4b1)










