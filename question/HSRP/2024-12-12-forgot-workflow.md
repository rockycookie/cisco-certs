### Routers R1 and R2 use the interface addresses shown in the figure. The configuration also enables HSRPv2 on those same interfaces, with VIP 10.1.1.15 and HSRPv2 group 14. PC1 and PC2 refer to 10.1.1.15 as their default router. Which answer(s) list the MAC addresses that could appear in the ARP tables of PC1 and PC2?
- [ ] 0000.0c9f.f00e
- [x] 0000.5e00.010e
- [ ] 0007.bf00.0e01
- [ ] 0000.0c9f.f00f
- [ ] 0000.5e00.010f
- [ ] 0000.c7ff.f001

HSRP uses one virtual MAC address per HSRP group, with the active router implementing the functions associated with the virtual MAC. So, any hosts using the HSRP VIP, when they use ARP, receive an ARP reply listing that HSRP group’s virtual MAC address, regardless of which router happens to be the currently-active router.

Both routers will calculate the same virtual MAC address value. With HSRPv2, the routers use the pattern 0000.0c9f.fzzz, where zzz is the three-digit hex equivalent of the decimal HSRP group number. With group number decimal 14 (hex E), to create the final three hex digits, you add leading 0s to create the three-digit equivalent (zzz) value of 00E. The virtual MAC address used by the routers will be 0000.0c9f.f00e.
