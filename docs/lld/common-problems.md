# LLD - Common Problems

## Parking Lot

**Entities:** ParkingLot, Floor, Slot, Vehicle, Ticket, Payment
**Patterns:** Strategy (pricing), Factory (vehicle/slot), Observer (slot availability)

```
Key Design Decisions:
- Slot types: SMALL, MEDIUM, LARGE → mapped to vehicle types
- Pricing: Strategy pattern (hourly, flat, tiered)
- Ticket: generated on entry, stores entryTime + slot + vehicle
- Payment: Strategy pattern (cash, card, UPI)
- Search: by vehicle number, owner name, mobile
```

---

## Vending Machine

**Entities:** VendingMachine, Product, Inventory, Coin, State
**Patterns:** State (idle → selecting → dispensing → refunding)

```
States: IdleState → HasMoneyState → SelectProductState → DispenseState
Key: Each state handles insertCoin(), selectProduct(), dispense(), cancel() differently
```

---

## URL Shortener

**Entities:** URL, User, ClickAnalytics
**Key:** Base62 encoding, counter-based or hash-based ID generation

---

## Todo List / Task Manager

**Entities:** Task, User, Board, List
**Patterns:** Observer (notify on change), Command (undo/redo)

---

## Elevator System

**Entities:** Elevator, Floor, Request, Scheduler
**Patterns:** Strategy (scheduling: FCFS, shortest seek), Observer (floor arrival)

---

## BookMyShow / Ticket Booking

**Entities:** Movie, Show, Theater, Seat, Booking, Payment
**Key decisions:** Seat locking (temp hold for 10 min), concurrency handling

---

## Chess / Tic-Tac-Toe

**Entities:** Board, Cell, Player, Piece, Move
**Patterns:** Strategy (AI difficulty), Command (undo move)

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->
