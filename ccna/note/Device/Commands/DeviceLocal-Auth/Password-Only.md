# Password-Only Device-Local Authentication

## Assigns a password for local CLI session over the console port
```
Device(config)# line console 0
Device(config-line)# password Ji8F5Z
Device(config-line)# login
```

## Assigns a password for remote CLI session
```
Device(config)# line vty 0 4
Device(config-line)# password H7x3U8
Device(config-line)# login
Device(config-line)# transport input telnet
```
Note:
- `transport input {telnet | all}` is needed as ssh requires username

## Configures a password for privileged EXEC mode
- Cisco recommends that you use the enable secret command
    - which is encrypted with the more secure MD5 algorithm

```
Device(config)# enable secret t6D77CdKq
```
or
```
Device(config)# enable password t6D77CdKq
```

## Configures password encryption for all passwords
```
Device(config)# service password-encryption
```
