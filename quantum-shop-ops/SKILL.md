# Quantum Shop Ops

## Work from the records he actually keeps

- Inputs are the daily khata and ledger spreadsheet, his shelf stock counts, and purchase receipts from buying trips. A count taken on paper or sent as a photo of the stock list is legitimate data; many shops count on a clipboard, and so does his.
- Always state the date a stock count is from. A count two weeks old produces a stockout date two weeks wrong.
- Never invent a sales figure, a stock level, a lead time or a price. Missing data is reported by item name, not smoothed over. Prices and totals come only from his records or figures he has given.

## Compute velocity in two windows

- For each stocked item, compute units sold per day over the last 7 days and over the last 28 days from the khata sales rows.
- The 7-day window catches what is happening now; the 28-day window is the stable baseline. Disagreement between them is information: an item selling at three times its baseline this week is trending or had one bulk order, and those need different responses.
- A period with zero sales because the item was out of stock is not zero demand; it is suppressed demand. Mark it as such, or the item gets under-ordered forever.
- New items with under two weeks of history are flagged "not enough history" by name and get no projected dates.

## Project stockouts conservatively

- Stockout date is stock on hand divided by the higher of the two velocities. Being early is cheap; being late loses the sale.
- Compare the stockout date against the buying-trip lead time (his Chawkbazar run cadence, typically days not weeks), and classify every item: order now (cover runs out within lead time plus a buffer), order on the next trip, fine, or not enough history.
- Sizing a reorder uses the 28-day rate, never the spike: target cover is the days until the following trip plus the lead time, minus stock on hand and minus anything already bought and inbound. Double-ordering a slow item buries cash for months.
- Round to the wholesale pack size and say which direction the rounding went. Every recommendation shows its taka cost, because he decides in cash, not in units.

## Enforce the dead-stock discipline

- Zero sales in 28 days means never a reorder candidate. Such items are reported as slow movers with the taka tied up in them; never compute days of cover for an item that is not selling.
- More than roughly 120 days of cover is overstock: report the excess units and the taka.
- Dead stock (no movement in about 90 days) gets a clearing proposal: bundle it with a mover, discount it, or move it to the counter. The total taka sitting in slow and dead stock is usually the most useful number in the whole report; lead with it after the stockout warnings.
- Seasonal items are the one exception: stock bought under a named seasonal plan (the winter plan, Eid stock) goes on a dated watch list tied to that plan instead of the clear-out list, and is judged when the season ends.

## Build the buy list, gated on his approval

- The buy list leads with the total taka and the count of items about to stock out, then order-now lines, next-trip lines, and slow movers. Every line carries velocity, days of cover, quantity and cost, so approval takes a minute instead of a rebuild.
- Nothing is ordered by the agent and no supplier is contacted. The list is a decision document for his buying trip; his yes is the purchase.
- Before a big trip, add a cash snapshot: cash on hand and bKash balance shown separately (never merged — his standing rule), the buy-list total, and what remains after, so the trip never silently eats the shop's running cash.
- Seasonality is applied only where a year of khata history supports it. With less, say so and ask him: he knows his school-front season (exams, new-class January, winter) better than a short history does. Use his seasonal plans as the input instead of inventing a multiplier.

## Run the weekly business pulse

- Once a week, produce a one-page pulse from the khata and the Page: cash balance and bKash balance separately, each with its change versus last week; sales this week versus last week; the top sellers by units and by taka; the order-now stock list; taka tied in dead stock; and one line of page numbers (posts published, best post).
- Numbers lead, words follow. Never write "sales are healthy"; write the figure and its delta and let him judge.
- End with the single most important thing needing his attention, named specifically with its next step. A vague worry is not a pulse item.
- Any section with no data is marked n/a and skipped, never filled with a guess. If he would rather supply three numbers by voice than open the sheet, build the same pulse from them and label the source as owner-supplied.

## Available connectors

- [Facebook](/opt/hatch/connectors/facebook_cli/CONNECTOR.md) for the Page side of the weekly pulse: posts, insights and engagement on Pages he manages.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

## Alternatives for better results

- For deeper analysis of the same numbers — trends, market research, experiment design — use quantum-data-insight; this skill runs the weekly operational rhythm.
- For selling what the ops side stocks (listings, captions, live sessions, follow-ups), use ai-sales-manager; for campaign planning use quantum-digital-marketing.
- The khata stays his record of truth. This skill reads it and proposes; it never rewrites history in it.
