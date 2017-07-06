What's New in 0.14.3
====================

Release 0.14.3 brings many incremental improvements over 0.14.2.  It does not
break consensus; 0.14, 0.14.1, and 0.14.2 nodes are compatible with 0.14.3 nodes.

This marks the beginning of a per-sprint release cycle.  Release notes will be
shorter between releases, since new releases will be scheduled every two to
three weeks.

Release Highlights (Anticipated)
--------------------------------

* **Multi-player Storage**.  This release includes an improved release of Gaia,
which now allows multi-user applications to share state.  Gaia was limited to
single-user applications in the previous release.  With Gaia, one user can store
data to their storage providers, and other users can read it.  This further
removes the need for developer-hosted data, and opens Blockstack up to a lot
more conventional types of applications.

* **Gaia Performance Improvements.**  The read and write paths of Gaia have been
refactored to run many I/O operations in parallel.  This leads to faster data
interaction times, even for indexed storage systems like Dropbox.

* **Initial subdomain support.**  This release allows users to register
subdomains of existing blockchain IDs, such that _subdomains are independently
owned_.  A user Bob can register `bob.alice.id`, where `alice.id` is owned by
Alice.  Queries on `bob.alice.id` resolve to Bob's signed profile and data, and
Alice cannot change Bob's public key.

* **Better Packaging for Test Mode.**  This release makes it easier to get
started testing Blockstack Core and Blockstack Browser alongside a Bitcoin
node in `regtest` mode.  Developers can register names and interact with storage
without having to spend Bitcoin or wait hours for names to be registered.

Selected Bugfixes and Fixes
---------------------------

* Issue #469 : Blockstack Core used to die in error cases when it should be 
able to fail more gracefully. This release fixes several such cases.

* Removed hash-based fresh-profile validation from the storage gateway interface
in the indexer.  This interface had been deprecated for some time, and new 
clients have been relying on timestamp-based fresh-profile validation for some
time now.

* Signing profiles and data is now done with a name's token file signing key,
not the catch-all data private key.  You can still verify data signed with the
old data key, however.