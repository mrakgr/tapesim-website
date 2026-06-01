# The trading screen

This is where you replay a session and place simulated orders. The header up top names the day and its size (e.g. *"EOSE — 2026-05-13 | 193 snapshots | 4642481 MBO records"*).

## The toolbar

From left to right:

- **← Library** — return to the [Library](#loading-a-day) (confirms first if you have an open position).
- **Play / Pause** — start or stop replay. Keyboard: **Space**. (See [Keyboard shortcuts](#keyboard-shortcuts).)
- **Speed** — `1.0x`, `5.0x`, `30.0x`, `300.0x`. The active speed is highlighted. Replay advances the session clock at this multiple of real time.
- **⚙ (settings)** — opens a flyout with your trading defaults:
  - **Order size (shares)** — how many shares each ladder click places.
  - **Tick size (cents)** — the price increment of the ladder, in half-cent steps.
  - **Venue** — which venue your simulated orders route to (the dropdown lists every venue in the loaded day).
- **Clock** — the current session time (`HH:MM:SS`) and whether it's *playing* or *paused*.
- **Cancel All** — cancels every working order at once.
- **Position** — *Flat*, or `Pos: +100 @ 95.42` when you hold one.
- **P&L** — `P&L: +25.00 (u -50.50)` — realized, with unrealized in parentheses; green when up, red when down.

> In **viewer mode**, the order size and venue controls are disabled, **Cancel All** is greyed out, and a **Viewer mode** badge replaces the position/P&L. Activate a license to enable trading — see [Activating your license](#activating-your-license).

## Scrubbing through the session

The **slider** under the toolbar spans the whole session. Drag it to jump to any moment. As replay plays, it tracks the current time. You can also nudge ±5 seconds with the **← / →** arrow keys.

## The panels

Below the toolbar are two tabs:

- **Ladder** — the DOM price ladder, where you place orders. This is the main view — see [The DOM ladder](#the-dom-ladder).
- **L2** — the Level-2 book (top) and time & sales (bottom), split by a draggable divider.

**Level-2 book** shows resting size by venue and price — bids on the left (best at top, green), asks on the right (best at top, red).

**Time & sales** is the tape: every print, newest at top, with time (to the millisecond), price, size, and venue — coloured green for trades at the bid, red at the ask, yellow at the mid. It keeps a rolling one-minute window.

Next: [The DOM ladder](#the-dom-ladder).
