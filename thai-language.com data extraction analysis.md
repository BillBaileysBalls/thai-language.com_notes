##  Current understanding of data-structure based on

LLM summarized copy of:

[Wayback copy of site information page](https://web.archive.org/web/20240815150527/http://www.thai-language.com/default.aspx?nav=news&newsmode=history)

### 1. Original system (1997–2000)

* Dictionary was just **static HTML files**, generated offline.
* Data source was a **proprietary tagged text file** (like a hand-rolled markup language).
* A **C++ console app** compiled this into giant HTML pages.
* A crude **Win32 GUI app (C++)** allowed appending new entries, but editing was hard.

---

### 2. First major redesign (2001)

* Aimed to make dictionary entries **dynamic, searchable, and editable**.
* Data was **migrated into a new binary file format** (custom schema).
* Glenn built:

  * A **C++ object library** that defined the dictionary data model.
  * A **GUI editor tool (DBEdit)** that used these objects to read/write the new binary file.
  * A **server-side COM/ActiveX object** (wrapping the same C++ objects) to serve entries on demand.
* ASP + VBScript pages on **IIS** called into the COM/ActiveX layer to dynamically generate dictionary pages.

 **This is when the "proprietary binary file" really became the core database.**

---

### 3. Second rewrite (2005–2009)

* 2005: all VBScript "glue" replaced by **C# ASP.NET code**.
* COM/ActiveX objects wrapped so C# could call them.
* 2007: moved to **C++/CLI interop** → phased out COM/ActiveX.
* 2008: moved to **.NET 3.5 + LINQ**.
* 2009: big leap: the **binary database layer was fully rewritten in C#**, using managed collections (`Dictionary<TKey,TValue>`) instead of assembly routines.
* Dictionary became **Unicode throughout**.

 By this point (2009+), the "runtime library" Glenn mentioned in his GitHub reply was a **C# data access layer** that read/wrote the lexicon in a **custom binary format**, no unmanaged code.

---

### 4. Later years (2009–2014+)

* .NET 4.5.1, LINQ, AJAX prefix search, etc.
* Code was modernized incrementally, but the **fundamental data model (binary file + C# access layer + editor)** stayed the same.

---

##  Migration Path (with this context)

Here's the clearer picture of **what exists today** and how to move it into a modern stack:

### What Glenn has

* **Lexicon database**:

  * A single binary file containing all Thai entries, phonetics, translations, metadata.
  * Proprietary format, readable only via Glenn's custom code.

* **C# runtime library**:

  * Fully managed (post-2009), with LINQ support.
  * Provides record access to the binary file (read/write).

* **DBEdit editor app**:

  * A Windows GUI app (C# after 2009, earlier C++).
  * Used by Glenn + volunteers to update entries.

* **ASP.NET website code**:

  * Early 2000s style, still running as custom HttpHandlers.
  * Not useful to carry forward — modern stacks are better.

---

### Extraction method

* The **runtime library + editor** are indeed the "decoder ring."
* To migrate:

  1. Take the C# library that reads the binary file.
  2. Write a small exporter program using that library.

  * Iterate through every dictionary entry.
  * Dump to JSON, CSV, or directly generate SQL inserts.
  3. Import into MySQL, MariaDB, Postgres, or SQLite.

 This is the safest path: **use Glenn's code to extract data, not reverse engineer the file format.**