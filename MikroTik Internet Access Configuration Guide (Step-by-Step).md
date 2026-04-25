# 🌐 MikroTik Internet Access Configuration Guide (Step-by-Step)

This document provides a structured guide to configure internet access on a MikroTik router for all clients. Follow each step carefully to ensure proper setup and connectivity.

---

## 🔐 Step 1: Connect to MikroTik via WinBox

1. Open **WinBox**
2. Connect using the following details:
   - **IP Address:** `192.168.1.100`
   - **Login:** `admin`
   - **Password:** `******`
3. Click **Connect**

---

## ⚙️ Step 2: Configure Interfaces

Navigate to the **Interfaces** section from the dashboard.

### 🔄 Rename Ethernet Interfaces

#### 🖧 Ethernet 1 → LAN
- **Rename:** Ethernet 1 as LAN  
- **Enabled:** ✔ (Tick mark on)  
- **Comment:** LAN  
- **Name:** LAN  
- **Default Name:** ethr1  
- **Type:** Ethernet  
- **MTU:** 1500  
- **Actual MTU:** 1500  
- **L2MTU:** 0  
- **VRF:** main  
- **MAC Address:** *******  
- **ARP:** enabled  

---

#### 🌍 Ethernet 2 → WAN
- **Rename:** Ethernet 2 as WAN  
- **Enabled:** ✔ (Tick mark on)  
- **Comment:** WAN  
- **Name:** WAN  
- **Default Name:** ethr2  
- **Type:** Ethernet  
- **MTU:** 1500  
- **Actual MTU:** 1500  
- **L2MTU:** 0  
- **VRF:** main  
- **MAC Address:** *******  
- **ARP:** enabled  

---

## 🌐 Step 3: Configure Internet Access (DHCP Client)

Navigate to: **IP → DHCP Client**

### 📋 Existing Configuration
Only the **LAN Interface** is available initially:

- **Interface:** LAN  
- **Use Peer DNS:** yes  
- **Use Peer NTP:** yes  
- **IP Address:** empty  
- **Expires After:** empty  
- **Status:** Searching  

---

### ➕ Add WAN Interface

1. Click **New**
2. Enter the following details:

- **Enabled:** ✔  
- **Comment:** WAN  
- **Interface:** WAN  
- **Use Peer DNS:** yes  
- **Use Peer NTP:** yes  
- **Add Default Route:** yes  
- **Status:** stopped  

3. Click **Apply**

> 📌 **Note:** After clicking *Apply*, the status will change to **Searching**, meaning the WAN interface is attempting to obtain an IP address from the ADSL router.

---

### ✅ Successful DHCP Assignment

Once successful, the status will change to **Bound**:

- **Status:** Bound  
- Click **OK**

---

### 📊 WAN Interface Details

- **Interface:** WAN  
- **Use Peer DNS:** yes  
- **Use Peer NTP:** yes  
- **IP Address:** `192.168.11.136/24`  
- **Expires After:** `00:29:56`  
- **Status:** Bound  

---

## 🧪 Step 4: Test Internet from MikroTik

1. Go to **New Terminal** from the dashboard  
2. Run the following command:

```bash
ping 8.8.8.8
````

* ✅ If replies are received, MikroTik has internet access.

---

## 💻 Step 5: Test Client Internet Access

1. Open **Microsoft Edge**
2. Search for: `google.com`

### ❌ Result:

* Error message displayed:

  ```
  "Hmm....can't reach this page"
  ```

---

## 🧭 Step 6: Configure DNS

Navigate to: **IP → DNS**

### ⚙️ DNS Settings

* **Server:** `8.8.8.8`
* **Server:** `8.8.4.4`
* **Dynamic Server:** `192.18.11.2`
* **Allow Remote Requests:** empty
* **VRF:** main
* **Max UDP Packet Size:** 4096
* **Query Server Timeout:** 2.000
* **Query Total Timeout:** 10.000
* **Max Concurrent Queries:** 100
* **Max Concurrent TCP Sessions:** 20

#### 🧠 Cache Settings

* **Cache Size:** 2048
* **Cache Max TTL:** 7d 00:00:00
* **Cache Used:** 42 KiB

➡️ Click **Apply → OK**

---

## 🔥 Step 7: Configure NAT (Masquerade)

Navigate to: **IP → Firewall → NAT**

1. Click **New**
2. Configure the NAT rule:

* **Action:** masquerade
* **Log:** ❌ (No tick mark)

3. Click **Apply → OK**

---

## 🔁 Step 8: Re-Test Client Internet Access

1. Open **Microsoft Edge**
2. Search for: `google.com`

### ✅ Result:

* Google search page loads successfully

---

## 🎉 Conclusion

Your MikroTik router is now successfully configured to provide internet access to all connected clients.

---

## 🙏 Thank You
