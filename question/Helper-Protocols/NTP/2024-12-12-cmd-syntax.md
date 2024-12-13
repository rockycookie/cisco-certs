### Which NTP server would be used, and why?
- [ ] R2 would be used because it is configured first.
- [ ] R2 would be used because it has a higher stratum value.
- [ ] R3 would be used because it is configured last.
- [x] R3 would be used because it has a lower stratum value.
- [ ] Neither NTP servers would be used because ntp master is not configured.

```
R1# show run | inc ntp
ntp server <R2 IP>
ntp server <R3 IP>

R1# show ntp associations
address     ...     st      ...
<R2 IP>     ...     2       ...
<R3 IP>     ...     1       ...
```
