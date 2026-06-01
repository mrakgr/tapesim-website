# Where data is stored

TapeSim keeps everything in a single folder in your user profile — `~/.tapesim`. On Windows that's:

```
C:\Users\<you>\.tapesim
```

Nothing is stored in the install folder, so updating or uninstalling TapeSim never touches your data, license, or settings.

## What's in it

```
.tapesim\
├─ data\databento\mbo\        downloaded market days
│  └─ <SYMBOL>\<DATE>\<VENUE>.dbn.zst
├─ api_key.json               your Databento API key
├─ license.json               your TapeSim license key
└─ session.json               your activation (machine-bound; not portable)
```

## Copying days in by hand

The library scans `data\databento\mbo` for downloaded days, so you can **add days without using the in-app downloader** — just place the files in the right layout:

```
…\.tapesim\data\databento\mbo\<SYMBOL>\<DATE>\<VENUE>.dbn.zst
```

For example:

```
…\.tapesim\data\databento\mbo\AAPL\2024-11-21\XNAS.dbn.zst
```

A day shows up in the library as soon as its folder contains at least one `…dbn.zst` venue file. (The files are Databento MBO data, zstd-compressed.)

## Changing the data location (advanced)

If you'd rather keep market data somewhere else (a different drive, a shared folder), set the **`TAPESIM_DATA_ROOT`** environment variable to the folder you want TapeSim to use. Both the in-app downloader and the library will read and write there instead of the default. The same `<SYMBOL>\<DATE>\<VENUE>.dbn.zst` layout applies under it.

## A note on `session.json`

Your activation is tied to the machine it was created on — copying `session.json` to another computer won't work (it simply won't be recognized there). To use TapeSim on another machine, just activate your key on it; see [Activating your license](#activating-your-license).
