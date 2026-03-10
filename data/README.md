# Data Files

This folder contains all datasets used in the thesis experiments.

## Files

| File | Size | Description |
|---|---|---|
| `NewStreoSet_Dataset.xlsx` | ~150KB | Annotated StereoSet with English & Persian parallel sentences, gold labels, and Persian targets |
| `stereoset_LLama.csv` | ~180KB | PLL scores, BiasScore, and CB for LLaMA-2 (English) |
| `stereoset_persianLLama.csv` | ~180KB | PLL scores, BiasScore, and CB for PersianLLaMA (Persian) |
| `stereoset_LLama_ByBiasType.csv` | ~205KB | LLaMA-2 results with CB aggregated by bias type (gender/race/religion/profession) |
| `stereoset_persianLLama_ByBiasType.csv` | ~204KB | PersianLLaMA results with CB aggregated by bias type |
| `APX_LLaMA.csv` | ~172KB | APX (perplexity-based) bias scores for LLaMA-2 |
| `APX_persianLLaMA.csv` | ~172KB | APX bias scores for PersianLLaMA |
| `stereoset_with_tokenizer_features.csv` | ~241KB | Extended dataset with tokenizer fragmentation features for both models |

## Column Descriptions

### Core Dataset (`NewStreoSet_Dataset.xlsx`)

| Column | Description |
|---|---|
| `target` | The social target (e.g., Bangladesh, himself, Muslim) |
| `bias_type` | Category: `gender`, `race`, `religion`, `profession` |
| `context` | Sentence with BLANK placeholder |
| `sentence` | Candidate sentence filling the BLANK |
| `gold_label` | 0=stereotype, 1=anti-stereotype, 2=unrelated |
| `label_name` | Human-readable label |
| `full_sentence` | Complete English sentence |
| `Persian` | Persian translation of full_sentence |
| `Persian_Target` | Persian translation of target word |

### PLL Results (`stereoset_LLama.csv`, `stereoset_persianLLama.csv`)

| Column | Description |
|---|---|
| `PLLEnglish` / `PLLPersian` | Pseudo-log-likelihood score |
| `BiasEnglish` / `BiasPersian` | BiasScore = PLL(stereo) - PLL(anti-stereo) per context |
| `CBEnglish` / `CBPersian` | Categorical Bias score (normalized across 3 candidates) |

### APX Results (`APX_LLaMA.csv`, `APX_persianLLaMA.csv`)

| Column | Description |
|---|---|
| `PPL_English` / `PPL_Persian` | Sentence perplexity |
| `MeanTargetPPL_English` / `MeanTargetPPL_Persian` | Mean PPL for that target across all 3 candidates |
| `APX_English` / `APX_Persian` | APX = PPL / MeanTargetPPL × 100 |

### Tokenizer Features (`stereoset_with_tokenizer_features.csv`)

| Column | Description |
|---|---|
| `token_count_en` | Number of tokens in English sentence (LLaMA tokenizer) |
| `token_count_fa` | Number of tokens in Persian sentence (PersianLLaMA tokenizer) |
| `word_count_en` | Number of words in English sentence |
| `word_count_fa` | Number of words in Persian sentence |
| `frag_ratio_en` | English fragmentation = tokens/words |
| `frag_ratio_fa` | Persian fragmentation = tokens/words |

## Data Ethics

This dataset is derived from [StereoSet](https://stereoset.mit.edu/) (Nadeem et al., 2021), used under academic research terms. The dataset contains potentially sensitive social stereotypes and is intended **exclusively for bias measurement research**.
