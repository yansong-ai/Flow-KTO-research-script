# Humanize Check Report

- Matrix path: `paper_rewriting_output/humanize_matrix.md`
- Humanize tier: medium
- Matrix rows: 37
- Manuscript paragraphs: 0
- Coverage: 0%
- Sentence length stddev: 0.0
- Connector density: 0.0/1k chars
- Status: PASS

## Dimension Scores

### D1 sentence structure: PASS [required]
- Metrics: sentence_count=0
- No dimension-specific risk found.

### D2 paragraph similarity: PASS [required]
- Metrics: paragraph_count=0, max_4gram_count=0, repeated_4gram_ratio=0.0
- No dimension-specific risk found.

### D3 information density: PASS [required]
- No dimension-specific risk found.

### D4 connector frequency: PASS [required]
- No dimension-specific risk found.

### D5 term-context matching: PASS [advisory]
- No dimension-specific risk found.

## Required Findings

- None

## Advisory Findings

- None

## Threshold Profile

- adjacent_similarity_max_fail: 0.65
- adjacent_similarity_mean_warning: 0.45
- max_4gram_count_warning: 5
- max_connector_density: 8
- max_generic_density: 7
- max_paragraph_connector_density: 14
- max_repeated_start_ratio: 0.35
- max_term_generic_context_ratio: 0.45
- min_info_anchor_density: 2.5
- min_paragraph_length_stddev: 25
- min_sentence_length_stddev: 6
- repeated_4gram_ratio_fail: 0.15
- repeated_4gram_ratio_warning: 0.08
- sentence_length_cv_fail: 0.25
- sentence_length_cv_warning: 0.35
- ttr_fail_en: 0.25
- ttr_fail_zh: 0.35
- ttr_warning_en: 0.32
- ttr_warning_zh: 0.42
