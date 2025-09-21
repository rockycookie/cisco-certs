# SSH

## Generate Keys - **Necessary**
```
Router(config)#crypto key generate rsa general-keys modulus 2048
% Please define a hostname other than Router.

Router(config)#hostname myrouter

myrouter(config)#crypto key generate rsa general-keys modulus 2048
% Please define a domain-name first.

myrouter(config)#ip domain-name myrouter.com

myrouter(config)#crypto key generate rsa general-keys modulus 2048
The name for the keys will be: myrouter.myrouter.com
% The key modulus size is 2048 bits
% Generating 2048 bit RSA keys, keys will be non-exportable...[OK]
*Mar 1 0:27:51.936: %SSH-5-ENABLED: SSH 1.99 has been enabled
```

## Allow remote seesion with SSH - **Necessary**
```
Device(config)# line vty 0 4
Device(config-line)# login local
Device(config-line)# transport input ssh
```
Note:
- `login local` assumes username-password exists

## Optionals
```
myrouter(config)# ip ssh ?
  authentication-retries  Specify number of authentication retries
  time-out                Specify SSH time-out interval
  version                 Specify protocol version to be supported

myrouter(config)# ip ssh version 2
```
