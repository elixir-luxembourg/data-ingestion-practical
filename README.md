# Practical exercise on data ingestion

In this practical, you will perform multiple steps needed on data ingestion and working environment setup. You will download the test dataset, verify its integrity and add minimal documentation. Finally, you will have data stored in optimal way for subsequent (re-)use in your future steps.

## Requirements

Participants are required to have several tools installed before the practical. These will allow them to work with `.7z` archives and verify MD5 checksums. Follow the link according to your platform:

* [Windows](./requirements/windows.md)
* [Mac](./requirements/mac.md)
* [Linux](./requirements/linux.md)

## Step 1: Register the data in your local data catalogue

Registering the data is necessary for compliance with GDPR. The record should also contain information on actual physical location of the data which should be known before actual ingestion.

## Step 2: Receive data and decryption password

Please, read the [email](./data/email-with-data-link.md) from your collaborator with download link and password link.

* Download the data
* Get encryption password

## Step 3: Checksums

Your collaborator/data provider has generated checksums before uploading the data on your shared storage. These are commonly saved in plain text file and placed close to the actual data.

In our test scenario, `md5sum` tool was used for checksum generation.

* Open the downloaded checksum file (`EPIC-DREM_chip-seq.7z.md5`) with your favorite text editor and inspect the content

### Verify checksums

Data might have been corrupted already on the server or during the transfer. This step ensures that the data are exactly the same as at the time of the last checksum computation.

#### Windows

1. Put the checksum file next to your file archive
2. Run `md5summer.exe` (see [instructions](../requirements/windows.md) for download)
3. Choose the root folder to be the folder with the file archive

   <img src='./img/win_checksum-root-folder.png' width=300>

4. Ensure the `MD5` algorithm is selected
5. Click `Verify sums` and select the file with checksums
6. Inspect the result

    <img src='./img/win_checksum-choose-file.png' width=300>

#### Mac with GUI

1. Install and run `Checksum` tool (see [instructions](../requirements/mac.md))
2. Choose MD5 algorithm
3. Drag and drop the file archive into `Checksum` window

   <img src="./img/mac_checksums-field.png" width=300>

4. Compare the result with the provided checksum by pasting it into `Paste reported checksum here` field. 

#### Linux
Place the file with checksums next to the file archive and run following command:
  
  ```bash
  md5sum -c EPIC-DREM_chip-seq.7z.md5
  ```

## Step 4: Decrypt and extract the data

### Windows

1. Right-click on the archive file
2. Select 7zip -> Extract here
3. Enter the encryption password

<img src='./img/win_7zip_extract-archive.png' width=300>
<img src='./img/win_7zip_enter-password.png' width=300>

### Mac with GUI

1. Right-click on the file archive and select "Open with" -> KEKA

   <img src="./img/mac_keka-right-click.png" width=300>

2. Enter the encryption password

### Linux

Use `7z` command line tool to extract the archive.

  ```bash
  7z x EPIC-DREM_chip-seq.7z
  # Enter the ecryption password
  ```

## Step 5: Create a README file

Write minimal information about the folder and data you have just downloaded.

The README file should be in plain format (TXT, Markdown) and contain following information:
  
  * dataset name/title
  * project name
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

#### Mac with GUI

1. Right-click on the folder/file and select "Get Info"
2. Expand the section `Sharing & Permissions`
3. If the small lock icon at the bottom is locked, click on it to unlock it.
4. Set Priviledge to `Read only` for all users/user groups.
5. Use bottom dropdown icon to apply changes to all enclosed items

    <img src=".img/../img/mac_read-only-permissions-apply.png" width=300>

#### Linux
Navigate the parent directory and use `chmod` - GNU coreutils tool for changing the mode of the files and directories to be read-only

  ```bash
  cd ..
  chmod -R a-w test-data
  ```

<!-- ## Step 7: Create a new version of your dataset

1. create new folder with proper file name (include suffix with version or date)
2. place new data into the folder
3. Add CHANGE.log describing the change -->

### Final Assingment

Your task will be to update the dataset and sent it to the trainer. To follow best practices, you should:
1. Prepare data for transfer
   1. include README file for recipient in the folder
   2. create an encrypted archive
   3. generate checksums
2. Send the data, checksums and encryption password securely. Remember to use secure channels designed for data transfer.

#### Windows

1. Right-click on the folder and select 7-zip -> Add to archive

    <img src="./img/win_7zip_add-to-archive-right-click.png" width=300>

2. Select archive name and format, enter encryption password and hit OK
  
    <img src="./img/win_7zip-add-to-archive.png" width=300>

3. For checksum generation you can use again the `md5summer` tool:
   1. Select the root folder
   2. Click on "Create sums"
   3. Add archive file to the selection and hit OK

      <img src=".img/../img/win_md5summer-add-to-list.png" width=300>

   4. Save the checksum file

#### Mac with GUI

1. Open KEKA tool

    <img src="./img/mac_keka-add-to-archive.png" width=300>

2. Choose the type of your archive and enter encryption password
3. Drag and drop the folder into the window
4. Hit OK
5. For checksum generation open the `Checksum` tool and drag and drop the file archive

#### Linux

Create an archive:

  ```bash
  7z a <name-of-the-archive>.7z <folder-to-be-archived> -p
  # enter the encryption password
  ```
  
Genereate checksum file for the archive:

  ```bash
  md5sum <name-of-the-archive>.7z > checksums.md5
  ```
