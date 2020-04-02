## <a name="cipher_aes128cbc"/>wxSQLite3: AES 128 Bit CBC - No HMAC

This cipher was added to [wxSQLite3](https://github.com/utelle/wxsqlite3) in 2007 as the first supported encryption scheme. It is a 128 bit AES encryption in CBC mode.

The encryption key is derived from the passphrase according to the algorithm described in the PDF specification (using the MD5 hash function and the RC4 algorithm).

The initial vector for the encryption of each database page is derived from the page number.

The cipher does not use a _Hash Message Authentication Code_ (HMAC), and requires therefore no reserved bytes per database page.

The following table lists all parameters related to this cipher that can be set before activating database encryption.

| Parameter | Default | Min | Max | Description |
| :--- | :---: | :---: | :---: | :--- |
| `legacy` | 0 | 0 | 1 | Boolean flag whether the legacy mode should be used |
| `legacy_page_size` | 0 | 0 | 65536 | Page size to use in legacy mode, 0 = default SQLite page size |

**Note**: It is not recommended to use [_legacy_ mode](/cipher_legacy/) for encrypting new databases. It is supported for compatibility reasons only, so that databases that were encrypted in _legacy_ mode can be accessed.