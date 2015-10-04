---
layout: default
sidebar: yes
permalink: /docs/server/mdb.yaml/
---

<pre>
<code class="config-file">
refmdb:
   # Valid loaders are: sheet, xtce or fully qualified name of the class
   - type: "sheet"
     spec: "mdb/refmdb-ccsds.xls"
     subLoaders:
         - type: "sheet"
           spec: "mdb/refmdb-subsys1.xls"

simulator:
    # Configuration of the active loaders
    # Valid loaders are: sheet, xtce or fully qualified name of the class
    - type: "sheet"
      spec: "mdb/simulator-ccsds.xls"
      subLoaders:
           - type: "sheet"
             spec: "mdb/simulator-tmtc.xls"
</code>
</pre>