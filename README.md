## Sears Tele-Games Super Video Arcade (49 C 75022)

Sears' Intellivision I clone, sold as the **Super Video Arcade**.

### Hardware

- **49 C 75022** — Sears Super Video Arcade console
- **49 C 75421** — extra controllers

### Catalog evidence

The system first appears in the 1981 Sears Christmas Book. It is listed on printed page 667 (archive viewer page 669) as the **Sears Super Video Arcade**, model 49 C 75022, at $266.99, with Poker/Blackjack included. The listing states compatibility with Sears and Mattel Intellivision cartridges.

- [1981 Sears toy catalog scan](doc/sears-1981-christmas-wish-book-toys-pages-480-671.pdf)
- [Extract: printed pages 663–667](doc/sears-1981-super-video-arcade-printed-pages-663-667.pdf)
- [1980 Sears toy catalog scan](doc/sears-1980-christmas-wish-book-toys-pages-480-670-searchable.pdf) — includes the Atari-compatible Sears Video Arcade, not the Super Video Arcade.

### Reference

Build target: <https://ebay.io/m/9a6etL>

# HP 1600A/1607A with a 10-bit CP1610 System

The CP1610 has a **16-bit address bus** and a **10-bit data bus**. Each address selects a 10-bit word, so its 16-bit address space contains up to **65,536 word addresses**. Some addresses may be assigned to system hardware or I/O rather than RAM or ROM.

The **HP 1600A** can monitor up to 16 logic signals at once. For a basic capture, connect it to the 10 data lines and use the remaining six inputs for signals such as the clock, read/write control, or selected address bits.

Adding the **HP 1607A** expands the setup to 32 monitored signals. That can let you watch all 10 data lines, all 16 address lines, and several control signals together. The additional analyzer provides **more signal coverage**, not a longer capture: the combined display shows up to 16 rows of captured data. The 1607A also requires a compatible external display, and using it disables the 1600A’s compare mode.

**In short:** the 1600A alone is enough to examine the 10-bit data bus. Add the 1607A when you want to correlate data with the full address bus and more control signals at the same time.
