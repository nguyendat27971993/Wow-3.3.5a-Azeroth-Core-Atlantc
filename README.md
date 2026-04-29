# Wow-3.3.5a-Azeroth-Core-Atlantc

**Atlantc** is a World of Warcraft 3.3.5a private server built on top of [AzerothCore](https://github.com/azerothcore/azerothcore-wotlk), an open-source, community-driven C++ game server framework.

---

## About

This project hosts and extends the AzerothCore engine to power the Atlantc WoW 3.3.5a experience. AzerothCore provides a stable, blizzlike foundation originally derived from MaNGOS, TrinityCore, and SunwellCore.

- **Game version:** World of Warcraft 3.3.5a (Wrath of the Lich King)
- **Upstream engine:** [AzerothCore](https://github.com/azerothcore/azerothcore-wotlk)
- **License:** [GNU GPL v2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)

---

## Requirements

Before setting up the server, make sure you have:

- A Linux, macOS, or Windows system
- Git
- CMake 3.16+
- A C++17-capable compiler (GCC 8+, Clang 7+, or MSVC 2019+)
- MySQL 5.7 / MariaDB 10.3 (or newer)
- Boost 1.74+
- OpenSSL 1.0.x or 1.1.x
- Original WoW 3.3.5a client data files

---

## Installation

Full installation instructions are provided by the upstream AzerothCore wiki:

- **[AzerothCore Installation Guide](https://www.azerothcore.org/wiki/installation)**

### Quick Start (Linux)

```bash
# 1. Clone this repository
git clone https://github.com/nguyendat27971993/Wow-3.3.5a-Azeroth-Core-Atlantc.git
cd Wow-3.3.5a-Azeroth-Core-Atlantc

# 2. Add the upstream AzerothCore source
git remote add upstream https://github.com/azerothcore/azerothcore-wotlk.git
git fetch upstream
git merge upstream/master

# 3. Build the server
mkdir build && cd build
cmake .. -DCMAKE_INSTALL_PREFIX=/opt/atlantc -DTOOLS=1
make -j$(nproc)
make install

# 4. Extract client data (point DATA_DIR to your WoW 3.3.5a client)
# See: https://www.azerothcore.org/wiki/client-setup

# 5. Import the database
# See: https://www.azerothcore.org/wiki/database-installation

# 6. Start the server
/opt/atlantc/bin/authserver &
/opt/atlantc/bin/worldserver
```

---

## Configuration

After building, copy the example configuration files and edit them:

```bash
cp /opt/atlantc/etc/authserver.conf.dist /opt/atlantc/etc/authserver.conf
cp /opt/atlantc/etc/worldserver.conf.dist /opt/atlantc/etc/worldserver.conf
```

Key settings in `worldserver.conf`:

| Setting | Description |
|---|---|
| `DataDir` | Path to extracted client data |
| `LoginDatabaseInfo` | MySQL connection string for auth DB |
| `WorldDatabaseInfo` | MySQL connection string for world DB |
| `CharacterDatabaseInfo` | MySQL connection string for characters DB |

---

## Modules & Customization

AzerothCore supports a modular extension system. Community modules can be found in the [AzerothCore Module Catalogue](https://www.azerothcore.org/catalogue.html#/). To add a module, clone it into the `modules/` directory before building.

---

## Contributing

Contributions to Atlantc-specific features and fixes are welcome. For upstream engine improvements, please contribute directly to [AzerothCore](https://github.com/azerothcore/azerothcore-wotlk).

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes
4. Open a Pull Request

---

## Upstream Resources

- [AzerothCore GitHub](https://github.com/azerothcore/azerothcore-wotlk)
- [AzerothCore Wiki](https://www.azerothcore.org/wiki)
- [AzerothCore Discord](https://discord.gg/gkt4y2x)
- [AzerothCore Module Catalogue](https://www.azerothcore.org/catalogue.html#/)

---

## Disclaimer

This project is not affiliated with or endorsed by Blizzard Entertainment. It is intended for educational and testing purposes only. Running a public server may violate Blizzard's Terms of Service.
