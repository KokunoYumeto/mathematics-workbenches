# The format of a workbench (format 1, 22 November 2026)

The format is made to outlive renamed repositories, moved files, rewritten histories, changed models and lost services.

## Where a work goes

- By the field of its main theorem, and not by the method, the source of the question, the prompt, or the event that
  started it. A work has one home. Other fields link to it.
- A new repository is made only when a work fits no row of `registry/workbenches.tsv`. The row is written first. A
  repository opens with its first checked work, so that none stands empty.

## Numbers and addresses

- A work gets the next number WB-nnnn in `registry/works.tsv`, and a page `works/WB-nnnn.md` here. Numbers are given
  out only in this repository and are never used again.
- A paper cites that page. If a work or a repository moves, the page is updated and is never deleted. The name of an
  old repository is never given to a new one.
- A paper also prints the SHA-256 of the manifest of its version, and the commit. The hash still identifies the files
  if the commit disappears.
- A paper contains all its proofs. The workbench holds programs, certificates and records, so a paper can still be
  read and checked if a workbench can't be reached.

## Inside a workbench

    work/WB-nnnn/vX/        one folder for each version
      the paper or note     LaTeX or Markdown; a PDF only beside its own TeX
      STATEMENTS.tsv        every statement, with a permanent tag WB-nnnn.kkk
      CHECK_EVENTS.tsv      every check, as what it was
      SOURCES.tsv           what was used of others, cited and linked, never copied
      checks/               records, programs, expected outputs
      MANIFEST.sha256       the hash of every file of the version
      DEPOSITED.md          once the version is deposited; the folder is then never edited

- A tag names one statement for ever. A theorem's printed number may change, and its tag doesn't. A changed statement
  gets a new tag and names the one it supersedes. A refuted or withdrawn statement keeps its row, with that status.
- A correction of a deposited version is a new version and a dated line on the work's page.
- A check event gives the date, the model with its effort (or the human) and one of these types: targeted proof check;
  independent re-proof; computation or formal certificate; used and rechecked in this run; carried as background
  without fault found; discussed in an expert conference; refuted, with the refined statement's id. Checks add up:
  none is deleted when a later one is made.
- Files are UTF-8 text in open formats, and programs state how to run them and what they should print. A file over
  5 MB isn't committed: its program and its hash are.
- Versions are marked by folders and git tags. Histories are not rewritten.
- A translation goes in `translations/<BCP 47 code>/` beside the text it translates, and names that text's hash.

## What never goes in

Other authors' papers, texts, scans or data; text extracted from them; prompt attachments; private records or
conversations; keys, e-mail addresses and paths on someone's computer. `tools/check_workbench.py` is run before every
push, and a person or model who knows whose each file is reads the list of what the push adds.
