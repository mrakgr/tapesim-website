# Troubleshooting

## "Windows protected your PC" when installing

TapeSim isn't code-signed yet, so Windows SmartScreen warns on the installer. Click **More info → Run anyway** to continue. Code signing is coming.

## "This license is activated on a different machine"

Your license activates on up to 3 machines. If you've moved to a new PC and hit the limit, either click **Activate** on the new machine (it uses one of your 3 activations) or email **support@tapesim.app** to extend your limit or free up the old machine. See [Activating your license](#activating-your-license).

## My downloaded days don't show up in the library

- Make sure the files are in the exact layout `…\.tapesim\data\databento\mbo\<SYMBOL>\<DATE>\<VENUE>.dbn.zst`. A day only appears once its folder holds at least one `…dbn.zst` file. See [Where data is stored](#where-data-is-stored).
- If you set **`TAPESIM_DATA_ROOT`**, the library reads from *there*, not the default folder — check the files are under that path.

## A venue says `no-mbo` or `out-of-range` when I quote

- `no-mbo` — that venue doesn't publish the order-by-order data TapeSim needs for that ticker; it's simply skipped.
- `out-of-range` — there's no data for that date on that venue (e.g. a non-trading day, or before the ticker existed). Try a different date.

See [Downloading market data](#downloading-data).

## The trading controls are greyed out

You're in **viewer mode**. The ladder, chart, book, and tape all work, but placing orders requires a license. Paste your key on the gate screen — see [Activating your license](#activating-your-license).

## How updates work

On Windows, TapeSim checks for updates in the background each launch and applies them automatically on the **next** launch — you don't need to reinstall. You'll know an update landed because the version number in the **window title** changes. The portable zip and the Linux build don't auto-update; re-download them from the [download page](download.html).

## Still stuck?

Email **support@tapesim.app** with what you were doing and what you saw, and we'll help. You can also open an issue on the [tapesim-website repository](https://github.com/mrakgr/tapesim-website) if you'd rather report it publicly.
