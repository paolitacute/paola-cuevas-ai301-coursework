# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

paolitacute

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/68#issuecomment-5860640434

Hello! I will start looking into this issue as soon as possible.

I am claiming this issue to investigate the ZeroDivisionError that triggers when KeywordSearcher.index() receives an empty corpus on the main branch.

I am working on the reproduction package and I will upload the report here when it is finished.


**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/68#issuecomment-5861079428

Here is the reproduction report for the ZeroDivisionError triggered when KeywordSearcher.index() receives an empty corpus.

**Environment:**
I reproduced this issue on a Windows machine running Python 3.13.7, specifically at commit 2f4e82f52efbcfcc57d65b3fa5348672163ca088.

**Steps to reproduce:**
1. Clone the repository and checkout the main branch.
2. Create and activate a virtual environment, then install the project dependencies (e.g., `python -m venv .venv`, `.\.venv\Scripts\activate`, and `pip install -e .`).
3. Run the specific unit test for keyword search while forcing xfails to run: `pytest tests\unit\test_keyword_search.py --runxfail`

**Expected vs. Actual Behavior:**
Expected: The `index()` method should handle an empty corpus without raising an error, similar to how `search()` handles it.
Actual: The test triggers a `ZeroDivisionError` from the `rank-bm25` library. 

**Artifacts:**
================================================= FAILURES =================================================
__________________________________ TestKeywordSearcher.test_empty_index ___________________________________

self = <tests.unit.test_keyword_search.TestKeywordSearcher object at 0x00000149D3CFE750>
searcher = <rag.retriever.keyword_search.KeywordSearcher object at 0x00000149D3CFEC50>

    @pytest.mark.xfail(
        strict=True,
        reason="issue #68 (manifest H-01): BM25 keyword search raises ZeroDivisionError on an empty index",
    )
    def test_empty_index(self, searcher):
        """Test searching on empty index."""
>       searcher.index([])

tests\unit\test_keyword_search.py:140: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
rag\retriever\keyword_search.py:25: in index
    self.bm25 = BM25Okapi(tokenized_corpus)
                ^^^^^^^^^^^^^^^^^^^^^^^^^^^
.venv\Lib\site-packages\rank_bm25.py:83: in __init__
    super().__init__(corpus, tokenizer)
.venv\Lib\site-packages\rank_bm25.py:27: in __init__
    nd = self._initialize(corpus)
         ^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <rank_bm25.BM25Okapi object at 0x00000149D3CFDE50>, corpus = []

    def _initialize(self, corpus):
        nd = {}  # word -> number of documents with word
        num_doc = 0
        for document in corpus:
            self.doc_len.append(len(document))
            num_doc += len(document)
 
            frequencies = {}
            for word in document:
                if word not in frequencies:
                    frequencies[word] = 0
                frequencies[word] += 1
            self.doc_freqs.append(frequencies)
 
            for word, freq in frequencies.items():
                try:
                    nd[word]+=1
                except KeyError:
                    nd[word] = 1
 
            self.corpus_size += 1
 
>       self.avgdl = num_doc / self.corpus_size
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^
E       ZeroDivisionError: division by zero

.venv\Lib\site-packages\rank_bm25.py:52: ZeroDivisionError

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

item    gold    verdict  agree  note
pkg-01  accept  accept   yes    
pkg-02  reject  reject   yes    
pkg-03  accept  accept   yes    
pkg-04  reject  reject   yes    
pkg-05  accept  reject   NO     failed: steps-reproducible
pkg-06  reject  reject   yes    
pkg-07  accept  accept   yes    
pkg-08  reject  reject   yes    
pkg-09  accept  reject   NO     failed: behavior-matches
pkg-10  accept  accept   yes    
pkg-11  accept  accept   yes    
pkg-12  accept  accept   yes    
pkg-13  reject  reject   yes    
pkg-14  reject  reject   yes    
pkg-15  reject  reject   yes    
pkg-16  reject  reject   yes    
pkg-17  reject  reject   yes    
pkg-18  reject  reject   yes    
pkg-19  reject  reject   yes    
pkg-20  reject  accept   NO     graded accept

**Package analysis**

Package pkg-20 received a gold label of "reject", but my rubric's run evaluated it as an "accept". The gold label rejected this package because the ghostty repository's stated AI policy requires disclosing all AI usage, and the package's comments failed to include this disclosure. My rubric mistakenly accepted it during this run because the evaluation criteria did not explicitly mandate a failure for silence on AI-use disclosures.

**Check rationale**

Check: behavior-matches   
Evidence: "The terminal output, logs, or artifact read against the error the issue describes."   
Pass condition: "The reproduction convincingly demonstrates the core behavior described in the issue, OR it provides an explicitly evidenced "cannot reproduce" with a clear control run."   
Weight: required

This check reads this way because an earlier, stricter version demanded that the exact behavior be triggered, which caused the rubric to falsely reject valid, honest "cannot reproduce" packages like pkg-09. By loosening the language to "core behavior" and introducing a dedicated logical branch for an explicitly evidenced "cannot reproduce," the check now evaluates the evidentiary quality of the attempt rather than automatically failing reports that correctly prove the bug does not trigger.

**Trade-offs**

Adding the explicitly evidenced "cannot reproduce" branch to the behavior-matches check accepts that some contributors might hastily run tests in completely mismatched environments. If a user fails to trigger the bug due to an incorrect setup and attaches a simple control run to claim "cannot reproduce," this check might now pass them, placing the burden of debugging the mismatched environment back onto the maintainers. However, keeping the check strictly focused on triggering the bug would cost us high-quality, heavily investigated negative results like pkg-09 and pkg-10, which provide valuable clues about what a triggering setup actually requires.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
