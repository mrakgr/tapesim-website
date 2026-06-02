# Getting started

TapeSim is a desktop order-flow simulator. It replays real recorded market days — the Level-2 book, time & sales, and a DOM ladder — tick by tick, and lets you place **simulated** orders against that flow to practice reading the tape. No broker, no real money.

## Install

1. Download **TapeSim** for your operating system from the [download page](download.html). Windows is the primary build (an installer that keeps itself up to date); Linux is a self-contained zip.
2. **Windows:** run `TapeSim-…-win-Setup.exe`. TapeSim isn't code-signed yet, so Windows SmartScreen may say *"Windows protected your PC"* — click **More info → Run anyway**. The app installs for your user, adds a Start Menu shortcut, and from then on **updates itself silently** (you'll see the version in the window title bump after an update).
3. **Linux:** unzip and run the `TapeSim.Ui` binary directly.

> Prefer not to install on Windows? A **portable .zip** is also on the download page — unzip and run, no installer (but it won't auto-update).

## First launch — the gate

When TapeSim opens you'll see the **Activate TapeSim** screen. You have two ways forward:

- **Activate a license** — paste the license key from your purchase email into the field and click **Activate**. This unlocks **sim trading**. See [Activating your license](#activating-your-license).
- **Continue as viewer** — click this to skip the key and use TapeSim in **viewer mode**. You can browse the chart, Level-2 book, time & sales, and the DOM ladder for any market day, but order placement stays locked.

You can start as a viewer and activate later — viewer mode is asked again each launch, while an activated license is remembered.

## What you get in each mode

| | Viewer (free) | Licensed |
|---|---|---|
| Chart, Level-2 book, time & sales | ✓ | ✓ |
| DOM ladder display + replay controls | ✓ | ✓ |
| Place simulated orders, position & P&L | — | ✓ |

## Your first session

Once past the gate you land on the **Library**. From here you:

1. [Download a market day](#downloading-data) (you'll need a free Databento API key first), or open one you already have.
2. [Open a day](#loading-a-day) to enter the trading screen.
3. [Place orders on the ladder](#the-dom-ladder) and watch your fills, position, and P&L.

Next: [Activating your license](#activating-your-license).
