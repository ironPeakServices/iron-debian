# ironpeakservices/iron-debian
Hardened debian linux baseimage for Docker.

Note: If you use Golang/Rust/..., build statically and use [iron-scratch](https://github.com/ironpeakservices/iron-scratch).
If you are using Java/Python/NodeJS/dotnet, use a [distroless image](https://github.com/GoogleContainerTools/distroless) instead.

`docker pull ghcr.io/ironpeakservices/iron-debian:1.0.0`

## How is this different?
- ca-certificates included
- /app for everything app-related; /app/conf, /app/tmp, /app/data
- no interactive shells for users
- removed unneccessary accounts, only 'app' and 'root' users
- removed crontabs
- removed dangerous commands and utilities
- strictened permissions on system files and directories
- removed temporary shadow/passwd/group
- removed suid/guid files
- removed init scripts
- removed kernel tunables
- removed /root/
- removed fstab
- post-install.sh:
	- removes apk manager after installation
	- sets permissions on /app after installation

## Example
`docker pull ghcr.io/ironpeakservices/iron-debian:1.0.0`

See [the nginx example](example/).

## Update policy
Updates to the official debian docker image are automatically created as a pull request and trigger linting & a docker build. When those checks complete without errors, a merge into master will trigger a deploy with the same version to packages.

## Additional
If you want, you can also enable vulnerability scanning during your build (for free).
Take a look at https://github.com/aquasecurity/microscanner
