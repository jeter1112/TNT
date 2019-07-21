# TNT: Transfer layer Network Tools

## Table of contents
- [netfilter](#netfilter)
- [Hotspot](#hotspot)
- [Atheros](#Atheros)

## Netfilter

> IP spoofing

- issues

    - `priority` compared to NAT
    - `check sum` 
 
- reference

    - [check IPspoof](https://github.com/jeter1112/pacmea)


## Hotspot
> create_ap  ---> hotspot

- create_ap

    - issues

        - `rate` 20-40Mbps, depends on [HT40+]
        - `5G` often failed, not improve `rate`

- hostapd

    - issues

        - `rate` 20-400Mbps, depends on 80211ac

        - `dnsmasq` conficts with `systemd-r`
    
    - reference
        
        - Hotspot.txt

## Atheros

- issues

    - `rate` as AP

        - 20M: IR,radar detection (`iw list | grep MHz`)

        - 400M: modify `ath.ko`,functions like `ath_reg_apply_radar_flags`,
        `ath_reg_apply_beaconing_flags`,
        `ath_reg_apply_ir_flags`. return immediately.
        `ath_regd_init_wiphy`, return before `custom-regulatory`.
    
    - `AIFS`

        - memory map

        - ieee80211_local
    
    - `source code`: from `backsport` to `linux-source`

        - compile format: kbuild like `hello world` kernel module makefile

        - install: if solid, mv to the '\lib\modules**\ath'
    - driver load order: unload top down, load bottom up.
        
- reference

    - [aifs](https://github.com/jeter1112/aifs)  
         
        