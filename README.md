  <h1>🚀 Small Office Network Design – Cisco Packet Tracer Project</h1>

  <p>This project demonstrates the design and implementation of a small branch office network for a fast-growing food trading company using <strong>Cisco Packet Tracer</strong>. The network is scalable, secure, and fully functional, designed to support Admin, Finance, and Customer departments with wired and wireless access.</p>

  <h2>🧱 Network Design Overview</h2>
  <ul>
    <li>1 Cisco Router</li>
    <li>1 Cisco Switch</li>
    <li>3 VLANs (Admin, Finance, Customer)</li>
    <li>Wireless Access Points (1 per department)</li>
    <li>DHCP configuration for automatic IP assignment</li>
    <li>Subnetting with a base network of <code>192.168.54.0/24</code></li>
    <li>Router-on-a-Stick for Inter-VLAN communication</li>
  </ul>

  <h2>🛠️ Technologies Used</h2>
  <ul>
    <li>VLANs (10, 20, 30)</li>
    <li>IPv4 Subnetting</li>
    <li>Inter-VLAN Routing (Router-on-a-Stick)</li>
    <li>DHCP Service</li>
    <li>Cisco CLI Configuration</li>
    <li>Wireless AP Integration</li>
    <li>Cisco Packet Tracer</li>
  </ul>

  <h2>🧠 IP Address Plan</h2>
  <table border="1" cellpadding="8" cellspacing="0">
    <thead>
      <tr>
        <th>Department</th>
        <th>VLAN ID</th>
        <th>Subnet</th>
        <th>Gateway IP</th>
        <th>DHCP IP Range</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Admin</td>
        <td>10</td>
        <td>192.168.54.0/26</td>
        <td>192.168.54.1</td>
        <td>192.168.54.2 - 62</td>
      </tr>
      <tr>
        <td>Finance</td>
        <td>20</td>
        <td>192.168.54.64/26</td>
        <td>192.168.54.65</td>
        <td>192.168.54.66 - 126</td>
      </tr>
      <tr>
        <td>Customer</td>
        <td>30</td>
        <td>192.168.54.128/26</td>
        <td>192.168.54.129</td>
        <td>192.168.54.130 - 190</td>
      </tr>
    </tbody>
  </table>

  <h2>🔧 Configuration Steps (Cisco Packet Tracer)</h2>

  <h3>🔹 Switch Configuration</h3>
  <pre><code>enable
configure terminal

vlan 10
name Admin
vlan 20
name Finance
vlan 30
name Customer

interface range fa0/1-8
switchport mode access
switchport access vlan 10
exit

interface range fa0/9-16
switchport mode access
switchport access vlan 20
exit

interface range fa0/17-24
switchport mode access
switchport access vlan 30
exit

interface gig0/1
switchport mode trunk
exit

do write</code></pre>

  <h3>🔹 Router Configuration</h3>
  <pre><code>enable
configure terminal
interface gig0/0
no shutdown

interface gig0/0.10
encapsulation dot1Q 10
ip address 192.168.54.1 255.255.255.192
exit

interface gig0/0.20
encapsulation dot1Q 20
ip address 192.168.54.65 255.255.255.192
exit

interface gig0/0.30
encapsulation dot1Q 30
ip address 192.168.54.129 255.255.255.192
exit

service dhcp

ip dhcp pool Admin-Pool
network 192.168.54.0 255.255.255.192
default-router 192.168.54.1
domain-name Admin.com
exit

ip dhcp pool Finance-Pool
network 192.168.54.64 255.255.255.192
default-router 192.168.54.65
domain-name Finance.com
exit

ip dhcp pool Customer-Pool
network 192.168.54.128 255.255.255.192
default-router 192.168.54.129
domain-name Customer.com
exit

do write</code></pre>

  <h2>📶 Wireless Access Points & Wireless Devices</h2>
  <ul>
    <li><strong>Access Points:</strong> Add 3 Wireless Access Points (APs), one per department (Admin, Finance, Customer)</li>
    <li><strong>VLAN Assignment:</strong> Connect each AP to the appropriate switch port configured for the corresponding VLAN</li>
    <li><strong>SSID Configuration:</strong> 
      <ul>
        <li><code>Admin-WiFi</code> → Assigned to VLAN 10</li>
        <li><code>Finance-WiFi</code> → Assigned to VLAN 20</li>
        <li><code>Customer-WiFi</code> → Assigned to VLAN 30</li>
      </ul>
    </li>
    <li><strong>DHCP:</strong> Ensure APs and wireless clients (like phones/laptops) get IPs dynamically from their respective VLAN DHCP pools</li>
  </ul>

  <h3>📱 Mobile / Wireless Device Configuration</h3>
  <ul>
    <li>Add <strong>wireless end devices</strong> (e.g., smartphones or laptops) from the Packet Tracer device list</li>
    <li>Open each device's GUI > Connect to the correct SSID (e.g., Admin-WiFi)</li>
    <li>Ensure the device receives an IP address via DHCP</li>
    <li>Test connectivity (e.g., use the ping command or web browser in the simulation)</li>
  </ul>

  <h3>🌐 Sample Wireless Configuration on Access Point</h3>
  <pre><code>// On Access Point GUI
SSID: Admin-WiFi
VLAN: 10
DHCP: Enabled
Security: WPA2-PSK (Optional for simulation)
</code></pre>

  <h2>✅ Final Output</h2>
  <ul>
    <li>All devices receive IP addresses via DHCP</li>
    <li>Inter-VLAN routing allows communication across departments</li>
    <li>Network is secure, scalable, and functional</li>
  </ul>


  <h2>📸 Screenshots</h2>
<img src="![Screenshot 2025-06-18 083854](https://github.com/user-attachments/assets/95713058-86ee-4cb3-bbf4-cb7fe49502af)
" alt="Screenshot - CMD Open in Folder" width="600" />
  

  <h2>🙌 Author</h2>
  <p><strong>Thamindu Kalhara</strong><br>
    IT Undergraduate | Network & Security Enthusiast<br>
    <a href="https://www.linkedin.com/in/ktdt-kalhara/">LinkedIn Profile</a>
  </p>
