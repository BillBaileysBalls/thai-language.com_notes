That's a very sharp and important concern. You're right: the technical part (exporting the data) is straightforward compared to the **legal and stewardship problem** of releasing a community-built lexicon into today's environment where commercial "vultures" can swoop in. Let's unpack it.

# thai-language.com legal and stewardship problem

Cut-down version of several LLM analysis

The technical part (exporting the data) is straightforward compared to the **legal and stewardship problem** of releasing a community-built lexicon into today's environment where commercial "vultures" can swoop in. 

# thai-language.com legal and stewardship problem

## 1. What the risks actually are

If Glenn or collaborators just **dump the raw data to GitHub with no license**, then by default:

* It's "all rights reserved" (copyright holder retains rights).
* But in practice, people will **still take and use it** without permission.
* Companies could:
  * Use it to build commercial apps (language learning, AI models, translation services).
  * Claim their derivative work is proprietary.
  * Potentially **trademark a brand around it**, muddying the waters.

So the danger isn't just "reuse" — it's **unattributed, commercial enclosure** of what has been a community cultural resource.

---

## 2. Open content license

* Strictly speaking, "open source" applies to **software code**, not **content/data**.
* For **data** (especially lexicons, corpora, dictionaries), the right parallel is **"open content" licenses**.
* Precedents:
    * **Wiktionary / Wikipedia** → Creative Commons Attribution-ShareAlike (CC BY-SA).
    * **WordNet** (the Princeton lexical database) → a BSD-like license, free for commercial and research use.
    * **Open Multilingual Wordnet** → CC BY.
    * **OpenStreetMap** → Open Database License (ODbL).
    * **PanLex / other lexica** → typically CC BY-SA or ODbL.

So yes, it can be opened — but you don't want "no license" or a too-permissive one if your concern is corporate appropriation.

---

## 3. Threat models

### A. **Commercial exploitation without giving back**

* A company clones the dataset, sticks it in an app, slaps ads/subscriptions on it.
* They never attribute Glenn or the community.

### B. **Lock-in through proprietary derivatives**

* Someone expands the dataset, adds proprietary annotations, then claims *that version* as closed/proprietary.

### C. **AI / LLM training without acknowledgment**

* The lexicon gets absorbed into language model training corpora.
* Later, nobody can tell where the original source came from.

### D. **Trademark / branding disputes**

* Someone registers a dictionary or app using the same name, creating confusion.

---

## 4. Mitigation strategies

The main lever here is **license choice**. You want something that:

* Allows use, remix, contribution.
* **Requires attribution.**
* **Prevents enclosure** (copyleft for data).
* Still permits beneficial use (research, teaching, apps).

### Options:

1. **CC BY-SA 4.0 (Creative Commons Attribution-ShareAlike)**

  * Standard in open lexicons & corpora.
  * Attribution required.
  * Derivatives must be open under same license.
  * Compatible with Wikipedia/Wiktionary if ever merged.
  Good balance, widely understood.

2. **ODbL (Open Database License)**

  * Made specifically for datasets (used by OpenStreetMap).
  * Protects against commercial enclosure: if you use the DB, you must share your improvements.
  * A little more niche than CC, but very protective.
  Strong anti-enclosure license for databases.

3. **CC BY (Attribution only)**

  * Permits commercial use, requires attribution.
  * Would allow companies to profit from it.
  Too permissive for your concern.

4. **Custom license (e.g. Apache-like for data)**

  * Possible, but risk: unfamiliar → harder for community adoption.

---

## 5. Broader stewardship issues

* **Ownership**: Glenn is (likely) the copyright holder. Volunteers may have moral claims, but unless there was a contributor license agreement, Glenn holds the copyright.
* **Governance**: To avoid the project becoming abandoned or captured, Glenn could:

  * Transfer it to a **foundation** (like Wikimedia, Open Knowledge Foundation, or a new Thai-language Foundation).
  * Set up a **GitHub org** managed by multiple maintainers.
* **Attribution preservation**: The license + README should clearly state Glenn and the community contributions.

---

## 6. Recommended path

* Release the **lexicon data** under **ODbL 1.0** or **CC BY-SA 4.0**.

  * If goal = maximum reuse (including research/AI) → CC BY-SA.
  * If goal = maximum protection against enclosure → ODbL.
* Release the **code** (runtime library, editor, site) under a standard open source license (Apache 2.0, MIT, GPL).
* Publish in a **GitHub org or foundation repo**, not Glenn's personal repo, to signal community stewardship.
* Add a **CONTRIBUTING.md** clarifying attribution rules for future contributions.

---

##  In layman's terms

If the dictionary is "dumped raw," companies can take it, close it up, and pretend it was always theirs.
But if it's released under the **right open license**, they can still use it — but they're **legally forced to credit Glenn/community, and to share improvements back**.

That's what prevents the "vulture problem."

