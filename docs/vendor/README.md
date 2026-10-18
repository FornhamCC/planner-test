# vendor — PDF libraries kept in the repository

The board makes PDFs with these two libraries. They are copied here, rather than loaded from another website, so the board keeps working even if that website changes or goes away.

| File | Library | Version | Licence |
| --- | --- | --- | --- |
| `jspdf.umd.min.js` | jsPDF — draws PDF pages | 4.2.1 | MIT (`jspdf-LICENSE.txt`) |
| `jspdf.plugin.autotable.min.js` | jsPDF-AutoTable — lays out tables across pages | 5.0.9 | MIT (`jspdf-autotable-LICENSE.txt`) |

They are only loaded when someone first presses **Make PDF**, so they never slow down opening the board.

To update one later: download the newer file of the same name from npm (`npm install jspdf jspdf-autotable`, then look in `node_modules/…/dist/`), replace the file here, and check every PDF type still looks right.
