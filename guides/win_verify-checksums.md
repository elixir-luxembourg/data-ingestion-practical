# Verify checksums on Windows
1. Put the `checksums.md5` file in your dataset directory
2. Install `md5summer` tool (see [instructions](../requirements/windows.md))
3. Run `md5summer.exe`
4. Choose the root folder to be the folder of the dataset
5. Ensure the `MD5` algorithm is selected

   <img src='../img/win_checksum-root-folder.png' width=300>

6. Click `Verify sums` and select the `checksums.md5` file
7. Verify that all your checksums are correct

    <img src='../img/win_checksum-choose-file.png' width=300>
