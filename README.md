# GoVC Docker

## Environment Variables

* `GOVC_URL`: URL of ESXi or vCenter instance to connect to.

    The URL scheme defaults to `https` and the URL path defaults to `/sdk`.
    This means that specifying `user:pass@host` is equivalent to
    `https://user:pass@host/sdk`.

    If password include special characters like `#` or `:` you can use
    `GOVC_USERNAME` and `GOVC_PASSWORD` to have a simple `GOVC_URL`

    When using govc against VMware Workstation, GOVC_URL can be set to "localhost"
    without a user or pass, in which case local ticket based authentication is used.

* `GOVC_USERNAME`: USERNAME to use if not specified in GOVC_URL.

* `GOVC_PASSWORD`: PASSWORD to use if not specified in GOVC_URL.

* `GOVC_TLS_CA_CERTS`: Override system root certificate authorities.

    ``` console
    $ export GOVC_TLS_CA_CERTS=~/.govc_ca.crt
    # Use path separator to specify multiple files:
    $ export GOVC_TLS_CA_CERTS=~/ca-certificates/bar.crt:~/ca-certificates/foo.crt
    ```

* `GOVC_TLS_KNOWN_HOSTS`: File(s) for thumbprint based certificate verification.

    ``` console
    # Thumbprint based verification can be used in addition to or as an alternative to
    $ GOVC_TLS_CA_CERTS for self-signed certificates.  Example:
    $ export GOVC_TLS_KNOWN_HOSTS=~/.govc_known_hosts
    $ govc about.cert -u host -k -thumbprint | tee -a $GOVC_TLS_KNOWN_HOSTS
    $ govc about -u user:pass@host
    ```

* `GOVC_TLS_HANDSHAKE_TIMEOUT`: Limits the time spent performing the TLS handshake.

* `GOVC_INSECURE`: Disable certificate verification.

    This option sets Go's `tls.Config.InsecureSkipVerify` flag and is false by default.
    Quoting https://golang.org/pkg/crypto/tls/#Config:
    > `InsecureSkipVerify` controls whether a client verifies the
    > server's certificate chain and host name.
    >
    > If `InsecureSkipVerify` is true, TLS accepts any certificate
    > presented by the server and any host name in that certificate.
    >
    > In this mode, TLS is susceptible to man-in-the-middle attacks.
    > This should be used only for testing.

* `GOVC_DATACENTER`

* `GOVC_DATASTORE`

* `GOVC_NETWORK`

* `GOVC_RESOURCE_POOL`

* `GOVC_HOST`

* `GOVC_GUEST_LOGIN`: Guest credentials for guest operations

* `GOVC_VIM_NAMESPACE`: Vim namespace defaults to `urn:vim25`

* `GOVC_VIM_VERSION`: Vim version defaults to `6.0`
