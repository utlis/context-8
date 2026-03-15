# Context-8

Context-8 is an evaluation dataset designed to assess context sensitivity in Machine Translation for English-to-Japanese translation. The first version consists of 130 groups comprising 533 English-to-Japanese translation examples, each requiring different context categories to produce fluent and appropriate translations.

Context-8 is built from both hand-crafted and online materials. Real-world sources include publicly available written and online materials, covering a wide range of text types and registers.

We begin with the English-to-Japanese pair in the first release. While some items are language-pair-dependent, a sizable portion of Context-8 is driven by properties of the English source. Combined with our construction workflow, this can support the construction of analogous datasets for other language pairs, including those with non-English source languages.

## Uses

This dataset is designed to test the capabilities of MT systems and LLMs to deal with the same text in different contexts, across a range of context categories.

## Dataset Structure

### Overview

The dataset is composed of groups of English-to-Japanese translation examples. The source text (ST) consists of groups of English examples. Each group is a contrastive set containing at least two examples. Examples within the same group share the same specific part as their translation focus (FOCUS) and differ in surrounding text (CONTEXT). The FOCUS may be a word, phrase, sentence, or longer unit. In our design, the FOCUS serves as the primary evaluation target. The CONTEXT refers to the surrounding text that influences the interpretation and translation of FOCUS. The CONTEXT may be a phrase, sentence, paragraph, or longer unit. The first example in each group presents the FOCUS only, and the remaining examples in that group introduce alternative CONTEXTs.

### JSON format

The released JSON file has the following top-level structure:

- `schema_version`: string  
- `category_map`: mapping from category codes to names  
- `items`: list of examples  

Each example in `items` contains:

- `group_id`: integer, group identifier  
- `sid`: string, example identifier within a group (e.g., `"12-0"`, `"12-1"`)  
- `st`: string, source text (English)  
- `ref`: string, reference translation (Japanese, human translation)  
- `context_impact`: string, `"accuracy"` or `"fluency"`  
- `context_categories`: list of strings, context-category codes (subset of `["A1","A2","A3","B1","B2","B3","B4","B5"]`)  

## Taxonomy of context

To construct Context-8, we defined a systematic taxonomy of contexts with wide coverage. The concept categories defined in this taxonomy are used as the contextual factors that affect translations in the construction of Context-8.

The framework of concepts of context consists of A Linguistic Context and B Non-linguistic Context. A Linguistic group contains three categories: A1 Message, A2 Language Events and A3 Genre. B Non-linguistic group contains five categories: B1 Participants, B2 Channel, B3 Social-cultural System, B4 Setting and Scene, and B5 Truth Value.

For additional information about the taxonomy of context, please refer to the paper.
