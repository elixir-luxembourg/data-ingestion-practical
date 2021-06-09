# Practical exercise on data ingestion

In this practical, you will perform multiple steps needed on data ingestion and working environment setup. You will download the test dataset, verify its integrity and add minimal documentation. Finally, you will have data stored in optimal way for subsequent (re-)use in your future steps.

## Requirements

Participants are required to have several tools installed before the practical. These will allow them to work with `.7z` archives and verify MD5 checksums:

* [Windows](./requirements/windows.md)
* [Mac](./requirements/mac.md)
* [Linux](./requirements/linux.md)
## Step 1: Register the data in your local data catalogue
Registering the data is necessary for compliance with GDPR. The record should also contain information on actual physical location of the data which should be known before actual ingestion.
## Step 2: Receive data and decryption password

* Download the data

  https://dropit.uni.lu/invitations?share=d068283d6e56c34e25d8&dl=0

* Get encryption password:
  
  https://privatebin.lcsb.uni.lu/?b9059abddf9a7450#3IHjjvfPnnRVwldOcxURjupy84D4KITVxzOKvFCc1JI=

(Just for reproducibility purposes the password can be found [here](./data/encryption_password.md). Trainees should always receive the password through a secure channel).

## Step 3: Decrypt and extract the data
### Windows
1. Right-click on the folder
2. Select 7zip -> Extract here
3. Enter the encryption password

<img src='./img/win_7zip_extract-archive.png' width=300>
<img src='./img/win_7zip_enter-password.png' width=300>

### Mac
TODO:

### Linux
Use `7z` command line tool to extract the archive.
  ```bash
  7z x EPIC-DREM_chip-seq.7z
  # Enter the ecryption password
  ```
## Step 4: Checksums

Your collaborator/data provider has generated checksums - digital signatures of the file - when posting the data on your shared storage. These are commonly saved in plain text file placed close to the actual data.

In our test scenario, `md5sum` tool was used for checksum generation.

* Download checksums:

  https://dropit.uni.lu/invitations?share=27c80a6f57748d13e9c6&dl=0

* Open the downloaded file with your favorite text editor and inspect the content

### Verify checksums

Data might have been corrupted already on the server or during the transfer. This step ensures that the data are exactly the same as at the time of the last checksum computation.
#### Windows
See steps on [verifying checksums on Windows](./guides/verify_checksums_windows.md)

#### Mac
See steps on [verifying checksums on Mac](./guides/verify_checksums_windows.md)
#### Linux
Place the file with checksums into your directory and run following command:
  
  ```bash
  md5sum -c checksums.md5
  ```

## Step 5: Create a README file

Write minimal information about the folder and data you have just downloaded.

The README file should be in plain format (TXT, Markdown) and contain following information:
  * dataset name/title
  * date of creation/download
  * data origin
  * version of the data
  * data owner/responsible
  * data structure
  * how was the data downloaded/received  
  * ...

## Step 6: Make data read-only

To ensure that nobody will be tempering with the single original copy of the data, it is a best practice to make it read-only.

#### Windows
  1. Right-click on the folder
  2. Select `Properties`
  3. In `Attributes` section, check the `Read-only` checkbox
  4. Click on `Apply` button and confirm
   
#### Mac
TODO:
#### Linux
Navigate the parent directory and use `chmod` - GNU coreutils tool for changing the mode of the files and directories to be read-only

  ```bash
  cd ..
  chmod -R a-w test-data
  ```

#### Create a new version of your dataset
TODO:
1. create new folder with proper file name (include suffix with version or date)
2. place new data into the folder
3. Add CHANGE.log describing the change