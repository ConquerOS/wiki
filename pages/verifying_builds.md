---
sidebar: home_sidebar
title: Verifying Build Authenticity
folder: meta
permalink: verifying-builds.html
toc: false
---

All official builds from ConquerOS are signed with our private keys. You can verify whether a build has been signed with our keys by following these steps:

{% include alerts/note.html content="To go ahead with the verification, `git`, `pip`, and `python` are required." %}

Download the verifier and install its dependencies:

```
git clone https://github.com/ConquerOS/update_verifier
cd update_verifier
pip install -r requirements.txt
```

Check the signature of the downloaded ZIP file:

```
python update_verifier.py conquer_pubkey /path/to/zip
```

If the script reports `verified successfully`, the ZIP file signature is valid.

For the paranoid, the contents of this page are stored on [our GitHub](https://github.com/conquer/wiki/blob/master/pages/verifying_builds.md).
