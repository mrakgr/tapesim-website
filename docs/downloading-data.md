# Downloading market data

TapeSim replays real recorded market days. You download those days **straight from inside the app**, using your own [Databento](https://databento.com) account — so the data (and its cost) is yours, billed to your Databento account, not ours.

## Step 1 — add your Databento API key (one time)

Before you can download anything, TapeSim needs your Databento API key.

> **At the time of writing, Databento gives new users $125 in free credits** — enough to download a good number of market days before you pay anything.

1. On the **Library** screen, click the **⚙** button next to **Quote**. (If you haven't set a key yet, a yellow banner reminds you: *"No Databento API key set. Open the ⚙ menu to add your key before downloading."*)
2. In the flyout, click **Open databento.com ↗** to create a free account and copy your API key from the portal.
3. Paste the key (it starts with `db-…`) into the field and click **Save key**.
4. TapeSim validates it and shows **✓ Key saved and valid** — or **✗ Key rejected** with the reason if something's off.

Your key is stored locally and reused for every download afterward.

## Step 2 — quote a day

In the **Download a new day** form:

1. Enter a **Symbol** (e.g. `EOSE`) and a **Date** (`YYYY-MM-DD`). Not sure what to try? Pick from the [gap play examples](#gap-play-examples).
2. Click **Quote**. TapeSim asks Databento which venues have data for that ticker-day and what it costs. You'll see *"Quoting…"* with an elapsed timer.

The result is a table, one row per venue:

| Status | Meaning |
|---|---|
| `cached` | You already have this venue's file — no charge. |
| `pending $X.XX` | Available to download, at this cost. |
| `no-mbo` | This venue doesn't publish the order-by-order data TapeSim uses. |
| `out-of-range` | No data for that date on this venue. |
| `err: …` | Something went wrong probing this venue. |

Below the table: **Aggregate cost: $X.XX (N to download)** — the total you'd be charged and how many venues are pending.

## Step 3 — download

Click **Confirm download** (enabled once at least one venue is pending). TapeSim downloads the venues **in parallel**, showing a progress bar per venue:

- `queued` → `…bytes (NN%)` → **done · …** (green), or **failed: …** (red) if a venue errors.

When it finishes you'll see a summary like *"Done. 12 downloaded, 3 cached, 0 errors."* and the day appears in your Library list, ready to [open](#loading-a-day).

> **Tip:** already have data files from elsewhere? You can drop them into the data folder by hand instead of downloading — see [Where data is stored](#where-data-is-stored).
