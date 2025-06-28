# android hacks

Some android dirty hacks I written.

## prop-trace (bionic)

- `bionic/0001-trace-property-reads.patch`

Tracing property reads.

## nobody ptraces (kernel)

- `./generic-kernel/0001-calm-down-nobody-is-ptracing-you.patch`

Force `TracerPid` to be zero, which could be used to ptrace an unwilling application (e.g. DroidGuard)

## fake nosuid and nodev mount options for /data (kernel)

- `./generic-kernel/fake-nosuid-and-nodev-for-data.patch`

DroidGuard reads `/proc/self/mount{s,info}`. So if you mount `/data` without nosuid and nodev,
SafetyNet and PlayIntegrity will show "No Integrity" to you.

This patch fakes the nosuid and nodev options for `/data` mountpoint.

## Make docker use overlayfs driver on devices that released after sdcardfs deprecation

- `./generic-kernel/overlayfs-dont-make-DCACHE-OP-HASH-or-COMPARE-weird.patch`

See the commit message and https://gist.github.com/FreddieOliveira/efe850df7ff3951cb62d74bd770dce27?permalink_comment_id=4842046#gistcomment-4842046
for more details.

## Delete directories with conflicting fscrypt policy to recover from bootloop

Sometimes you might find yourself messed up with fscrypt policy on some directories and stuck in an infinite bootloop.
The following patch could delete the offending directory and recover from the bootloop.

- `system/core/0001-Delete-directory-with-fscrypt-policy-conflict-that-c.patch`

