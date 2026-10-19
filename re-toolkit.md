# RE Toolkit and Lab Rules

Run once in the lab VM. Never install these on a device holding real accounts.

## Install (Ubuntu)

```
sudo apt update
sudo apt install -y default-jre apktool
```

For jadx, download the latest release zip from the skylot/jadx GitHub releases page, unzip it, and add its `bin` folder to PATH.

Verify with: `java -version`, `apktool -version`, `jadx -version`.

## Lab rules

- Keep all samples under `~/workspace/re-lab/` and never outside it.
- Name every sample by its SHA256 hash, not by what you think it is.
- No real logins, no real phone numbers and no personal files inside the lab.
- Snapshot or copy the lab folder before detonating anything suspicious.
- Confirm the toolkit install by decompiling a harmless open source APK before touching any unknown sample.

## First session checklist

- [ ] Toolkit installed and versions confirmed
- [ ] Lab directory created and isolated
- [ ] Target ownership confirmed (own app, open source, training or CTF binary)
- [ ] Goal written down in one sentence, defensive framing only
