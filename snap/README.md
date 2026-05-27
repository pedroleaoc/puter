# Puter Snap Package

Build and run [Puter](https://puter.com) as a snap on Ubuntu (and other
snap-enabled distros) — no `curl | sh` required.

## Status

This snap uses **`grade: devel`**, which means it can only be published to
the **edge** and **beta** channels in the Snap Store. This is intentional:
the packaging is experimental and should be treated as a toy/preview until
it graduates to `grade: stable`.

## Building locally

```bash
# Install snapcraft if you haven't already
sudo snap install snapcraft --classic

# Build the snap (from the repo root)
snapcraft

# Install the locally-built snap
sudo snap install puter_*.snap --dangerous --devmode
```

## Installing from the Snap Store

Once published:

```bash
# Install from the edge channel (experimental)
sudo snap install puter --edge

# Or from beta once promoted
sudo snap install puter --beta
```

## Usage

After installation Puter runs as a system daemon:

```bash
# Check the service status
sudo snap services puter

# View logs
sudo snap logs puter

# Open in browser
xdg-open http://puter.localhost:4100
```

## Configuration

```bash
# Change the HTTP port
sudo snap set puter port=8080

# Restart to pick up changes
sudo snap restart puter
```

Configuration is stored in `$SNAP_COMMON/config.json`
(typically `/var/snap/puter/common/config.json`).

## Channel strategy

| Channel | Purpose                              |
|---------|--------------------------------------|
| edge    | Every green build from `main`        |
| beta    | Manual promotion after basic testing |
| stable  | Not used yet (`grade: devel` blocks) |

When the snap matures, change `grade` to `stable` in `snap/snapcraft.yaml`
to unlock the candidate and stable channels.
