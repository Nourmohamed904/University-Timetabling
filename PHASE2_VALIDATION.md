# Phase 2 – Validation & Verification

This document describes how each of the implemented SonarQube‑reported changes was verified.

---

## Change 1 – Remove commented‑out code block in InstructionalOffering.hbm.xml (Jira: UT‑7)

**SonarQube rule:** `xml:S125` – Sections of code should not be commented out.

### What was done
Deleted the entire commented‑out `<set>` block for `creditConfigs` (the legacy mapping inside `<!-- ... -->`).

### Verification steps
1. **XML well‑formedness**  
   The file `InstructionalOffering.hbm.xml` was inspected in IntelliJ IDEA.  
   All XML tags are correctly balanced; there are no missing closing tags.  
   The only warning (`Cannot resolve package unitime`) is a pre‑existing IDE configuration issue, unrelated to this change.

2. **Static analysis re‑check**  
   SonarLint (and the project‑wide inspection) was run on the file after the deletion.  
   The `xml:S125` warning is no longer present.

3. **Build attempt**  
   The project was compiled with `mvn compile` (minus pre‑existing Java 11 compatibility issues in other files).  
   No new errors were introduced by this XML modification.

4. **Git history**  
   The removed block is preserved in the Git history (visible via `git log`). It can be restored from any previous commit if needed.

### Evidence
- Git diff output: see `diff-xml.txt` (shows the exact 14 lines deleted)
- SonarLint / Inspection results after change: no `xml:S125` for this file

---

## Change 2 – Parameterize raw `Class` type in Debug.java (UT‑10)

### What was done
Changed `Class source` to `Class<?> source` in the method `getSource()` of `Debug.java`.

### Verification steps
1. **Syntax check** – The file compiles without errors in IntelliJ.
2. **Static analysis re‑check** – SonarLint no longer reports java:S3740 for Debug.java.
3. **Build attempt** – No new compilation errors introduced.

### Evidence
- Git diff (see `diff-rawtype.txt`) – shows the single line change.

