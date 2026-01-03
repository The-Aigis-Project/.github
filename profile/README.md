<img src="https://files.catbox.moe/zsslg5.png" alt="THE AIGIS PROJECT LOGO" width="100%"/>

## Legal & Disclaimer

**This document is for educational purposes.**

The information contained herein is intended to help individuals protect themselves from surveillance, hacking, and privacy violations. It is not a guide for illegal activity. The author provides no warranties and assumes no liability for how this information is used.



## Intro

This document exists to bridge the knowledge gap of personal digital security for the average joe. It also exists to protect thousands of men and women from being tracked by corporations, governments or being exploited by cybercriminals.

The main ethos of The Aigis Project is 'You cannot hope to shield from that wich you do not understand'. In this document we will cover everything from basic core concepts to highly technical practices and as much material in between to strengthen understanding. Furthermore, we impose the idea that you take everything written here with a grain of salt; not everything is 100% accurate and there may be flaws in many things. In such cases, edits are suggested (see contact information at the bottom of this document)



## Core Concepts

### Threat Modeling


### Security Layers


### Common Terms Explained
- **Endpoint:** Your device (phone, computer)
- **Metadata:** Data about data (who you contacted, when, for how long)
- **E2EE:** End-to-End Encryption (only sender and receiver can read)
- **Zero Trust:** Assume all systems are compromised
- **Attack Surface:** The total ways someone can attack you

## Device Hardening

### Immediate Actions (30 minutes)
```yaml
Completed: [ ]
- Enable full-disk encryption (BitLocker/FileVault/LUKS)
- Install system updates
- Remove unused software
- Create separate user account for daily use
- Enable firewall
```

### Account Security
```
Priority Matrix:
┌─────────────┬──────────────────────────────┐
│ High Risk   │ Email, Password Manager      │
│ Medium Risk │ Banking, Social Media        │
│ Low Risk    │ Forums, Newsletter Subscriptions │
└─────────────┴──────────────────────────────┘
```

For each account:
1. Generate unique password (16+ characters)
2. Enable 2FA (prefer app over SMS)
3. Review connected apps/services
4. Check recovery options
5. Audit login history

### Browser Configuration
```
Firefox Recommended Settings:
about:config modifications:
- privacy.resistFingerprinting = true
- privacy.firstparty.isolate = true
- network.http.referer.trimmingPolicy = 2

Essential Extensions:
- uBlock Origin (filter lists: all)
- LocalCDN / Decentraleyes
- Cookie AutoDelete
- HTTPS Everywhere
```

## Operating Systems Compared

### Quick Reference Table
| System | Best For | Privacy | Difficulty | Maintenance |
|--------|----------|---------|------------|-------------|
| **Windows 10/11** | Gaming, Office work | Poor | Easy | High |
| **macOS** | Creative work, Development | Moderate | Easy | Medium |
| **Ubuntu** | General use, Servers | Good | Medium | Medium |
| **Fedora** | Development, Security | Very Good | Medium | Low |
| **Tails** | Maximum anonymity | Excellent | Hard | Per-session |
| **Qubes OS** | Compartmentalization | Excellent | Very Hard | High |

### Specialized Distributions

**Tails** (The Amnesic Incognito Live System)
```
Boot Method: USB drive (8GB minimum)
Memory: 4GB RAM required
Persistence: Optional encrypted volume
Network: Tor-only by design
Use Case: Sensitive research, whistleblowing
Warning: Not for daily driving or high-performance tasks
```

**Qubes OS** Architecture:
```
┌─────────────────────────────────────────┐
│   Admin Domain (dom0)                   │
│   ┌─────────┐ ┌─────────┐ ┌─────────┐  │
│   │ Work    │ │ Personal│ │ Banking │  │
│   │ VM      │ │ VM      │ │ VM      │  │
│   └─────────┘ └─────────┘ └─────────┘  │
│   ┌─────────────────────────────────┐  │
│   │ Networking VM (handles all net) │  │
│   └─────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

## 🧠 OPSEC: The Human Layer

### Common Mistakes Catalog
```
MISTAKE                         CONSEQUENCE
─────────────                   ─────────────────────────
Using same device for           Links anonymous activity
sensitive and normal work       to real identity

Discussing operations           Creates metadata patterns
on insecure channels            before/during activities

Regular schedules               Predictable behavior =
for sensitive acts              easier surveillance

Security through                Single point of failure
obscurity thinking
```

### Practical OPSEC Framework
1. **Information Classification**
   ```
   Public      → Social media posts
   Internal    → Friend group chats  
   Confidential→ Financial data
   Secret      → Activist planning
   ```

2. **Need-to-Know Basis**
   Share information only with those who require it to function. Document who knows what.

3. **Counter-Surveillance Habits**
   - Vary your routines
   - Watch for anomalies
   - Assume compromise after exposure
   - Have contingency plans

## 🌐 Network Tools Deep Dive

### TOR: Reality Check
```
What Tor Actually Does:
✓ Hides your IP from destination
✓ Encrypts traffic between relays
✓ Provides access to .onion sites

What Tor Doesn't Do:
✗ Encrypt traffic beyond exit node
✗ Protect against browser fingerprinting
✗ Hide Tor usage from your ISP
✗ Defend against compromised endpoints

Performance Expectations:
Web browsing: 1-3 MB/s
File downloads: 50-500 KB/s
Video streaming: Not practical
```

**Bridge Configuration Example:**
```
# torrc configuration for bridges
UseBridges 1
ClientTransportPlugin obfs4 exec /usr/bin/obfs4proxy
Bridge obfs4 1.2.3.4:1234 cert=abcdef... iat-mode=0
Bridge obfs4 5.6.7.8:5678 cert=ghijkl... iat-mode=0
```

### VPN Industry Analysis

**The Business Model Problem:**
```
Free VPNs → Sell your data
"Lifetime" VPNs → Oversubscribed servers
"Military-grade" VPNs → Marketing term for standard encryption
"No-logs" VPNs → Rarely proven in court
```

**Verified Providers (as of 2026):**
- **Mullvad** - Accepts cash, no email required
- **IVPN** - Independent audits, transparent leadership
- **ProtonVPN** - Swiss-based, connected to trusted email service

**When to Use a VPN:**
```
Appropriate:                      Inappropriate:
- Public WiFi                     - High-risk anonymity needs
- ISP tracking avoidance          - Journalist-source communication
- Geo-restriction bypass          - Activist organizing
```

## 🗣️ Communication Protocols

### IRC: Legacy Protocol, Modern Risks
```
Protocol Age: 1988
Default Encryption: None
IP Exposure: Usually visible
Logging: Universal by servers

If You Must Use It:
1. Connect over Tor
2. Use SASL authentication
3. Assume all messages archived
4. Consider OTR or PGP for sensitive DMs
```

### Modern Alternatives Comparison
```
Matrix/Element:
+ E2EE by default
+ Self-hosting possible
+ Rich features
- Complex for beginners
- Server metadata exposure

Signal:
+ Simple E2EE
+ Phone number required (problematic)
+ Wide adoption
- Centralized
- Metadata vulnerable to subpoena

Session:
+ No phone number
+ Onion routing built-in
+ Decentralized
- Smaller network
- Slower messages
```

## 🏗️ Infrastructure Security

### Virtual Machine Setups
```
Base Host: Clean, minimal OS
│
├── VM1: Daily browsing
│   ├── Regular updates
│   ├── VPN client
│   └── Standard precautions
│
├── VM2: Sensitive work
│   ├── Tails or Whonix
│   ├── No personal accounts
│   └── Encrypted volumes
│
└── VM3: Testing
    ├── Network isolated
    ├── Snapshots enabled
    └── Disposable
```

### Burner Device Protocol
```
Phase 1: Acquisition
- Pay with cash, no cameras
- Purchase far from home/work
- Buy from large retailer
- Use gloves if concerned

Phase 2: Configuration
- Never connect to personal WiFi
- Use public network for setup
- Install minimum apps
- Enable all encryption

Phase 3: Usage
- Single purpose only
- Regular disposal schedule
- No connection to real identity
- Assume 30-day lifespan
```

## 🕵️ Detection & Countermeasures

### Honeypot Identification
Common honeypot characteristics:
- Too-perfect target (wide-open server with valuable data)
- Software with known vulnerabilities still unpatched
- "Free" services requesting sensitive information
- Unexpected contact from "recruiters" or "sources"

**Red Flags in Communications:**
```
⚠️  Urgency without reason
⚠️  Requests for operational details
⚠️  Too much shared too quickly
⚠️  Avoidance of verifiable claims
⚠️  Pressure to use specific tools
```

### Digital Footprint Reduction Workflow
```
Phase 1: Discovery (Week 1-2)
├── Google yourself weekly
├── Check data brokers (Spokeo, Whitepages)
├── Audit social media visibility
└── List all online accounts

Phase 2: Removal (Month 1-3)
├── Close unused accounts
├── Submit removal requests
├── Delete old posts/comments
└── Update privacy settings

Phase 3: Maintenance (Ongoing)
├── Monthly self-search
├── Quarterly broker checks
├── Annual account audit
└── Mindful sharing habit
```

## 📈 Risk Assessment Matrix

Use this to prioritize your efforts:

```
               Impact if Compromised
               Low      Medium    High
           ┌─────────┬─────────┬─────────┐
           │         │         │         │
    Low    │   Ignore│  Plan   │  Act    │
           │         │         │         │
Likelihood ├─────────┼─────────┼─────────┤
           │         │         │         │
   Medium  │  Monitor│   Act   │  Act    │
           │         │         │         │
           ├─────────┼─────────┼─────────┤
           │         │         │         │
    High   │   Act   │  Act    │  Act    │
           │         │         │  Now    │
           └─────────┴─────────┴─────────┘
```

## 🎯 Implementation Roadmap

### Week 1: Foundation
- Enable disk encryption
- Install password manager
- Configure basic browser privacy
- Audit social media settings

### Month 1: Strengthening
- Implement 2FA everywhere
- Set up encrypted backups
- Learn basic OPSEC habits
- Reduce public footprint

### Month 3: Advanced
- Evaluate need for Tails/Qubes
- Test communication tools
- Practice secure workflows
- Establish maintenance routine

## 🔄 Maintenance Schedule

```
Daily:
├── Check for system updates
├── Review running processes
└── Monitor unusual activity

Weekly:
├── Update all software
├── Review firewall logs
├── Check account security
└── Backup important data

Monthly:
├── Test backup restoration
├── Audit installed software
├── Review privacy settings
└── Search for personal data leaks

Quarterly:
├── Password rotation
├── Security tool evaluation
├── Threat model review
└── Training/learning update
```

## ⚡ Quick Reference: Threat Response

**If you suspect compromise:**
1. Disconnect from network immediately
2. Document everything (screenshots, logs)
3. Preserve evidence on isolated media
4. Consult with trusted security expert
5. Plan remediation (wipe vs. forensic analysis)

**Essential Recovery Toolkit:**
- Offline bootable USB (Tails/Live Linux)
- Encrypted external storage
- Paper backups of critical credentials
- Pre-established secure communication channel

## 📖 Further Resources

### Books
- "Data and Goliath" by Bruce Schneier
- "The Art of Invisibility" by Kevin Mitnick
- "Permanent Record" by Edward Snowden

### Websites
- EFF.org (guides and tools)
- PrivacyGuides.org (current recommendations)
- CTemplar.com/blog (privacy news)

### Communities
- Privacy-focused subreddits (read, don't post)
- Local infosec meetups (verify legitimacy)
- University security clubs

## 🏁 Final Notes

Security is a journey of constant adjustment. What works today may be broken tomorrow. The most sophisticated tool is useless without disciplined habits.

Remember:
1. **Perfect security doesn't exist.** Aim for "good enough" given your threat model.
2. **Complexity is the enemy.** Each additional tool introduces new failure points.
3. **Trust is a vulnerability.** Verify claims, especially in the security industry.
4. **Silence is data.** Sometimes not communicating is the most secure option.

This document is a snapshot of current understanding. Technology changes. Laws change. Threats evolve. Stay informed, stay skeptical, and remember that the goal is protection—not paranoia.

---
*Document Version: Aigis v2.6 • 2026-01-04*
*"The strongest armor is knowing where you're vulnerable."*
