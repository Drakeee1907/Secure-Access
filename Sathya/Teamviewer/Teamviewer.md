# TeamViewer – Remote Access and Remote Support

## 1. Installation

### 1.1 Introduction

TeamViewer is a remote access and remote support application that allows one computer to connect to and control another computer over the internet.

For this practical, two systems were used:

- **Mac:** Controller / Technician system
- **Windows:** Remote system

The overall setup was:

```text
+-------------------+                 +----------------------+
|       Mac         |                 |       Windows        |
| Controller        |  Internet       | Remote Computer      |
|                   | --------------> |                      |
+-------------------+                 +----------------------+
```
---
### 1.2 Installing TeamViewer on macOS

The Mac was configured as the computer that would control the Windows system.

 1. Open a web browser on the Mac.
 2. Visit the official TeamViewer website.
 3.  Navigate to the download section.
 4.  Select the version for macOS.
5. Download the TeamViewer installer.
6.  Open the downloaded installer.
7.  Follow the installation instructions.
8.  Allow the required macOS permissions  when prompted.
9.  Complete the installation and open TeamViewer.

After installation, the TeamViewer interface is displayed.

![Relative](./TVimg/Fig%201.1.png)
**Fig. 1:**  TeamViewer Provide Support interface displaying the device ID, temporary password, and remote-support connection options.

---

### 1.3 Installing TeamViewer on Windows

The Windows computer was configured as the remote computer.

For the initial remote-support exercise, TeamViewer QuickSupport was used.


1. Open a web browser on Windows.
2. Visit the official TeamViewer website.
3. Navigate to the download section.
4. Select the Windows version.
5. Download TeamViewer QuickSupport.
6. Open the downloaded application.
7. Allow the application to run.
8. TeamViewer displays the connection information.
9. Keep the application open while the remote-support connection is being established.

QuickSupport is useful for attended remote support, where the person using the remote computer is available to start the session.

--- 

### 1.4 TeamViewer Installation Difference

The software used on each computer depends on how the computer will be used.

| System  | Role                    | Typical Software                               |
| ------- | ----------------------- | ---------------------------------------------- |
| Mac     | Controller / Technician | TeamViewer                                     |
| Windows | Remote / Client         | QuickSupport for attended support              |

>**Note:** In this practical, the Mac PC was used as the controller, so the TeamViewer full/Provide Support version was installed on the Mac. The Windows PC was used as the remote computer, so TeamViewer QuickSupport was installed on it.

--- 

## 2. Initial Connection – Mac to Windows

After installing TeamViewer on both systems, the Mac was connected to the Windows computer.

### 2.1 Finding the Windows TeamViewer ID

1. Open TeamViewer on Windows.
2. Locate the TeamViewer ID.
3. Note the ID.
4. Keep TeamViewer running.

The TeamViewer ID identifies the remote TeamViewer device.

--- 

### 2.2 Connecting from Mac

1. Open TeamViewer on the Mac.
2. Select the option to control a remote device.
3. Enter the Windows TeamViewer ID.
4. Select Connect.
5. Wait for the authentication prompt.
6. Enter the required password/authentication information.
7. Complete the connection.

Once authentication is successful, the Windows desktop appears inside the TeamViewer window on the Mac.

![Relative](./TVimg/Fig%202.png)
**Fig 2:** Flow diagram illustrating the TeamViewer remote connection process from the Mac controller to the Windows remote PC.

---

### 2.3 Successful Remote Connection

After the connection was established, the Mac could control the Windows computer remotely.

The following were tested:

- Mouse control
- Keyboard control
- Copy and paste
- File transfer
- Annotation
- Ctrl + Alt + Delete
- Locking the computer
- Rebooting the computer
- Reconnecting after reboot

---

## 3. Basic Remote-Control Features

Once the remote session is established, TeamViewer provides several tools for controlling and managing the remote computer.

### 3.1 Mouse and Keyboard Control

The controller can use the mouse and keyboard to interact with the remote computer.

For example:

- Moving mouse cursor
- Left-click
- Right-click
- Scrolling
- Typing
- Open applications
- Navigate menu

The actions performed on the Mac are transmitted to the remote Windows computer. 

--- 

### 3.2 Copy and Paste

TeamViewer can provide clipboard sharing between the connected computers.

**Mac → Windows**

```bash
Mac:
Command + C

Windows:
Ctrl + V
```
**Windows → Mac**

```bash
Windows:
Ctrl + C

Mac:
Command + V
```

This is useful for transferring text, commands, URLs, and other supported clipboard content.

**Clipboard vs File Transfer**
| Feature       | Purpose                      |
| ------------- | ---------------------------- |
| Clipboard     | Copy/paste supported content |
| File Transfer | Transfer actual files        |

---

### 3.3 File Transfer

TeamViewer provides a File Transfer feature for transferring files between the two systems.

Files can be transferred in both directions, either from Windows to Mac or vice versa.

**Example:** Mac → Windows

- Establish the TeamViewer connection.
- Open the File Transfer feature.
- Select a file from the Mac.
- Select the destination on Windows.
- Start the transfer.
- Wait for the transfer to complete.
- Verify the file on Windows.

A small test file such as:
```bash
Transferfile.txt
```
can be used to verify this feature.

---

### 3.4 Annotation

The annotation feature allows the technician to mark or highlight parts of the remote screen.

It can be used to:

- Draw arrows
- Circle buttons
- Highlight areas
- Point out settings
- Explain troubleshooting steps

For example, a technician can highlight a particular button and tell the remote user where to click.

---

### 3.5 Send Ctrl + Alt + Delete

TeamViewer allows the technician to send the Windows:

```bash
Ctrl + Alt + Delete
```

This command is particularly useful when controlling Windows from a Mac because the two operating systems use different keyboard shortcuts.

1. Establish the remote connection.
2. Open TeamViewer remote actions.
3. Select Send Ctrl + Alt + Delete.
4. The Windows security screen appears.

The Windows security screen can provide options such as:

- Lock
- Switch user
- Sign out
- Task Manager
- Change password

---

### 3.6 Lock Remote Computer

The remote Windows computer can be locked from the TeamViewer session.

1. Establish the remote session.
2. Open the TeamViewer remote actions.
3. Select the lock option.
4. Windows displays the lock screen.

The authorized Windows user can then unlock the computer normally.

--- 

### 3.7 Reboot Remote Computer

TeamViewer can be used to restart the remote computer.

1. Establish the remote session.
2. Open the remote actions.
3. Select Reboot.
4. Confirm the operation if prompted.
5. Windows begins restarting.

The TeamViewer connection will temporarily disconnect because the computer is restarting.

--- 

### 3.9 Reconnect After Reboot

After the Windows computer finishes restarting:

1. Wait for Windows to completely boot.
2. Verify that TeamViewer is available.
3. Return to the Mac.
4. Enter the Windows TeamViewer ID.
5. Select Connect.
6. Provide the required authentication/password.
7. Re-establish the remote session.

The workflow is:

![Relative](./TVimg/Fig%203%20Reconnection.png)
**Fig 3:** This Flow demonstrates that remote administration can continue after a reboot when the remote setup supports reconnection.

--- 

## 4. Additional TeamViewer Features



### 4.1 TeamViewer Account

A TeamViewer account allows users to manage and organize remote devices from the TeamViewer interface.

After signing in, devices can be added to the Devices section. This makes it easier to identify and access previously configured computers.

Basic Procedure
Sign in to the TeamViewer account.
Open the Devices section.
Add or associate the required remote device.
The device appears in the device list.
The device can then be managed or accessed according to the available permissions.

A remote Windows device was added to the TeamViewer account and was displayed in the Devices section.

![Relative](./TVimg/Fig%204.1.png)

**Fig. 4.1:** TeamViewer Devices section showing the added remote Windows device.

The TeamViewer ID of the remote Windows PC was obtained from TeamViewer QuickSupport and manually entered in the TeamViewer application on the Mac. After selecting Connect, the password provided by the Windows PC was entered to establish the remote session.

---

### 4.2 Easy Access

Easy Access provides a convenient way to connect to an authorized remote computer through a TeamViewer account.

After enabling Grant Easy Access to this device, the remote computer is associated with the authorized TeamViewer account. This allows the device to be accessed through the account without manually entering the TeamViewer ID and password each time.

Basic Procedure
1. Open TeamViewer on the remote Windows PC.
2. Sign in or configure the appropriate TeamViewer account.
3. Select Grant Easy Access.
4. Associate the device with the authorized account.
5. Open the TeamViewer Devices section on the controller.
6. Select the configured remote device.
7. Establish the remote connection.

Easy Access was enabled on the Windows PC and the device was successfully associated with the TeamViewer account.

![Relative](./TVimg/Fig%204.2.png)


**Fig. 4.2:** Easy Access configuration used to associate the Windows PC with the TeamViewer account.

--- 

### 4.3 Unattended Access

Unattended Access allows an authorized user to connect to a remote computer **without requiring someone at the remote computer to manually accept the connection**.

It is useful when a computer needs to be accessed remotely while the user is not present.

Common uses include:

- Remote maintenance
- Accessing a personal computer
- IT administration
- Regular remote support

The remote computer must be configured appropriately before unattended access can be used.

> **Note:** Unattended Access was studied conceptually but was not fully tested during this practical session.

---

### 4.4 Personal Password

TeamViewer can provide a **personal/permanent password** for a device, depending on the installed version and configuration.

Unlike a temporary password that may change between sessions, a personal password can be used for future connections to the same device.

The basic concept is:

```text
TeamViewer ID + Personal Password
              |
              v
          Remote Connection

```

---

## 5. Security

Remote access provides significant control over another computer, so security must be considered carefully.

### 5.1 Protect Credentials

Do not share the following publicly:

- TeamViewer passwords
- Personal passwords
- Account passwords
- Authentication codes

---

### 5.2 Verify the Remote Computer

Before connecting, verify:

- The TeamViewer ID
- The identity of the remote user
- That remote access is authorized
- That the correct computer is being accessed

---

### 5.3 Use Strong Passwords

Personal passwords should be:

- Strong
- Unique
- Difficult to guess
- Not reused on other services

---

### 5.4 Enable Two-Factor Authentication

Where available, enable two-factor authentication on the TeamViewer account to provide an additional layer of security.

---

### 5.5 End Remote Sessions

After completing the support task:

- Finish the required work.
- Verify the result.
- Disconnect the TeamViewer session.
- Close TeamViewer if it is no longer required.

---

### 5.6 Keep Software Updated

TeamViewer and the operating system should be kept updated to receive security fixes and improvements.

--- 

## 6. Troubleshooting
### 6.1 Cannot Connect

Check following possibilities, 

- Internet connection
- Correct TeamViewer ID
- Correct password
- TeamViewer is running
- Windows PC is powered on
- Firewall or network restrictions

---

### 6.2 Copy/Paste Not Working

Check following possibilities,:

- Clipboard functionality
- TeamViewer permissions/settings
- Whether the content is supported
- Whether the target application allows clipboard operations

---

### 6.3 File Transfer Not Working

Check following possibilities,:

- File Transfer feature
- Network connection
- Destination permissions
- Available disk space
- File permissions

---

### 6.4 Connection Lost After Reboot

This is expected because the Windows computer temporarily shuts down during the restart.

Wait until Windows finishes booting and then reconnect.

---

### 6.5 QuickSupport After Restart

QuickSupport is mainly intended for attended support.

After restarting the Windows PC, the remote user may need to open QuickSupport again before a new attended connection can be established.

For regular unattended access, an appropriate unattended-access configuration should be used.

---

## 7. Practical Conclusion

TeamViewer was successfully used to establish a remote connection between a Mac PC and a Windows PC.

The Mac was used as the controller, while the Windows PC was used as the remote computer.

The practical exercise covered:

- Installing TeamViewer
- Installing QuickSupport
- Obtaining the TeamViewer ID
- Connecting Mac to Windows
- Remote mouse and keyboard control
- Copy and paste
- File transfer
- Full-screen mode
- Annotation
- Ctrl + Alt + Delete
- Locking the remote computer
- Rebooting the remote computer
- Reconnecting after reboot
- TeamViewer accounts
- Easy Access
- Basic understanding of unattended access
- Basic understanding of personal passwords
- Security practices
- Basic troubleshooting

The practical demonstrated how TeamViewer can be used for remote technical support and remote computer administration while maintaining proper authorization and security.

--- 