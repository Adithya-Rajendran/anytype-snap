# Anytype (Unofficial Snap)

This repository contains the source configuration for building the **unofficial** Snap package of [Anytype](https://anytype.io), the local-first, peer-to-peer knowledge OS.

This package bundles the official [Anytype TypeScript/Electron Client](https://github.com/anyproto/anytype-ts) and the [Anytype Heart](https://github.com/anyproto/anytype-heart) (Go middleware) into a strictly confined Snap container.

## 📦 Installation

You can install this package directly from the Snap Store:

```bash
sudo snap install adithya-anytype
```

(Note: If you need access to removable media, you may need to connect the `removable-media` plug manually, though this build focuses on strict confinement defaults.)

## ⚠️ Disclaimer

This is an unofficial community build.

- **Do not report installation or packaging issues to the official Anytype team**. Please open an issue in this repository instead.
- This package is built from the official source code provided by Anytype but is packaged and maintained independently.

## 🛠 Building from Source

To build this snap locally, you need snapcraft and a build provider (LXD is recommended for Linux).

Prerequisites

- Snapcraft: `sudo snap install snapcraft --classic`
- LXD: `sudo snap install lxd --channel=6/stable` (Ensure your user is in the `lxd` group)

Build Instructions
1. Clone the repository:
2. Start the build:
3. How the build works: This process utilizes a core22 base. It performs a multi-stage build:
    1. Heart: Pulls anyproto/anytype-heart (Go), builds the middleware, and prepares the libraries.
    2. Client: Pulls anyproto/anytype-ts (Electron), installs Node.js dependencies, links the compiled Heart middleware, and generates the final Linux distributable.
4. Install your local build:

## 🐛 Troubleshooting

If the application fails to launch, you can check the logs:

```bash
snap logs adithya-anytype
```

Common Issues:

- Fonts/Icons missing: The snap uses the GNOME extension to bridge desktop themes. Ensure you are running a compatible desktop environment.
- Permissions: If the app cannot access a specific file in your home directory, ensure it is within the standard $HOME paths allowed by the home interface.

## 🔗 Upstream Resources

- Official Website: [anytype.io](https://anytype.io/)
- Source Code (Client): [anyproto/anytype-ts](https://github.com/anyproto/anytype-ts)
- Source Code (Middleware): [anyproto/anytype-heart](https://github.com/anyproto/anytype-heart)

## 📄 License

The packaging code in this repository is open source. The Anytype application itself is licensed under the Any Source Available License 1.0.
