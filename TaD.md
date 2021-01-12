# Speech and Language Processing

## Chapter 1 

*conversational agent / dialogue system* : programs that converse with humans in natural language

*machine translation* : automatically translate a document from one language to another

*web-based question answering* : generalization of simple Web search, where instead of just typing keywords, a user might ask complete questions

### Answering Questions

*speech recognition/speech synthesis* : requires phonetics and phonology 

_phonetics_ : how words are pronounced in terms of sequences of sounds
_phonology_ : how sounds are realized acoustically

*producing contractions like I’m and can’t* : requires morphology 

_contractions_ : shortened form of a word \(or group of words\) that omits certain letters or sounds

_morphology_ : the way words break down into component parts that carry meanings like singular versus plural

*syntax* : the order and grouping of words

*lexical semantics* : the meaining of words

*compositional semantics* : the meaning of a phrase determined by combining the meanings of its subphrases

*pragmatic/dialogue knowledge* : The actions intended by use of sentences 

*coreference resolution* : knowledge about how words like that or pronouns like it or she refer to previous parts of the discourse

_discourse_ : communication by words / knowledge about linguistic units larger than a single utterance

### Ambiguity 

*ambiguous input* : multiple alternative linguistic structures can be built for the input

*part-of-speech tagging* : process of marking up a word in a text as corresponding to a particular part of speech, based on both its definition and its context

*word sense disambiguation* : determining which meaning of a word is activated by the use of the word in a particular context

*lexical disambiguation* : identifying which meaning of a word is used in context

*syntactic disambiguation* : identifying the meaning of a sentence from its structure

*probabilistic parsing* :  the process of determining the parses of an input string according to a formal grammar

_parse_ : to separate a sentence into grammatical parts

*speech act interpretation* : determining whether a sentence is a statementor a question

### Models and Algorithms 

_See AF2 for state machines_

The key advantage of probabilistic models is their ability to solve the many kinds of ambiguity problems that we discussed earlier; almost any speech and language processing problem can be recast as “given N choices for some ambiguous input, choose the most probable one”

_examples of formal rule systems_ : regular grammars and regular relations, context-free grammars, and feature-augmented grammars

*Markov model / weighted automaton* : a state machine augmented with probabilities

For non-probabilistic tasks, such as tasks involving state machines, we use well-known graph algorithms such as depth-first search. For probabilistic tasks, we use heuristic variants such as best-first and A* search and rely on dynamic programming algorithms for computational tractability.

*computational tractability* : how the resources needed for execution of the algorithm increase as we increase the size of the input 

*classifiers* : attempts to assign a single object to a single class

_examples of classifiers_ : decision trees,support vector machines,Gaussian mixture models, and logistic regression

*sequence models* : attempts to jointly classify a sequence of objects into a sequence of classes

_examples of sequence models_ : hidden Markov  models, maximum entropy Markov models

Many tools from ML apply in language processing, distinct training and test sets, statistical techniques like cross-validation, and careful evaluation of trained systems

### Language, Thought, and Understanding

*Turing test* : an empirical test, a game, in which a computer’s use of language would form the basis for determining if the machine could think

*explaination of the Turing test*
There are three participants: two people and a computer. One of the people is a contestant who plays the role of an interrogator. To win, the interrogator must determine which of the other two participants is the machine by asking a series of questions via a teletype. The task of the machine is to fool the interrogator into believing it is a person by responding as a person would to the interrogator’s questions.The task of the second human participant is to convince the interrogator that the otherparticipant is the machine and that she is human.

*ELIZA* : an early natural language processing system capable of carrying on a limited form of conversation with a user, a remarkably simple program that uses pattern matching to process the input and translate it into suitable outputs.

### The State of the Art

*Examples of modern language processing*

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

*regular expression* : Regular expressions can be used to specify strings we might want to extract from a document such as definingstrings like $199 or $24.99 for extracting tables of prices from a document

*text normalisation* : converting text to a more convenient, standard form

*tokenization* : The seperation of words in running text

*lemmatization* : determining that two words have the same root, despite their surface differences

*lemmatizer* : mapping words to their root

*Stemming* : stripping suffixes

*sentence segmentation* : the breaking of a text into sentences by grammatical cues

*edit distance* : how similar are two strings by the number of edits it takes to change one string to the other, widely used from spell check to speech recognition

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

*Anchors* : special characters that anchor regex to particular places in a string

- The dollar sign matches to the end of a line
- The carat matches to the start of a line
- \\b matches to a word boundary
- \\B matches to a non-word boundary

_Example regex_

/\(ˆ\|\[ˆa-zA-Z\]\)\[tT\]he\(\[ˆa-zA-Z\]\|$\)/ would correctly find all instances of 'the' in a text, it searches for 'The' and 'the' requiring either a line beginning or a non alphabetic character while avoiding any instances of 'the' found within words e.g 'theory'.

Regex must be checked for false positves such as 'theory' and false negatuves such as missing 'The'. Addressing these errors has to occur often to reduce the overall error rate in language processing. 

*More Operators*

- \\d matches any digit
- \\D matches any non-digit
- \\w matches any alphanumeric or underscore
- \\W matches any non-alphanumeric
- \\s matches whitespace
- \\S matches any non-whitespace

*Counting Operators*
- \* : zero or more occurences of previous char or expression
- \+ : one or more occurrences of the previous char or expression
- ? : exactly zero or one occurrence of the previous char or expression
- \{n\} : n occurrences of the previous char or expression
- \{n,m\} : from n to m occurences of the previous char or expression
- \{,m\} : up to m occurences of the previous char or expression

*Special Characters*
- \\\* matches an asterisk
- \\. matches a period
- \\? matches a question mark
- \\n matches a newline
- \\t matches a tab

*capture group* : use of parenthesis to store a pattern in memory

*non-capture group* : using :? within parenthesis will not store the pattern in memory 

*lookahead assertion* : uses =? to search for a pattern without advancing further on in the text

?! returns true if there is not match but does not advance in the text.

### Words 

*corpus* : a computer-readable collection of text or speech

*utterance* : the correlating speech to a sentence

*disfluency* : normal irregularities that occur during speech

*filled pause* : an articulation by the speaker that may be encountered between utterances but is not to be mistaken for a lengthened sound within a word

_some disfluencies are kept for example a filled pause could indicate that the speaker is restarting the clause or idea_

*lemma* : a set of lexical forms having the same stem

_stem_ : a major part-of-speech or word sense

*word form* : the full inflected or derived form of a word

*types* : the number of distinct words in a corpus

*tokens* : total number of running words

*dictionary boldface forms* : very rough upper bound on the number of lemmas

### Corpora 

*code switching* : use of multiple languages in a single communicative act

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


*Unix Commands*
- tr : systemically change specific characters in an input
- sort : sorts input in alphabetical order
- uniq : collapses and counts identical lines 

_Refer to 2.4.1 for an extensive example of these commands_

Often punctuation is broken off into a seperate token. Commas are a useful piece of information for parsers, periods help indicate sentence boundaries. Punctuation that occurs in word such as 'Ph.D' is kept. Special characters are often kept such as '$49.99' as well as numbers as we wouldnt want to split that price into '$, 49, 99'.

In English we split numbers every 3 digits with punctuation so we must consider these cases when tokenizing.

Tokenizing can assist with clitic contractions such as expanding 'They're' to 'They are'.

_clitic_ : part of a word that cannot stand on its on only occuring as a part of another word

*named entitity recognition* : detecting names, dates and organizations

*Penn Treebank tokenization standard* : used for the treebanks released by the LDC

_treebank_ : parsed corpora

_LDC_ :  Linguistic Data Consortium, a source of useful datasets

_The standard method for tokenization is to use deterministic algorithms based on regex compiled into efficient finite state automata_

*Hanzi* : Characters in the Chinese language

_Chinese NLP tasks take characters rather than words as input as meaning can be derived with less ambiguity and with smaller dictionaries_

_For Japanese and Thai NLP tasks characters do not offer enough semantic meaning so word segmentation is required_

NLP algorithms often use one training corpus then use facts derived to make decisions about a seperate test corpus and its language.

_In modern tokenization most tokens are words but some are frequently occuring morphemes_ 

*Token learner* : takes a raw training corpus \(sometimes roughly pre-separated into words, for example by whitespace\) and induces a vocabulary, a set of tokens

*Token segementer* : takes a raw test sentence and segments it into the tokens in the vocabulary

*Common tokenization algorithms*
- byte-pair encoding
- unigram language modeling
- WordPiece
- SentencePiece : uses BPE and ULM

*Byte-pair encoding*

The BPE token learner begins with a vocabulary that is just the set of all individual characters. It then examines the training corpus, chooses two symbols that are the most frequently adjacent and adds a new new symbol that merges these two symbols replacing every occurence of these adjacent symbols with this new single merged symbol. It continues to count and merge creating new and longer character strings until k merges have been done creating k novel tokens. The resulting vocabulary consists of the original set of individual characters plus k new symbols.

_Once we have 'learned' our vocabulary the token parser is used to tokenize a test sentence running on the test data with the merges we have learned in the order we learned them._

In real instance of BPE there are thousands of merges on a very large input corpus, the result yeild mostly full words with only rare occurences being represented by their parts.

*Word normalization* : putting words/tokens into a standard format

_A single normal form is chosen, this standardization may be valuable, despite the spelling information that is lost in the normalization process_

*Case folding* : mapping everything to lower case

Case folding is helpful for generalization in tasks such as information retrieval and speech recognition. For sentiment analysis and other text classification tasks case can be helpful thus case folding is not usually done. This is done because maintaining the difference between for example 'US' the country_and 'us' the pronoun can outweigh the advantage of generalization that case folding would provide for other words.

*morphological parsing* : parsing words into morphenes, stems and affixes

_affixes_ : additions to a word to add meaning e.g adding 's' as a suffix to mean plural

*cascade* : when the output of an algorithm pass is fed in as the next input

*Cues for sentence segmentation*
- punctuation
- question marks and exclamation points

_Periods can be ambiguous as they can represent a sentence boundary marker or an abbriviation or both_

In general sentence tokenization methods work by first deciding whether a period is part of a word or a sentence boundary. An abbreviation dictionary can help determine whether a period is part of a common abbreviation.

*Minimum edit distance* : the minimum number of editing operations \(insertion, deletion and substution\) needed to transform one string to another

*alignment* : given two sequences, the correspondence between substring of the two sequences

*Example operation list*
- d : deletion
- i : insertion
- s - substitution

_This is used to expres how we convert one string to another._

### Minimum Edit Distance

*Coreference* : Deciding whether two strings refer to the same entity

*Levenshtein distance* : the simplest weighting factor in which each of the three aformentioned operations has a cost of 1.

*Dynamic programming* : a class of algorithms that apply a table-driven method to solve problems by combining solutions to sub-problems.

*Minimum edit distance algorithm* : a dynamic programming algorithm that finds the minimum edit distance by combining the edit distances recursively from the empty string to the longest of the two strings.

_A psudocode implementation can be found at 2.5.1_

*Parallel corpus* : a corpus with a text in two languages

*Backtrace* : Start from the last cell in a distance matrix and follow pointers back to the empty string, each complete path is a minimum distance alignment.

*Viterbi* : A probibalistic extension of minimum distance, computing te maximum probability alignment instead of the minimum edit distance. _Discussed further in chapter 8._

### Summary

_Direct Copy_

- The regular expression language is a powerful tool for pattern-matching.
- Basic operations in regular expressions include concatenation of symbols, disjunction of symbols \(\[\], \|, and .\), counters\(\*,+, and\{n,m\}\), anchors\(ˆ,$\) and precedence operators \(\(,\)\)
- Word tokenization and normalization are generally done by cascades of simple regular expression substitutions or finite automata.
- The Porter algorithm is a simple and efficient way to do stemming, stripping off affixes. It does not have high accuracy but may be useful for some tasks.
- The minimum edit distance between two strings is the minimum number of operations it takes to edit one into the other. Minimum edit distance can becomputed by dynamic programming, which also results in an alignment of the two strings.

# Lectures

## Lecture 1 

### Slides

*Text Processing as a Pipeline*
- download web page, strip html if necessary, trim to desired content
- tokenize the text, select tokens of interest, create an NLTK text
- normalize the words, build the vocabulary

_NLTK_ : Natural Language ToolKit

Words aren't the only unit for tokenising, sometimes "n-grams" can be useful too. These can be obtained by passing a sliding window over a token stream. Different n-gram indexing can be achieved using sliding windows of larger sizes.

*Morphemes* : The small meaningful units that make up words

_Outcome of stemming may not be a word, instead will group similar words_

_Lemmatization is slower than stemming due to word lookup being required_

*one-hot encoding* : A vector that represents a text as a set of its terms, 1 if a term occurs, 0 if not

_The vectors for one-hot encoding all have \|V\| dimensions being the number of unique normalized tokens in the vocabulary for the corpus_

*What do we need to transform documents from a stream of tokens into a one-hot encoding?*
- know for each term, what its offset is in the dictionary / vocabulary
- The dimension of the vector, i.e. the size of the map

_If a new word is found in a text it is either added to the dictionary or in the case of the dictionary being frozen it is considered out-of-vocabulary_

_Can save space by only storing the id of terms that occur in a text rather than all in the vocabulary_

*Large Dictionary Solutions*
- Ommit rare words
- Hash the dictionary directly mapping words to vector indices of a fixed size

_Hash collisions are typically dealt with by using freed-up memory to increase the number of hash buckets_

*Handling OOV Words*
- Observation: Most unseen words are new morphological forms (or numbers)
- Wordpiece tokenization breaks words into “subword” pieces
- Learn common patterns from a large corpus of text

*Many text applications are based on comparing the similarity of pieces of text*
- grouping together tweets or news articles about the same event
- identifying documents similar to a user's query

*similarity measure* : a function that computes the degree of similarity between a pair of vectors

*Why set-based similarity?*
- Works well for small texts
- trivial to compute with basic data structures
- there are fast and efficient approximations

*Matching coefficient* : Number of terms (dimensions) that are both are non-zero

*Overlap coefficient* : Intersection divided by the size of smallest set

*Dice Similarity* : The intersection of the two sets mulitplied by 2, divided by the sum of the cardinality of the two sets

_cardinality_ : the number of elements in a set

*Jaccard Similarity* : the size of the intersection divided by the size of the union of the sample sets

*Summary*
- There are a plethora of text mining applications
- Text mining starts with representations of the words in the text, e.g. one-hot encoding 
- Examined set-based similarity measures

*Outstanding issues:*
- similarity is based on sets and doesn’t use counts
- Not all words are equally useful or discriminative. In the next lecture, we'll discuss statistical techniques that can identify the utility of words

### Pre-recorded Lecture

Twitter trending does not just look at what are the most popular terms right now but instead the terms that are being spoken about more than previously.

*Indentifying what a text is about*
- Important 'key' words
- Entities
- Properties of a person
- Things
- Actions

_Filler words do not give context_

_Generally ignore URLs_