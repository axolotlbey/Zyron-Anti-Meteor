# 🛡️ Zyron Anti Meteor

A highly advanced, lightweight, and automated security solution for **Paper/Spigot 1.21.11** servers. **Zyron Anti Meteor** is specifically engineered to detect, block, and instantly punish malicious incoming connections originating from the **Meteor Client** and similar Fabric-based cheat networks before they can compromise your server.

---

## ✨ Features

* **Instant Meteor Detection:** Hooks directly into incoming raw plugin channels (`meteor:caps`, `meteor:system`, etc.) and brand identifiers to catch hackers at the front gate.
* **Smart Duration Parser:** Supports flexible ban durations out-of-the-box (e.g., `7d` for days, `12h` for hours, `30m` for minutes).
* **Fully Configurable:** Every message, ban reason, alert broadcast, and punishment action can be completely customized inside `config.yml`.
* **Built-in Advanced Ban System:** Comes with standalone administrative commands (`/zyronban`, `/zyronunban`, `/zyroncheck`) that log configurations safely.
* **Optimized for Paper 1.21.11:** Developed on Java 21 with asynchronous handling where necessary to keep your server's Main Thread running smoothly with 20 TPS.

---

## 📂 Project Structure

```text
ZyronAntiMeteor/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── zyron/
│       │           └── antimeteor/
│       │               ├── ZyronAntiMeteor.java (Main Class)
│       │               ├── commands/
│       │               │   └── BanCommands.java (Administrative Actions)
│       │               └── listeners/
│       │                   └── MeteorDetector.java (Packet/Brand Filter)
│       └── resources/
│           ├── plugin.yml
│           └── config.yml
└── pom.xml

## 🛠️ Commands & Permissions

> ⚠️ **Important:** This plugin utilizes a strict permission structure. Being a Server Operator (OP) does **not** automatically grant access to these commands. You must explicitly assign these nodes using a permission manager like **LuckPerms**.

| Command | Description | Required Permission | Default Access |
| :--- | :--- | :--- | :--- |
| `/zyronban <player> <duration> <reason>` | Bans a player temporarily (e.g., `30d`, `2h`). | `zyron.ban` | `false` (Nobody) |
| `/zyronunban <player>` | Lifts an active ban from the player database. | `zyron.unban` | `false` (Nobody) |
| `/zyroncheck <player>` | Queries the database for active ban logs and reasons. | `zyron.check` | `false` (Nobody) |

* **Staff Notifications node:** Give `zyron.admin` to your moderators/admins so they can view real-time alert broadcasts in chat whenever a Meteor Client user is intercepted.

⚙️ Configuration Blueprint (config.yml)

YAML
settings:
  prefix: "&8[&bZyron&3AntiMeteor&8] "
  no-permission: "&cYou do not have permission to execute this command!"

meteor-detection:
  enabled: true
  ban-duration: "30d"
  ban-reason: "Malicious Client Exploitation (Meteor)"
  kick-message: "&c🛡️ Zyron Anti Meteor 🛡️\n\n&7Connections via &eMeteor Client &7are strictly prohibited!\n&7Ban Duration: &b%duration%\n&7Reason: &f%reason%"
  alert-message: "&b[ZYRON-ALERT] &e%player% &7attempted to join using Meteor Clien
