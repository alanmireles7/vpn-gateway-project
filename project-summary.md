# VPN Gateway Project Summary

## 🔍 Explanation of the Project

This project involved setting up a secure VPN (Virtual Private Network) Gateway using OpenVPN on an Ubuntu server hosted on Microsoft Azure. The primary aim was to replicate a real-world scenario where secure remote access to internal network resources is required. By creating an encrypted communication tunnel between a remote client and a private network, we demonstrated a practical use case of VPNs for enhancing data privacy, preventing eavesdropping, and ensuring secure communication over untrusted networks.

VPN technology is widely utilized in both personal and corporate settings to provide a safe remote work environment, protect against data interception, and allow secure access to internal services. Through this project, we gained hands-on experience configuring VPN servers and clients, managing cryptographic keys, and implementing secure communication protocols.

## 🛠️ Breakdown of the Implementation

### Network Topology
- **Server**: Azure-hosted Ubuntu 20.04 LTS VM configured as the OpenVPN Gateway.
- **Client**: Local macOS system using Tunnelblick to initiate a VPN connection.
- **Network**: VPN tunnel routed traffic to the internal subnet `10.8.0.0/24`, simulating access to protected internal resources.

### Configuration Details
- **Server Setup**:
  - Installed OpenVPN and Easy-RSA.
  - Generated necessary certificates: CA, server, client, `ta.key`, and DH params.
  - Enabled IP forwarding, adjusted UFW rules, and configured `iptables` for NAT.
  - Configured `/etc/openvpn/server/server.conf` with parameters for encryption and TLS-auth.
- **Client Setup**:
  - Created `.ovpn` config file containing CA, cert, key, and TLS-auth directives.
  - Imported into Tunnelblick for connection on macOS.

### Communication Flow
1. Client uses `.ovpn` configuration to start a secure handshake.
2. OpenVPN server verifies client credentials and shared keys.
3. Once authenticated, a tunnel is created.
4. Client receives internal IP (10.8.x.x) and routes its traffic securely via the server.

## 🧰 Tools and Technologies
- **Microsoft Azure** (cloud platform hosting the Ubuntu VM)
- **OpenVPN** (VPN protocol and server framework)
- **Easy-RSA** (key and certificate management)
- **Tunnelblick** (macOS VPN client)
- **GitHub** (version control and project documentation)

## 📸 Demonstration and Screenshots

All screenshots were added to the `/screenshots/` folder in this repository:

1. ✅ `tunnelblick-connected.png` – Tunnelblick connection established
2. ✅ `server-status.png` – `systemctl status` showing OpenVPN server active
3. ✅ `client-config.png` – Contents of the `.ovpn` client configuration
4. ✅ `ping-test.png` – Terminal ping to verify tunnel connectivity (10.8.0.1)
5. ✅ `server-config.png` – `server.conf` OpenVPN configuration file content
6. ✅ `git-setup.png` – Terminal showing successful GitHub commit and push