# Device Security

## Objective
Configure basic security settings on Cisco devices.

## Commands Used
- hostname
- enable password
- enable secret
- service password-encryption
- copy running-config startup-config

## Verification
- show running-config

## What I Learned

- "enable secret" is more secure than "enable password"
- "enable secret" is stored as a hash and takes precedence over 1enable password"
- "service password-encryption" encrypts plain-text passwords in the configuration
- The running configuration can be saved using 'copy running-config startup-config''write''write memory'



