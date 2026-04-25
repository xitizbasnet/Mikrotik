# 📡 How to Configure DHCP Server on MikroTik Router (Step-by-Step)

## 📘 Overview
This guide provides a structured, step-by-step process to configure a **DHCP Server** on a MikroTik router using **Winbox**. It includes connection setup, IP configuration review, DHCP setup, and client-side verification.

---

## 🔐 Step 1: Access MikroTik via Winbox

1. Open **Winbox**.
2. Enter the following credentials:

```

Connect To: 192.168.1.100
Login: admin
Password: *************

```

3. Click **Connect**.

---

## 🌐 Step 2: Verify IP Address Configuration

1. Navigate to:

```

IP > Addresses

```

2. Review the existing address list:

### 📍 Address 1 (LAN Interface)
- **Address:** 192.168.1.100/24  
- **Network:** 192.168.1.0  
- **Interface:** LAN  

### 📍 Address 2 (WAN Interface)
- **Address:** 192.168.11.136/24  
- **Network:** 192.168.11.0  
- **Interface:** WAN  

---

## ⚙️ Step 3: Configure DHCP Server

1. Navigate to:

```

IP > DHCP Server

```

2. Click **DHCP Setup**.

---

## 🧭 Step 4: DHCP Setup Wizard Configuration

Follow the setup wizard steps carefully:

### 1️⃣ Select DHCP Interface
- **DHCP Server Interface:** LAN  
- Click **Next**

---

### 2️⃣ Define DHCP Address Space
- **DHCP Address Space:** 192.168.1.0/24  
- Click **Next**

---

### 3️⃣ Configure Gateway
- **Gateway for DHCP Network:** 192.168.1.100  
- Click **Next**

---

### 4️⃣ Define IP Address Pool

- **Addresses to Give Out:**
```

192.168.1.1 - 192.168.1.20
192.168.1.30 - 192.168.1.99

```

- **Excluded Range:**
```

192.168.1.21 - 192.168.1.29

```

- Click **Next**

---

### 5️⃣ Configure DNS Settings

- Enable DNS option (✔ Tick mark ON)

- **DNS Servers:**
```

192.168.11.2    (ADSL Router IP)
192.168.1.201   (Domain Controller IP)
8.8.4.4         (Google DNS)

```

- Click **Next**

---

### 6️⃣ Set Lease Time
- **Lease Time:** 00:30:00 (30 minutes)  
- Click **Next**

---

### ✅ DHCP Configuration Complete

At this stage, the DHCP Server has been successfully created and configured.

---

## 💻 Step 5: Verify Configuration on Client Computer

1. Go to the client computer.
2. Open **Ethernet Settings**.
3. Ensure IP configuration is set to:

```

Obtain an IP address automatically

```

---

### 📊 Example Client Configuration

After connecting via Ethernet, the client may receive:

```

IP Address:            192.168.1.99
IPv4 Default Gateway:  192.168.1.100
IPv4 DHCP Server:      192.168.1.100
IPv4 DNS Servers:      192.168.11.2
192.168.1.201
8.8.4.4

```

---

## 📝 Notes
- Ensure the **LAN interface** is correctly selected during DHCP setup.
- Confirm there are no IP conflicts within the defined DHCP pool.
- DNS servers should be reachable for proper name resolution.

---

## 🎯 Conclusion
You have successfully configured a DHCP Server on a MikroTik router. This allows automatic IP address assignment to client devices within the specified network range.

---


