# Device-Local Authentication

- What it covers:
    - Different levels of authorization for CLI sessions
    - Assign passwords to CLI sessions
    - Requir log-in with a username
    - Change privilege levels
- What it is:
    - the least complex option
    - baseline level of security
    - non-AAA security feature
    - device-locally configured

## IOS CLI Modes
- User EXEC Mode
    - one-time commands, such as show or more commands
- Privileged EXEC Mode
    - access to all commands
- Global Configuration Mode
    - affect the system as a whole
- Interface Configuration Mode
- Subinterface Configuration Mode

## Terminalogies
- `line`
    - the software component that manage local/remote CLI sessions
    - local: `line console 0`
    - remote: `line vty <line-number> [<ending-line-number>]`

## Local Password Encryption
- The following password types are stored as plain text in the configuration by default:
    - Console passwords for local CLI sessions
    - Virtual terminal line passwords for remote CLI sessions
    - Username passwords
    - Privileged EXEC mode passwords
    - Authentication key chain passwords (RIPv2 and EIGRP)
    - OSPF authentication keys for authenticating OSPF neighbors
    - BGP, IS-IS passwords
- To encrypt them, run `service password-encryption`
