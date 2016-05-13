# ssh-show-digests

## visual aid for `authorized_keys` and `known_hosts` files

## Description

Show `authorized_keys` or `known_hosts` in an easy to read format.

`ssh-show-digests` shows { user@host, algorithm, key-digest }
in a format that is easier to read.

#### The Problem

Sometimes `authorized_keys` or `known_hosts` files
get cluttered with duplicates, dead keys,
things copied in from other systems, and so on.
It can be difficult to just look at a raw file
with long public keys and tell where the problems are.

`ssh-show-digest` provides some visual aids.
  1. It formats the data.
  2. It shows a digest of the public key instead of the key itself.
  3. It show a small digest-id, which is even smaller than a digest.
  4. It prints a report of duplicates, at the end.

This sort of visual aid is likely to be even more helpful
as minimum requirements for public keys evolve.  It is likely that
the key generation algorithms in common use will get better.
But, better algorithms or no, the generated keys will likely get longer.

In the case of `known_hosts`, 
`ssh-show-digest` shows { hostname, algorithm, public-key-digest }.

In the case of `authorized_keys`,
`ssh-show-digest` shows { user@host, algorithm, public-key-digest }.

You can specify one of `--keys` or `--hosts` options.
If neither option is given, then `ssh-show-digest`
will attempt to auto-detect the file type.

#### Small digest IDs

The small digest IDs are ephemeral.
They are not related to the digests in any meaningful way
outside of the current report.  Another run of the same
program might assign a different digest-id any given
digest.  They are just number stamps, in order of arrival
for each new digest.  But for a single report, all occurrences
of a digest get the same digest-id.

####

-- Guy Shaw

   gshaw@acm.org

