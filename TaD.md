# Speech and Language Processing

## Chapter 1 

*conversational agent / dialogue system* : programs that converse with humans in natural language

*machine translation* : automatically translate a document from one language to another

*web-based question answering* : generalization of simple Web search, where instead of just typing keywords, a user might ask complete questions

###Answering Questions

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
_metadata_ : data that describes other data
- Annotation Process : What are the annotations, what are the demographics of the annotators, how were they trained, how was the data annotated?
- Distribution : Are there copyright or other intellectual property restrictions?