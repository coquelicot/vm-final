# VM Final - Topic 10, Report on Memory De-duplication

## Specs.

### Readingn List

- "_Difference Engine: Harnessing Memory Redundancy in Virtual Machines_"

    D. Gupta, et. al., **OSDI 2008**.

- "_Decentralized Deduplication in SAN Cluster File Systems_"

    T. Austin, **USENIX 2009**.

- "_XLH: More effective memory deduplication scannersthrough cross-layer hints_"

    Konrad Miller, et. al., **USENIX Annual Technical Conference (USENIX ATC ’13), 2013**

- "_Introspection-based memory de-duplication and migration_"

    Jui-Hao Chiang, et. al., **VEE '13 Proceedings of the 9th ACM SIGPLAN/SIGOPS international conference on Virtual execution environments**

### Report Format

The format is part of the report specification, as indicated on the CEBIA.
**We must upload our slide to the CEIBA at least 1 hr before our presentation**.

- Paper titles
- Paper information: publication forum, author affiliations
- Outline
- Motivations
- Technical highlights
- Major experimental results
- Main contributions
- Comparisons
- Our own idea inspired by the papers

## Outline

1. What's dedup; why dedup

1. how to dedup
  * Finding candidates, scanning, etc
  * make the page copy-on-write

1. Scanning order (XLH)

1. Free pages (Introspec)
  * Treat them as zero!

1. Not only identical pages (Diff)
  * diff + compression

1. Issues?

1. More benefits
  * Get more VM!
  * Fast migration

1. Dedup on (SAN) FS!
  * Underlying FS: VMFS
