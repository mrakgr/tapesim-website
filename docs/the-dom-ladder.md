# The DOM ladder

The ladder is a vertical price grid — the heart of TapeSim. Each row is one price level; you place and cancel simulated orders by clicking on it.

## The columns

| Column | Shows |
|---|---|
| **Vol** | Volume traded at that price this session (a histogram bar + count). |
| **Price** | The price level. May carry suffixes (below). |
| **Bid** | Resting bid size at that price. |
| **Bid T** | Recent trades that hit the bid (fade out over time). |
| **Mid** | Recent trades at the mid. |
| **Ask T** | Recent trades that lifted the ask (fade out). |
| **Ask** | Resting ask size at that price. |

The best bid/ask rows are tinted faint green/red so the spread is easy to spot. Trade prints flash a coloured box in the trade columns and fade away, so you can see flow as it happens.

## Placing orders

With a license active (and your order size set in the **⚙** flyout):

- **Left-click in the Bid column** of a row → places a **buy** limit at that price.
- **Left-click in the Ask column** of a row → places a **sell** limit at that price.

Each order uses the **Order size** and **Venue** from the toolbar's ⚙ settings.

## Cancelling

- **Right-click a row** → cancels your working orders at that price.
- Or use **Cancel All** in the toolbar to clear everything at once.

## Reading your orders and position on the ladder

The **Price** cell shows where you stand at that level:

- `·100` — you have a working order of 100 shares resting at this price.
- `⊕+250` — you hold a position of +250 (long) anchored here; a negative number is short.
- Both can appear together, e.g. `95.42 ·100 ⊕+250`.

Rows with a working order are tinted green (buy) or red (sell); your position row is tinted blue.

## Moving the ladder

- **Double-click** the grid → recenter on the current mark price.
- **Mouse wheel** → scroll the visible price range up or down.

As the market moves, recentre whenever the action drifts off-screen.

> In **viewer mode** the ladder still renders fully and updates live — clicks just don't place anything. Activate a license to trade.

Next: [Keyboard shortcuts](#keyboard-shortcuts).
