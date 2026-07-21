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


<img width="415" height="358" alt="show_running-config" src="https://github.com/user-attachments/assets/9748e9fa-3ae6-451f-842d-9a4ce2b3b99d" />

<img width="538" height="399" alt="basic_device_security" src="https://github.com/user-attachments/assets/135a84a1-3897-4e81-b086-264d9d55d577" />


