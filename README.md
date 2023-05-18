# Fireblocks recovery key utility
## Installation

* Please clone the repository:
  * `git clone https://github.com/fireblocks/fireblocks-key-recovery-tool.git`

* cd fireblocks-key-recovery-tool

### Prerequisites

* Backup file `<backup.zip>`
* Private key `<key.pem>`
* Passphrase

## Running in Docker

### Build the utility in docker
* docker build -t fb_recover_key.

### Run the utility in docker
* cd to `<directory containing the backup file and the private key>`
* Run: docker run -it -v "${PWD}:/opt/fb_recover_keys/backup" fb_recover_key:latest bash
* See below for instructions on how to run the recovery tool.

## Running Locally

### Build the utility locally
* install python 3.9
* install pip3
* run: pip3 install -r requirements.txt

### Run the utility locally
* See below for instructions on how to run the recovery tool

1. Recommended: 
    * run `./fireblocks_key_backup_and_recovery.py`

   #### It opens a menu with the following options:
   1. Create a recovery key pair - generate a recovery key-pair. You'll be asked to choose a 
      passphrase that will be used to encrypt the private key, make sure you remember it
   2. Verify the public backup key - verify the public key file of the recovery key-pair. This is useful 
      for users with the self-serve backups that want to validate that their workspace owner’s request to 
      back up the keys matches the key pair at their premise. Requires: the recovery key-pair public key
   3. Verify the recovery package - run a sanity test of the workspace key backup package. Requires: the 
      backup package, the recovery key pair private file, the passphrase to that private file, and the 
      owner’s passphrase
   4. Reveal the private backup key - Requires: the backup package, the recovery key pair private file, 
      the passphrase to that private file, and the owner’s passphrase

2. Use the Legacy script:
   * run `./fb_recover_keys.py <backup zip file> <RSA recovery private key>` --prv
