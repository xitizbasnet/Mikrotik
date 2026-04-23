# 🕒 How to Sync Time Using NTP Server on MikroTik Router (Step-by-Step)

## 📌 Overview
This guide explains how to synchronize system time on a MikroTik router using an NTP (Network Time Protocol) server. Accurate time synchronization is essential for logging, monitoring, and network operations.

---

## 🔐 Step 1: Access MikroTik Router

- Open MikroTik using your login credentials.

---

## ⚙️ Step 2: Enable NTP Server

1. Navigate to:
```

System > NTP Server

```
2. Configure the following:
- ✅ Tick mark on **Enabled**
- ✅ Tick mark on **Broadcast**
3. Click:
- **Apply**
- **OK**

---

## 🖥️ Step 3: Enable NTP Client

1. Go to:
```

System > NTP Client

```
2. Configure:
- ✅ Tick mark on **Enabled**

> **Note:** Currently, the status will be shown as **Stopped**.

3. Click:
- **Apply**

> **Note:** Now the status will change from **Stopped** to **Waiting**.

---

## 🌐 Step 4: Find NTP Servers (NTP Pool)

To synchronize time, you need valid NTP servers.

1. Open a web browser (e.g., Google Chrome).
2. Search for **NTP Pool** or visit:
```

https://www.ntppool.org/en/

```
3. Search for your country name:
- Example: **Nepal**
```

https://www.ntppool.org/zone/np

```

4. You will find multiple server pool names such as:
```

server 0.asia.pool.ntp.org
server 1.asia.pool.ntp.org
server 2.asia.pool.ntp.org
server 3.asia.pool.ntp.org

```

---

## 🔄 Step 5: Configure NTP Server in MikroTik

1. Go back to MikroTik.
2. Navigate to NTP Client settings.
3. Enter the NTP Server:
```

0.asia.pool.ntp.org

```
4. Click:
- **Apply**

> **Note:** Now the status will change from **Waiting** to **Synchronized**.  
> **Synced Server:** `0.asia.pool.ntp.org`

---

## ➕ Step 6: Add Additional NTP Servers

1. On the right-side corner, locate the options:
```

OK | Cancel | Apply | Reset Drift | Servers | Peers

```
2. Click on:
- **Servers**

3. A popup window will appear showing the synchronized server:
```

0.asia.pool.ntp.org

````

4. To add another server:
- Click on the **➕ Plus Icon** at the top
- Enter:
  ```
  Address: 1.asia.pool.ntp.org
  ```
- Click:
  - **Apply**
  - **OK**

5. Now you will see two server addresses:
```
0.asia.pool.ntp.org
1.asia.pool.ntp.org
```


6. Click:
- **Apply**
- **OK**

---

## ✅ Final Status

- NTP Client Status: **Synchronized**
- Active Servers:
- `0.asia.pool.ntp.org`
- `1.asia.pool.ntp.org`

---

## 📎 Notes

- Ensure internet connectivity is active for NTP synchronization.
- Adding multiple NTP servers increases reliability.
- Time synchronization may take a few moments after configuration.

---

## 🙏 Thank You

