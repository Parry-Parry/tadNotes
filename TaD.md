# Speech and Language Processing

## Chapter 1 

**conversational agent / dialogue system** : programs that converse with humans in natural language

**machine translation** : automatically translate a document from one language to another

**web-based question answering** : generalization of simple Web search, where instead of just typing keywords, a user might ask complete questions

### Answering Questions

**speech recognition/speech synthesis** : requires phonetics and phonology 

_phonetics_ : how words are pronounced in terms of sequences of sounds

_phonology_ : how sounds are realized acoustically

**producing contractions like I’m and can’t** : requires morphology 

_contractions_ : shortened form of a word \(or group of words\) that omits certain letters or sounds

_morphology_ : the way words break down into component parts that carry meanings like singular versus plural

**syntax** : the order and grouping of words

**lexical semantics** : the meaining of words

**compositional semantics** : the meaning of a phrase determined by combining the meanings of its subphrases

**pragmatic/dialogue knowledge** : The actions intended by use of sentences 

**coreference resolution** : knowledge about how words like that or pronouns like it or she refer to previous parts of the discourse

_discourse_ : communication by words / knowledge about linguistic units larger than a single utterance

### Ambiguity 

**ambiguous input** : multiple alternative linguistic structures can be built for the input

**part-of-speech tagging** : process of marking up a word in a text as corresponding to a particular part of speech, based on both its definition and its context

**word sense disambiguation** : determining which meaning of a word is activated by the use of the word in a particular context

**lexical disambiguation** : identifying which meaning of a word is used in context

**syntactic disambiguation** : identifying the meaning of a sentence from its structure

**probabilistic parsing** :  the process of determining the parses of an input string according to a formal grammar

_parse_ : to separate a sentence into grammatical parts

**speech act interpretation** : determining whether a sentence is a statementor a question

### Models and Algorithms 

_See AF2 for state machines_

The key advantage of probabilistic models is their ability to solve the many kinds of ambiguity problems that we discussed earlier; almost any speech and language processing problem can be recast as “given N choices for some ambiguous input, choose the most probable one”

_examples of formal rule systems_ : regular grammars and regular relations, context-free grammars, and feature-augmented grammars

**Markov model / weighted automaton** : a state machine augmented with probabilities

For non-probabilistic tasks, such as tasks involving state machines, we use well-known graph algorithms such as depth-first search. For probabilistic tasks, we use heuristic variants such as best-first and A* search and rely on dynamic programming algorithms for computational tractability.

**computational tractability** : how the resources needed for execution of the algorithm increase as we increase the size of the input 

**classifiers** : attempts to assign a single object to a single class

_examples of classifiers_ : decision trees,support vector machines,Gaussian mixture models, and logistic regression

**sequence models** : attempts to jointly classify a sequence of objects into a sequence of classes

_examples of sequence models_ : hidden Markov  models, maximum entropy Markov models

Many tools from ML apply in language processing, distinct training and test sets, statistical techniques like cross-validation, and careful evaluation of trained systems

### Language, Thought, and Understanding

**Turing test** : an empirical test, a game, in which a computer’s use of language would form the basis for determining if the machine could think

**Explaination of the Turing test**

There are three participants: two people and a computer. One of the people is a contestant who plays the role of an interrogator. To win, the interrogator must determine which of the other two participants is the machine by asking a series of questions via a teletype. The task of the machine is to fool the interrogator into believing it is a person by responding as a person would to the interrogator’s questions.The task of the second human participant is to convince the interrogator that the otherparticipant is the machine and that she is human.

**ELIZA** : an early natural language processing system capable of carrying on a limited form of conversation with a user, a remarkably simple program that uses pattern matching to process the input and translate it into suitable outputs.

### The State of the Art

**Examples of modern language processing**

_Direct Copy_

- Travelers calling Amtrak, United Airlines, and other travel providers interact with conversational agents that guide them through the process of making reservations and getting arrival and departure information.
- Car makers provide automatic speech recognition and text-to-speech systems that allow drivers to control their environmental, entertainment, and navigational systems by voice. A similar spoken dialogue system has been deployed by astronauts on the International Space Station.
- Video search companies provide search services for millions of hours of video on the Web by using speech recognition technology to capture the words in the sound track.
- Google provides cross-language information retrieval and translation services whereby users can supply queries in their native language to search collections in another language. Google translates the query,finds the most relevant pages,and then automatically translates them back to the user’s native language.
- Large educational publishers such as Pearson and testing services like ETS use automated systems to analyze thousands of student essays, grading and assessing them in a manner that is indistinguishable from human graders.
- Interactive virtual agents, based on lifelike animated characters, serve as tutors for children learning to read.
- Text analysis companies provide marketing intelligence based on automated measurements of user opinions, preferences, attitudes as expressed in weblogs, discussion forums, and user groups.

### Some Brief History

_Refer to 1.6, it is not worth summarising a history lesson_

### Summary

_Direct Copy_

- A good way to understand the concerns of speech and language processing re-search is to consider what it would take to create an intelligent agent like HAL from 2001: A Space Odyssey, or build a Web-based question answerer, or a machine translation engine.
- Speech and language technology relies on formal models, or representations, of knowledge of language at the levels of phonology and phonetics, morphology,syntax, semantics, pragmatics and discourse. A number of formal models in-cluding state machines, formal rule systems, logic, and probabilistic models areused to capture this knowledge.
- The foundations of speech and language technology lie in computer science, linguistics, mathematics, electrical engineering, and psychology. A small numberof algorithms from standard frameworks are used throughout speech and language processing.
- The critical connection between language and thought has placed speech and language processing technology at the center of debate over intelligent machines. Furthermore, research on how people interact with complex media indicates that speech and language processing technology will be critical in the development of future technologies.
- Revolutionary applications of speech and language processing are currently in use around the world. The creation of the Web, as well as significant recent improvements in speech recognition and synthesis, will lead to many more applications.

## Chapter 2

**regular expression** : Regular expressions can be used to specify strings we might want to extract from a document such as definingstrings like $199 or $24.99 for extracting tables of prices from a document

**text normalisation** : converting text to a more convenient, standard form

**tokenization** : The seperation of words in running text

**lemmatization** : determining that two words have the same root, despite their surface differences

**lemmatizer** : mapping words to their root

**Stemming** : stripping suffixes

**sentence segmentation** : the breaking of a text into sentences by grammatical cues

**edit distance** : how similar are two strings by the number of edits it takes to change one string to the other, widely used from spell check to speech recognition

### Regular Expressions

The simplest kind of regular expression is a sequence of simple characters. To search for woodchuck, we type /woodchuck/. The expression /Buttercup/ matches any string containing the substring Buttercup; _grep_ with that expression would return the line I’m called little Buttercup. The search string can consist of a single character \(like /!/\) or a sequence of characters \(like /urgl/\). Regex are case-sensitive.

- Expressions using square braces specify a disjunction of characters to match e.g /\[abc\]/ matches with a, b or c 
- Expressions using a dash specify a range of characters to match e.g /\[a-d\]/ matches with a, b, c and d
- Expressions using a carat as the first character after a square brace match the opposite of the stated pattern e.g /\[^a\]/ matches any single lowercase character except a
- A question mark indicates the preceding character or nothing e.g /\[colour?s\]/ would match with both colour and colours
- An asterisk indicates zero or more of the preceding character e.g /aa\*/ would match with one or more a's, /\[ab\]\*/ would match with zero or more a's or b's
- A plus sign indicates one or more of the preceding character
- A perioid indicates a wildcard that can match any character e.g /hell./ would match hello, hell', hell0 among others
- A pipe symbol \(disjunction operator\) matches one pattern or another e.g /cat\|dog/ would match cat or dog
- Enclosing characters in brackets treats them as a single character for the purposes of operators like \| and \*

**Anchors** : special characters that anchor regex to particular places in a string

- The dollar sign matches to the end of a line
- The carat matches to the start of a line
- \\b matches to a word boundary
- \\B matches to a non-word boundary

_Example regex_

/\(ˆ\|\[ˆa-zA-Z\]\)\[tT\]he\(\[ˆa-zA-Z\]\|$\)/ would correctly find all instances of 'the' in a text, it searches for 'The' and 'the' requiring either a line beginning or a non alphabetic character while avoiding any instances of 'the' found within words e.g 'theory'.

Regex must be checked for false positves such as 'theory' and false negatuves such as missing 'The'. Addressing these errors has to occur often to reduce the overall error rate in language processing. 

**More Operators**

- \\d matches any digit
- \\D matches any non-digit
- \\w matches any alphanumeric or underscore
- \\W matches any non-alphanumeric
- \\s matches whitespace
- \\S matches any non-whitespace

**Counting Operators**
- \* : zero or more occurences of previous char or expression
- \+ : one or more occurrences of the previous char or expression
- ? : exactly zero or one occurrence of the previous char or expression
- \{n\} : n occurrences of the previous char or expression
- \{n,m\} : from n to m occurences of the previous char or expression
- \{,m\} : up to m occurences of the previous char or expression

**Special Characters**
- \\\* matches an asterisk
- \\. matches a period
- \\? matches a question mark
- \\n matches a newline
- \\t matches a tab

**capture group** : use of parenthesis to store a pattern in memory

**non-capture group** : using :? within parenthesis will not store the pattern in memory 

**lookahead assertion** : uses =? to search for a pattern without advancing further on in the text

?! returns true if there is not match but does not advance in the text.

### Words 

**corpus** : a computer-readable collection of text or speech

**utterance** : the correlating speech to a sentence

**disfluency** : normal irregularities that occur during speech

**filled pause** : an articulation by the speaker that may be encountered between utterances but is not to be mistaken for a lengthened sound within a word

_some disfluencies are kept for example a filled pause could indicate that the speaker is restarting the clause or idea_

**lemma** : a set of lexical forms having the same stem

_stem_ : a major part-of-speech or word sense

**word form** : the full inflected or derived form of a word

**types** : the number of distinct words in a corpus

**tokens** : total number of running words

**dictionary boldface forms** : very rough upper bound on the number of lemmas

### Corpora 

**code switching** : use of multiple languages in a single communicative act

_text also reflects the demographic characteristics of the writer \(or speaker\): their age, gender, race, socioeconomic class can all influence the linguistic properties of the text we are processing._

A corpus creator should create a datasheet or data statement for each corpus considering:

- Motivation : Why was the corpus collected, by whom, and who funded it?
- Situation : When and in what situation was the text written/spoken? For example, was there a task? Was the language originally spoken conversation, edited text, social media communication, monologue vs. dialogue?
- Language Variety : What language \(including dialect/region\) was the corpus in?
- Speaker Demographics : What was, e.g., age or gender of the authors of the text?
- Collection Process : How big is the data? If it is a subsample how was it sampled? Was the data collected with consent? How was the data pre-processed, and what metadata is available?
- Annotation Process : What are the annotations, what are the demographics of the annotators, how were they trained, how was the data annotated?
- Distribution : Are there copyright or other intellectual property restrictions?

_metadata_ : data that describes other data

### Text Normalization

Before almost any natural language processing of a text, the text has to be normalized. At least three tasks are commonly applied as part of any normalization process:

- Tokenizing words
- Normalizing word formats
- Segmenting Sentences


**Unix Commands**
- tr : systemically change specific characters in an input
- sort : sorts input in alphabetical order
- uniq : collapses and counts identical lines 

_Refer to 2.4.1 for an extensive example of these commands_

Often punctuation is broken off into a seperate token. Commas are a useful piece of information for parsers, periods help indicate sentence boundaries. Punctuation that occurs in word such as 'Ph.D' is kept. Special characters are often kept such as '$49.99' as well as numbers as we wouldnt want to split that price into '$, 49, 99'.

In English we split numbers every 3 digits with punctuation so we must consider these cases when tokenizing.

Tokenizing can assist with clitic contractions such as expanding 'They're' to 'They are'.

_clitic_ : part of a word that cannot stand on its on only occuring as a part of another word

**named entitity recognition** : detecting names, dates and organizations

**Penn Treebank tokenization standard** : used for the treebanks released by the LDC

_treebank_ : parsed corpora

_LDC_ :  Linguistic Data Consortium, a source of useful datasets

_The standard method for tokenization is to use deterministic algorithms based on regex compiled into efficient finite state automata_

**Hanzi** : Characters in the Chinese language

_Chinese NLP tasks take characters rather than words as input as meaning can be derived with less ambiguity and with smaller dictionaries_

_For Japanese and Thai NLP tasks characters do not offer enough semantic meaning so word segmentation is required_

NLP algorithms often use one training corpus then use facts derived to make decisions about a seperate test corpus and its language.

_In modern tokenization most tokens are words but some are frequently occuring morphemes_ 

**Token learner** : takes a raw training corpus \(sometimes roughly pre-separated into words, for example by whitespace\) and induces a vocabulary, a set of tokens

**Token segementer** : takes a raw test sentence and segments it into the tokens in the vocabulary

**Common tokenization algorithms**
- byte-pair encoding
- unigram language modeling
- WordPiece
- SentencePiece : uses BPE and ULM

**Byte-pair encoding**

The BPE token learner begins with a vocabulary that is just the set of all individual characters. It then examines the training corpus, chooses two symbols that are the most frequently adjacent and adds a new new symbol that merges these two symbols replacing every occurence of these adjacent symbols with this new single merged symbol. It continues to count and merge creating new and longer character strings until k merges have been done creating k novel tokens. The resulting vocabulary consists of the original set of individual characters plus k new symbols.

_Once we have 'learned' our vocabulary the token parser is used to tokenize a test sentence running on the test data with the merges we have learned in the order we learned them._

In real instances of BPE there are thousands of merges on a very large input corpus, the result yeild mostly full words with only rare occurences being represented by their parts.

**Word normalization** : putting words/tokens into a standard format

_A single normal form is chosen, this standardization may be valuable, despite the spelling information that is lost in the normalization process_

**Case folding** : mapping everything to lower case

Case folding is helpful for generalization in tasks such as information retrieval and speech recognition. For sentiment analysis and other text classification tasks case can be helpful thus case folding is not usually done. This is done because maintaining the difference between for example 'US' the country and 'us' the pronoun can outweigh the advantage of generalization that case folding would provide for other words.

**morphological parsing** : parsing words into morphenes, stems and affixes

_affixes_ : additions to a word to add meaning e.g adding 's' as a suffix to mean plural

**cascade** : when the output of an algorithm pass is fed in as the next input

**Cues for sentence segmentation**
- punctuation
- question marks and exclamation points

_Periods can be ambiguous as they can represent a sentence boundary marker or an abbriviation or both_

In general sentence tokenization methods work by first deciding whether a period is part of a word or a sentence boundary. An abbreviation dictionary can help determine whether a period is part of a common abbreviation.

**Minimum edit distance** : the minimum number of editing operations \(insertion, deletion and substution\) needed to transform one string to another

**alignment** : given two sequences, the correspondence between substring of the two sequences

**Example operation list**
- d : deletion
- i : insertion
- s - substitution

_This is used to expres how we convert one string to another._

### Minimum Edit Distance

**Coreference** : Deciding whether two strings refer to the same entity

**Levenshtein distance** : the simplest weighting factor in which each of the three aformentioned operations has a cost of 1.

**Dynamic programming** : a class of algorithms that apply a table-driven method to solve problems by combining solutions to sub-problems.

**Minimum edit distance algorithm** : a dynamic programming algorithm that finds the minimum edit distance by combining the edit distances recursively from the empty string to the longest of the two strings.

_A psudocode implementation can be found at 2.5.1_

**Parallel corpus** : a corpus with a text in two languages

**Backtrace** : Start from the last cell in a distance matrix and follow pointers back to the empty string, each complete path is a minimum distance alignment.

**Viterbi** : A probibalistic extension of minimum distance, computing te maximum probability alignment instead of the minimum edit distance. _Discussed further in chapter 8._

### Summary

_Direct Copy_

- The regular expression language is a powerful tool for pattern-matching.
- Basic operations in regular expressions include concatenation of symbols, disjunction of symbols \(\[\], \|, and .\), counters\(\*,+, and\{n,m\}\), anchors\(ˆ,$\) and precedence operators \(\(,\)\)
- Word tokenization and normalization are generally done by cascades of simple regular expression substitutions or finite automata.
- The Porter algorithm is a simple and efficient way to do stemming, stripping off affixes. It does not have high accuracy but may be useful for some tasks.
- The minimum edit distance between two strings is the minimum number of operations it takes to edit one into the other. Minimum edit distance can becomputed by dynamic programming, which also results in an alignment of the two strings.

## Lecture 1 

### Slides

**Text Processing as a Pipeline**
- download web page, strip html if necessary, trim to desired content
- tokenize the text, select tokens of interest, create an NLTK text
- normalize the words, build the vocabulary

_NLTK_ : Natural Language ToolKit

Words aren't the only unit for tokenising, sometimes "n-grams" can be useful too. These can be obtained by passing a sliding window over a token stream. Different n-gram indexing can be achieved using sliding windows of larger sizes.

**Morphemes** : The small meaningful units that make up words

_Outcome of stemming may not be a word, instead will group similar words_

_Lemmatization is slower than stemming due to word lookup being required_

**one-hot encoding** : A vector that represents a text as a set of its terms, 1 if a term occurs, 0 if not

_The vectors for one-hot encoding all have \|V\| dimensions being the number of unique normalized tokens in the vocabulary for the corpus_

**What do we need to transform documents from a stream of tokens into a one-hot encoding?**
- know for each term, what its offset is in the dictionary / vocabulary
- The dimension of the vector, i.e. the size of the map

_If a new word is found in a text it is either added to the dictionary or in the case of the dictionary being frozen it is considered out-of-vocabulary_

_Can save space by only storing the id of terms that occur in a text rather than all in the vocabulary_

**Large Dictionary Solutions**
- Ommit rare words
- Hash the dictionary directly mapping words to vector indices of a fixed size

_Hash collisions are typically dealt with by using freed-up memory to increase the number of hash buckets_

**Handling OOV Words**
- Observation: Most unseen words are new morphological forms (or numbers)
- Wordpiece tokenization breaks words into “subword” pieces
- Learn common patterns from a large corpus of text

**Many text applications are based on comparing the similarity of pieces of text**
- grouping together tweets or news articles about the same event
- identifying documents similar to a user's query

**similarity measure** : a function that computes the degree of similarity between a pair of vectors

**Why set-based similarity?**
- Works well for small texts
- trivial to compute with basic data structures
- there are fast and efficient approximations

**Matching coefficient** : Number of terms (dimensions) that are both are non-zero

**Overlap coefficient** : Intersection divided by the size of smallest set

**Dice Similarity** : The intersection of the two sets mulitplied by 2, divided by the sum of the cardinality of the two sets

_cardinality_ : the number of elements in a set

**Jaccard Similarity** : the size of the intersection divided by the size of the union of the sample sets

**Summary**
- There are a plethora of text mining applications
- Text mining starts with representations of the words in the text, e.g. one-hot encoding 
- Examined set-based similarity measures

**Outstanding issues:*
- similarity is based on sets and doesn’t use counts
- Not all words are equally useful or discriminative. In the next lecture, we'll discuss statistical techniques that can identify the utility of words

### Pre-recorded Lecture

Twitter trending does not just look at what are the most popular terms right now but instead the terms that are being spoken about more than previously.

**Indentifying what a text is about**
- Important 'key' words
- Entities
- Properties of a person
- Things
- Actions

_Filler words do not give context_

_Generally ignore URLs_

# Introduction to Information Retrieval
### Chapter 5

**Benefits of Compression**
- increased use of caching

Search systems use some parts of the dictionary and the index much more than others, if we cache cache the postings list of a frequently used query term t, then the computations necessary for respondingto the one-term query t can be entirely done in memory.

_There are simple and efficient decompression methods, so that the penalty of having to decompress the postings list is small._

Because memory is a more expensive resource than disk space, increased speed owing to caching – rather than decreased space requirements – is often the prime motivator for compression.

- faster transfer of data from disk to memory

Efficient decompression algorithms run so fast on modern hardware that the total time of transferring a compressed chunk of data from disk and then decompressing it is usually less than transferring the same chunk of data in uncompressed form.

We can reduce input/output  \(I/O\)  time by loading a much smaller compressed postings list, even when you add on the cost of decompression. 

_For  improved cache utilization and faster disk\-to\-memory transfer, decompression speeds must be high_

**posting** : a docID in a postings list

_Postings in most search systems also contain frequency and position information_

#### Statistical properties of terms in information retrieval

**∆%** : the reduction in size from the line previous in a text
**T%** : the cumulative reduction from unfiltered

**Table of a Model**
- shows the number of terms for different levels of preprocessing
- number of terms is the main factor in determining the size of the dictionary
- number of nonpositional postings is an indicator of the expected size of the nonpositional index of the collection
- The expected size of a positional index is related to the number of positionsit must encode

**Effects of operations**
- Preprocessing affects the size of the dictionary and the number of nonpositional postings greatly
- Stemming and case folding reduce the  number of \(distinct\) terms by 17% eachand the number of nonpositional postings by 4% and 3%, respectively.

**rule of 30** : the 30 most common words account for 30% of the tokens in written text

Eliminating the 150 most common words from indexing cuts 25% to 30% of the nonpositional postings. Although a stop list of 150 words reduces the number of postings by a quarter or more, this size reduction does not carry over to the size of the compressed index.

_The postings lists of frequent words require only a few bits per posting after compression_

**Compression Techniques**
- _loseless_ : all information is preserved
- _lossy_ : better compression ratios than loseless but discards some information

**Lossy**

- Case folding, stemming, and stop word elimination are forms of lossy compression
- Lossy compression makes sense when the “lost” information is unlikely ever to be used by the search system

_stop word_ : a word that is not indexed

- For example, web search is characterized by a large number of documents, short queries, and users who only look at the first few pages of results 
- As a consequence, we can discard postings ofdocuments that would only be used for hits far down the list 
- Thus, there are retrieval scenarios where lossy methods can be used for compression withoutany reduction in effectiveness

#### Heaps’ law: Estimating the number of terms

**Heaps’ law** : estimates vocabulary size as a function of collection size

M = kT<sup>b</sup>

- M : number of distinct terms in a collection
- T : number of tokens in the collection
- k & b : parameters with typical values 30 ≤ k ≤ 100 and b≈0.5

- Heaps’ law is that the simplest possible relationship between collection size and vocabulary size is linear in log–log space
- The parameter _k_ is quite variable because vocabulary growth depends alot on the nature of the collection and how it is processed
- Case\-folding and stemming reduce the growth rate of the vocabulary, whereas including numbers and spelling errors increase it

**Heaps’ law suggests that:**
- the dictionary size continues to increase with more documents in the collection, rather thana maximum vocabulary size being reached
- the size of the dictionary is quite large for large collections

#### Zipf’s law: Modeling the distribution of terms

**Zipf’s law** :  if t<sub>1</sub> is the most common term in the collection, t<sub>2</sub> is the next most common, and so on, then the collection frequency c<sub>fi</sub> of the ith most common term is proportional to 1/i.

cf<sub>i</sub> ∝ 1/i

- if the most frequent term occurs cf<sub>1</sub> times
- the second most frequent term has half as many occurrences
- the third most frequent term a third as many occurrences, and so on

_The intuition is that frequency decreases very rapidly with rank._

#### Dictionary compression

- One of the primary factors in determining the response time of an IR system is the number of disk seeks necessary to process a query
- If parts of the dictionary are on disk, then many more disk seeks are necessary in query evaluation

_Thus, the main goal of compressing the dictionary is to fit it in main memory, or at least a large portion of it, to support high query throughput._

Although dictionaries of very large collections fit into the memory of a standard desktop machine, this is not true of many other application scenarios
- We want to be able to design search systems for limited hardware such as mobile phones and onboard computers
- Other reasons for wanting to conserve memory are fast startup time and having to share resources with other applications

#### Dictionary as a string

_The simplest data structure for the dictionary is to sort the vocabulary lexicographically and store it in an array of fixed\-width entries:_
- We allocate 20 bytes for the term itself
- 4 bytes for its document frequency
- 4 bytes for the pointer to its postings list

_Four-byte pointers resolve a 4 gigabytes address space._

_Using fixed-width entries for terms is clearly wasteful._

- The average length of a term in English is about eight characters
- On average we are wasting twelve characters in the fixed\-width scheme
- We have no way of storing terms with more than twenty characters

_We can overcome these shortcomings by storing the dictionary terms as one long string of characters._

- The pointer to the next term is also used to demarcate the end of the current term
- we locate terms in the datastructure by way of binary search in the \(now smaller\) table

_This scheme saves us 60% compared to fixed\-width storage._

#### Blocked storage

- We can further compress the dictionary by grouping terms in the string into blocks of size k and keeping a term pointer only for the first term of each block
- We store the length of the term in the string as an additional byte at the beginning of the term
- We thus eliminate k−1 term pointers, but need an additional k bytes for storing the length of each term

- By increasing the block size k, we get better compression
- However, there is a tradeoff between compression and the speed of term lookup

_We search for terms in the un\-compressed dictionary by binary search_
- In the compressed dictionary, we first locate the term’s block by binary search and then its position within the list by linear search through the block 
- Searching the uncompressed dictionary takes on average 1.6 steps

_By increasing k,  we can get the size of the compressed dictionary arbitrarily close to the minimum but term lookup becomes prohibitively slow for large values of k._

**front coding** : A sequence of terms with identical prefix \(“automat”\) is encoded by marking the end of the prefix with ∗ and replacing it with ⋄ in subsequent terms. As before, the first byte of each entry encodes the number of characters

**minimal perfect hashing** : a hash function that maps M terms onto \[1, ..., M\] without collisions

_However, we cannot adapt perfect hashes incrementally because each new term causes a collision and therefore requires the creation of a new perfect hash function. Therefore, they cannot be used in a dynamic environment._

- It may  not be feasible to store the entire dictionary in main memory for very large text collections and for hardware with limited memory
- If we have to partition the dictionary onto pages that are stored on disk, then we can index the first term of each page using a B-tree
- For processing most queries, the search system has to go to disk anyway to fetch the postings
- One additional seek for retrieving the term’s dictionary page from disk is a significant, but tolerable increase in the time it takes to process a query

#### Postings file compression

- Document identifiers are log<sub>2</sub>800,000≈20 bits long

To devise a more efficient representation of the postings file, one that uses fewer than 20 bits per document, we observe that the postings for frequent terms are close together.

- The key idea is that the gaps between postings are short, requiring alot less space than 20 bits to store
- In fact, gaps for the most frequent terms such as _the_ and _for_ are mostly equal to 1
- Gaps for a rare term have the same order of magnitude as the docIDs and need 20 bits

To encode small numbers in less space than large numbers, we look at two types of methods:
- bytewise compression
- bitwise compression

_These methods attempt to encode gaps with theminimumnumber of bytes and bits, respectively._

#### Variable byte codes

**Variable byte (VB) encoding** : uses an integral number of bytes to encode a gap

- The last 7 bits of a byte are “payload” and encode part of the gap
- The first bit of the byte is a continuation bit
- It is set to 1 for the last byte of the encoded gap and to 0 otherwise

To decode a variable byte code, we reada sequenceof bytes with continuation bit 0 terminated by a byte with continuation bit 1. We then extract and concatenate the 7-bit parts.

_The idea of VB encoding can also be applied to larger or smaller units than bytes._

- Larger words further decrease the amount of bit manipulation necessary at the cost of less effective \(or no\) compression
- Word sizes smaller than bytes get even better compression ratios at the cost of more bit manipulation
- In general, bytes offer a good compromise between compression ratio and speed of decompression

If disk space is a scarce resource, we can achieve better compression ratios by using bit-level encodings

#### γ codes

- **Bit\-level codes** adapt the length of the code on the finer grained bit level
- The simplest bit\-level code is **unary code**

_The unary code of n is a string of n 1s followed by a 0_

**γ encoding** : variable\-length encoding by splitting the representation of a gap G into a pair oflength and offset

- Offset is G in binary, but with the leading 1 removed
- Length encodes the length of offset in unary code

- A γ code is decoded by first reading the unary code up to the 0 that terminates it
- γ codes are always of odd length and they are within a factor of 2 of what we claimed to be the optimal encoding length log<sub>2</sub>G

The characteristic of a discrete probability distribution P that determines its coding properties \(including whether a code is optimal\)is its entropy H\(P\)

H\(P\) = -ΣP\(x\)log<sub>2</sub>P\(x\) for x in X

- Where X is the set of all possible numbers we need to be able to encode
- Entropy is a measure of uncertainty for a probability distribution P over two possible outcomes

- Entropy is maximized \(H\(P\) = 1\) for P\(x<sub>1</sub>\) = P\(x<sub>2</sub>\) = 0.5 when uncertainty about which x<sub>i</sub> will appear next is largest

- Entropy is minimized \(H\(P\) = 0\) for P\(x<sub>1</sub>\) = 1, P\(x<sub>2</sub>\) = 0 and for P\(x<sub>1</sub>\) = 0, P\(x<sub>2</sub>\) = 1 when there is absolute certainty

A code like γ code with the property of being within a factor of optimal for an arbitrary distribution P is called universal.

In addition to universality, γ codes have two other properties that are useful for index compression:
- They are prefix free, namely, no γ code is the prefix of another

_There is always a unique decoding of a sequence of γ codes – and we do not need delimiters between them._

- The second property is that γ codes are parameter free

_For many other efficient codes, we have to fit the parameters of a model to the distribution of gaps in the index._

- Many bit\-level operations – shifts and masks – are necessary to de\-code a sequence of γ codes as the boundaries between codes will usually be somewhere in the middle of a machine word
- As a result, query processing is more expensive for γ codes than for variable byte codes

### Chapter 6

#### Parametric and zone indexes

- The possible values of a field should be thought of as finite 
- There is one parametric index for each field

_parametric index_ : an index that allows retrieval of documents based on the values of parameters

- Zones are similar to fields, except the contents of a zone can be arbitrary free text
- Document titles and abstracts are generally treated as zones
- The dictionary for a parametric index comes from a fixed vocabulary, the dictionary for a zone index must structure whatever vocabulary stems from the text of that zone
- We can reduce the size of the dictionary by encoding the zone in which a term occurs in the postings

#### Weighted zone scoring

- Given a Boolean query _q_ and a document _d_, weighted zone scoring assigns to the pair \(q,d\) a score in the interval \[0, 1\], by computing a linear combination of zone scores
- Each zone of the document contributes a Boolean value

For ℓ zones the weighted zone score is defined as:

Σg<sub>i</sub>s<sub>i</sub> for i in range \(1, ℓ\)

_Weighted zone scoring is sometimes referred to also as ranked Boolean retrieval._

Implementing the computation of weighted zone scores
- directly from inverted indexes
- One algorithm treats the case when the query<sub>q</sub> is a two-term query consisting of query terms q<sub>1</sub> and q<sub>2</sub>, and the Boolean function is AND: 1 if both query terms are present in a zone and 0 otherwise
- We now  compute a score for each such document
- Some literature refers to the array scores\[\] above as a set of accumulators

#### Learning weights

**machine\-learned relevance** : a general class of approaches to scoring and ranking in information retrieval

- We are provided with a set of training examples, each of which is a tuple consisting of a query _q_ and a document _d_, together with a relevance judgment for _d_ on _q_ 

_In the simplest form, each relevance judgments is either Relevant or Non\-relevant._

- The weights g<sub>i</sub> are then “learned” from these examples, in order that the learned scores approximate the relevance judgments in the training examples

- For weighted zone scoring, the process may be viewed as learning a linear function of the Boolean match scores contributed by the various zones
- The expensive component of this methodology is the labor\-intensive assembly of user\-generated relevance judgments from which to learn the weights, especially in a collection that changes frequently

The total error of a set of training examples is given by:

Σε\(g, Φ<sub>j</sub>\) in range (0, j)

- g is a constant between 0 and 1
- Where Φ\(training example\) is a triple of the form Φ<sub>j</sub> = \(d<sub>j</sub>, q<sub>j</sub>, r\(d<sub>j</sub>, q<sub>j</sub>\)\)
- Each training example has two boolean variables, s<sub>T</sub>\(d,q\) and s<sub>B</sub>\(d,q\)

score\(d,q\) =g·s<sub>T</sub>\(d,q\) + \(1−g\)s<sub>B</sub>\(d,q\) to determine the relavance of d to q

- The function r\(\) is a relevance judgment

The problem of learning the constant _g_ from the given training examples then reduces to picking the value of _g_ that minimizes the total error

#### The optimal weight g

- We begin by noting that for any training example Φ<sub>j</sub> for which s<sub>T</sub>(d<sub>j</sub>, q<sub>j</sub>) = 0 and s<sub>B</sub>(d<sub>j</sub>, q<sub>j</sub>) = 1, the score computed is equal to g \- 1

- Let n<sub>01r</sub>\(respectively, n<sub>01n</sub>\)  denote  the  number  of  training  examples for which s<sub>T</sub>(d<sub>j</sub>, q<sub>j</sub>) = 0 and s<sub>B</sub>(d<sub>j</sub>, q<sub>j</sub>) = 1
- the editorial judgment is Relevant \(respectively, Non\-relevant\)
- Then the contribution to the total error from training examples for which s<sub>T</sub>(d<sub>j</sub>, q<sub>j</sub>) = 0 and s<sub>B</sub>(d<sub>j</sub>, q<sub>j</sub>) = 1 is:

\[1−\(1−g\)\]<sup>2</sup>n<sub>01r</sub> + \[0−\(1−g\)\]<sup>2</sup>n<sub>01n</sub>

By writing in similar fashion the error contributions from training examples of the other three combinations of values the total error is:

\(n<sub>01r</sub> + n<sub>10n</sub>\)g<sup>2</sup> + \(n10r+n01n\)\(1−g\)<sup>2</sup> + n<sub>00r</sub> + n<sub>11n</sub>

By differentiating with respect to g and setting the result to zero, it follows that the optimal value of g is:

n<sub>10r</sub> + n<sub>01n</sub> / n<sub>10r</sub> + n<sub>10n</sub> + n<sub>01r</sub> + n<sub>01n</sub>

_The last few equations and expressions have been the worst thing I have have ever had to write in markdown_

#### Term frequency and weighting

**free text query** :  a query in which the terms of the query are typed free form into the search interface, without any connecting search operators

- We assign to each term in a document a weight for that term, that depends on the number of occurrences of the term in the document
- We would like to compute a score between a query term _t_ and a document _d_, based on the weight of _t_ in _d_

**term frequency** : the number of occurrences of term _t_ in document _d_, denoted tf<sub>t,d</sub>

- For a document _d_, the set of weights determined by the tf weights above may be viewed as a quantitative digest of that document
- In this view of a document, known in the literature as the bag of words model, the exact ordering of the terms in a document is ignored but the number of occurrences of each term is material

#### Inverse document frequency

Raw term frequency as above suffers from a critical problem : all terms are considered equally important when it comes to assessing relevancy on a query.

**Collection Frequency** : the total number of occurrences of a term in the collection

_The idea would be to reduce the tf weight of a term by a factor that grows with its collection frequency._

**document frequency** : more commonly used than collection frequency, defined to be the number of documents in the collection that contain a term _t_, denoted df<sub>t</sub>

_This is because in trying to discriminate between documents for the purpose of scoring it is better to use a document\-level statistic_

We define the inverse document frequency of a term _t_ as follows:

idf<sub>t</sub> = log\(df<sub>t</sub>\)

_Thus the idf of a rare term is high, whereas the idf of a frequent term is likely to be low._

#### Tf\-idf weighting

We now combine  the definitions of term frequency and inverse documentfrequency, to produce a composite weight for each term in each document.

The tf\-idf weighting scheme assigns to term _t_ a weight in document _d_ given by:

tf\-idf<sub>t,d</sub> = tf<sub>t,d</sub> × idf<sub>t</sub>

In other words, tf\-idf<sub>t,d</sub> assigns to term _t_ a weight in document _d_ that is:
- highest when _t_ occurs many times within a small number of documents
- lower when the term occurs fewer times in a document, or occurs in many documents
- lowest when the term occurs in virtually all documents

At this point, we may view each document as a vector with one component corresponding to each term in the dictionary, together with a weight for each componenent

- For dictionary terms that do not occur in a document, this weight is zero
- This vector form is crucial to scoring and ranking

- As a firststep, we introduce the overlap score measure

**Overlap Score Measure** : the score of a document _d_ is the sum, over all query terms, of the number of times each of the query terms occurs in _d_

-  We can refine this idea so that we add up not the number of occurrences of each query term _t_ in _d_, but instead the tf-idf weight of each term in _d_

Score\(q,d\) =∑tf-idf<sub>t,d</sub> for t∈q

#### The vector space model for scoring

**vector space model** : the representation of a set of documents as vectors in a common vector space

This model is fundamental to a host of information retrieval operations ranging from scoring documents on a query, document classification and document clustering.

#### Dot products

- We  denote  by V\->\(d\)the  vector  derived  from  document _d_,  with  one  component in the vector for each dictionary term
- The set of documents in a collection may be viewed as a set of vectors in a vector space, in which there is one axis for each term
- This representation loses the relative ordering of the terms in each document

To compensate for the effect of document length, the standard way of quantifying the similarity between two documents d<sub>1</sub> and d<sub>2</sub> is to compute the cosine similarity of their vector representations V\->\(d<sub>1</sub>\) and V\->\(d<sub>2</sub>\)

sim\(d<sub>1</sub>, d<sub>2</sub>\) = V\->\(d<sub>1</sub>\) \· V\->\(d<sub>2</sub>\) / \|V\->\(d<sub>1</sub>\)\|\|V\->\(d<sub>1</sub>\)\| 

- where the numerator represents the dot product
- while the denominator is the product of their Euclidean lengths
- The effect of the denominator is thus to length\-normalize the vectors

_This measure is the cosine of the angle θ between the two vectors_

Viewing a collection of N documents as a collection of vectors leads to a natural view of a collection as a term\-document matrix.

**term\-document matrix** : An M x N matrix whose rows represent the M terms of the N columns, each of which corresponds to a document

_As always, the terms being indexed could be stemmed before indexing._

#### Queries as vectors

- we can also view a query as a vector
- Consider the query q = jealous gossip
- This  query  turns  into  the  unit  vector v\-\>\(q\)  =  \(0, 0.707, 0.707\)
- The key idea is to assign to each document d a score equal to the dot product

v\-\>\(q\) · v\-\>\(d\)

- To summarize, by viewing a query as a “bag of words”, we are able to treat it as a very short document
- As a consequence, we can use the cosine similarity between the query vector and a document vector as a measure ofthe score of the document for that query
- A document may have a high cosine score for a query even if it does not contain all query terms

#### Computing vector scores

- In a typical setting we have a collection of documents each represented by a vector, a free text query represented by a vector, and a positive integer K
- We seek the K documents of the collection with the highest vector space scores on the given query
- We now initiate the study of determining the K documents with the highest vector space scores for a query

**term\-at\-a\-time scoring** : adding in contributions one query term at a time

_Contributions_ : The contribution to the vector score from a term t in a query

_document\-at\-a\-time scoring_ : score is calculated one document at a time

#### Variant tf\-idf functions

For assigning a weight for each term in each document, a number of alternatives to tf and tf\-idf have been considered, the principal alternatives are discussed follwing this point.

#### Sublinear tf scaling

- It seems unlikely that twenty occurrences of a term in a document truly carry twenty times the significance of a single occurrence
- A common way to count occurences uses the logarithm of the term frequency, which assigns a weight given by:

wf<sub>t,d</sub> if tf<sub>t,d</sub> > 0 : \{1 + logtf<sub>t,d</sub>\} else: \{0\}

In this form, we may replace tf by some other function wf to obtain:

wf-idf<sub>t,d</sub> = wf<sub>t,d</sub> × idf<sub>t</sub>

#### Maximum tf normalization

- One well\-studied technique is to normalize the tf weights of all terms occurring in a document by the maximum tf in that document
- For eachdocument d, let tf<sub>max</sub>(d) = max<sub>τ∈d</sub>tf<sub>τ,d</sub>
- where τ ranges over all terms in d
- Then, we compute a normalized term frequency for each term t in document d by:

ntf<sub>t,d</sub> = a + \(1 \- a\)\(tf<sub>t,d</sub> / tf<sub>max</sub>\(d\)\)

_where a is a value between 0 and 1 and is generally set to 0.4_

The term a is a smoothing term whose role is to damp the contribution of the second term – which maybe viewed as a scaling down of tf by the largest tf value in d.

The main idea of maximum tf normalization is to mitigate the following anomaly: we observe higher term frequencies in longer documents, merely because longer documents tend to repeat the same words over and over again

_Maximum tf normalization does suffer from the following issues:_
- The method is unstable in the following sense: a change in the stop wordlist can dramatically alter term weightings \(and therefore ranking\). Thus, it is hard to tune
- A document may contain an outlier term with an unusually large number of occurrences of that term, not representative of the content of that document
- More generally, a document in which the most frequent term appears roughly as often as many other terms should be treated differently fromone with a more skewed distribution

#### Document and query weighting schemes

Variations from one vector space scoring method to another hinge on the specific choices of weights in the vectors V\-\>\(d\)and V\-\>\(q\)

**SMART notation**

- The mnemonic for representing a combination of weights takes the form ddd.qqq where:
- the first triplet gives the term weighting of the document vector
- the second triplet gives the weighting in the query vector
- The first letter in each triplet  specifies the term frequency component of the weighting, the second the document frequency component, and the third the form of normalization used

#### Pivoted normalized document length

**Longer documents:**
- as a result of containing more terms – have higher tf values
- contain more distinct terms

_These factors can conspire to raise the scores of longer documents, which \(at least for some information needs\) is unnatural_

Longer documents can broadly be lumped into two categories:
- verbose documents that essentially repeat the same content – in these, the length of the document does not alter the relative weights of different terms
- documents covering multiple different topics, in which th esearch terms probably match small segments of the document but not all of it – in this case, the relative weights of terms are quite different from a single short document that matches the query terms

**pivoted document length normalization** : we compute the dot product score between a \(unit\) query vector and a normalized document, the score is skewed to account for the effect of document length on relevance

**probability of relevance** :  a function of document length, averaged over all queries in an ensemble

### Chapter 16.4 K\-means

- K\-means is the most important flat clustering algorithm
- Its objective is tominimize the average squared Euclidean distance of documents from their cluster centers where a cluster center is defined as the mean or centroid μ of the documents in a cluster ω:

μ\(ω\) = \(1/\|ω\|\)∑x for x∈ω

- The definition assumes that documents are represented as length\-normalized vectors in a real\-valued space in the familiar way
- The ideal cluster  in K\-means is a sphere with the centroid as its center  of gravity
- Ideally, the clusters should not overlap

**residual sum of squares** : the squared distance of each vector from its centroid summed over all vectors

RSS<sub>k</sub> = ∑\|x\−μ\(ω<sub>k</sub>\)\|<sup>2</sup> for x∈ω<sub>k</sub>

- RSS is the objective function inK-means and our goal is to minimize it
- Since N is fixed, minimizing RSS is equivalent to minimizing the average squared distance, a measure of how well centroids represent their documents

#### Working with K\-means

- The first step of K\-means is to select as initial cluster centers K randomly selected documents, the _seeds_
- The algorithm then moves the cluster centers around in space in order to minimize RSS
- This is done iteratively by repeating two steps until a stopping criterion is met: reassigning documents to the cluster with the closest centroid; and recomputing each centroid based on the current members of its cluster

We can apply one of the following termination conditions:
- A fixed number of iterationsIhas been completed.  This condition limits the runtime of the clustering algorithm, but in some cases the quality of the clustering will be poor because of an insufficient number of iterations
- Assignment of documents to clusters \(the partitioning function γ\) doesnot change  between iterations. Except for cases with a bad local minimum, this produces a good clustering, but runtimes may be unacceptably long
- Centroids μ<sub>k</sub> do not change between iterations. This is equivalent to γ not changing 
- Terminate when RSS falls below a threshold. This criterionensures thatthe  clustering is of a desired quality after termination
- Terminate when the decrease in RSS falls below a threshold θ. For small θ,this indicates that we are close to convergence. Again, we need to combine it with a bound on the number of iterations to prevent very long runtimes

**refer to 16.8 \- 16.10 for a proof that K\-means converges by proving that RSS monotonically decreases in each iteration**

- If a document set contains many outliers; documents that are far from any other documents and therefore do not fit well into any cluster then there is no guarantee that a global minimum in the objective function will be reached
- Frequently, if an outlier is chosen as an initial seed, then no other vector is assigned to it during subsequent iterations. Thus, we end up with a singleton cluster\(a cluster with only one document\)

Another type of suboptimal clustering that frequently occurs is one with empty clusters.

Effective heuristics for seed selection include:
- excluding outliers from the seed set
- trying out multiple starting points and choosing the clustering with lowest cost
- obtaining seeds from another method such as hierarchical clustering

_A robust method that works well for a large variety of document distributions is to select i \(e.g., i=10\) random vectors for each cluster and use their centroid as the seed for this cluster._

####  Time complexity of K\-means

- Most of the time is spent on computing vector distances, one such operation costs Θ\(M\)
- The reassignment step computes KN distances, so its overall complexity is Θ\(KNM\)
- In the recomputation step, each vector gets added to a centroid once, so the complexity of this step is Θ\(NM\)
- For a fixed number of iterations I, the overall complexity is therefore Θ\(IKNM\)

_Thus, K\-means is linear in all relevant factors: iterations, number of clusters, number of vectors and dimensionality of the space_

- In most cases, K\-means quickly reaches either complete convergence or a clustering that is close to convergence
- In the latter case, a few documents would switch membership if further iterations were computed, but this has a small effect on the overall quality of the clustering

**K\-medoids** : a variant of K\-means that computes medoids instead  of centroids as cluster centers

_medoid_ : the document vector that is closest to the centroid

#### Cluster cardinality in K\-means

**A heuristic method to guess K through minimizing RSS**

- We first perform i\(e.g., i=10\) clusterings with K clusters \(each with a different initialization\) and compute the RSS of each
- Then we take the minimum of the i RSS values \(RSS<sub>min</sub>\(K\)\)
- Now we can inspect the values RSS<sub>min</sub>\(K\) as K increases and find the “knee” in the curve – the point where successive decreases in RSS<sub>min</sub> become noticeably smaller

- A second type of criterion for cluster cardinality imposes a penalty for each new cluster 
- we start with a single cluster containing all documents and then search for the optimal number of clusters K by successively incrementing K by one

 To determine the cluster cardinality in this way, we create a generalized objective function that combines two elements:
 - distortion, a measure of how much documents deviate from the prototype of their clusters \(e.g., RSS for K\-means\)
 - a measure of,model complexity, We interpret a clustering here as a model of the data
 - Model complexity in clustering is usually the number of clusters or a function thereof

 For K\-means, we then get this selection criterion for K:

 K = arg min\[RSS<sub>min</sub>\(K\) + λK\]

 where λ is a weighting factor. 

 _A large value of λ favors solutions with few clusters.  For λ=0, there is no penalty for more clusters and K=N is the best solution._

 - In some cases, we can choose values of λ that have worked well for similar data sets in the past
 - For example, if we periodically cluster news stories from a newswire, there is likely to be a fixed value of λ that gives usthe right K in each successive clustering

**Akaike Information Criterion** : an  information\-theoretic measure that trades off distortion against model complexity

The general form of AIC is:

K = arg minK\[\−2L\(K\) + 2q\(K\)\]

- where −L\(K\), the negative maximum log\-likelihood of the data for K clusters, is a measure of distortion
- q\(K\),  the number of parameters of a model with K clusters, is a measure of model complexity

- The first property of a good model of the data is that each data point is modeled well by the model

- The derivation of AIC is based on a number of assumptions e.g the data are independent and identically distributed
- These assumptions are only approximately true for data sets in information retrieval
- As a consequence, the AIC can rarely be applied without modification in text clustering

## Week 3

### Chapter 3: N\-gram Language Models

- A probabilistic model of word sequences could suggest that briefed reporters on is a more probable English phrase than briefed to reporters \(which has an awkward to after briefed\) or introduced reporters to\(which uses a verb that is less fluent English in this context\)
- Probabilities are also important for augmentative and alternative communication systems
- People often use such AAC devices if they are physically unable to speak or sign but can instead use eye gaze or other specific movements to select words from a menu to be spoken by the system. Word prediction can be used to suggest likely words for the menu
- Models that assign probabilities to sequences of words are called language models or LMs

**n-gram** : An n\-gram is a sequence of n words used to assign probabilities to sentences and sequences

#### N\-Grams

P\(w\|h\) : the probability of a word w given some history h

One way to estimate this probability is from relative frequency counts:  
- take avery large corpus
- count the number of times we see 'its water is so transparent that
- count the number of times this is followed by 'the' 
- This would be answering the question “Out of the times we saw the history h, how many times was it followed bythe word w”, as follows:  

P\(the\|its water is so transparent that\) = C\(its water is so transparent that the\) / C\(its water is so transparent that\)

- While this method of estimating probabilities directly from counts works fine in many cases, it turns out that even the web isn’t big enough to give us good estimates in most cases
- This is because language is creative; new sentences are created all the time, and we won’t always be able to count entire sentences
- If we wanted to know the joint probability of an entire sequence of words like its water is so transparent, we could do it by asking “out of all possible sequences of five words, how many of them are its water is so transparent?”

- We’ll need to introduce more clever ways of estimating the probability of a word w given a history h, or the probability of an entire word sequence W
- To represent the probability of a particular random variable X<sub>i</sub> taking on the value “the”, or P\(X<sub>i</sub>=“the”\), wewill use the simplification P\(the\)
- We’ll represent a sequence of N words either as w<sub>1</sub>...w<sub>n</sub> or w<sub>1:n</sub>
- For thejoint probability of each word in a sequence having a particular value P\(X=w<sub>1</sub>,Y=w<sub>2</sub>,Z=<sub>3</sub>,...,W=w<sub>n</sub>\) we’ll use P\(w<sub>1</sub>,w<sub>2</sub>,...,w<sub>n</sub>\)

**chain rule of probability:**

P\(X<sub>1</sub>...X<sub>n</sub>\) = ∏ P\(X<sub>k</sub>\|X<sub>1:k−1</sub>\) for k in range 1 to n

- The chain rule shows the link between computing the joint probability of a sequence and computing the conditional probability of a word given previous words
- We don’t know any way to compute the exact probability of a word given a long sequence of preceding words

_The intuition of the n\-gram model is that instead of computing the probability of a word given its entire history, we can approximate the history by just the last few words_

- The bigram model, for example, approximates the probability of a word given all the previous words by using only the conditional probability of the preceding word

- The assumption that the probability of a word depends only on the previous word is called a Markov assumption
- Markov models are the class of probabilistic models Markov that assume we can predict the probability of some future unit without looking too far into the past

The general equation for this n\-gram  approximation to the conditional probability of the next word in a sequence is:

P\(w<sub>n</sub>\|w<sub>1:n−1</sub>\) ≈ P\(w<sub>n</sub>\|w<sub>n−N+1:n−1</sub>\)

Given the bigram assumption for the probability of an individual word, we can compute the probability of a complete word sequence by:

P\(w<sub>1:n</sub>\) ≈ ∏ P\(w<sub>k</sub>\|w<sub>k−1</sub>\)

- An intuitive way to estimate probabilities is called maximum likelihood estimation or MLE
- We get the MLE estimate for the parameters of an n\-gram model by getting counts from a corpus, and normalizing the counts so that they lie between 0 and 1

We’ll compute the count of the bigram C\(xy\) and normalize by the sum of all the bigrams that share the same first word x:

P\(w<sub>n</sub>\|w<sub>n−1</sub>\) = C\(w<sub>n−1</sub>w<sub>n</sub>\) / C\(w<sub>n−1</sub>\)

**relative frequency** : estimates the n\-gram probability by dividing the observed frequency of a particular sequence by the observed frequency of a prefix

- We always represent and compute language model probabilities in log format as log probabilities. Since probabilities are less than or equal to 1,  the more probabilities we multiply together, the smaller the product becomes
- Multiplying enough n\-grams together would result in numerical underflow
- By usinglog probabilities instead of raw probabilities, we get numbers that are not as small
- Adding in log space is equivalent to multiplying in linear space, so we combine log probabilities by adding them

#### Evaluating Language Models

- The best way to evaluate the performance of a language model is to embed it in an application and measure how much the application improves
 - Such end\-to\-end evaluation is called extrinsic evaluation
- Extrinsic evaluation is the only way to know if a particular improvement in a component is really going to help the task at hand
- Thus, for speech recognition, we can compare the performance of two language models by running the speech recognizer twice, once with each language model, and seeing which gives the more accurate transcription

_This is expensive._

- Instead, it would be nice to have a metric that can be used to quickly evaluate potential improvements in a language mode
 - An intrinsic evaluation metric is one that measures the quality of a model independent of any application
- For an intrinsic evaluation of a language model we need a test set
- As with man yof the statistical models in our field, the probabilities of an n\-gram model come from the corpus it is trained on, the training set or training corpus
- We can then measure the quality of an n\-gram model by its performance on some unseen data called the test set or test corpus

_Whichever model assigns a higher probability to the test set, meaning it more accurately predicts the test set, is a better model._

-  Given two probabilistic models, the better model is the one that has a tighter fit to the test data or that better predicts the detailsof the test data, and hence will assign a higher probability to the test data
- Training on the test set introduces a bias that makes the probabilities all look too high, and causes huge inaccuracies in perplexity, the probability\-based metric we introduce below

- We call the initial test set the development test set or, dev set
- In practice, we often just divide our data into 80% training, 10% development, and 10% test

#### Perplexity

- In practice we don’t use raw probability as our metric for evaluating language models, but a variant called perplexity
 - The perplexity \(sometimes called PP for short\) of a language model on a test set is the inverse probability of the test set, normalized by the number of words

- Note that because of the inverse, the higher the conditional probability of the word sequence, the lower the perplexity
- Thus, minimizing perplexity is equivalent to maximizing the test set probability according to the language model

_Since this sequence will cross many sentence boundaries, we need to include the begin\- and end\-sentence markers<\s\>and</\s\>in the probability computation. We also need to include the end-of-sentence marker</\s\>\(but not the beginning-of-sentence marker<\s\>\) in the total count of word tokens N._

- There is another way to think about perplexity: as the weighted average branching factor of a language
 - The branching factor of a language is the number of possible next words that can follow any word

- An \(intrinsic\) improvement in perplexity does not guarantee an \(extrinsic\) improvement in the performance of a language processing task like speech recognition or machine translation
- Nonetheless, because perplexity often correlates with such improvements, it is commonly used as a quick check on an algorithm
- But a model’s improvement in perplexity should always be confirmed by an end\-to\-end evaluation of a real task before concluding the evaluation of the model

#### Generalization and Zeros

- The n\-gram model, like many statistical models, is dependent on the training corpus
- One implication of this is that the probabilities often encode specific facts about a given training corpus
- Another implication is that n\-grams do a better and better job of modeling the training corpus as we increase the value of N

- We can visualize both of these facts by generating random sentences from different n\-gram  models
 - It’s simplest to visualize how this works for the unigram case:

- Imagine all the words of the English language covering the probability space between 0 and 1, each word covering an interval proportional to its frequency
- We choose a random value between 0 and 1 and print the word whose interval includes this chosen value
- We continue choosing random numbers and generating words until we randomly generate the sentence\-final token </\s\>
- We can use the same technique to generate bigrams by first generating a random bigram that starts with <\s\>
 - Let’s say the second word of that bigram is w
- We next chose a random bigram starting with w, and so on

- The longer the context on which we train the model, the more coherent the sentences
- In the unigram sentences, there is no coherent relation between words or any sentence\-final punctuation
- The bigram sentences have some local word\-to\-word coherence \(especially if we consider that punctuation counts as a word\)

**sparsity** 

- For any n\-gram that occurred a sufficient number of times, we might have a good estimate of its probability
- But because any corpus is limited, some perfectly acceptable English word sequences are bound to be missing from it
- That is, we’ll have many cases of putative “zero probability n\-grams” that should really have some non\-zero probability

#### Unknown Words

- The previous section discussed the problem of words whose bigram probability is zero
- But what about words we simply have never seen before?

- Sometimes we have a language task in which this can’t happen because we know all the words that can occur
- In such a closed vocabulary system the test set can only contain words from this lexicon, and there will be no unknown words

_This is a reasonable assumption in some domains, such as speech recognition or machine translation, where we have a pronunciation dictionary or a phrase table that are fixed in advance, and so the language model can only use the words in that dictionary or phrase table._

- An open vocabulary system is one in which we model these potential unknown words in the test set by adding a pseudo-word called <UNK\>

There are two common ways to train the probabilities of the unknown word model <UNK\>:

- The first one is to turn the problem back into a closed vocabulary oneby choosing a fixed vocabulary in advance
 - Choose a vocabulary\(word list\) that is fixed in advance
 - Convert in the training set any word that is not in this set \(any OOV word\) to the unknown word token <UNK\> in a text normalization step
 - Estimate the probabilities for <UNK\> from its counts just like any other regular word in the training set

- The second alternative, in situations where we don’t have a prior vocabulary in advance, is to create such a vocabulary implicitly, replacing words in the training data by <UNK\>based on their frequency
 - For example we can replace by <UNK\> all words that occur fewer than n times in the training set, where n is some small number, or equivalently select a vocabulary size V in advance \(say 50,000\) and choose the top V words by frequency and replace the rest by UNK

#### Smoothing

- What do we do with words that are in our vocabulary but appear in a test set in an unseen context?
- To keep a language model from assigning zero probability to these unseen events, we’ll have to shave off a bit of probability mass from some more frequent events and give it to the events we’ve never seen
- This modification is called smoothing or discounting

#### Laplace Smoothing

- The simplest way to do smoothing is to add one to all the bigram counts,  before we normalize them into probabilities
- All the counts that used to be zero will nowhave a count of 1, the counts of 1 will be 2, and so on

_Laplace smoothing does not perform well enough to be used in modern n\-gram models, but it usefully introduces many of the concepts that we see in other smoothing algorithms, gives a useful baseline, and is also a practical smoothing algorithm for other tasks liketext classification._

Recall that the unsmoothed maximum likelihood estimate of the unigram probability of the word w<sub>i</sub> is its count c<sub>i</sub> normalized by the total number of word tokens N:

P\(w<sub>i</sub>\) = c<sub>i</sub> / N

- Laplace smoothing merely adds one to each count
- Since there are V words in the vocabulary and each one was incremented, we also need to adjust the denominator to take into account the extra V observations

P<sub>Laplace</sub>\(w<sub>i</sub>\) = \(c<sub>i</sub> + 1\) / \(N \+ V\)

- Instead of changing both the numerator and denominator, it is convenient to describe how a smoothing algorithm affects the numerator, by defining an adjusted count c<sup>∗</sup>
- This adjusted count is easier to compare directly with the MLE counts andcan be turned into a probability like an MLE count by normalizing by N

To define this count, since we are only changing the numerator in addition to adding 1 we’ll also need to multiply by a normalization factor:

c<sup>∗</sup><sub>i</sub> = \(c<sub>i</sub> \+ 1\) \* \(N / N \+ V\)

We can now turn c<sup>∗</sup><sub>i</sub> into a probability P<sup>∗</sup><sub>i</sub> by normalizing by N

- A related way to view smoothing is as discounting\(lowering\) some non\-zero discounting counts in order to get the probability mass that will be assigned to the zero counts
- Thus, instead of referring to the discounted counts c<sup>∗</sup>, we might describe a smoothing algorithm in terms of a relative discount d<sub>c</sub>,  the ratio of the discounted countsdiscountto the original counts:

d<sub>c</sub> = c<sup>∗</sup> / c

A sharp change in counts and probabilities occurs because too much probability mass is moved to all the zeros

#### Add\-k Smoothing

- One alternative to add\-one smoothing is to move a bit less of the probability mass from the seen to the unseen events
- Instead of adding 1 to each count, we add a fractional count k

P<sup>\*</sup><sub>Add\-k</sub>\(w<sub>n</sub> \| w<sub>n\-1</sub>\) = \[C\(w<sub>n\-1</sub>w<sub>n</sub>\) \+ k\] / \[C\(w<sub>n\-1</sub>\) + kV\]

- Add\-k smoothing requires that we have a method for choosing k; this can be done, for example, by optimizing on a dev set
- It it still doesn’t work well for language modeling, generating counts with poor variances and often inappropriate discounts

####  Backoff and Interpolation

- Sometimes using less context is a good thing, helping to generalize more for contexts that the model hasn’t learned much about
- In backoff, we use the trigram if the evidence is sufficient, otherwise we use the bigram, otherwise the unigram. In other words, we only “back off” to a lower\-order n\-gram if we have zero evidence for a higher\-order n\-gram
- In interpolation, we always mix the probability estimates from all the n\-gram estimators, weighing and combining the trigram, bigram, and unigram counts

- In simple linear interpolation, we combine different order n\-grams by linearly interpolating all the models
- Thus, we estimate the trigram probability by mixing together the unigram, bigram, and trigram probabilities, each weightedby a λ

- In a slightly more sophisticated version of linear interpolation, each λ weight is computed by conditioning on the context
- This way, if we have particularly accurate counts for a particular bigram 
- Assume that the counts of the trigrams based on this bigram will be more trustworthy, so we can make the λs for those trigrams higher and thus give that trigram more weight in the interpolation
- Both the simple interpolation and conditional interpolation λs are learned from a held\-out corpus
- A held\-out corpus is an additional training corpus that we use to set hyperparameters like these λ values, by choosing the λ values that maximize the likelihood of the held\-out corpus

- In a backoff n\-gram model, if the n\-gram we need has zero counts, we approx-mate it by backing off to the \(N\-1\)\-gram
- We continue backing off until we reach a history that has some counts
- In order for a backoff model to give a correct probability distribution, we have to discountthe higher\-order n\-grams to save some probability mass for the lower order n\-grams
- Just as with add\-one smoothing, if the higher\-order n\-grams aren’t discounted and we just used the undiscounted MLE probability, then as soon as we replaced an n\-gram which has zero probability with a lower\-order n\-gram, we would be adding probability mass
 - the total probability assigned to all possible strings by the language model would be greater than 1
- In addition to this explicit discount factor, we’ll need a function α to distribute this probability mass to the lower order n\-grams

- This kind of backoff with discounting is also called Katz backoff
 - In Katz backoff we rely on a discounted probability P<sup>∗</sup> if we’ve seen this n\-gram before 
 - Otherwise, we recursively back off to the Katz probability for the shorter\-history \(N\-1\)\-gram

- Katz backoff is often combined with a smoothing method called Good\-Turing
- The combined Good\-Turing backoff algorithm involves quite detailed computation for estimating the Good\-Turing smoothing and the P<sup>∗</sup> and α values

#### Kneser\-Ney Smoothing

- One of the most commonly used and best performing n\-gram smoothing methodsis the interpolated Kneser\-Ney algorithm 
- Kneser-Ney has its roots in a method called absolute discounting
 - Recall that discounting of the counts for frequent n\-grams is necessary to save some probability mass for the smoothing algorithm to distribute to the unseen n\-grams

- Consider an n\-gram that has count 4
 - We need to discount this count by some amount
 - look at a held\-out corpus and just see what the count is for all those bigrams that had count4 in the training set

- Absolute discounting formalizes this intuition by subtracting a fixed \(absolute\) discount d from each count
- The intuition is that since we have good estimates already for the very high counts, a small discount d won’t affect them much
- It will mainly modify the smaller counts, for which we don’t necessarily trust the estimate anyway

Kneser-Ney discounting augments absolute discounting with a more sophisticated way to handle the lower\-order unigram distribution.

The Kneser-Ney intuition is to base our estimate of P<sub>CONTINUATION</sub> on the number of different contexts word w has appeared in, that is, the number of bigram types it completes. Every bigram type was a novel continuation the first time it was seen. We hypothesize that words that have appeared in more contexts in the past are more likely to appear in some new context as well.

#### Huge Language Models and Stupid Backoff

- Efficiency considerations are important when building language models that use large sets of n\-grams
- Rather than store each word as a string, it is generally represented in memory as a 64\-bit hash number, with the words themselves stored on disk
- Probabilities are generally quantized using only 4\-8 bits \(instead of 8\-byte floats\), and n\-grams are stored in reverse tries
- N\-grams can also be shrunk by pruning, for example only storing n\-grams with counts greater than some threshold

- Stupid backoff gives up the idea of trying to make the language a true probability distribution
- There is no discounting of the higher\-order probabilities
- If a higher\-order n\-gram has a zero count,  we simply backoff to a lower order n\-gram, weighed by a fixed \(context\-independent\) weight

#### Advanced: Perplexity’s Relation to Entropy

The perplexity measure actually arises from the information\-theoretic concept of cross\-entropy, which explains otherwise mysterious properties of perplexity \(why the inverse probability, for example?\) and its relationship to entropy.

- Entropy is a measure of information
 - One intuitive way to think about entropy is as a lower bound on the number of bits it would take to encode a certain decision or piece of information in the optimal coding scheme

- We can take a single sequence that is long enough instead of summing over all possible sequences
- The intuition of the Shannon\-McMillan\-Breiman theorem is that a long enough sequence of words will contain in it many other shorter sequences and that each of these shorter sequences will reoccur in the longer sequence according to their probabilities
- A stochastic process is said to be stationary if the probabilities it assigns to a sequence are invariant with respect to shifts in the time index

_In other words, the probability distribution for words at time t is the same as the probability distribution at time t \+ 1.  Markov models, and hence n\-grams, are stationary._

_To summarize, by making some incorrect but convenient simplifying assumptions, we can compute the entropy of some stochastic process by taking a very long sample of the output and computing its average log probability._

**Cross-entropy** : draws sequences according to the probability distribution p, but sum the log of their probabilities according to m \(a model of p\).

This means that, as for entropy, we can estimate the cross-entropy of a model m on some distribution p by taking a single sequence that is long enough instead of summing over all possible sequences.

## Week 4
### Reading

### Chapter 4: Naive Bayes and Sentiment Classification

**text categorization** : the task of assigning a label or category to an entire text or document

**sentiment analysis** : the extraction of sentiment

_sentiment_ :  the positive or negative orientation that a writer expresses toward some object

* The simplest version of sentiment analysis is a binary classification task
* the words of a text provide excellent cues
* Words like great, richly, awesome, and pathetic, and awful and ridiculously are very informative cues

**Spam detection** :  the binary classification task of assigning an email to one of the two classes spam or not\-spam

**language id** : Identifying the language\(s\) a text is written in

_Subject category classification is the task for which the naive Bayes algorithm was invented in 1961_

* Classification is essential for tasks below the level of the document as well
* We’ve already seen:
	* period disambiguation \(deciding if a period is the end of a sentence or part of a word\)
	* word tokenization \(deciding if a character should bea word boundary\)
* Even language modeling can be viewed as classification: 
	* each word can be thought of as a class, and so predicting the next word is classifying the context so far into a class for each next word
* A part\-of\-speech tagger classifies each occurrence of a word in a sentence as, e.g., a noun or a verb

* The goal of classification is:
	* to take a single observation
	* extract some useful features
	* and thereby classify the observation into one of a set of discrete classes
* One method for classifying text is to use handwritten rules
	* There are many areas of language processing where handwritten rule\-based classifiers constitute a state\-of\-the\-art system, or at least part of it

_Most cases of classification in language processing are done via supervised machine learning._

* In supervised machine learning, we have a data set of input observations, each associated with some correct output \(a ‘supervision signal’\)
* The goal of the algorithm is to learn how to map from a new observation to a correct output
* A probabilistic classifier additionally will tell us the probability of the observation being in the class
	* This full distribution over the classes can be useful information for downstream decisions
	* avoiding making discrete decisions early on can be useful when combining systems

_Many kinds of machine learning algorithms are used to build classifiers._

* Generative classifiers like naive Bayes build a model of how a class could generate some input data
	* Given an observation, they return the class most likely to have generated the observation
* Discriminative classifiers like logistic regression instead learn what features from the input are most useful to discriminate between the different possible classes
* While discriminative systems are often more accurate and hence more commonly used, generative classifiers still have a role

#### Naive Bayes Classifiers

**multinomial naive Bayes classifier** :  it is a Bayesian classifier that makes a simplifying \(naive\) assumption about how the features interact

* We represent a text document as if it were a bag\-of\-words, that is, an unordered set of words with their positions ignored, keeping only their frequency in the document
* Naive Bayes is a probabilistic classifier, meaning that for a documentd, out of all classes c∈C the classifier returns the class  ˆc which has the maximum posterior probability given the document
* ˆ represents the estimate of the correct class

**Bayes' Rule**

P\(x\|y\) = P\(y\|x\)P\(c\) / P\(y\)

ˆc = argmax P\(d\|c\)P\(c\) / P\(d\) for a class c and a document d

_As d is the same for all classes in a document we can remove these terms from the equation._

ˆc = argmax P\(d\|c\)P\(c\)

* We call Naive Bayes a generative model because we can read the above equation as stating a kind of implicit assumption about how a document is generated
	* first a class is sampled from P\(c\)
	* then the words are generated by sampling from P\(d\|c\)

* We compute the most probable class ˆcgiven some document d by choosing the class which has the highest product of two probabilities:
	* the prior probability of the class P\(c\)
	* the likelihood of the document P\(d\|c\)
* Without loss of generalization, we can represent a document d as a set of features

* Naive Bayes classifiers make two simplifying assumptions:
	* we assume position doesn’t matter, and that the word “love” has the same effect on classification whether it occurs as the 1<sup>st</sup>, 20<sup>th</sup>, or last word in the document
	* The second is commonly called the **naive Bayes assumption**

This is the conditional independence assumption that the probabilities P\(f<sup>i</sup>\|c\)are independent giventhe classcand hence can be ‘naively’ multiplied as follows:

P\(f<sup>1</sup>, f<sup>2</sup>, ..., f<sup>n</sup> \| c\) = P\(f<sup>1</sup>\|c\)·P\(f<sup>2</sup>\|c\)·...·P\(f<sup>n</sup>\|c\)

* To apply the naive Bayes classifier to text, we need to consider word positions, by simply walking an index through every word position in the document:
* positions ← all word positions in test document
* Naive Bayes calculations, like calculations for language modeling, are done in logspace, to avoid underflow and increase speed

C<sub>NB</sub> = argmax logP\(c\) \+ ∑ logP\(w<sub>i</sub>\|c\) for i∈positions

_Classifiers that use a linear combination of the inputsto make a classification decision — like naive Bayes and also logistic regression — are calledlinear classifiers._

#### Training the Naive Bayes Classifie

* How can we learn the probabilities P\(c\) and P\(f<sub>i</sub>\|c\)?
* Let’s first consider the maximum likelihood estimate
* We’ll simply use the frequencies in the data
* For the class prior P\(c\) we ask what percentage of the documents in our training set are in each class c
	* Let N<sub>c</sub> be the number of documents in our training data with class c and N<sub>doc</sub> be the total number of documents
	* Then:

ˆP\(c\) = N<sub>c</sub> / N<sub>doc</sub>

* To learn the probability P\(f<sub>i</sub>\|c\)
	* we’ll assume a feature is just the existence of a word in the document’s bag of words
	* so we’ll want P\(w<sub>i</sub>\|c\), which we compute as the fraction of times the word w<sub>i</sub> appears among all words in all documents of topic c
* We first concatenate all documents with category c into one big “category c” text
* Then we use the frequency of w<sub>i</sub> in this concatenated document to give a maximum likelihood estimate of the probability: 

ˆP\(w<sub>i</sub>\|c\) = count\(w<sub>i</sub>\|c\) / ∑ count\(w,c\) for w∈V

* Here the vocabulary V consists of the union of all the word types in all classes, not just the words in one class c
* There is a problem, however, with maximum likelihood training
	* Imagine we are trying to estimate the likelihood of the word “fantastic” given class positive
	* but suppose there are no training documents that both contain the word “fantastic” and are classified as positive
	* Perhaps the word “fantastic” happens to occur \(sarcastically?\)  in the class negative
	* In this case the probability for this featire will be zero

_But since naive Bayes naively multiplies all the feature likelihoods together, zero probabilities in the likelihood term for any class will cause the probability of the class to be zero, no matter the other evidence!_

* The simplest solution is the add\-one \(Laplace\) smoothing
	* While Laplace smoothing is usually replaced by more sophisticated smoothing algorithms in language modeling, it is commonly used in naive Bayes text categorization:

ˆP\(w<sub>i</sub>\|c\) = count\(w<sub>i</sub>\|c\) \+ 1 / ∑ count\(w,c\) \+ \|V\| for w∈V

* What do we do about words that occur in our test data but are not in our vocabulary at all because they did not occur in any training document in any class? 
	* The solution for such unknown words is to ignore them — remove them from the test document and not include any probability for them at all
* Finally, some systems choose to completely ignore another class of words:
	* **stop words** : very frequent words like the and a
	* This can be done by sorting the vocabulary by frequency in the training set, and defining the top 10–100 vocabulary entries as stop words

#### Optimizing for Sentiment Analysis

* For sentiment classification and a number of other text classification tasks
	* whether a word occurs or not seems to matter more than its frequency
	* Thus it often improves performance to clip the word counts in each document at 1 
	* This variant is called binary multinomial naive Bayes or binary NB
* The variant uses the same equation except that for each document we remove all duplicate words before concatenating them into the single big document

* A very simple baseline that is commonly used in sentiment analysis to deal with negation is the following: 
	* during text normalization,  prepend the prefix NOT to every word after a token of logical negation until the next punctuation mark
	* Newly formed ‘words’ like NOTlike, NOTrecommend will thus occur more often in negative document and act as cues for negative sentiment
	* while words like NOTbored, NOTdismiss will acquire positive associations

* Finally, in some situations we might have insufficient labeled training data to train accurate naive Bayes classifiers using all words in the training set to estimate positive and negative sentiment
	* In such cases we can instead derive the positive and negative word features from sentiment lexicons  
	_sentiment lexicons_ :  lists of words that are pre\-annotated with positive or negative sentiment  
	* A common way to use lexicons in a naive Bayes classifier is to add a feature that is counted whenever a word from that lexicon occurs
	* Thus we might add a feature called ‘this word occurs in the positive lexicon’, and treat all instances of words in the lexicon as counts for that one feature
	* Similarly,  we might add as a second feature ‘this word occurs in the negative lexicon’ of words in the negative lexicon
* If we have lots of training data, and if the test data matches the training data, using just two features won’t work aswell as using all the words
* But when training data is sparse or not representative ofthe test set, using dense lexicon features instead of sparse individual\-word features may generalize better

#### Naive Bayes as a Language Model

* A naive Bayes model can be viewed as a set of class\-specific unigram language models, in which the model for each class instantiates a unigram language model
* Since the likelihood features from the naive Bayes model assign a probability to each word P\(word\|c\), the model also assigns a probability to each sentence:

P\(s\|c\) = ∏ P\(w<sub>i</sub>\|c\)

#### Evaluation: Precision, Recall, F\-measure

**gold labels** : the human\-defined labels for each document that we are trying to match
 
* To evaluate any system for detecting things, we start by building a confusion matrix  
_confusion matrix_ : a table for visualizing how an algorithm performs with respect to the human gold labels, using two dimensions \(system output and gold labels\), and each cell labeling a set of possible outcomes  
* Instead of accuracy we generally turn to two other metrics precision and recall
	* Precision measures the percentage of the items that the system detected \(i.e., the system labeled as positive\) that are in fact positive \(i.e.,are positive according to the human gold labels\)
	* Precision is defined as:  
	Precision = true positives / true positives \+ false positives  
	* Recall measures the percentage of items actually present in the input that were correctly identified by the system
	* Recall is defined as:  
	Recall = true positives / true postives \+ false negatives

* There are many ways to define a single metric that incorporates aspects of both precision and recall
* The simplest of these combinations is the F\-measure defined as:  
F<sub>β</sub> = \(β<sup>2</sup>\+1\)PR / β<sup>2</sup>P \+ R  
* The β parameter differentially weights the importance of recall and precision, based perhaps on the needs of an application
* Values of β > 1 favor recall, while values of β < 1 favor precision
* When β=1, precision and recall are equally balanced; this is the most frequently used metric, and is called F<sub>β=1</sub> or just F<sub>1</sub>:  
F<sub>1</sub> = 2PR / P \+ R  
* F\-measure comes from a weighted harmonic mean of precision and recall
	* The harmonic mean of a set of numbers is the reciprocal of the arithmetic mean of reciprocals
* Harmonic mean is used because it is a conservative metric
* The harmonic mean oftwo values is closer to the minimum of the two values than the arithmetic mean is
* Thus it weighs the lower of the two numbers more heavily

#### Evaluating with more than two classes

* For sentiment analysis we generally have 3 classes \(positive, negative, neutral\)

**macroaveraging** : the performance for each class, and then average over classes

**microaveraging** : the decisions for all classes into a single confusion matrix, and then compute precision and recall from that table

_A microaverage is dominated by the more frequent class since the counts are pooled._

#### Test sets and Cross\-validation

* The training and testing procedure for text classification follows what we saw with language modeling 
	* we use the training set to train the model
	* then use the development test set\(also called a devset\) to perhaps tune some parameters
	* decide what the best model is
* Once we come up with what we think is the best model, we run it on the \(hitherto unseen\) test set to report its performance

* While the use of a devset avoids overfitting the test set having a fixed training set, devset, and test set creates another problem:
	* in order to save lots of data for training, the test set \(or devset\) might not be large enough to be representative
* Wouldn’t it be better if we could somehow use all our data for training and still use all our data for test?
* We can do this by cross\-validation: 
	* we randomly choose a cross\-validation training and test set division of our data
	* train our classifier
	* then compute the error rate on the test set
	* Then we repeat with a different randomly selected training set and test set
	* We do this sampling process 10 times and average these 10 runs toget an average error rate
	* This is called 10\-fold cross\-validation
* The only problem with cross\-validation is that because all the data is used for testing
	*  we need the whole corpus to be blind
	* we can’t examine any of the data to suggest possible features and in general see what’s going on
	* because we’d be peeking at the test set
	* and such cheating would cause us to overestimate the performance of our system

#### Statistical Significance Testing

* Suppose we’re comparing the performance of classifiers A and B on a metric M such as F<sub>1</sub>, or accuracy
* Perhaps we want to know if our logistic regression sentiment classifier A gets a higher F<sub>1</sub> score than our naive Bayes sentiment classifier B on a particular test set x
* Let’s call M\(A,x\) the score that system A gets on test set x, and δ\(x\) the performance difference between A and B on x:  
δ\(x\) = M\(A,x\)−M\(B,x\)  
* We would like to know if δ\(x\)>0, meaning that our logistic regression classifierhas a higher F<sub>1</sub> than our naive Bayes classifier on X
* δ\(x\) is called the effect size
	* a bigger δ means that A seems to be way better than B
	* a small δ means A seems to be only a little better

* A might just be accidentally better than B on A particular x
* we want to know if A’s superiority over B is likely to hold again if we checked another test set x′
* In the paradigm of statistical hypothesis testing, we test this by formalizing two hypotheses:
	H<sub>0</sub> : δ\(x\)≤0
	H<sub>1</sub> : δ\(x\)>0  
* The hypothesis H<sub>0</sub>, called the null hypothesis, supposes that δ\(x\) is actually negative or zero, meaning that A is not better than B
* We would like to know if we can confidently rule out this hypothesis, and instead support H<sub>1</sub>, that A is better
	* We do this by creating a random variable X ranging over all test sets
	* Now weask how likely is it, if the null hypothesis H<sub>0</sub> was correct, that among these test sets we would encounter the value of δ\(x\) that we found
* We formalize this likelihood as the p\-value:
	* the probability, assuming the null hypothesis H<sub>0</sub> is true, of seeing the δ\(x\) that we saw or one even greater
* A very small p\-value means that the difference we observed is very unlikely under the null hypothesis, and we can reject the null hypothesis

* There are two common non\-parametric tests used in NLP:
	* approximate randomization
	* bootstrap test
* Paired tests are those in which we compare two sets of observations that are aligned:
	* each observation in one set can be paired with an observation in another

#### The Paired Bootstrap Test

* The word bootstrapping refers to repeatedly drawing large numbers of smaller samples with replacement \(called bootstrap samples\) from an original larger sample
	* The intuition of the bootstrap test is that we can create many virtual test sets from an observed test set by repeatedly sampling from it
	* The method only makes the assumption that the sample is representative of the population

p\-value\(x\) = ∑ 1\(δ\(x<sup>\(i\)</sup>\)−δ\(x\)≥δ\(x\) for range \(i, b\) where b is the total number of samples

#### Avoiding Harms in Classification

_It is important to avoid harms that may result from classifiers, harms that exist both for naive Bayes classifiers and for the other classification algorithms._

**representational harms** : harms caused by a system that demeans a social group, for example by perpetuatingnegative stereotypes about them

* In other tasks classifiers may lead to both representational harms and other harms, such as censorship
	* For example the important text classification task of toxicity detectionis the task of detecting hate speech, abuse, harassment, or other toxicity detection kinds of toxic language
* While the goal of such classifiers is to help reduce societal harm, toxicity classifiers can themselves cause harms
	* For example, researchers have shown that some widely used toxicity classifiers incorrectly flag as being toxic sentences that are non\-toxic but simply mention minority  identities like women, blind people or gay people
	* Such false positive errors, if employed by toxicity detection systems without human oversight, could lead to the censoring of discourse by or about these groups

These problems can be caused by:   
* labels
* resources such as lexicons or pretrained embeddings
* model architecture

### Chapter 5: Logistic Regression

**logistic regression** : the base\-line supervised machine learning algorithm for classification

**neural network** : can be viewed as a series of logistic regression classifiers stacked on top of each other

_Logistic regression can be used to classify an observation into one of two classes, or into one of many classes._

* A generative model like naive Bayes makes use of a likelihood term, which expresses how to generate the features of a document if we knew it was of class c
* By contrast a discriminative model in this text categorization scenario attempts to directly compute P\(c\|d\)
	* Perhaps it will learn to assign a high weight to document features that directly improve its ability to discriminate between possible classes
	* even if it couldn’t generate an example of one of the classes

* Like naive Bayes, logistic regression is a probabilistic classifier that makes use of supervised machine learning
* Machine learning classifiers require a training corpus of m input/output pairs
* Components of a probabilistic machine learning classifier:
	* A feature representation of the input: For each input observation this will be a vector of features
	* A classification function that computes  ˆy, the estimated class, via p\(y\|x\). 
	* An objective function for learning, usually involving minimizing error on training examples
	* An algorithm for optimizing the objective function

* Logistic regression has two phases:
	* **training** : we train the system \(specifically the weights w and b\) using stochastic gradient descent and the cross\-entropy loss
	* **test** : Given a test examplex we compute p\(y\|x\) and return the higher probability label y=1 or y=0

#### Classification: the sigmoid

* The goal of binary logistic regression is to train a classifier that can make a binary decision about the class of a new input observation
* Here we introduce the **sigmoid classifier** that will help us make this decision
* Consider a single input observationx, which we will represent by a vector of features
	* The classifier output y can be 1 \(meaning the observation is a member of the class\) or 0 \(the observation is not a member of the class\)
	* We want to know the probability P\(y=1\|x\) that this observation is a member of the class
	* P\(y=1\|x\) is the probability that the document has positive sentiment
	* P\(y=0\|x\) is the probability that the document has negative sentiment

* Logistic regression solves this task by learning, from a training set, a vector of weights and a bias term
* Each weight w<sub>i</sub> is a real number, and is associated with one of the input features x<sub>i</sub>
* The weight w<sub>i</sub> represents how important that input featureis to the classification decision, and can be:
	* positive \(providing evidence that the instance being classified belongs in the positive class\)
	* negative \(providing evidencethat the instance being classified belongs in the negative class\)
* The bias term, also called the intercept, is another real number that’s added to the weighted inputs

* To make a decision on a test instance
	* after we’ve learned the weights in training
	* the classifier first multiplies each x<sub>i</sub> by its weight w<sub>i</sub>
	* sums up the weighted features, and adds the bias term b
	* The resulting single number z expresses the weighted sum of the evidence for the class

z = \(∑w<sub>i</sub>x<sub>i</sub> for i in range\(1, n\)\) \+ b

z = w·x\+b

* To create a probability, we’ll pass z through the sigmoid function σ\(z\)
* The sigmoid function is also called thelogistic function, and gives logistic regression its name
* The sigmoid has the following equation: 

y = σ\(z\) = 1 / 1\+e<sup>\-z</sup> = 1 / 1 \+ exp\(\-z\)

* The sigmoid has a number of advantages:
	* it takes a real\-valued number and maps it into the range \[0,1\]
	* Because it is nearly linear around 0 but flattens toward the ends, it tends to squash outlier values toward 0 or 1
	* it’s differentiable

P\(y=1\) = 1 / 1 \+ exp\(\-\(w·x\+b\)\)

P\(y=0\) = exp\(\-\(w·x\+b\)\) / 1 \+ exp\(\-\(w·x\+b\)\)

The sigmoin function has the property:  

1−σ\(x\) = σ\(−x\)

* For a test instance x, we say yes if the probability P\(y=1\|x\) is more than \.5, and no otherwise
	* We call \.5 the decision boundary

**Designing  features:**   
* Features are generally designed by examining the training set with an eye to linguistic intuitions and the linguistic literature on the domain
* A careful error analysis on the training set or devset of an early version of a system often provides insights into features
* For some tasks it is especially helpful to build complex features that are combinations of more primitive features
	* For logistic regression and naive Bayes these combination features or feature interactions have to be designed by hand
* For many tasks we'll need a large number of features
	* Often these are created automatically via feature templates, abstract specifications of features
* For example a bigram template for period disambiguation might create a feature for every pair of words that occurs before a period in the training set
	* Thus the feature space is sparse, since we only have to create a feature if that n\-gram exists in that position in the training set

**Choosing a classifier**  

* When there are many correlated features, logistic regression will assign a more accurate probability than naive Bayes
* So logistic regression generally works better on larger documents or datasets and is a common default

* naive Bayes can work extremely well \(sometimes even better than logistic regression\) on very small datasets or short documents
* Furthermore, naive Bayes is easy to implement and very fast to train \(there’s no optimization step\). So it’s still a reasonable approach to use in some situations

#### Learning in Logistic Regression

* What the system produces is ˆy, the system’s estimate of the true y
* We want to learn parameters \(meaning w and b\) that make ˆy for each training observation as close as possible to the true y
* This requires two components:
	* The first is a metric for how close the current label \( ˆy\) is to the true gold label y
	* Rather than measure similarity, we usually talk about the opposite of this: the distance between the system output and the gold output, and we call this distance the loss function or the cost function
	* The second thing we need is an optimization algorithm for iteratively updating the weights so as to minimize this loss function

#### The cross\-entropy loss function

* We need a loss function that expresses, for an observationx, how close the classifier output \(ˆy=σ\(w·x\+b\)\) is to the correct output \(y, which is 0 or 1\)
	* We call this:  
	L\(ˆy,y\) = How much  ˆy differs from the true y  
* We do this via a loss function that prefers the correct class labels of the training examples to be more likely
* This is called conditional maximum likelihood estimation:
	* we choose the parameters w,b that maximize the log probability of the true y labels in the training data given the observations x
	* Since there are only two discrete outcomes \(1 or 0\), this is a Bernoulli distribution, and we can express  the  probability p\(y\|x\) that our classifier produces for  one observation as the following:  
	p\(y\|x\) = ˆyy\(1−ˆy\)<sup>1−y</sup>  
	* Now we take the log of both sides:  
	logp\(y\|x\) = ylog ˆy \+ \(1−y\)log\(1−ˆy\)  
* Why does minimizing this negative log probability do what we want?
	* A perfect classifier would assign probability 1 to the correct outcome \(y=1 or y=0\) andprobability 0 to the incorrect outcome
	* That means the higher ˆy\(the closer it is to 1\), the better the classifier; the lower ˆyis \(the closer it is to 0\), the worse the classifier
	* The negative log of this probability is a convenient loss metric since it goes from 0 \(negative log of 1, no loss\) to infinity \(negative log of 0, infinite loss\)
* This loss function also ensures that as the probability of the correct answer is maximized, the probability of the incorrect answer is minimized
	* since the two sum to one, any increase in the probability of the correct answer is coming at the expense of the incorrect answer

#### Gradient Descent

* Our goal with gradient descent is to find the optimal weights: minimize the loss function we’ve defined for the model
* the loss function L is parameterized by the weights, which we’ll refer to in machine learning in general as θ \(in the case of logistic regression θ=w,b\)
* So the goal is to find the set of weights which minimizes the loss function, averaged over all examples:  
^θ = argmin 1 / m ∑L<sub>CE</sub>\(f\(x<sup>\(i\)</sup>;θ\), y<sup>\(i\)</sup>\)

* Gradient descentis a method that finds a minimum of a function by figuring out in which direction\(in the space of the parameters θ\) the function’s slope is rising the most steeply, and moving in the opposite direction
* For logistic regression, this loss function is conveniently convex
	* A convex function has just one minimum; there are no local minima to get stuck in, so gradient descent starting from any point is guaranteed to find the minimum
* The gradient of a function of many variables is a vector pointing in the direction of the greatest increase in a function
* The gradient is a multi\-variable generalization of the slope, so for a function of one variable we can informally think of the gradient as the slope

* The magnitude of the amount to move in gradient descent is the value of the sloped d/dw of f\(x;w\) weighted by a learning rate η
* A higher \(faster\) learning rate means that we should move w more on each step
* The change we make in our parameter is the learning rate times the gradient  

w<sup>t+1</sup> = w<sup>t</sup> − η d/dw of f\(x;w\)

#### The Stochastic Gradient Descent Algorithm

* The learning rate η is a hyperparameter that must be adjusted
	* If it’s too high, hyperparameter the learner will take steps that are too large, overshooting the minimum of the loss function
	*  If it’s too low, the learner will take steps that are too small, and take too long to get to the minimum
* It is common to start with a higher learning rate and then slowly decrease it, so that it is a function of the iteration k of training; the notation η<sub>k</sub> can be used to mean the value of the learning rate at iteration k

####  Mini\-batch training

* Stochastic gradient descent is called stochastic because it chooses a single random example at a time, moving the weights so as to improve performance on that single example
* That can result in very choppy movements, so it’s common to compute the gradient over batches of training instances rather than a single instance
* For example in batch training we compute the gradient over the entire dataset
	* By seeing so many examples, batch training offers a superb estimate of which direction to move the weights, at the cost of spending a lot of time processing every single example in the training set to compute this perfect direction
* A compromise is mini\-batch training: we train on a group of m examples \(per\-mini\-batchhaps 512, or 1024\) that is less than the whole dataset
* Mini\-batch training also has the advantage of computational efficiency
	* The mini\-batches can easily be vectorized, choosing the size of the mini\-batch based on the computational resources
	* This allows us to process all the examples in one mini\-batch in parallel and then accumulate the loss, something that’s not possible with individual or batch training

#### Regularization

* There is a problem with learning weights that make the model perfectly match the training data
* If a feature is perfectly predictive of the outcome because it happensto only occur in one class, it will be assigned a very high weight
* The weights for features will attempt to perfectly fit details of the training set, in fact too perfectly, modeling noisy factors that just accidentally correlate with the class
	* This problem is called overfitting
	* A good model should be able to generalize well from the training at a to the unseen test set, but a model that overfits will have poor generalization
* To avoid overfitting, a new regularization term R\(θ\) is added to the objective regularization function resulting in the following objective for a batch of m examples:  
^θ = argmax ∑ logP\(y<sup>\(i\)</sup>\|x<sup>\(i\)</sup>\) − αR\(θ\) for i in range\(1, m\)
* The new regularization term R\(θ\) is used to penalize large weights
* Thus a setting of the weights that matches the training data perfectly — but uses many weights with high values to do so — will be penalized more than a setting that matches the data a little less well, but does so using smaller weights
* There are two common ways to compute this regularization term R\(θ\)
	* L2 regularization is a quadratic function of the weight values, named because it uses the \(square of the\) L2 norm of the weight values
	* The L2 norm, \|\|θ\|\|<sub>2</sub>, is the same as the Euclidean distance of the vector θ from the origin  
	R\(θ\) = \|\|θ\|\|<sub>2</sub><sup>2</sup> = ∑θ<sub>j</sub><sup>2</sup> for j in range\(1, n\)  
	* L1 regularizationis a linear function of the weight values, named after the L1 norm \|\|W\|\|<sub>1</sub>, the sum of the absolute values of the weights, or Manhattan distance\(the Manhattan distance is the distance you’d have to walk between two points in a city with a street grid like New York\):  
	R\(θ\) = \|\|θ\|\|<sub>1</sub> = ∑\|θ<sub>i</sub>\| for i in range\(0,n\)

* These kinds of regularization come from statistics, where L1 regularization is called lasso regression
* L2 regularization is called ridge regression
* L2 prefers weight vectors with many small weights,
* L1 prefers sparse solutions with some larger weights but many more weights set to zero
	*  Thus L1 regularization leads to much sparser weight vectors, that is, far fewer features

* Both L1 and L2 regularization have Bayesian interpretations as constraints on the prior of how weights should look
* L1 regularization can be viewed as a Laplace prior on the weights
* L2 regularization corresponds to assuming that weights are distributed according to a Gaussian distribution with mean μ=0
* In a Gaussian or normal distribution, the further away a value is from the mean, the lower its probability \(scaled by the variance σ\)
* By using a Gaussian prior on the weights, we are saying that weights prefer to have the value 0

#### Multinomial logistic regression

* Sometimes we need more than two classes
* In such cases we use multinomial logistic regression, also called softmax regression \(or, historically, the maxent classifier\)
* In multinomial logistic regressionthe target y is a variable that ranges over more than two classes; we want to know the probability of y being in each potential class c∈C, p\(y=c\|x\)

* The multinomial logistic classifier uses a generalization of the sigmoid, called the softmax function, to compute the probabilityp \(y=c\|x\)
* The softmax function softmax takes a vector of k arbitrary values and maps them to a probability distribution, with each value in the range \(0,1\), and all the values summing to 1

#### Features in Multinomial Logistic Regression

* Features in multinomial logistic regression function similarly to binary logistic regression, with one difference that we’ll need separate weight vectors \(and biases\) for each of the K classes
* In binary classification a positive weight w<sub>5</sub> on a feature influences the classifier toward y=1 \(positive sentiment\) and a negative weight influences it toward y=0\(negative sentiment\) with the absolute value indicating how important the feature is
* For multinominal logistic regression, by contrast, with separate weights for each class, a feature can be evidence for or against each individual class

_In 3\-way multiclass sentiment classification, for example, we must assign each document one of the 3 classes \+,−, or 0 \(neutral\). Now a feature related to exclamation marks might have a negative weight for 0 documents, and a positive weight for \+ or \- documents._

#### Interpreting models

* Often we want to know more than just the correct classification of an observation
* We want to know why the classifier made the decision it did
* That is, we want our decision to be interpretable: the core idea is that as humans we should know why our algorithms reach the conclusions they do
* Logistic regression can be combined with statistical tests investigating whether a particular feature is significant by one of these tests, or inspecting its magnitude 
	* This can help us interpret why the classifier made the decision it makes

## Week 6
### Chapter 6: Vector Semantics and Embeddings

**distributional  hypothesis** : how words are distributed and similarity in what they mean

**vector semantics** : defines semantics & interprets word meaning to explain features such as word similarity

#### Lexical Semantics

##### Lemmas and Senses 

* Let’s start by looking at how one word \(we’ll choose mouse\) might be defined in a dictionary \(simplified from the online dictionary WordNet\):mouse \(N\)
	* any of numerous small rodents...
	* a hand\-operated device that controls a cursor...
* Here the form mouse is the lemma,  also called the citation form
* The form mouse would also be the lemma for the word mice; dictionaries don’t have separate definitions for inflected forms like mice
* In many languages the infinitive form is used as the lemma for the verb, so Spanish dormir “to sleep” is the lemma for duermes “you sleep”
* The specific forms sung or carpets or sing or duermes are called wordforms
* As the example above shows, each lemma can have multiple meanings; the lemma mouse can refer to the rodent or the cursor control device
* We call each of these aspects of the meaning of mouse a word sense

##### Synonymy

* One important component of word meaning is the relationship between word senses
	* For example when one word has a sense whose meaning is identical to a sense of another word, or nearly identical, we say the two senses ofthose two words are synonyms
* A more formal definition of synonymy \(between words rather than senses\) is that two words are synonymous if they are substitutable for one another in any sentence without changing thetruth conditions of the sentence, the situations in which the sentence would be true
	* We often say in this case that the two words have the same propositional meaning  
**principle of contrast** :  a difference in linguistic form is always associated with some difference in meaning  
* In practice, the word synonym is therefore used to describe a relationship of approximate or rough synonymy

**Word Similarity**  
* While words don’t have many synonyms, most words do have lots of similar words
	* Cat is not a synonym of dog, but cats and dogs are certainly similar words
* In moving from synonymy to similarity, it will be useful to shift from talking about relations between word senses \(like synonymy\) to relations between words \(like similarity\)
* The notion of word similarity is very useful in larger semantic tasks
	* Knowing how similar two words are can help in computing how similar the meaning of two phrases or sentences are, a very important component of natural language understanding tasks like question answering, paraphrasing, and summarization

##### Word Relatedness

* The meaning of two words can be related in ways other than similarity
	* One such class of connections is called word relatedness
* Consider the meanings of the words coffee and cup
	* Coffee is not similar to cup; they share practically no features \(coffee is a plant or a beverage, while a cup is amanufactured object with a particular shape\)
	* But coffee and cup are clearly related; they are associated by co\-participating in an everyday event \(the event of drinking coffee out of a cup\)
* One common kind of relatedness between words is if they belong to the same semantic field
	* A semantic field is a set of words which cover a particular semantic domain and bear structured relations with each other
* Semantic fields are also related to topic models, like Latent Dirichlet Allocation, LDA, which apply unsupervised learning on large sets of texts to induce sets of associated words from text

##### Semantic Frames and Roles

* Closely related to semantic fields is the idea of asemantic frame
	* A semantic frame is a set of words that denote perspectives or participants in a particular type of event
* Frames have semantic roles, and words in a sentence can take on these roles
* Being able to recognize such paraphrases is important for question answering, and can help in shifting perspective for machine translation

##### Connotation

* Finally, words have affective meanings or connotations
	* The word connotations has different meanings in different fields, but here we use it to mean the aspects of a word’s meaning that are related to a writer or reader’s emotions, sentiment, opinions, or evaluations
* Even words whose meanings are similar in other ways can vary in connotation; consider the difference in connotations between fake, knockoff, forgery, on the one hand, and copy, replica, reproductionon the other, or innocent\(positive connotation\) and naive\(negative connotation\)
* Positive or negative evaluation language is called sentiment and word sentiment plays a role in important sentiment tasks like sentiment analysis, stance detection, and applications of NLP to the language of politics and consumer reviews
* Early work on affective meaning found that words varied along three important dimensions of affective meaning:
	* valence: the pleasantness of the stimulus
	* arousal: the intensity of emotion provoked by the stimulus
	* dominance: the degree of control exerted by the stimulus

##### Vector Semantics

* Vectors semanticsis the standard way to represent word meaning in NLP, helping us model many of the aspects of word meaning we saw in the previous section
* We can use a point in three\-dimensional space to represent the connotation of a word, and the proposal by linguists to define the meaning of a word by its distribution in language use, meaning its neighboring words or grammatical environments
* The idea of vector semantics is to represent a word as a point in a multidimensional semantic space that is derived \(in ways we’ll see\) from the distributions of word neighbors
* Vectors for representing words are called embeddings

* In the tf\-idf model, an important baseline, the meaning of a word is defined by a simple function of the counts of nearby words
* We will see that this method results in very long vectors that are sparse
* We’ll introduce the word2vec model family for constructing short, dense vectors that have useful semantic properties
* We’ll also introduce the cosine, the standard way to use embeddings to compute semantic similarity, between two words, two sentences, or two documents, an important tool in practical applications like question answering, summarization, or automatic essay grading

#### Words and Vectors

* Vector or distributional models of meaning are generally based on a co\-occurrence matrix, a way of representing how often words co\-occur.

##### Vectors and documents

* In a term\-document matrix, each row represents a word in the vocabulary and each column represents a document from some collection of documents
* Each cell in this matrix represents the number of times a particular word \(defined by the row\) occurs in a particular document \(defined by the column\)
* To review some basic linear algebra, a vector is, at heart, just a list or array of vector numbers
* A vector space is a collection of vectors, characterized by their dimension
* The ordering of the numbers in a vector space indicates different meaningful dimensions on which documents vary
* We can think of the vector for a document as a point in \|V\|\-dimensional space; thus the documents are points in 4\-dimensional space
* Term\-document matrices were originally defined as a means of finding similar documents for the task of document information retrieval
* Two documents that are similar will tend to have similar words, and if two documents have similar words their column vectors will tend to be similar

* A real term\-document matrix, of course, wouldn’t just have 4 rows and columns, let alone 2
* More generally, the term\-document matrix has \|V\| rows \(one for eachword type in the vocabulary\) and D columns \(one for each document in the collection\); as we’ll see, vocabulary sizes are generally in the tens of thousands, and the number of documents can be enormous \(think about all the pages on the web\)
* Information retrieval \(IR\) is the task of finding the document d from the D information retrieval documents in some collection that best matches a query q
* For IR we’ll therefore also represent a query by a vector, also of length \|V\|, and we’ll need a way to compare two vectors to find how similar they are. \(Doing IR will also require efficient ways to store and manipulate these vectors by making use of the convenient fact that these vectors are sparse, i.e., mostly zeros\)

##### Words as vectors: document dimensions

An alternative to using the term\-document matrix to represent words as vectors of document counts, is to use the term\-term matrix, also called the word\-word matrix or the term\-context matrix, in which the columns are labeled by words rather word\-word matrix than documents

* This matrix is thus of dimensionality \|V\|×\|V\| and each cell records the number of times the row \(target\) word and the column \(context\) word co\-occur in some context in some training corpus
* The context could be the document, in which case the cell represents the number of times the two words appear in the same document
* Note that \|V\|, the length of the vector, is generally the size of the vocabulary, often between 10,000 and 50,000 words \(using the most frequent words in the training corpus; keeping words after about the most frequent 50,000 or so is generally nothelpful\).
* Since most of these numbers are zero these are sparse vector representations; there are efficient algorithms for storing and computing with sparse matrices

#### Cosine for measuring similarity

To  measure  similarity  between  two  target  words v and w, we need a metric that takes two vectors \(of the same dimensionality, either both with words as dimensions,hence of length \|V\|, or both with documents as dimensions as documents, of length \|D\|\) and gives a measure of their similarity.

The cosine—like most measures for vector similarity used in NLP—is based on the dot product operator from linear algebra, also called the inner product. 

* As we will see, most metrics for similarity between vectors are based on the dot product
* The dot product acts as a similarity metric because it will tend to be high just when the two vectors have large values in the same dimensions
* This raw dot product, however, has a problem as a similarity metric: it favors long vectors
* The vector length is defined as:  
\|v\| = sqrt\(∑v<sup>2</sup><sub>i</sub> for i in range\(1, N\)\)  
* The dot product is higher if a vector is longer, with higher values in each dimension
* More frequent words have longer vectors,  since they tend to co\-occur with more words and have higher co\-occurrence values with each of them
	* The raw dot product thus will be higher for frequent words
	* But this is a problem; we’d like a similarity metric that tells us how similar two words are regardless of their frequency
* We modify the dot product to normalize for the vector length by dividing thedot product by the lengths of each of the two vectors
	* This normalized dot product turns out to be the same as the cosine of the angle between the two vectors, following from the definition of the dot product between two vectors a and b

#### TF\-IDF: Weighing terms in the vector

* The co\-occurrence matrices above represent each cell by frequencies, either of words with documents , or words with other words
	* But raw frequency is not the best measure of association between words
	* Raw frequency is very skewed and not very discriminative

**tf\-idf algorithm** : the product of two terms, each term capturing one of these two intuitions:  
* **term frequency** : the frequency of the wordt in the document d
* The second factor in tf\-idf is used to give a higher weight to words that occur only in a few documents
	* Terms that are limited to a few documents are useful for discriminating those documents from the rest of the collection; terms that occur frequently across the entire collection aren’t as helpful

**document frequency** : the number of documents a term occurs in

**collection frequency** : the total number of times a word appears in the whole collection in any document

#### Pointwise Mutual Information \(PMI\)

**Pointwise mutual information** : a measure of how often two events x and y occur, compared with what we would expect if they were independent

PMI\(w, c\) = log<sub>2</sub> P\(w, c\) / P\(w\) P\(c\)

* The numerator tells us how often we observed the two words together 
* The denominator tells us how often we would expect the two words to co\-occur assuming they each occurred independently; recall that the probability of two independent events both occurring is just the product of the probabilities of the two events
* Thus, the ratio gives us an estimate of how much more the two words co\-occur than we expect by chance

PMI values range from negative to positive infinity.  But negative PMI values \(which imply things are co\-occurring less often than we would expect by chance\) tend to be unreliable unless our corpora are enormous. To distinguish whether two words whose individual probability is each 10<sup>−6</sup> occur together less often thanchance, we would need to be certain that the probability of the two occurring together is significantly different than 10<sup>−12</sup>, and this kind of granularity would requirean enormous corpus.

## FROM HERE IM SUMMARISING SLIDES AND ADDING TO THEM FROM READING

##### Prediction\-based models: An alternative way to get dense vectors

* Word2vec \(and variants\)
* Learn embeddings as part of the process of wordprediction \(language modeling\)
* Train a neural network to predict neighboring words
	* Inspired by neural net language models
	* In so doing, learn dense embeddings for the words in the training corpus
* Advantages:
	* Fast, easy to train 
	* Available online in the word2vec \(gensim in python\) package
	* Including sets of pretrained embeddings

##### Word2vec outline 

* A framework for learning word vectors using language modeling
* Start with a large corpus of text
* Every word in a fixed vocabulary \(V\) is represented by a vector \(initially random\)
* Go through each position t in the text, which has a center word c and context \(“outside”\) words o 
* Use the similarity of the word vectors for c and o to calculate the probabilityof o given c \(or vice versa\)
* Keep adjusting the word vectors to maximize this probability 

* In other words, for each position 𝑡 = 1, ... , 𝑇, predict context words within a window of fixed size m, given center word 𝑤<sub>t</sub>

##### Word2vec details

* Skip\-grams \(SG\)
	* Predict context \(”outside”\) words \(position independent\) given center word
* Continuous Bag of Words \(CBOW\)
	* Predict center word from \(bag of\) context words

* What about words not in the vocabulary?
	* We may have removed stopwords
	* Or truncated the vocabulary to \|V\| to remove rare words
* UNK words all mapped to one entry in the vector

##### New models: ELMo & BERT

* Shift from context\-free models to contextual models based on language modeling \(predicting sequences of words\)
* ELMo representations are:
	* Contextual: The representation for each word depends on the previous words
	* Deep: Combine all layers of a deep pre\-trained neural network
	* Character based: Purely character based, allowing the network to use morphological clues to form robust representations for out-of-vocabulary tokens unseen in training
* BERT representations:
	* Bi\-directional context
	* Deep\(er\) \+ Wider 
	* Based on Words \+ character n\-grams
	* Seq2Seq models: Transformer model \+ attention
	* Extensible: Extendable to  a classifier / ranking model

_BERT\-based classifiers are leading to major breakthroughs in NLP and IR_

##### Evaluating embedding effectiveness

* Extrinsic \(task-based, end\-to\-end\) Evaluation:
	* Word analogies
	* Question Answering
	* Spell Checking
	* Essay grading
* Intrinsic Evaluation:
	* Correlation between algorithm and human word similarity ratings
		* Wordsim353: 353 noun pairs rated 0\-10.   sim\(plane,car\)=5.77
	* Taking TOEFL multiple\-choice vocabulary tests
		* Levied is closest in meaning to: imposed, believed, requested, correlated

##### Before and after: Word representations

* Sparse Bag\-of\-Words Model
	* Word is a binary / count occurrence
	* Each word in the vocabulary is represented by one position in a HUGE vector
	* Context information is not utilized
* Word Vectors
	* Each word occurrence is represented by a vector of fixed number of dimensions \(generally 300\)
	* Unsupervised, built just by reading huge corpus
	* Context information is \(sometimes\) used

## Week 7

#### What does NLP involve?

* Syntax
	* Identifying the syntactic roles of words in sentences
* Semantics
	* Worrying about the meanings of the words, phrases or sentences
* Pragmatics
	* Worrying about how communicative context affects meaning

#### NLP tasks

* Machine Translation
	* English to French
* Single or Multi\-Doc Summarization
	* Document to Outline
* Entity disambiguation
	* Apple \(computer\) vs. Apple \(fruit\)
* Relation Extraction
	* <\entity> <\relationship> <\entity\>
* Semantic parsing
	* Which college did Obama go to? 🡪 \(and \(Type University\) \(Education BarackObama\)\)
* Textual entailment
	* Does Sentence 1 imply sentence 2? 

* Why is NLP hard? 
	* Ambiguity
	* Context Dependence
	* Background Knowledge

#### A typical NLP pipeline

* Tokenization and lemmatization
* Sentence boundary detection
	* Most NLP operates on individual sentences
* Part\-of\-speech\-tagging
	* Identify nouns, verbs, adjectives, etc...
* Parsing \(dependency\)
	* Diagraming sentences
* Named Entity Recognition
	* Detect and classify entities
* Coreference resolution
	* Resolve pronouns to named entities 

#### How is all this done?

* Rule\-based approaches
	* Linguistic \+ Domain knowledge
	* Example: tokenization \- re.split\(‘r\\W\+’, raw\)
	* Maintaining/updating rules manually is difficult
* Statistical methods for identifying patterns
	* Supervised machine learning
* Learn from human interactions with computers
	* Mainly as a way to acquire training data

#### The Supervised ML model approach

* Training
	1. Collect a set of representative training documents
	2. Label each piece of text with its label
	3. Design feature extractors appropriate to the text and classes
	4. Train a classifier to predict the labels from the data
* Testing
	1. Receive a set of test text 
	2. Run model inference to label each piece of text
	3. Appropriately output the label
	4. Evaluate correctness of predicted labels

#### Regularities in language

* Word n\-grams model : regularities in word sequences
* Language has richer structure
	* Phrases : There are groupings of words in sentences that behave like a unit \(collocations, entities\)
	* Dependencies : Words in a sentence have specific syntactic \(and semantic\) relationships
* We use ML \(Hidden Markov Models, and others\) to predict these

#### Part\-of\-Speech \(POS\) Tagging

* Given a sentence, what role does each word play?
* Primary school: NOUN, PRONOUN, ADJ, VERB, etc.
* Part\-of\-speech tagging is the most basic syntactic analysis we can do
	* Input: A sequence of tokens \(e.g., a sentence, tweet, search queries\)
	* Output: An assignment of POS tags for each word in the input

#### Hidden Markov Model

* Generalization of Naïve Bayes to sequences
* Assume an underlying set of hidden \(unobserved\) states \(labels\), y,  in which the model can be
* Assume probabilistic transitions between states over time as sequence is generated
* Assume a probabilistic generation of tokens from states \(e.g. words generated for each POS\)
* Assume current state is dependent only on the previous state. \(known as the ‘markov assumption’\)
	* The assumption may vary \(2<sup>nd</sup> order = previous 2 states\)

##### Parts of the model

* x<sub>i</sub> : observed nodes \(i.e. words\)
* y<sub>i</sub> : hidden nodes \(i.e. POS tags\)
	* goal will be to predict theses
* Transitions: 
	* p\(y<sub>i</sub> \| y<sub>i\-1</sub>\)\(horizontal arrows\)
* Emissions: 
	* p\(x<sub>i</sub> \| y<sub>i</sub>\) \(vertical arrows\)
* Things to Do:
	* Training: learn p\(y<sub>i</sub> \| y<sub>i\-1</sub>\) and p\(x<sub>i</sub> \| y<sub>i</sub>\)
	* Inference \(test\) : given x<sub>i</sub> , infer y<sub>i</sub> or p\(y<sub>i</sub>\)

#### Training time: what can we learn?

Just count and normalize \(over training data\)

##### HMMs: POS Training

* Transitions: p\(y<sub>i</sub> \| y<sub>i\-1</sub>\)
	* Pr\(V\|N\) = 1/2
	* Pr\(DT\|V\) = 1/1
	* Pr\(N\|DT\) = 1/1
	* Pr\(END\|N\) = 1/2
* Emissions: p\(x<sub>i</sub> \| y<sub>i</sub>\)
	* Pr\(James \| N\) = 1/2
	* Pr\(ate \| V\) = 1
	* Pr\(the \| DT\) = 1
	* Pr\(food \| N\) = 1/2

N \-\> James  
V \-\> ate  
DT \-\> the  
N \-\> food  

### For POS inference diagrams refer to week 7 

#### HMMs: POS Inference

* Brute force:
	1. Enumerate all possible state assignments
	1. Score each assignment
	1. Do one of:
		a. Pick the “best” \(Viterbi\)  
		b. Compute statistics \(Forward\-backward\)

##### HMMs: Viterbi

We take the path from <\end\> to <\start\> that has the highest value. \[Looks at horizontal values in sequences\]

Steps:  
* Find the best sequence to get V in position 2
* Find the best suffix with V in position 2
* Take the best overall sequence

#### HMMs: Forward\-Backward

Steps:  
1. Find the sequences to get N \(or V, or whatever\) in position 2
2. Find the sequences that carry on from N in position 2  
Add them all up

#### POS punch line

* State\-of\-the\-art techniques achieve \> 98% accuracy on news
* Average POS tagging disagreement amongst expert human judges for the Penn Treebank was 3.5%
* POS tagging in resource poor languages is harder \(\~87%\)
* POS tagging for Tweets is harder \(state\-of\-the art \~88%\)

#### Sequence tagging problems

* Many problems in NLP have data which is a sequence of characters, words, phrases, lines, or sentences ...
* We can think of our task as one of labeling each item in order

#### Other ML Sequence Models

* Chain Conditional Random Fields
	* Generalization of logistic regression to sequences
	* Easy to incorporate arbitrary features \(e.g. Capitalization\)
	* Works well with limited amounts of data
	* Most widely used sequence labeling algorithm \(for now\)
* Neural\-network based sequence models
	* Recurrent Neural Networks \(RNNs\)  \(e.g. Long\-short\-term memory \(LSTM\) models\)
	* ’en vogue’ as the current hot way to do things – but requires lots of data
	* Packages – Standard in deep learning \(Tensorflow, CNTK, PyTorch\)

#### Why do we care about this syntactic structure?

* Many aspects of meaning can be learnt using the syntactic structure
	* The NP preceding VP is likely the subject of the action
	* The NP following the VP is likely the object of the action
* Knowing basic units is helpful in modeling language
	* You can use this to predict or complete the sentence \(language modeling\)
	* Re\-organize sentences or simplify them \(summarization\)

#### Parsing: Overview

* Types of Parsing:
	* Constituency / phrase-structure
	* Dependency
	* Semantic / frame
* Parsing Techniques / Algorithms:
	* Transition\-based
	* Graph\-based
	* Chart\-based

* Similar goal: Find the best tree. 
* Different formalisms, but similar algorithms used for all types.

##### Dependency Parsing

* Given a sentence, draw edges between pairs of words, and label them
	* Result should be a tree
	* The edge\-labels between word pairs should convey the correct syntactic relation
* Parsing
	* Not a single formalism / correct answer
	* Methods work regardless: just need training data

**Formal definition of Dependency Parsing**

Formally, a dependency structure for a given sentence is a directed graph originating out of a unique and artificially inserted root node, which we always insert as the left most word.

* In the most common case, every valid dependency graph has the following properties
	* It is weakly connected \(replacing its edges with undirected edges results in connected graph\)
	* Each word has exactly one incoming edge in the graph \(except the root, which has no incoming edge\)
	* Acyclic

##### Transition Based Parsing

* Imagine a machine that has a stack and a buffer
* It makes arc decisions about entries in the top of the stack and buffer
* Keeps shifting words from the buffer until all words are consumed

* Mechanism: build parse tree by sequence of actions \(transitions\)
* Set\-up \(state\):
	* A buffer initialized with the words
	* A stack to store state:
		* Words under consideration for more edges
	* Dependency arcs \(edges\)
		* The partially\-constructed tree
* Arc\-Standard parsing:
	* Shift: pop from buffer, push to stack
	* Left\-arc: add left edge
	* Right\-arc: add right edge

* “Shift\-reduce” parsing:
	* Shift: \(shift\) move from buffer to stack
	* Reduce: \(left\-arc, right\-arc\) add edges, and remove elements from stack

* For N tokens:
	* O\(N\) shift operations \(one for each token\)
	* O\(N\) reduce operations \(one for each edge\)

_O\(N\) = linear time parsing!_

Actions are irreversible! Cannot undo with other transitions  
* Corollary: must choose correct* action every time!

##### How to choose transitions?

* Multi\-class prediction
	* Inputs: state = \{stack, buffer, other features\}
	* Targets: transitions = \{shift, left\-arc, right\-arc\}
* Classifier: score\(a<sub>i</sub> \| state<sub>i</sub>\) at step i
	* Rule\-based, SVM, NN, etc.
* Training:
	* Predict “gold” actions \(from true tree\)
	* Or: “dynamic oracle” rewards good actions

#### Parsing Summary

* Syntactic parsing aims to find phrase\-structure in sentences and word\-word relations

* Dependency parsing
	* Word\-word relations e.g., nsubj\(ate, Elephant\)
	* Parsing generates dependency trees by predicting edges or pruning edges
	* Transition\-based parsing formulates edge prediction as a classification task
		* Predict one of four actions to take next

* Parsing is a widely used step in constructing deeper, semantic representations

#### NLP Summary

* NLP provides us with tools to model language beyond simple lexical \(word\) features
* Sequence models like HMMs and CRFs allow us to label break apart patterns in language
	* Part\-of\-speech tags
	* Sentence or word breaks
	* Patterns in language discourse \(your coursework!\)
* Tree structured prediction
	* Predict complex patterns in language \(We saw dependency parsing\)
	* Critical for advanced applications \(QA, Dialogue Systems, etc.\)

## Week 8

#### Representations of a word

* Up until now, we have learnt we can represent words as Vectors learning from its context:
* However we have a problem:
	* The same vector representation for a word regardless its current context
* We just have one representation for a word, but words have different aspects, including semantics, syntactic behavior, and register/connotations

#### Intro to RNNs \(Recurrent Neural Networks\)

* RNNs solve this by having a “memory” state
* As inputs are passed to the RNN the memory is updated to remember what it has seen
* Memory states are passed as input progresses

#### LSTM: Long Short Term Memory RNN

* The Gate of Forgetting
	* What past hidden state is worth keeping \(still relevant\) or no: \(0 forget \- 1 keep\) * past
* The Gate of Input
	* What past hidden state will be useful to figure out this input? Input \+ \(remembered past\)
* The Gate of Output
	* What out of past state \+ this current input will be useful later?

#### What is ELMo?: Language Modeling task

* ELMo’s use comes from its pre\-training
* Train on a large dataset of unlabeled text
* The pre\-training task is Language Modeling
* A language Model predicts the probability of the next word given context

##### ELMo specifics

* ELMo reads in words as character n\-grams
* The learning objective is modeling language bidirectionally
* Once trained, weights are “frozen”, but still providing contextual information

#### RNNs have trouble remembering

* Even with dedicated memory cells like LSTMs and GRUs, path length between cells grows with sequence length
* This means RNNs on their own can’t remember for very long
* Trouble with long term dependencies

#### Motivation for transformers

* We want parallelization but RNNs are inherently sequential
* RNNs need attention mechanism to deal with long range dependencies
	* path length between states grows with sequence length

#### Attention: selectively weighting words

* Objective: have all context words in the input selectively influence the embedding of a target word
* We are showing self-attention here: all words are being influenced by all others in the same input
* The target word is the “query”, context words are “keys”

#### Enhancing RNNs with attention

* W<sub>q</sub> & W<sub>k</sub> are trainable weight matrices
* They have been trained by the attention mechanisms

* Sum all weighted hidden states together to get the contextual embedding C<sub>3</sub>
* a<sub>t</sub> are the attention scalars used to weigh each state
* THey are the same for all computations of attention in a single pass

* Attention layers can be stacked
* Simulates a deeper network

#### Transformer Overview

* Non\-recurrent sequence\-to\-sequence encoder\-decoder model
* Good for GPU parallelisation
* Task: machine translation
* Data: parallel sentences in each language

#### BERT’s preprocessing:

* Custom Tokeniser: Bert will generate embeddings for words and subwords. E.g.:
	* Disable =\> di, ##sable
* Custom tags:
	* \[CLS\] <\- Indicates this is classification task, always the first sentence element
	* \[SEP\] <\- Separates sentences, and marks the end of a sentence

* Preprocessing of “Disable the screensaver” : 

\[CLS\], 'di', '##sable', 'the', 'screens', '##aver', \[SEP\]

#### BERT: Just a Transformer encoder

* BERT is trained using a modification on the original Language Modeling task: Masked Language Modeling
	* Hide 15% of words from the input and try to predict them
* Inherently bi\-directional since attentionallows all words to contribute to the prediction
* BERT uses next\-sentence prediction as a secondary task

#### Contextual embedding summary

* Shift from context\-free models to contextual models based on language modeling \(predicting sequences of words\)
* ELMo representations are:
	* Contextual: The representation for each word depends on the previous words
	* Character based: Purely character based, allowing the network to use morphological clues to form robust representations for out-of-vocabulary tokens unseen in training
* BERT representations
	* Bi\-directional context
	* Based on Words \+ character n\-grams
	* Seq2Seq models: Transformer model \+ attention
	* Extensible: Extendable to a classifier / ranking model

## Week 9

#### Goals of information extraction

* Organize information so that it is useful to people 
	* Info boxes in Wikipedia 
	* Summary of facts across an entire collections of news
* Organize information so that it is useful for machine algorithms 
	* Data analytics 
	* Question answering 

#### What is Information Extraction \(IE\)? 

* Goal: Discover/extract structured information from text 
* How: by mining lots of information from a corpus 
* “Machine reading” of text

Information extraction = segmentation \+ classification \+ association \+ clustering

* IE = extracting information from text 
	* Clear, factual information 
	* Often: <\subject\> <\relation\> <\object\> RDF triples 
	* Ex: <Lithospermum radix\> <\contains\_compound\> <\beta\-HIVS\>
* Extract entities 
	* Example: proteins, plant, chemical, diseases, medicines, ... 
	* E.g.: trap1\(protein\), Lithosperm radix \(plant\), beta\-HIVS \(chemical\) 
* Extract the relations between entities 
	* E.g. contains, is\_a, regulates, causes, interacts\_with, ... 
* Figure out the larger events that are taking place 
	* Cancer cell death occurs as part of a medical treatment

#### Information Extraction pipeline 

* Named Entity Recognition \- Detect and classify entities
* Coreference resolution \- Resolve pronouns to named entities
* Entity Resolution \(linking\) 
	* Ground entities to a representation of ‘world’ knowledge
* Relation Extraction - Classify relationships between entities 

#### Coreference Resolution

* Goal: resolve different mentions of the same entity 
	* Mention: a single “chunk” \(often a noun phrase\)
	* Entity: a grounded “thing”

#### Coreference Process

* Detect the mentions
* Cluster the mentions
	* what mention relates to what entity

#### Mention detection 

* Three kinds of mentions: 
	* Pronouns
		* I, your, it, she, him, etc.
		* Use a PoS tagger 
	* Named entities 
		* People, places, etc.
		* NER tagger
	* Noun phrases 
		* “a dog,” “the big fluffy cat stuck in the tree”
		* Use a parser 

#### Linguistics note on coreference Resolution 

* Coreference is when two mentions refer to the same entity in the world 
	* Anaphora: expression depends on antecedent
		* “Sally arrived, but nobody saw her” 
	* Cataphora: expression depends in postcedent 
		* “Before her arrival, nobody saw Sally”
* Exophora: external context \(maybe unresolved\) 
	* “He was standing over there”

#### Four models for Coreference

* Rule\-based \(pronominal anaphora resolution\) 
* Mention Ranking 
* Mention Pair 
* Clustering

#### Rule\-based

* Hobbs \(1978\) proposes an algorithm that searches parse trees for antecedents of a pronoun
* Starting at the NP node immediately dominating the pronoun 
* Search previous trees, in order of recency, left\-to\-right, breadth\-first
* Looking for the first match of the correct gender and number \(male\-female/sing ular\-plural\)

##### Coreference Resolution Problems

_Hard cases require nuanced semantic understanding of the world._

#### Pairwise coreference model 

Task: Given a mention \(m<sub>i</sub>\) and earlier mentions \(m<sub>1</sub>, … m<sub>i\-1</sub>\) classify whether it refers to each earlier entity or not \(m<sub>i</sub> == m<sub>j</sub>\) given the surrounding context. 

This is a Binary classification problem

* Mention Pair models 
	* Create a coreference chain as a collection of pairwise mention links
* Make independent pairwise decisions
* Reconcile them in some deterministic way \(e.g., transitivity or greedy partitioning\) 
	* A single mistake can lead to huge \(incorrect\) clusters

#### Possible coreference features

* Person/Number/Gender agreement 
	* Jack gave Mary a gift. She was excited.
* Semantic compatibility 
	* ...the mining conglomerate...the company...
* Certain syntactic constraints 
	*  John bought him a new car. \[him can not be John\]
* More recently mentioned entities preferred for referenced 
	*  John went to a movie. Jack went as well. He was not busy.
* Grammatical Role: Prefer entities in the subject position 
	*  John went to a movie with Jack. He was not busy.
* Parallelism: 
	*  John went with Jack to a movie. Joe went with him to a bar.

#### Mention ranking 

* Assign each mention its highest scoring candidate antecedent according to the model
* Dummy NA mention allows model to decline linking the current mention to anything \(“singleton” or “first” mention\)

##### Ranking Model Inference 

* Pretty much the same as mention\-pair model except each mention is assigned only one antecedent

#### Ranking Model 

* Standard feed\-forward neural network 
	* Input layer: word embeddings and a few categorical features

**Input Features**

* Embeddings
	* Previous two words, first word, last word, head word, ... of each mention
		* The head word is the 'most important' word in the mention, can be found using a parser
* Other features:
	* Distance
	* Document genre
	* Speaker information

#### End\-to\-End Model 

* Base for current state\-of\-the\-art model for coreference resolution 
* Mention ranking model 
* Improvements over simple feed\-forward NN 
	* Use an LSTM 
	* Use attention 
* Do mention detection and coreference end\-to\-end 
	* No mention detection step! 
	* Instead consider every span of text \(up to a certain length\) as a candidate mention 
	* A span is just a contiguous sequence of words
* Next, represent each span of text i going from START\(i\) to END\(i\) as a vector

##### End\-to\-end Scoring

* Score each pair of spans to decide if they are coreferent mentions
* Scoring functions take the span representations as input
	* May include multiplicative interactions between representations
	* May include extra features

#### Coreference clustering 

* Start with each mention in it’s own singleton cluster 
* Merge a pair of clusters at each step 
* Use a model to score which cluster merges are good

##### Intuition

* Mention\-pair decision is difficult
	* are Google and Google Plus coreferent?
* Cluster\-pair decision is easier
	* Are \[Google, the company\] and \[Google Plus, the product\] coreferent?

##### Neural Model 

Mention Pairs \-\> Mention\-Pair Representations \-\> Cluster\-Pair Representation \-\> Score

##### Evaluation 

* Many different metrics: MUC, CEAF, LEA, B\-CUBED, BLANC 
	* Often report the average over a few different metrics

* B\-Cubed \- for each mention, compute a precision and a recall 
	* Precision: % of elements in a hypothesized reference chain that are in the true reference chain 
	* Recall: % of elements in a true reference chain that are in the hypothesized reference chain 
	* Overall precision & recall are the average of per\-chain precision & recall
* Optimizing chain\-chain pairings is a hard problem 
	* In the computational NP-hard sense – a greedy alignment is used

#### CoRef in practice \- Spacy Coreference 

* Rule\-based mention\-extraction
* Scorer is a neural mention ranking model
* Still has lots of heuristics in it

#### Current SOTA: The time for BERT

* Lee 2017 is the end\-to\-end neural mention base model 
* Lee 2018 adds ELMO 
* This adds BERT \+ a new objective

#### SpanBert \(2019\) 

* Objective: mask random contiguous spans, rather than random individual tokens 
* Span\-Boundary Objective \(SBO\) \-  predict the entire masked span from the observed tokens at its boundary
* Ranking model using BERT \+ hand\-engineered features \(Lee 2017 model\)

## Week 10

#### Information Extraction pipeline 

* Named Entity Recognition \- Detect and classify entities
* Coreference resolution \- Resolve pronouns to named entities
* Entity Resolution \(linking\) 
	* Ground entities to a representation of ‘world’ knowledge 
	* China \(LOC\) 🡪 https://en.wikipedia.org/wiki/China 
* Relation Extraction \- Classify relationships between entities 

### Entity linking

#### Entity ‘Grounding’

* Low\-level NLP: everything ungrounded 
	* Recall: manipulate text with parsing and part\-of\-speech, but no idea what it means
* Information Extraction starts \(partly\) to resolve this 
	* From strings to things
* Deal with entities. Can ground to “real world” \(for example entries in Wikipedia\)

#### Entity Linking 

* Link detected entities in text to a knowledge base

##### Formally

* Named Entity Disambiguation \(NED\), Wikification
	* Input a text document D = \{w<sub>1</sub>, ..., w<sub>n</sub>\} of words and a list of entity mentions M<sub>d</sub> = \{m<sub>1</sub>, ..., m<sub>n</sub>\}
	* Output a list of mention\-entity pairs \{\(m<sub>i</sub>, e<sub>i</sub>\)\} for i in \[1, n\] where each entity is an entry in a knowledge base \(KB\) 

#### It’s not as easy as it looks

* Nested entity mentions 
	* Four nested entities 
	* Three layers deep
* Slang entity mentions 
	* \[McSame\], \[MCCane\], \[Obamessiah\], \[Nobama\], and \[uz\-becky\-beckybecky\-stan\-stan\] 
	* Entity linking with Urban Dictionary \(Dalton, 2013\)

#### Entity linking as retrieval

* Given a mention, perform search over the KB to find candidates 
	* Simple string name matching heuristics 
	* Retrieval algorithm \(BM25, etc..\)
* Optionally, re\-rank candidates 
	* Possibly ‘collectively’ with evidence from all mentions in D

#### Dense entity representations 

* Zero\-shot Entity Linking with Dense Entity Retrieval \(Riedel 2019\) \[using BERT\]
	* Learn a representation for each entity from text descriptions \(cache these\)
	* Perform approximate “fuzzy” retrieval in dense vector space, score candidates

### Relation Extraction

* Parses text into structured relations to populate a database / knowledge base
* Resource Description Framework \(RDF\) triples: 
	*  <\subject\> <\relation\> <\object\> \[optional context\]

#### Why is relation extraction difficult? 

* Linguistic variability 
	* President Barack Obama versus Barack Obama, president of the United States
* Entity Ambiguity
	* Apple produces seeds versus Apple produces iPhones
* Implicit Relations
	* Obama met with Putin in Moscow =\> Obama traveled to Moscow
* Complex language with many clauses, long list of qualifiers, negations etc
	* Pentoxifylline \(PTX\) affects many processes that may contribute to the pathogenesis of severe malaria and it has been shown to reduce the duration of coma in children with cerebral malaria

#### Relations

* Binary relation: relational triple \(e\_1, relation, e\_2\) 
	* \(Barack Obama, place\-of\-birth, Honolulu\) 
* Many relations are not binary: 
	* “<\company\> appointed <\person\> as <\position\>”
* But can decompose: 
	* \(<\person\>, employed\-by, <\company\>\) 
	* \(<\person\>, has\-job\-title, <\position\>\)
	* \(<\company\>, uses\-job\-title, <\position\>\)

#### Example Knowledge Bases

* WordNet: low\-level semantic relations 
	* Hypernymy: \(Giraffe, hyponym\-of, animal\) 
	* Meronymy: \(leg, part\-of, chair\)
* Freebase / Satori / Wikidata / Google Knowledge Graph: world knowledge 
	* \(Fight Club, /film/film/starring, Brad Pitt\) 
* UMLS – medical knowledge

#### How to extract?

* Basic task: 
	* Find mentions of entities 
	* Extract relations from the context of the mentions of the entities 
		* “<\Barack Obama\> is the <\president\> of the <United States\>.” 
		* \(Barack Obama, head\-of\-state, United States\)

* Formulations: 
	* Rule\-based    \(e.g. Hearst patterns\) 
	* Supervised    \(extract & score\)
	* Semi\-supervised    \(bootstrapping\)
	* Unsupervised    \(clustering of patterns\)

#### Extracting Richer Relations Using Rules

* Intuition: relations often hold between specific entities 
	* located\-in \(ORGANIZATION, LOCATION\) 
	* founded \(PERSON, ORGANIZATION\) 
	* cures \(DRUG, DISEASE\)
* Start with Named Entity tags to help extract relation

#### Supervised Relation Extraction

* Find all pairs of named entities \(usually in same sentence\)
* Decide if 2 entities are related
* If yes, classify the relation

* Why the 2nd step? 
	* Faster classification training by eliminating most pairs 
	* Can use distinct feature\-sets appropriate for each task

#### Relation Extraction

* What type of supervised task?
* What is your learning model?
* What are your features? 

##### Features Example

* American Airlines, a unit of AMR, immediately matched the move, spokesman Tim Wagner said
	* employer\(American Airlines, Tim Wagner\)

* Bag\-of\-words features 
	* WM1 = \{American, Airlines\}, WM2 = \{Tim, Wagner\} 
* Head\-word features 
	* HM1 = Airlines, HM2 = Wagner, HM12 = Airlines\+Wagner
* Words in between 
	* WB\-NULL = false, WBF\-L = NULL, WBF = a, WBL = spokesman, WBO = \{unit, of, AMR, immediately, matched, the, move\}
* Words before and after 
	* BM1F = NULL, BM1L = NULL, AM2F = said, AM2L = NULL 

#### Distant supervision

* How do we scale relation extraction? 
	* Don’t want to manually label millions of sentences with thousands of relations!
* Distant supervision 
	* Use an \(existing\) large database to get huge \# of examples 
	* Create lots of features from all these examples 
	* Combine in a supervised classifier

#### Software tools 

* Entity resolution \(linking\) 
	* TagMe, DbPedia Spotlight, others…
* Relation extraction 
	* Stanford CoreNLP, DeepDive, Stanford MIMLE\-RE, UMass Factorie
	* Many custom packages

#### Result: Large\-scale knowledge bases

* The result of extraction are facts that can be represented in a knowledge base
* What can we do with these? 
	* Monitor changes in the world \(for fun or profit!\) 
	* Run structured database queries \(data analytics!\) 
	* Answer questions! 
