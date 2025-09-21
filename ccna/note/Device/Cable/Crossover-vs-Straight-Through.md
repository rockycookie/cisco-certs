# Crossover vs Stright-Through
Summary:
- Straight-through cable must connect exactly one end from Switch/Bridge/Hub
- everythin else needs crossover

## Details
- UPT pintouts
    - Same --> crossover
    - Diff --> straight-through
- Switch/Bridge/Hub pinouts are special, everything else are the same

| UTP cable type between | PC               | Switch/Bridge/Hub | WLAN AP   | Router    |
|------------------------|------------------|-------------------|-----------|-----------|
| PC                     | crossover        |                   |           |           |
| Switch/Bridge/Hub      | straight-through | crossover         |           |           |
| WLAN AP                | crossover        | straight-through  | crossover |           |
| Router                 | crossover        | straight-through  |           | crossover |
