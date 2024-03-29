# 2ACoin-Checkpoints

### How To Sync Quickly
##### In 2ACoin v1.1.0+ you can sync a fresh chain from 0 much quicker by loading "checkpoints" with your daemon.

### Setup

- Go to the latest release of 2ACoin-Checkpoints [https://github.com/2acoin/2acoin-checkpoints/releases/latest](https://github.com/2acoin/2acoin-checkpoints/releases/latest)
- Click the **checkpoints.zip** attached to the release and perform a `Save As...` to download the latest checkpoints.zip.
- Extract the zip file and place checkpoints.csv in the same folder as your 2ACoind daemon
- You can get 2ACoind from here if you don't have it already: https://latest.2acoin.org
- Make sure you shut down any GUI wallets, or any other instances of 2ACoind.

### Usage

#### Windows

- First, open a command prompt in the same directory as 2ACoind.
- This can easily be done by moving to the 2ACoind directory in Windows Explorer, then typing `cmd` in the search bar and hitting enter:

![Opening cmd](https://i.imgur.com/JQ4N8HF.png)  

- Finally, type `2ACoind.exe --load-checkpoints checkpoints.csv` in the command prompt.

#### Linux, Apple

- First, open a command prompt in the same directory as 2ACoind.
- You can use the `cd` command to change to this directory. For example, `cd Downloads/2acoin-vx.x.x`
- Alternatively, your file manager may provide the ability to open a terminal in your current directory. Navigate to the folder with 2ACoind in, and try right clicking, to see if you can open a terminal there:

![Opening terminal](https://i.imgur.com/VJWWgL2.png)

- Open your terminal program 
- Finally, type `./2ACoind --load-checkpoints checkpoints.csv` in the terminal.

### Expected Output

If you did the steps correctly, you should see something like this output.

```
2018-Sept-13 11:58:39.654478 INFO    Welcome to 2ACoin vx.x.x.x ()
2018-Sept-13 11:58:39.654914 INFO    Module folder: 2ACoind
2018-Sept-13 11:58:39.655249 INFO    Loading Checkpoints for faster initial sync...
2018-Sept-13 11:58:40.854979 INFO    Loaded 35432 checkpoints from checkpoints.csv
```

- 2ACoind will then start syncing from checkpoints.
- If you are using the CLI wallet, then you can just wait for it to finish syncing, and open your wallet.
- If you are using a GUI wallet, let it finish syncing, close it down by typing `exit` in the window, then open your GUI wallet.

### Common Errors

#### Invalid checkpoint file format

```
2018-Sept-13 12:10:08.325056 INFO    Loading Checkpoints for faster initial sync...
2018-Sept-13 12:10:08.339667 ERROR   Invalid checkpoint file format
2018-Sept-13 12:10:08.341758 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, the file you are opening is either not a .csv file, or hasn't been downloaded correctly.
- Ensure you downloaded the file from the most current release by clicking the file attached to the release, and choosing `Save As...`.
- If you incorrectly chose the wrong file, you can accidentally download a html page instead.
- When you open up the file in a text editor, it should have lots of lines like this:

```
0,7fb97df81221dd1366051b2d0bc7f49c66c22ac4431d879c895b06d66ef66f4c
1,8c9738f961a278486f27ce214d1e4d67e08f7400c8b38fe00cdd571a8d302c7d
2,2ef060801dd27327533580cfa538849f9e1968d13418f2dd2535774a8c494bf4
```

#### Failed to load checkpoints

```
2018-Sept-13 12:14:57.544286 INFO    Loading Checkpoints for faster initial sync...
2018-Sept-13 12:14:57.544569 ERROR   Could not load checkpoints file: checkpoints.csv
2018-Sept-13 12:14:57.544823 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, it means the file isn't present in the directory you are in.
- Make sure you have placed the checkpoints.csv file in the same directory as 2ACoind.

#### 2ACoind.exe is not recognized / No such file or directory

```
C:\Users\your_user>2ACoind.exe --load-checkpoints checkpoints.csv
'2ACoind.exe' is not recognized as an internal or external command,
operable program or batch file.
```

`bash: ./2ACoind: No such file or directory`

- If you see output like one of the above, it means your terminal isn't in the same folder as the 2ACoind program.
- You can type `pwd` to see what folder you are currently in.
- Try following the steps above to get into the right folder, then try again.
- If you type `ls`, you should see the 2ACoind program, if you are in the correct folder:

```
[2acoin-v1.1.0]λ ls  
2ACoind  2acoin-service  miner  zedwallet
```

#### IO error

```
2018-Sept-13 11:58:40.857058 INFO    Opening DB in /home/your_user/.2ACoin/DB
2018-Sept-13 11:58:40.858174 ERROR   DB Error. DB can't be opened in /home/your_user/.2ACoin/DB. Error: IO error: While lock file: /home/your_user/.2ACoin/DB/LOCK: Resource temporarily unavailable
2018-Sept-13 11:58:40.873692 ERROR   Exception: IO error
```

- If you see output like the above, something else has got the database open already.
- Make sure you have closed down any other 2ACoind's, GUI wallets, and walletd.
- Use a task manager to help you find any which might be running in the background, then try again!
