# FTP vs TFTP
|                                  | FTP | TFTP |
|----------------------------------|-----|------|
| Username/Password Authentication | ✅   | No   |
| Data Encryption                  | No  | No   |
| Directory/File Listing           | ✅   | No   |
| Transport Layer Protocol         | TCP | UDP  |

## FTP
- modes
    - active: server initiates data connections
        - port 20 for data
    - passive: client initiates data connections
        - port 21 for control
        - using dynamically allocated port for data
