# fusenetmd
This is a script that will mount a directory as a FUSE drive, allowing users to load data files onto a non-HiMD-formatted MiniDisc. This leverages NetMD exploits and is unstable, so this is not recommended for reliable storage or transfer of data.

### Requirements
- Mac or Linux machine
- FUSE File System Driver
- Node Version 18 (later versions will not work)
- A NetMD-compatible MiniDisc Recorder

### Initial setup
- Open a terminal and navigate to the project directory
- Run the following commands:
```
npm i
mkdir [path to mount directory]
ts-node src/main.ts
```

- Alternatively, update the `start` script in `package.json` to `ts-node src/main.ts [path to mount directory]` and run:

```
npm run start
```

### Transferring files
The path specified as your mount directory will appear as a FUSE drive. Copying files will cause the app to write the data to the disc in the connected NetMD Recorder.

If attempting to write fixes/extend the app, mounting the drive to a directory outside the project is recommended as applications using the directory may hang.

NOTE: MiniDiscs are very slow to write, so even a few megabytes will take a while.

### Ejecting
Files may not be written correctly when ejecting the drive. You will need to enter the following command to ensure the write completes:
```echo 1 > [path to mount directory]/\$system/force_immediate_flush`

### Known issues
- The application is generally unstable and requires patience
- (reproduced on Mac) dragging and dropping of files may cause a freeze when writing to disc. Opening a separate terminal to copy files over will perform better
- On Mac, once a write completes, you may not need to flush before ejecting. There is no guarantee the write will be successful.



