# sing-box rule bundle

This repository publishes validated, versioned sing-box rule-set bundles.

The bundle contains public rule data only. It must never contain server
addresses, credentials, UUIDs, private keys, or sing-box configuration files.

Consumers download `current.json` and `current.sig`, verify the signature with
`public-key.pem`, then download only the immutable files named by the signed
manifest. A consumer stages and validates a complete bundle before replacing
its local rule files. A failed update leaves the previous bundle untouched.

The publisher resolves the upstream `MetaCubeX/meta-rules-dat` `sing` branch
to one commit and downloads every file by that commit SHA. This prevents a
single update from mixing files generated at different upstream revisions.

Runtime services use local rule files. Network access is required only by the
update process, not by sing-box startup.
