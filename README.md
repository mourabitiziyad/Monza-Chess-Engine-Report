<!-- Copy and paste the converted output. -->

<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see inline alerts.
* ERRORs: 0
* WARNINGs: 1
* ALERTS: 23

Conversion time: 10.082 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β33
* Tue Jul 12 2022 18:57:40 GMT-0700 (PDT)
* Source doc: AN OPEN SOURCE MAGIC BITBOARDS IMPLEMENTATION OF A CHESS ENGINE
* Tables are currently converted to HTML tables.
WARNING:
Found a long single-cell table (17964 characters) starting with:
**start sample:**
[Event "BBCxMonza.at"]
[Site "VD
**end sample**
Check to make sure this is supposed to be a code block.

* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<img width="141" alt="image" src="https://user-images.githubusercontent.com/60394642/178786673-47eec0a9-842a-40d3-a430-6a2a845b4eeb.png">


**SCHOOL OF SCIENCE AND ENGINEERING**

**AN OPEN-SOURCE MAGIC BITBOARDS IMPLEMENTATION OF A CHESS ENGINE**

SPRING 2022

**Ziyad MOURABITI**

Supervised by

**Dr. Naeem Nisar Sheikh**

AN OPEN-SOURCE MAGIC BITBOARDS IMPLEMENTATION OF A CHESS ENGINE

Capstone Report

** **

## TABLE OF CONTENTS

   * [TABLE OF CONTENTS](#table-of-contents)
   * [ACKNOWLEDGEMENTS](#acknowledgements)
   * [ABSTRACT](#abstract)
   * [ABSTRACT (IN FRENCH)](#abstract-in-french)
   * [LIST OF FIGURES](#list-of-figures)
   * [LIST OF TABLES](#list-of-tables)
   * [LIST OF ACRONYMS](#list-of-acronyms)
   * [1   	INTRODUCTION](#1---introduction)
   * [2	FEASIBILITY STUDY](#2feasibility-study)
   * [3	LITERATURE REVIEW](#3literature-review)
      * [3.1 	Board Representation](#31-board-representation)
      * [3.2 	Move Generation](#32-move-generation)
      * [3.3 	Forsyth–Edwards Notation](#33-forsythedwards-notation)
      * [3.4 	Magic Numbers / Magic Bitboards](#34-magic-numbers--magic-bitboards)
      * [3.5 	Perft Testing](#35-perft-testing)
      * [3.6 	Search and Evaluation](#36-search-and-evaluation)
      * [3.6.1 	Search](#361-search)
      * [3.6.2 	Evaluation](#362-evaluation)
      * [3.6.3 	Zobrist Hashing](#363-zobrist-hashing)
      * [3.6.4 	Transposition Tables](#364-transposition-tables)
      * [3.7	Chess Interface](#37chess-interface)
   * [4	IMPLEMENTATION &amp; TESTING](#4implementation--testing)
      * [4.1	Board Representation](#41board-representation)
      * [4.2	Move Encoding](#42move-encoding)
      * [4.3	Move Generation &amp; Magic Numbers](#43move-generation--magic-numbers)
      * [4.4	Forsyth-Edwards Notation](#44forsyth-edwards-notation)
      * [4.5	Perft Testing](#45perft-testing)
      * [4.6	Search &amp; Evaluation](#46search--evaluation)
      * [4.7	Chess Interface / UCI Protocol Implementation](#47chess-interface--uci-protocol-implementation)
      * [4.8	Open Sourcing the Project](#48open-sourcing-the-project)
   * [5   	STEEPLE ANALYSIS](#5---steeple-analysis)
      * [5.1 	Societal Implications](#51-societal-implications)
      * [5.2	Technological Implications](#52technological-implications)
      * [5.3	Economic Implications](#53economic-implications)
      * [5.4	Environmental Implications](#54environmental-implications)
      * [5.5	Political Implications](#55political-implications)
      * [5.6	Legal Implications](#56legal-implications)
      * [5.7	Ethical Implications](#57ethical-implications)
   * [6   	CONCLUSION](#6---conclusion)
   * [7	REFERENCES](#7references)

<!-- Created by https://github.com/ekalinin/github-markdown-toc -->



## 


## ACKNOWLEDGEMENTS

List of individuals and groups making any sorts of additions to the chess documentation, which would include the references.

## ABSTRACT

Chess engines, especially ones that can play at a very high level, are not as common as one would think. There are few notable mentions of very powerful engines that are widely used among different online chess services like Chess dot com and Lichess, to name a few. Although the actual use of engines is common among chess players, chess programming as an area continues to be scarce in terms of interest and availability of information, relative to how often they are referred to in usage.

Chess programmers, players, and mathematicians continue to provide vast improvements and ingenious techniques to strengthen existing chess engine implementations in different regards, notably in board representation, move generation, search, and move evaluation. Such improvements are built on top of very high levels of knowledge and understanding that stem from years of experience. It is thus very interesting to explore the complexities that go about implementing a modern and performant bitboard-based chess engine with good fundamentals in both search and evaluation, while at the same time having an implementation that is readable by new and upcoming chess programmers, without sacrificing too much of performance.

Research and personal testing prove that, although it is great to push the limits of how fast the move generator can be, an engine with exceptional evaluation and heuristics can reach optimal positions in far lower depths. Monza, this capstone project which has been created in C++ without a third-party use of any library, can communicate with users and interfaces through a Universal Chess Interface protocol, utilizes defacto standards in move generation, i.e the use of Magic Numbers in a Bitboard-based board representation. It also houses search algorithms that optimize an exponentially growing search tree by up to 99.8%. This high standard of search was complemented by a basic, but fundamental implementation of evaluation routines and heuristics that have seen Monza dominate and outperform engines rated at 1800 and 1900, respectively. Specific engine developments have had years of iterative updates and improvements that put it on the top engine performers. The work that has gone into developing Monza within the very short timeframe of 4 months has yielded results that are far beyond any average level engine, which makes for a very promising future development process that can see rating grow by 60-80% through improving the evaluation aspect alone, outperforming every single Grandmaster and Super Grandmaster in the world of chess. It can also reach much faster speeds than the status quo by looking at parallel search implementations.

**Keywords: _Chess Engine, Open-Source, Bitboards, Magic Numbers, Board Representation, Move Generation, Perft Testing, Negamax Search, Alpha-Beta Pruning, Iterative Deepening, Quiescence Search, Principle Variation Search, Principle Variation Move Ordering, Killer Heuristics, Late Move Reductions, Zobrist Hashing, Transposition Tables, Material Evaluation, Positional Evaluation, Mobility Score, King Safety, Passed, Isolated, and Stacked Pawn Bonuses and Penalties, Open & Semi-Open File Bonuses, Mating Bonuses & Stalemate Detection, Most Valuable Victim - Least Valuable Aggressor, Universal Chess Interface (UCI) Protocol._**




## ABSTRACT (IN FRENCH)

Les moteurs d'échecs, en particulier ceux qui peuvent jouer à un haut niveau, ne sont pas aussi courants qu'on pourrait le penser. Il y a peu de moteurs très puissants qui sont largement utilisés parmi différents services d'échecs en ligne comme Chess dot com et Lichess. Bien que l'utilisation réelle des moteurs soit courante chez les joueurs d'échecs, la programmation d'échecs en tant que domaine continue d'être rare en termes d'intérêt et de disponibilité des informations, par rapport à la fréquence à laquelle ils sont utilisés.

Les programmeurs d'échecs, les joueurs et les mathématiciens continuent de fournir de vastes améliorations et des techniques ingénieuses pour renforcer les implémentations existantes des moteurs d'échecs à différents égards, notamment dans la représentation de l'échiquier, la génération de coups, la recherche et l'évaluation des coups. De telles améliorations reposent sur des niveaux très élevés de connaissances et de compréhension qui découlent d'années d'expérience. Il est donc très intéressant d'explorer les complexités liées à l'implémentation d'un moteur d'échecs moderne et performant basé sur un bitboard avec de bons fondamentaux à la fois en recherche et en évaluation, tout en ayant en même temps une implémentation lisible par les programmeurs d'échecs nouveaux et futurs.

La recherche et les tests personnels prouvent que, bien qu'il soit formidable de repousser les limites de la rapidité du générateur de coups, un moteur doté d'une évaluation et d'une heuristique exceptionnelles peut atteindre des positions optimales dans des profondeurs bien moindres. Monza, le projet de ce capstone, a été créé en C++ sans l'utilisation d'une bibliothèque third-party, peut communiquer avec les utilisateurs et les interfaces par le biais d'un protocole d'interface universelle d'échecs, utilise les normes conventionnelles dans la génération de coups, c'est-à-dire l'utilisation de nombres magiques dans une représentation de l'échiquier basée sur un Bitboard. Il abrite également des algorithmes de recherche qui optimisent un arbre de recherche à croissance exponentielle jusqu'à 99,8 %. Ce haut niveau de recherche a été complété par une mise en œuvre basique, mais fondamentale, de routines d'évaluation et d'heuristiques qui ont permis à Monza de dominer et de surpasser des moteurs évalués respectivement à 1800 et 1900. Le développement de moteurs spécifiques a bénéficié de plusieurs années de mises à jour et d'améliorations itératives qui l'ont placé parmi les moteurs les plus performants. Le travail effectué pour développer Monza dans un délai très court de 4 mois a donné des résultats bien supérieurs à ceux de n'importe quel moteur de niveau moyen, ce qui laisse présager un processus de développement futur très prometteur qui pourrait voir le classement augmenter de 60 à 80 % rien qu'en améliorant l'aspect évaluation, surpassant ainsi tous les grands maîtres et super grands maîtres du monde des échecs. Il peut également atteindre des vitesses beaucoup plus rapides que le statu quo en examinant les implémentations de recherche parallèle.

**Mots-clés:_ Chess Engine, Open-Source, Bitboards, Magic Numbers, Board Representation, Move Generation, Perft Testing, Negamax Search, Alpha-Beta Pruning, Iterative Deepening, Quiescence Search, Principle Variation Search, Principle Variation Move Ordering, Killer Heuristics, Late Move Reductions, Zobrist Hashing, Transposition Tables, Material Evaluation, Positional Evaluation, Mobility Score, King Safety, Passed, Isolated, and Stacked Pawn Bonuses and Penalties, Open & Semi-Open File Bonuses, Mating Bonuses & Stalemate Detection, Most Valuable Victim - Least Valuable Aggressor, Universal Chess Interface (UCI) Protocol._**




## LIST OF FIGURES

**Figure 1**: Starting position on a chessboard with coordinates

**Figure 2**: Bitboard representation of a starting position

**Figure 3**: All bits allocated to one encoded move

**Figure 4**: FEN representation of a starting chess position

**Figure 5**: Extracting Relevant Piece Occupancy Bits given a rook on D4

**Figure 6**: Chess position for a white rook on C3

**Figure 7**: Possible rook moves in the position

**Figure 8**: Tord Kallqvist Romstad’s trial and error approach for generating magics

**Figure 9**: Sample Perft Function in C

**Figure 10**: Minmax Search Algorithm

**Figure 11**: Maximizing Side of Minmax

**Figure 12**: Minimizing Side of Minmax

**Figure 13**: Negamax Search Pseudocode

**Figure 14**: Negamax Search with Alpha-Beta Pruning

**Figure 15**: Search Tree with branch cutoffs

**Figure 16**: Principle Variation Search

**Figure 17**: Board illustration of a Fianchetto

**Figure 18**: A transposition table entry in the form of a C++ struct

**Figure 19**: White Pawns Bitboard in a Starting Position

**Figure 20**: Bitboard Representation of White Pawns in a Starting Position

**Figure 21**: Extracting board information through piece and occupancy bitboards

**Figure 22**: Chess Starting Position in Unicode

**Figure 23**: A summary of some important macros used throughout the implementation

**Figure 24**: Move Encoder Macro Implementation

**Figure 25**: Finding magics for the Rook

**Figure 26**: Detecting whether a square is attacked on the board

**Figure 27**: Perft - Position #1 - r3k2r/p1ppqpb1/bn2pnp1/3PN3/1p2P3/2N2Q1p/PPPBBPPP/R3K2R w KQkq -		

**Figure 28**: Perft - Position #2 - rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1

**Figure 29**: Perft - Position #3 - r3k2r/Pppp1ppp/1b3nbN/nP6/BBP1P3/q4N2/Pp1P2PP/R2Q1RK1 w kq - 0 1

**Figure 30**: Arena Chess Interface connected to Monza Chess Engine

**Figure 31**: Monza Chess Engine CLI

## 


## LIST OF TABLES

**Table 1**: Extracting the Magic Index

**Table 2**: Retrieve possible moves through the acquired magic index

**Table 3**: Material Score in Classical Chess

**Table 4**: Sliding Pieces Relevant Occupancy Bits

**Table 5**: Performance gains from different points of the Chess Engine Implementation




## LIST OF ACRONYMS

**CSS** - Cascading Style Sheets

**DOM** - Document Object Model

**FEN** - Forsyth–Edwards Notation

**GCC** - GNU Compiler Collection

**GUI **- Graphical User Interface

**HTML** - Hyper Text Markup Language

**JS** - JavaScript

**JSX **-** **JavaScript XML → JavaScript Extensible Markup Language

**LMR** - Late Move Reductions

**MVV-LVA **- Most Valuable Victim - Least Valuable Aggressor

**NNUE** - Efficiency Updatable Neural Network

**NPS **- Nodes Per Second

**PGN** - Portable Game Notation

**PV** - Principle Variation

**PVS** - Principle Variation Search

**UCI **- Universal Chess Interface

**ULL** - Unsigned Long Long




## 1   	INTRODUCTION


A chess engine is a computer program that can be used on various levels of chess. It essentially acts as a tool for players to evaluate their chess games and improve their decision-making through position evaluations after concluding their games. Chess engines are also used by analysts and spectators during live chess events in big tournaments, notably during the Chess World Championship, Chess Candidates Tournament, and others. Chess positions during play can be obscure to beginners and intermediate followers. This makes the engine a reliable way of better understanding who has an advantageous position or an absolute advantage during the play.

Chess engines fall within the framework of game development and theory, involving complex search and evaluation strategies. Chess Programming also relies on other aspects that improve search efficiency and speed. Additionally, it is important to understand that the topic of Chess Engine Programming is not common among programmers or computer science students. Engine projects fall within the framework of applications of search algorithms that one may encounter in a class of Artificial Intelligence. A lot of these engines, although provide a proof of concept for how a certain search algorithm functions are given a board of 64 squares, it does not keep in mind other factors of what an efficient representation should look like, or what kind of effects a certain search technique could lead, simply because these two areas will not necessarily fall in the scope of the project.

The aim is to develop a fully functional chess engine that should, in theory, play a high level of chess. As we will explore later, this theory is based on the idea that many of the applications and methods followed to build this engine are, fundamentally speaking, de facto standards for state-of-the-art engines like Stockfish[1], Leela[2], or Berserk[3]. An additional, and future aim to achieve once all implementation details are fully ready, is to make the project open-source and available to the public, either through a web version or by accessing the source code directly. Ideally, this capstone should represent a progressive process that involves taking some of the core ideas that go about chess engine implementations, digesting them, and applying them to the capstone project. Part of digesting these ideas involves thorough reading on these concepts and looking at developer feeds. Sections involving the implementation details of the project are as follows:


1. Board Representation
2. Move Generation (using magic numbers)
3. Perft Testing
4. Search
5. Evaluation
6. Visual Interface or Graphical User Interface


## 2	FEASIBILITY STUDY

Several areas go about the implementation of the chess engine, each of which constitutes decisions at the level of the tools and environments to be used. For this capstone, these areas are broken down into the following: The chess engine build, the graphical user interface, the environment, and version control.

Upon further analysis into adopting a fast programming language for the chess engine, it was seen that using C++ provides plenty of efficiency concerning the implementation requirements of the project and it is versatile enough that it can support newly added concepts in the future as needed. This is without being limited by a lack of Object-Oriented Programming features, for instance, if there was a need to adopt such a way to implement the engine.

For the graphical user interface, two options are present. It is possible to go down the route of implementing a user interface using JavaScript or Python. Although JavaScript is an untyped language and the use of Typescript is a much better alternative, the overall GUI will not require communication with a backend system. Note that the term “untyped” in this context refers to the fact that a programmer cannot explicitly set return types for functions or type arguments, which can make the project susceptible to bugs. Additionally, Any DOM manipulations would also be heavily reduced, or even discarded, using JavaScript/TypeScript framework like React. The other, more feasible option is to make the chess engine follow a UCI protocol so that available chess software can communicate with it easily.

The implementation environment of the project varies. XCode will be used to code, debug, and build the chess engine in C++ as it provides built-in support for the compiler along with version control management. The entire implementation is done on a personal laptop.

The project incorporates version control, making it easy to convert into an open-source project that is available to the public. 

Overall, and due to the time restrictions of capstone projects, it is expected that the chess engine portion of the project in C++ to take around 8 weeks in total, and one week to link the Graphical User Interface to the engine.




## 3	LITERATURE REVIEW

Many resources regarding chess and chess engines, especially more recent ones, do not necessarily present themselves as publications but rather discussions through forum posts or references and works of observation that chess programmers discuss in a wiki or video format. However, some essential resources play a part in explaining and laying out fundamental concepts in great detail. The idea of the review is to cover aspects mentioned in the introduction that go about the implementation of the chess engine and provide some explanation on why a specific approach was followed.


### 3.1 	Board Representation

One of the most common board representations involves the use of arrays. Array-based representation can be through the use of 2-dimensional arrays that hold 8x8 elements or a one-dimensional array with 64 elements.



<img width="151" alt="image" src="https://user-images.githubusercontent.com/60394642/178787865-0055fe23-a3b9-4f5b-b2a3-fa304d175d89.png">

**Figure 1: Starting position on a chessboard with coordinates**

The way this 2-dimensional array can be in such a way that if we were to put a piece in a1, we would map it to `array_board[0][0]`, a piece in h1 would be `array_board[0][7]`, b3 to `array_board[2][1]`, and so on[4].

Although this method looks easy to manage, it can be extremely inefficient when moving to the process of move generation, affecting this particular area would essentially impact the performance and strength of the entire engine. Inefficient generation means a longer time to generate moves and search for the move, making the engine very likely to lose a chess game on time or be unreliably slow. The methods of indexing and accessing array elements, as well as checking for boundaries, lead to more operations that prove to be expensive when accumulated. There are ways to mitigate the constant check for board bounds, some of them are addressed in variants of the array-based representation and **0x88 board representation**[5]. This approach is simply not as fast as other board representations from a hardware or CPU standpoint.

Another common approach to board representation is through the use of **Bitboards**. a bitboard is seen as a 64-bit word. Many resources mention the use of a double 32-bit representation, but at this point, it is safe to assume that a 64-bit processor architecture is what most computers operate on today. This word, which can be represented in C/C++ as an unsigned long long, represents the entire board position, with 1s and 0s signifying whether a square is occupied or not, respectively. Bitboards are highly efficient as they take advantage of CPU-efficient bitwise operations like AND, OR, XOR, as well as bit shifting. The use of bitboards can be combined with the idea of array-based representation such that an array of 12 elements can each hold a bitboard signifying a piece type. So, in order to retrieve all pieces of both colors into one bitboard, we can simply perform the OR operation on these 12 elements. Moving a piece is a matter of shifting, and so on. Overall, in its core concept, Bitboards are a much better alternative to a plain array-based representation due to aspects of speed and memory compactness. But they are **much more complex** to implement and maintain[6]. 
**Figure 2** provides a bitboard representation of the starting position shown in **Figure 1**.


<img width="181" alt="image" src="https://user-images.githubusercontent.com/60394642/178797520-40f47d06-6136-48e8-816c-c13e34296ac3.png">

**Figure 2: Bitboard representation of a starting position**

The chess engine being implemented uses Bitboards as our board representation. Future sections will involve the discussion of how exactly bitboards have been implemented and the kind of routines that I followed to take advantage of this representation. A later study of different bitboard patterns in move generation will be discussed in the future as part of this literature review or in the implementation section of this report, notably the study of Rotated Bitboards and **Magic Bitboards**. The latter is what our implementation consists of due to certain pros that I will discuss as well, but similarly to our earlier comparison between array-based and bitboards, Magic Bitboards are also much more complex to implement than rotated bitboards, but way more efficient.


### 3.2 	Move Generation

Most of the processes that go about generating all possible moves given a chess position involve a lot of hard-coded condition checking, notably with non-sliding pieces like knights, kings, and pawns. We do not need to check if there is a piece blocking the movement of one of these pieces but checking adjacent squares is enough, except for knights since they move slightly differently. Not the same thing however can be said about Sliding Pieces which are rooks, bishops, and queens. Their moves depend on the board occupancy, meaning that we need to follow a special routine to efficiently find possible moves of the piece given its source square and a bitboard that represents all other board occupancies. This can be achieved through the very core idea of magic bitboards that will be expanded on with great detail.

Once the generation of all the moves for all the squares, while also keeping in mind different piece-related rules, we can look at routines to make the move and update the board state. These **special** rules and states are as follows: En passant, double pawn pushes, castling moves, promotion (or underpromotion), and an explicit distinction between a quiet move, and a capture move. As the former requires additional operations to satisfy the new board state with both the captured piece and movement of the capturing piece.

One way to encode these moves in a unified way so that they can be understood by all the routines and techniques being implemented in code is through the following binary representation shown in Figure 3.



![image](https://user-images.githubusercontent.com/60394642/178797652-83896476-381e-42dd-87d9-3eecc022e3ab.jpeg)


**Figure 3: All bits allocated to one encoded move**

This representation[7] allows for one single move to contain all relevant state changes and information that we can feed into the move generator to update the board state accordingly, and to the search and evaluation functions to provide a comprehensive picture of the different possibilities and potential effects of every move. This particular representation has been used in the implementation of our bitboard engine.

Once we generate our encoded moves, we can store them in an array or a struct of moves. A make_move function should be able to preserve the current board state before making any alterations to it. Such mechanisms are essential for internal board movements during the search phase. This is because in the move generation, for instance, we do not factor whether or not the conclusion of a certain move could result in our king being in check or not. If the move puts our king in check, we would like to be able to revert to the original board position and proceed to search for other pseudo-legal moves that do not realize themselves as illegal[8] when they are made internally.


### 3.3 	Forsyth–Edwards Notation

In chess, it is worth noting a concise way of representing a game state is done through the use of FEN strings. The string is a representation of a board position. Figure 4 shows an example notation. This very notation is graphically represented in figure 1.


```
rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1
```


**Figure 4: FEN representation of a starting chess position**

This FEN string represents the starting position of the chessboard for each rank (separated by '/'), with details[9] that include whose turn it is to move (w or b), casting rights, En passant rule, number of moves, and plies (plural for ply, a half move).

To clarify, uppercase letters refer to white chess pieces, while lowercase letters refer to black pieces. The notation of “KQkq” means that the white king can castle both king and queen sides and that the black king can also castle king and queen sides, respectively. If a side is not available for castling, the letter is substituted by a dash “-”.

The implementation of a FEN parser is an essential component of any chess engine, as it is considered a de facto way of communicating a board position between engines and chess graphical interfaces.


### 3.4 	Magic Numbers / Magic Bitboards

Both magic numbers and magic bitboards refer to the same concept. Magic Numbers continue to be considered “one of the fastest, most versatile move-bitboard generators for individual sliding pieces”[10]. They are very fast but can be very complex to the uninitiated. Because our chess engine is using bitboards for board representation, it is only logical to explore move generators that take advantage of it.

For every square on the board, indexed [0…63] or [a8…h1], we can have an entire table that, provided with a composite occupancy bitboard, can return all the possible moves from that square. To clarify, a composite occupancies bitboard refers to a 64-bit representation of both black and white piece occupancies of the board, hence the word “composite”. The problem with this approach is that, if done naively, it would take hundreds, if not thousands of terabytes of memory to manage. Simply imagine how many possible moves can be done by a bishop or a rook in a given square given a board position! The number of possible moves a rook has in a8 would be 2^12, this idea, if factored into all the move combinations for all the squares and for all sliding pieces, can amount to about 8*2^64 bytes (more than 147 exabytes)[11]. However, there are ways to reduce that memory to a few megabytes if we act upon a few fundamental observations and key ideas[12].

For instance, given a rook on B8, we would notice that only the 8th file and B rank matter to us. Piece occupancies on every other square do not affect the rook’s available moves. We can examine this further by also looking at figure 5.



<img width="336" alt="image" src="https://user-images.githubusercontent.com/60394642/178799337-0cee1285-bca0-4f90-853a-e414b5aed983.png">


**Figure 5: Extracting Relevant Piece Occupancy Bits given a rook on D4**

Like the previous example on the rook on B8, we can assume a rook on D4. The final masked-down version of the bitboard would be the second bitboard in figure 5. In order to ensure that the piece can be captured, it is enough to perform an **AND** operation between the second bitboard to another bitboard containing only white piece occupancies, or friendly pieces. The same idea applies to bishops and the queen. The latter is a logical combination of both rooks and bishops.

An interesting source[13] provides an overview of how the magic numbers are calculated, and how they are used to index our pre-calculated sliding piece attack tables. Given figure 6, we would like to walk through the process of returning the possible moves of the rook on C3.



<img width="230" alt="image" src="https://user-images.githubusercontent.com/60394642/178799656-6e9129e8-7623-4b1e-8338-99fba09f9e9b.png">


**Figure 6: Chess position for a white rook on C3**

Table 1[13] depicts and describes the operations done to generate a magic index. The latter is used to then index the piece attack tables, which are then bitwise ANDed with the inverse of the friendly piece bitboard to get the possible moves in the position.

**Table 1: Extracting the Magic Index**


![image](https://user-images.githubusercontent.com/60394642/178799817-d47bf185-ac1c-4afe-aae2-bcee1faa1fa5.jpeg)



“All Pieces” refers to the bitboard representation of figure 6. that bitboard is bitwise ANDed with the rook mask for said square, which refers to all the squares where the rook can move, assuming an empty board. Note that we do not include the edges for two reasons: the edges are assumed to be blockers and will be included when we later define whether they are friendly or not, an unfriendly blocker is the same as an empty square, meaning the piece can move or perform a capture on that square. The second reason is that this simplification saves us some bits, which is helpful in the calculation.

The resulting occupancy bitboard is multiplied by the rook magic number for C3 that, for this example, is assumed to be already generated for every square. We then shift the resulting bitboard by (64 - number of bits in the rook mask for C3), giving us the magic index as a result. The bitboard array index has an equal count of bits to the relevant occupancy bits that were pre-generated (4 bits).

Table 2 shows our use of the index to retrieve the possible moves of the rook on C3. Figure 7 is a graphical representation of the same Move Destinations output.

**Table 2: Retrieve possible moves through the acquired magic index**


![image](https://user-images.githubusercontent.com/60394642/178799871-e3a56111-82dd-4dda-9786-c7d9b58c1811.jpeg)


**Figure 7: Possible rook moves in the position**

We need to note that the **magicMovesRook** is a pre-calculated rook attacks table that is involved in the process of creating the candidate keys for magic numbers, which involves a brute force trial and error method[14].

Tord Kallqvist Romstad, who is an author of the Stockfish chess engine, one of the most powerful open-source engines today, proposed this method of finding magic numbers[15][16]. The code displayed below has been slightly modified for formatting purposes, presented in figure 8. It is important to note that these magic numbers can be statically stored in arrays, which omits the need to generate these numbers at runtime as multiple sources provide magics for move generation. Because of the exploratory purposes of this capstone, Torn Romstad’s approach was used to create magics to be used for this engine. However, the logical approach of the random magics generator remains to be further studied. There are a multitude of variants and ways by which we can generate these magics. Some chess engines even generate magic numbers on the fly, rather than just once.


```
uint64 find_magic(int sq, int m, int bishop) {
  uint64 mask, b[4096], a[4096], used[4096], magic;
  int i, j, k, n, mbits, fail;

  mask = bishop? bmask(sq) : rmask(sq);
  n = count_bits(mask);

  for(i = 0; i < (1 << n); i++) {
    b[i] = get_occupancy_set(i, n, mask);
    a[i] = bishop? bishop_attacks(sq, b[i]) : rook_attacks(sq, b[i]);
  }
  for(k = 0; k < 100000000; k++) {
    magic = random_uint64_fewbits();
    if(count_bits((mask * magic) & 0xFF00000000000000ULL) < 6) continue;
    for(i = 0; i < 4096; i++) used[i] = 0ULL;
    for(i = 0, fail = 0; !fail && i < (1 << n); i++) {
      j = (int)((b[i] * magic) >> (64 - m));
      if(used[j] == 0ULL) used[j] = a[i];
      else if(used[j] != a[i]) fail = 1;
    }
    if(!fail) return magic;
  }
  printf("***Failed***\n");
  return 0ULL;
}
```


**Figure 8: Tord Kallqvist Romstad’s trial and error approach for generating magics**


### 3.5 	Perft Testing

As per the previous two points in this review, we can see that it is essential, given the level of complexity that the move generation can amount to, it is very important to ensure that move generation, with the appropriate mapping of encoded moves and board representation that we are adopting, that our engine generates all the moves correctly. This is where Perft Testing comes to play. We can also use Perft testing to measure the speed by which moves are generated. This part is crucial if we want to compare how fast our move generator fares compare to other chess engines. Figure 9 shows a barebone code version of a Perft function in C[17].



![image](https://user-images.githubusercontent.com/60394642/178802018-8555ea16-4828-481d-9160-3fa83b3c71d5.jpeg)

![alt_text](images/image10.png "image_tooltip")

**Figure 9: Sample Perft Function in C**

Perft testing will be a key part of evaluating the move generator of our engine in the implementation phase of the capstone report. Part of understanding potential weaknesses of our engine in terms of speed and efficiency can be uncovered through the use of this type of testing. 

It is worth noting that there is no standard way of writing Perft tests. This means that comparing the speed by which a specific number of nodes is searched given a board position may differ based on the code implementation, but the number of nodes searched overall should be identical as it is a necessary component that reflects whether or not the move generator is free of bugs.


### 3.6 	Search and Evaluation


### 3.6.1 	Search

Many evaluation techniques are usually embedded within the search itself. Without going too much into detail, scoring information which are core elements of search will be discarded from the evaluation portion of this point, and vice versa.

Overall, a common technique in performing game searches and adversarial searches is referred to as Minmax search. Another variant which will be discussed later is referred to as negamax search. However, it is important to preface this by mentioning that chess engines do not rely on minmax or negamax searches alone due to the exponential branching factor in chess, which calls for further improvements and algorithms. Figure 10 shows the algorithm in its most abstract form.


```
int MinMax(int depth) {
      if (SideToMove() == WHITE)	// White is the "maximizing" player.
          return Max(depth);
      else                          // Black is the "minimizing" player.
          return Min(depth);
}
```


**Figure 10: Minmax Search Algorithm**

In minmax search, assuming that White is the first to move, for instance, the search should yield the maximum possible score. But Black wants to minimize that score. With that logic, it is safe to say that when searching for instance at depth 3, minmax will find the best move for White, followed by what would Black play as a response, and then White’s response to Black’s move. 

Figures 11 and 12 show sample implementations of the maximizing and minimizing functions of minmax search[18].



![image](https://user-images.githubusercontent.com/60394642/178802116-17d87c28-cff2-4320-a202-35e0f507ebe2.jpeg)
![alt_text](images/image11.png "image_tooltip")


**Figure 11: Maximizing Side of Minmax**



![image](https://user-images.githubusercontent.com/60394642/178802142-2cbfeb02-b1fa-4ad7-8dfc-9c64669969b1.jpeg)


**Figure 12: Minimizing Side of Minmax**

From figures 11 and 12, we can see how for each depth down the tree, the functions alternate between maximizing the position value and minimizing it. The search reaches terminal nodes and scores the moves from White perspective (the base case), the parent node would then either choose the max value out of the two or the min, depending on whether it is a maximizing side or a minimizing one. Scoring from White perspective means that scores that put White at an advantage are higher than 0, while scores which are more advantageous for Black are negative.

Interestingly, there is a more concise representation of minmax search, through the implementation of what is referred to as negamax. A sample implementation is provided in figure 13.



![image](https://user-images.githubusercontent.com/60394642/178802160-16c3e42d-2a2a-42ca-9fbd-229499319c33.jpeg)
![alt_text](images/image13.png "image_tooltip")


**Figure 13: Negamax Search Pseudocode**

Two factors combine both minmax into one sole implementation. The first is the dynamic perspective of scoring when depth is less than 1. Instead of always giving the score from White’s perspective, the score is returned based on whose turn it is to move. The MakeMove macro naturally changes the flag for whose turn it is to move on the board, which triggers the changes in the score function. The second factor is the negation of the value of negamax when called. Assume that White is looking for the best move given two leaf nodes. The scores will be from Black’s perspective, which means they will have to be negated to reflect the true value behind those scores from White’s perspective.

As mentioned earlier, the high branching factor that comes with chess makes the negamax search, in its basic implementation, while reliable, still makes for very slow execution. Running the perft test at depth 7 from a starting chess position yields a total number of nodes of 3,195,901,860[19]. This number, from manual testing, can take between 1 and 3 minutes to generate, depending on other optimizations, including compiler optimizations when building the source code of the project. The biggest, and most fundamental complementary approach to negamax search is Alpha-Beta Pruning, shown in figure 14.



![image](https://user-images.githubusercontent.com/60394642/178802186-626ea129-06b0-4f4b-bacb-3d5f64baae6a.jpeg)


**Figure 14: Negamax Search with Alpha-Beta Pruning**





**Figure 15: Search Tree with branch cutoffs**

Following the logic of maximizing and minimizing sides in minmax and negamax, we can observe that there are cases where searching branches would not yield any meaningful results. As seen from figure 15[20] (above), if Black is presented with two moves to choose from (5 or 8), knowing that it is the minimizing side, it would be worthless to search through the entire branch where 8 is the parent maximizing node because the parent minimizing node would discard it anyway. The branch will of course be pruned regardless of which move comes out on top, as the maximizing side will have already picked a better move. 

In Alpha-Beta Pruning, we refer to the maximizing side (White) as Alpha and minimizing side as Beta. Concrete cases where we prune nodes or entire branches include cases where the score is greater than Beta score, in which case we return beta.

It is worth noting that the performance of Alpha-Beta Pruning is heavily dependent on the order by which moves are searched[21]. Therefore, performing some Move Ordering before any search is a crucial step to ensure a degree of performance gain. Aside from evaluation techniques that assign quiet, and capture move scores, some ordering tricks are performed such that “killer heuristics”[22], or nodes that caused an alpha-beta cutoff are given search priority for the next iteration.

Another slight improvement over Alpha-Beta Pruning is referred to as Principle Variation Search. The discussion on the logic behind alpha-beta nodes expands to include Principle Variation Nodes. These nodes refer to moves that are greater than Alpha, but none of them score higher than Beta.

The idea is simply that if the search finds a PV move, it will assume that, provided the move ordering is good enough, it will not be able to find a better PV move or a beta cutoff. In that case, the search is done with the sole purpose of proving that all the other moves are bad, and if it turns out that a value score is greater than that of the PV move, a re-search will occur. Although the process of researching is more expensive, the savings gained from performing PVS are much more substantial.

Figure 16 shows a sample implementation of Principle Variation Search on top of Alpha-Beta Pruning[23].


```

int AlphaBeta(int depth, int alpha, int beta) {

    BOOL fFoundPv = FALSE;

    if (depth == 0) return Evaluate();

    GenerateLegalMoves();

    while (MovesLeft()) {

        MakeNextMove();

        if (fFoundPv) {
            val = -AlphaBeta(depth - 1, -alpha - 1, -alpha);
            if ((val > alpha) && (val < beta)) // Check for failure.
                val = -AlphaBeta(depth - 1, -beta, -alpha);
        } else
            val = -AlphaBeta(depth - 1, -beta, -alpha);

        UnmakeMove();

        if (val >= beta)
            return beta;
        if (val > alpha) {
            alpha = val;

            fFoundPv = TRUE;
        }
    }
    return alpha;
}

```


**Figure 16: Principle Variation Search**

As seen from figure 16, when a PV node is found, we perform the search on a much smaller interval (Alpha, Alpha + 1). This search is referred to as Null Window or Zero Window search where **Beta = Alpha + 1**. The Null Window is used purely to check whether or not the PV node can be improved, and as stated earlier, the performance gains from these variants depend highly on move ordering.

Another key extension to Negamax with Alpha-Beta Pruning and PVS is the inclusion of Iterative Deepening. Instead of searching at the provided depth directly, we perform a search from depth 1 to N, iterating over each depth. Even if we decide to perform the search directly at depth 7 instead of using ID, the latter would still be faster due to optimizations that also include storing history moves (in addition to the killer moves).

It is worth noting that there are certain cases where when we search at a certain depth given unstable chess positions where pieces on the chessboard can be captured), the fixed-depth search may cause the issue of the Horizon Effect. A chess engine may not realize for instance that it can recapture a piece in the next turn, and it will not favor that position when it is down material in that depth. Running what is referred to as Quiescence Search at the conclusion of Negamax will include a limited branching factor, as we would only be looking at nodes representing capture moves.

When depth reaches 0 in alpha-beta search, instead of returning the static evaluation of the position, quiescence search looks at the capture moves that can occur in the position[24]. The search does not have to yield a capture move. In fact, it looks from personal observation that it is used to avoid falling for blunders where you are, for whatever reason, unable to detect that a queen is hanging on the board.

An additional improvement to search, which also relies on having move ordering pre-implemented, is what is known as Late Move Reductions. LMR is a technique that involves omitting moves that are ordered towards the very end. It is important however that not all moves are omitted. Chess Programming Wiki provides an overview of cases in which LMR should not be considered[25] as it may otherwise cause instabilities with regard to search accuracy.

These cases include



* PV-Nodes when performing a PVS search
* Tactical Moves (captures and promotions)
* Moves while in check or ones that give check.
* Depth &lt; 3 (or depth &lt; 2, results and search accuracy vary)


### 3.6.2 	Evaluation

Evaluation ranges across different aspects of the chess engine and differs in complexity. The most basic form of evaluation is the material score. Each chess piece holds particular importance based on its strength and mobility. In chess, players calculate their material advantage following this points system in Table 3.

**Table 3: Material Score in Classical Chess**


<table>
  <tr>
   <td><strong>Chess Piece</strong>
   </td>
   <td><strong>Material Score</strong>
   </td>
  </tr>
  <tr>
   <td>Pawn
   </td>
   <td>1
   </td>
  </tr>
  <tr>
   <td>Knight
   </td>
   <td>3
   </td>
  </tr>
  <tr>
   <td>Bishop
   </td>
   <td>3
   </td>
  </tr>
  <tr>
   <td>Rook
   </td>
   <td>5
   </td>
  </tr>
  <tr>
   <td>Queen
   </td>
   <td>9
   </td>
  </tr>
  <tr>
   <td>King
   </td>
   <td>Infinity
   </td>
  </tr>
</table>


Material evaluation in chess engines is very similar to that of classical in terms of weights. There may however be some differences in the way queens vs rooks or knights vs bishops are evaluated. As we can see from the figure, two rooks are worth more than a queen. But there are cases where a player would prefer the faster mobility coverage of the queen over the two rooks. In other aspects of chess, it is usually preferred to maintain what is referred to as the “Bishop Pair”, i.e. keeping both bishops on the board by trading pieces with the knights instead. A knight can move to any square on the board, unlike the bishop. But the latter has more mobility, which can be helpful in the endgame. The idea here is that piece scoring and evaluation are heuristics and require hundreds of games of testing, analysis, and tinkering parameters.

Another area of evaluation is referred to as positional scores. This is very useful when we know that a chess piece can have much better control over a position if it was to be at a given range of squares. Scores like these encourage the search to favor certain moves over others. For instance, it is better to play the knight in the center of the board, rather than on the edge for better overall central control. This does not mean that the knight will always be pushed towards the center. It may still play that move at a later depth if it sees that the knight can be re-routed to a more favorable position.

These positional scores do not assume piece occupancies over the board but rather a generalized assumption of where pieces should be developed overall. However, using what was established in the move generation, it is possible to use the attack masks for sliding pieces by calculating the number of bits (i.e. how many squares are controlled by the sliding piece) and accumulating a score based on the total number of controlled squares. This would further encourage the engine to favor positions where the piece can take control over sensitive squares, particularly during the middle game, or by setting up a “Fianchetto” position. Figure 17 illustrates a fianchetto position where the g pawn is pushed so that the bishop can move to g7 and have full control of the diagonals[26]. In the King’s Indian Defense, the knight goes to F6 so that any future knight move has the potential of causing a double threat by both knight and bishop pieces.



![image](https://user-images.githubusercontent.com/60394642/178802279-9cacba88-fb4b-4c78-a1bf-99f711577ef5.jpeg)


**Figure 17: Board illustration of a Fianchetto**

A Fianchetto position can also be set up in other chess openings. A queenside setup of the Fianchetto is also possible, some more contemporary openings with the bishop pair can include a double Fianchetto setup. All these strategies are part of a much grander chess theory of piece positioning and openings. Meaning that it is very welcome for an engine to follow such a theory based on a pure application of positional heuristics and search evaluation across the board.

Another notable area of evaluation is in captures. This area looks to maximize the material advantage when trading pieces, i.e. avoiding capturing a pawn with a queen if instead it can be captured by another pawn or a bishop. This is referred to as Most Valuable Victim - Least Valuable Aggressor. The implementation is based on a heuristics approach as it is about manually defining the best possible exchange and how it scores in comparison to other moves. Examples of such capture moves are Pawn(1pt) takes Knight(3pts), Bishop(3pts) takes Rook(5pts), or Pawn(1pt) takes Queen(9pts).	

Other notable evaluation techniques also incorporate penalties. The engine for instance can be penalized for having isolated pawns and double-stacked pawns. Pawn isolation means that the latter does not have any other pawns which are adjacent to it, while double-stacked pawns refer to instances where there are two or more pawns that are right on top of each other. These two situations can result in poor endgame performance which is why it is preferred that the engine ignores moves that cause it. Although it was previously mentioned that with MVV-LVA we would prefer taking a bishop using a pawn, for instance, the engine may discard the pawn capture if it results in an isolated pawn or a double pawn stack, unless necessary. Another important concept is what is known as a passed pawn. given a pawn on the F file, the pawn would be considered a passed pawn if there are no opponent pawns positioned in the E, F, and G files. Any quiet or capture moves that lead to a passed pawn are given priority as it becomes very likely that it creates an opportunity for pawn promotion. A similar idea, but is applied instead to rooks, states that the piece should find opportunities to move to higher ranks (6th rank and beyond) on the board, through an “Open File”, to restrict the opponent’s movement of the king and break their pawn structure.

It is worth noting that, provided that there is relatively good speed from the move generator, which can be partially satisfied by the very idea of Bitboards and Magic Numbers, the biggest bottleneck to a chess engine’s performance is the evaluation and move heuristics that are in place. This means that this literature review does not necessarily provide all the details regarding the kind of evaluation techniques being used in chess engines, but rather a fundamental look at the essentials that allow the engine to avoid moves that can be considered “objectively” bad.


### 3.6.3 	Zobrist Hashing

Some essential contributors to performance gains in terms of both search and evaluation aspects of the engine require some routines by which a chess position can be recognized through a unique identifier. One crucial routine involves the use of hash tables, specifically known as transposition tables, which will be covered in the next section.

Zobrist Hashing involves the idea of assigning random numbers to every chess-related parameter. These parameters involve the following: black chess pieces for every square in which a piece can fall into, white chess pieces for every square in which a piece can fall into, all four castling rights, turn to move, en passant rule for all 64 squares. Once all these chess parameters are initialized with random numbers, there would be two different ways of retrieving a position key, and that is based on the stage in which the engine instantiates the position.

If the engine is passed a FEN string, a hash generator can be called after the board setup and variable definitions. The way by which the hash key is created is simply by taking a key that, for instance, represents a black bishop on E4, and performing an XOR operation to assign its piece key to the hash key. The same operation is done if, for instance, the very piece is no longer available on the board.

The other way in which the hash key is updated is through the use of incremental hash updates. Although implementation wise it can be difficult to ensure that no chess parameters are not hashed properly, it remains a much more efficient option if compared to generating an entire hash key every time a MakeMove macro is called. Fortunately, we can ensure that the incremental hash updates work as intended when compared to the results brought by the hash generator during the debugging phase.

Hash numbers are usually 64-bits, making it very unlikely, but not impossible, to get the same hash key for two different positions[27]. With a 64-bit hash, a collision may be expected after 2^32, or rather 4 billion positions[28]. Concretely speaking, this case is too rare to cater to, as long as the program does not crash if a hash collision occurs, it should not severely impact the performance of the engine[29]. When implementing transposition tables, chess interfaces, and other areas where chess engines compete in games for testing, enforce a maximum of around 120 MB as a size for the transposition table. a position structure in the implementation can take around 20 bytes of space, meaning that the number of overall chess positions that are being stored should not exceed 6 million unique positions. Further decreasing the likelihood of a collision occurring.

Looking at the implementation of Zobrist Hashing to generate a unique identifier for each chess position that can be found, it would be valid to wonder why other unique representations of chess positions are not used, notably the FEN string. This is simply because XOR operations and dealing with integer calculations overall are much simpler and cost-efficient compared to string manipulations. This is especially noticeable when scaled to the millions of occurrences in which the calculation would need to take place. Using FEN and modifying its value would also require extra steps taken to ensure that a FEN string remains valid.


### 3.6.4 	Transposition Tables

As mentioned prior, there are many uses and benefits of incorporating Zobrist Hashing into a chess engine. Some of these help with move scoring, particularly in repetition detection. There are certain cases where, despite the engine being in complete control over the position and up material, it may still fall into three-fold repetition. Three-fold repetition is a rule in chess that ends the game in a draw if players repeat moves.

The main application for Zobrist Hashing though is in Transposition Tables or Hash Tables. During the search, we may establish that two or three identical board positions can be established but through a different move order. A board position, regardless of the order or the stage of the game in which it occurs, would always hold the same score. Using the transposition table, we may skip searching nodes that we have already seen in previous iterations, increasing search performance as a result.

A Transposition Table holds entries in a format that is specified in figure 18[30]. The sum of each entry amounts to 20 bytes, which explains the logic behind calculating the number of moves typically stored in a transposition table in the earlier section about Zobrist Hashing and the likelihood of collisions. Note that comments have been added to illustrate the size of each variable which amounts to a total of 20 bytes.


```
#define	hashfEXACT   0
#define	hashfALPHA   1
#define	hashfBETA    2
 
typedef struct tagHASHE {
	U64 hash_key; // 8 bytes - Note that U64 => Unsigned Long Long
	int depth;    // 4 bytes
	int flags;    // 4 bytes
	int value;    // 4 bytes
}   HASHE;
```


**Figure 18: A transposition table entry in the form of a C++ struct**

It is worth noting that hashfEXACT, hashfALPHA, and hashfBETA flags refer to the points in which the position was returned. Either as an exact score (which may be considered a PV move), an alpha score, or a beta score, which would have produced a cutoff. This is useful information that provides insight into how good the move was when it was first encountered during the search.

Storing the depth is also very important, it gives information on which depth the move was found. Assuming that the search incorporates iterative deepening with an expected depth of 8 when searching at depth 3, we may find a move in the transposition table that was mapped to a depth of 4. The search should not use that transposition because the expected initial search ply was 8, which is a much deeper search that should, in theory, give a more accurate best move.

In spite of the mention of how rare it is to encounter hash collisions; it does not mean that they should be ignored. There are certain methods to cater to these collisions that are directly related to the transposition entry parameters. The methods do not discard however the usefulness of storing the hash key at **collision_index + n**, given that n is the first empty array index, or the use of buckets (i.e. more than one transposition table), provided of course that not too many buckets are used as it would otherwise take time to look at all the buckets before determining that a move is new. Other methods do exist of course.

Aside from the simplest case, which is to directly assign the move to the resulting index without checking whether or not there is a collision, one of the easiest, and best, ways to counter collisions is by comparing the depths in which the two identical positions were found, the one position with the higher depth makes its score and alpha-beta flag to be more reliable[31].

Similar to the replacement strategy used to counter collisions, that same strategy, along with others, is used to mitigate the effects of filling up the transposition table. This can happen more often than not due to the size of the branching factor, all optimizations considered, especially when certain moves may no longer be relevant as the game moves forward towards the endgame. More research can be done to look exactly at how often some moves can be discarded based on their “age”. The age may be assigned to the half-moves count[32], indicating the stage at which the move was found in the game. The smaller the number, the earlier the stage of the game in which the move was found, the older the hash table entry is, and thus the less reliable it is.


### 3.7	Chess Interface

As mentioned previously in the feasibility study, the chess interface side of the project can be implemented in such a way that facilitates communication between the chess engine and the chess interface in which a graphical chessboard is visible. Regardless of whether or not a custom-made interface can be made and linked to the engine. It may be seen as impractical, or not a priority for several reasons. 

A scale of a chess interface can itself be considered a standalone project. Aside from providing support for a chess engine to be loaded into the interface. The interface needs to ensure that it can fact-check the legal aspects of all chess rules, moves, time controls, and so on. It should be able to apply all known time controls (bullet, chess, rapid, games with increment, etc.). Additionally, the chess engine should be able to modify aspects of an engine to ensure that, when two are paired together, they are playing at equal parameters. For instance, if the game search is based on a depth limit, one of the engines should not be able to search at a higher depth, another instance is that the transposition tables for both engines, assuming they are implemented for both engines, should be set to the same memory capacity.

In order to ensure that such properties are read in a cross-compatible way, chess engines and interfaces transmit and receive commands following a variety of protocols. The most notably known chess protocol is known as the Universal Chess Interface. Commands are used which pass the best move found by the engine “position fen &lt;fen_string> &lt;moves>”, to start the new engine “ucinewgame”, changing the transposition table size “setoption name Hash value &lt;number>”[33], etc.

For the purposes of this capstone project, the priority is to make the engine compatible with the UCI protocol. This step is crucial for future development of the engine, whether it involves the creation of a custom made engine that can be published online, or for its inclusion with the available chess interfaces.


##  4	IMPLEMENTATION & TESTING


### 4.1	Board Representation

In the implementation phase of the project, board representation has been achieved through the use of Bitboards. An Unsigned Long Long type definition is required to ensure that all bits are properly assigned to 64 bits and that there would be no cases where a signed bit unexpectedly disrupts any indexing or bitwise operations.

Figure 19 shows how white pawns are stored in a “white pawns” bitboard given the starting chess position.


```
0000000011111111000000000000000000000000000000000000000000000000
```


**Figure 19: White Pawns Bitboard in a Starting Position**

Once formatted, figure 19 is visualized in figure 20 as follows:


```
8      0  0  0  0  0  0  0  0
7      0  0  0  0  0  0  0  0
6      0  0  0  0  0  0  0  0
5      0  0  0  0  0  0  0  0
4      0  0  0  0  0  0  0  0
3      0  0  0  0  0  0  0  0
2      1  1  1  1  1  1  1  1
1      0  0  0  0  0  0  0  0

       A  B  C  D  E  F  G  H
```


**Figure 20: Bitboard Representation of White Pawns in a Starting Position**

An array containing 12 elements holds 12 bitboards, which can be indexed by pre-defined enum values. So instead of referring to a bitboard in the array by an integer value, it can be referred to by the piece (P for white pawn, p for black pawn, Q for the white queen, q for black queen, etc.). To retrieve all the pieces in one bitboard, it is enough to perform the OR operation through all 12 bitboards, as implemented in figure 21. Such operations are very CPU efficient, hence the adoption of the Bitboards approach for the Engine’s Board Representation.


```
for (int piece = P; piece <= K; piece++)
    piece_occupancy[white] |= piece_bitboards[piece];
        
for (int piece = p; piece <= k; piece++)
    piece_occupancy[black] |= piece_bitboards[piece];

piece_occupancy[both] |= piece_occupancy[white] | piece_occupancy[black];
```


**Figure 21: Extracting board information through piece and occupancy bitboards**

Eventually, the board can be constructed visually through the following steps:



1. Loop through all 64 board squares.
2. Within the parent loop, loop through all board pieces, like in figure 21.
3. Check if the square is occupied by one of the elements in the bitboards array.
4. If the square is occupied, print 1, otherwise print 0.

Step 3 is executed through a routine that performs an AND operation between a bitboard and a square bit. The result is 1 would of course mean that the square is occupied by a piece. The identity and color of the piece are known thanks to the earlier separation of all piece bitboards, as seen earlier. Step 4 is subject to some modifications to provide a better visual output. Instead of printing “1”, it is possible to print the chess piece symbols, as they are available as Unicode characters or piece acronyms because not all interfaces can support Unicode. Instead of printing 0, a simple dot can be shown instead for better visual navigation. While figure 2 shows the chess starting position in 1s and dots (or 0s), the same routine using Unicode yields the result in figure 22.



<img width="165" alt="image" src="https://user-images.githubusercontent.com/60394642/178803034-dbb08ca8-8fea-4573-8287-2b77f4689f5e.png">



**Figure 22: Chess Starting Position in Unicode**

It may become clear that certain operations will be required throughout the development of the engine. Such operations have been defined as macros for a more concise and readable implementation. Some of these macros are shown in figure 23 and are self-explanatory. 

Note that “~” means “NOT”. count_bits and ls1b use built-in methods which are provided by GCC.


```
# define is_bit_on_square(board, square) ((board) & (1ULL << square))
# define set_bit(board, square) ((board) |= (1ULL << square))
# define pop_bit(board, square) ((board) &= ~(1ULL << (square)))
# define count_bits(bitboard) __builtin_popcountll(bitboard)
# define ls1b(bitboard) (__builtin_ctzll(bitboard))
```


**Figure 23: A summary of some important macros used throughout the implementation**



Additionally, ”1ULL &lt;< square” means that the bit is left-shifted by the square value. If we would like to assign a bit to square B8, which through the enum definition translates to 1, means that the bit will be left-shifted by 1 so that it is set at the appropriate bit position within a 64-bit ULL bitboard.

The way by which Board Representation is set up will prove to be very efficient, especially when implementing move generation and conducting Perft tests.


### 4.2	Move Encoding

Before starting the work on generating moves and developing magic numbers, it is important to first build routines that help with move encoding, which should follow the specific bit allocation sequences shown in figure 3. Figure 24 provides a macro implementation of a move encoder.


```
# define encode_move(source, target, piece, promoted, capture, double, enpassant, castling)  \
(source)            | \
(target << 6)       | \
(piece << 12)       | \
(promoted << 16)    | \
(capture << 20)     | \
(double << 21)      | \
(enpassant << 22)   | \
(castling << 23)
```


**Figure 24: Move Encoder Macro Implementation**

This macro takes each argument, pushes its bits to their allocated range, which is specified by figure 3, returning ,as a result, one bitboard containing all information regarding source square, target square, the piece in question, whether the move is a promotion (and in case of that, which piece is it going to promote to), and/or a capture move, or an en passant move, or a castling move. The source and target squares are indeed represented as a ULL, while the other arguments are integers, all being integer Booleans except for the piece and promoted, which are regular integers.

All the information stored in the encoded move can be extracted through additional macro definitions. Each macro, say for instance seeing if the move is a capture, takes the move and performs an AND operation with the hexadecimal constant in which the capture flag bit is located. Refer to figure 3 for the list of hexadecimal constants and their binary representations.

This compact representation of moves is used so that they can be stored in a move list. A C++ struct is defined which would contain an array of moves and an integer for the count. Now once a move is found at the level of the move generator, it can easily be encoded and stored in the move list for search and evaluation.


### 4.3	Move Generation & Magic Numbers

Developing magic numbers is an integral part of move generation for this implementation. Now that the move list is available and moves can be encoded through the aforementioned macro definitions, a long set of routines are due to be implemented in order to generate attack moves for sliding and non-sliding pieces.

The first set of routines involves the creation of piece attack masks. Each piece requires its own logic to follow. For instance, masking bishop moves given a square can involve 4 separate masks for each diagonal relative to the square. Rooks mask the file and rank that correspond to the square. It is worth reiterating that for attack masks, we do not include the border squares (i.e. the first and last files and ranks) as explained in the magic numbers section of the literature review. The resulting bitboard would look like the example in Table 1 regarding the magic index extraction through the Rook Mask on C3. There are additional routines for sliding pieces that involve masking the edge squares as well to generate magic numbers. All pieces, with the exception of pawns, move in the same way regardless of their color.

Once all the routines for generating masks are ready, the next steps involve the extraction of the magic number. Note that for this capstone project, magic numbers are being created manually rather than extracted from the web.

A direct implementation of the explanations following the literature review is laid down in the following figure 25. A find_magic function takes the square, the occupancy bits for that piece given the square, and the piece type.


```
for (int square = 0; square < 64; square++)
    printf("0x%llxULL,\n", find_magic(square, rook_occupancy_bits[square],                            
    rook));
```


**Figure 25: Finding magics for the Rook**

Note that the rook and bishop occupancy bits is nothing but the number of squares that can be attacked by the piece, assuming an empty board. Such a number does not need to be calculated as each square yields a fixed number of bits. One way to take advantage of this idea is by having an array that contains pre-calculated occupancy bits for both the rook and bishop. Table 4 shows the relevant occupancies for rooks and bishops. The table can be read by taking into consideration that the first index refers to A8 and that the edge squares are not considered relevant.

**Table 4: Sliding Pieces Relevant Occupancy Bits**


<table>
  <tr>
   <td>rook_relevant_occupancy_bits[64]
   </td>
   <td>bishop_relevant_occupancy_bits[64]
   </td>
  </tr>
  <tr>
   <td><strong><code> 12, 11, 11, 11, 11, 11, 11, 12,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code> 11, 10, 10, 10, 10, 10, 10, 11,</code></strong>
<strong><code>12, 11, 11, 11, 11, 11, 11, 12</code></strong>
   </td>
   <td><strong><code>6, 5, 5, 5, 5, 5, 5, 6,</code></strong>
<strong><code>5, 5, 5, 5, 5, 5, 5, 5,</code></strong>
<strong><code>5, 5, 7, 7, 7, 7, 5, 5,</code></strong>
<strong><code>5, 5, 7, 9, 9, 7, 5, 5,</code></strong>
<strong><code>5, 5, 7, 9, 9, 7, 5, 5,</code></strong>
<strong><code>5, 5, 7, 7, 7, 7, 5, 5,</code></strong>
<strong><code>5, 5, 5, 5, 5, 5, 5, 5,</code></strong>
<strong><code>       6, 5, 5, 5, 5, 5, 5, 6</code></strong>
   </td>
  </tr>
</table>


The algorithm showcased in figure 8 is now used to generate the magics. It is worth noting that the “get_occupancy_set” in said algorithm refers to a routine that returns a mask of either the rook or bishop given an index and the relevant occupancy bits. The main idea behind it is as follows: 

Given for instance a rook on H1. The number of squares that it can move to, excluding the edges and the square in which it is located, is 12. Now, on a real board, the actual number is not always going to be 12 but rather a value from 0 to 12. Now the function generates all the possible combinations given all possible occupancies that change the output of the moves which can be done by the piece. The exact number of combinations is 2^12 = 4096. This also explains why Tord Romstad’s algorithm of the brute-force may involve loops or array definitions that are set at 4096, being the highest possible cardinality of the moves sample space.

The following step of generating the magics can be described as follows:



1. Loop infinitely or stop at some number set in the millions.
2. Generate a random 64-bit number.
3. Generate a magic index using the operation of **mask * bits >> (64 - nbits)** described in the literature review.
4. Now loop over all the generated occupancy sets (all 4096 of them as the worst case) and ensure that this magic index can successfully be used to index a piece mask given all the possible occupancies.
5. On each iteration, assign to a “used” array, through the magic index, the attacks of the piece, which now include the edge squares. If the “used” array indexed by the magic index is already occupied, it needs to contain the exact same attack mask, otherwise, the magic index for the square is not valid and a new random number will have to be assigned and tested.
6. Once the index is validated, return it. The function has now returned a magic number for a rook or bishop for a specific square. This means that the same process is done 64 times for the rook and another 64 for the bishop.

**Appendices A** and **B **provide the list of generated magic numbers for both the rook and bishop during the engine implementation.

Finally, the pre-calculated sliding piece attacks are generated through the new magic numbers using the same process that was exemplified in the magic numbers section of the literature review.

The magic numbers take about 8 seconds in total to be generated. The length it takes and the degree of efficiency in the generator are not relevant enough to constitute a need to improve the generation time. This is due to the fact that they are hardcoded, as provided in Appendices A and B.

Now that we have the pre-calculated attack tables for both sliding and non-sliding pieces, and before moving to the process of generating all the moves, there is another important routine to introduce, which is regarding the detection of whether or not a certain square is attacked. Figure 26 provides the implementation of this routine.


```
static inline int is_square_attacked(int square, int side) {
    if (side == white) {
        return ((pawn_attack_moves[black][square] & piece_bitboards[P])
        | (knight_attack_moves[square] & piece_bitboards[N])
        | (king_attack_moves[square] & piece_bitboards[K])
        | (get_bishop_attacks(square, piece_occupancy[both]) & piece_bitboards[B])
        | (get_rook_attacks(square, piece_occupancy[both]) & piece_bitboards[R])
        | (get_queen_attacks(square, piece_occupancy[both]) & piece_bitboards[Q])) ? 1 : 0;
    } else if (side == black){
        return ((pawn_attack_moves[white][square] & piece_bitboards[p])
        | (knight_attack_moves[square] & piece_bitboards[n])
        | (king_attack_moves[square] & piece_bitboards[k])
        | (get_bishop_attacks(square, piece_occupancy[both]) & piece_bitboards[b])
        | (get_rook_attacks(square, piece_occupancy[both]) & piece_bitboards[r])
        | (get_queen_attacks(square, piece_occupancy[both]) & piece_bitboards[q])) ? 1 : 0;
    }
    return 0;
}

```


**Figure 26: Detecting whether a square is attacked on the board**

There is no one way to generate all the moves given. The process can and has produced bugs as it can be easy to miss some details in the conditions and move encoding parameters. The main framework uses most of the macros that were previously introduced. Briefly speaking, the process of generating all the moves given a bitboard value can be summarized in the following steps:



1. Loop over all the pieces from White Pawn to Black King. (P to k inclusive).
2. Create a copy of the piece_bitboards[piece]. The program is interested in the piece-specific bitboard rather than all the pieces at once.
3. Extract the least significant first bit of the bitboard copy, this bit is essentially the source square.
4. Check the piece type
    1. If the piece is a pawn, check its location to see whether it can perform a double pawn push or if it is high enough on the board (assuming it is white to move) that it can be promoted. It is also important to check if en passant is available. Checks for en passant captures, regular captures, promotion captures, and quiet moves are also necessary for move generation.
    2. If the piece is a king, check if castling from both sides is available and generate all pseudo-legal moves of the king. Note that pseudo-legal does not consider whether the move results in the king falling into a check. This check is taken care of by the Copy Make approach of internally making the move and then checking its effects before deciding on its legality. It is also required to check for quiet and capture moves and encode them as well before proceeding.
    3. The other pieces, since do not affect castling and en passant, use a quiet and capture moves check.
5. Once the checks are done, the piece bit is popped from the bitboard copy, and the next bit is inspected until all bits are examined.
6. The move list is generated and returned for reference in the next routines.

Before moving to test whether or not the move generator works as intended and does not discard certain legal moves or includes illegal moves, Perft testing must be successful. It seems that the usual way to test a move generator is by providing a specific FEN sequence that is already documented and making sure that the results yielded from the Perft test are identical to the documentation. Otherwise, it would mean that there are bugs in the move generator.

Performing the Perft test is preceded by the necessity to include support for parsing FEN strings to the engine.


### 4.4	Forsyth-Edwards Notation

The FEN parsing function is quite short; it does not contain much logic aside from traversing the string and parsing each letter (piece) or number (number of empty squares). **Appendix C** provides a simplified implementation that assumes that the engine will always receive **valid** FEN strings. Note that the FEN Parser provided is in its final version, hence the inclusion of repetition variables and Zobrist Hashing definitions.


### 4.5	Perft Testing

Now that both the move generator and FEN parser are ready, Perft can be conducted on three chess positions chosen from Chess Programming Wiki[19]. Figures 27, 28, and 29 consist of these three chess positions.



![image](https://user-images.githubusercontent.com/60394642/178803106-1612b065-f105-4877-9530-45386f2fca6c.jpeg)



**Figure 27: Perft - Position #1- **

**r3k2r/p1ppqpb1/bn2pnp1/3PN3/1p2P3/2N2Q1p/PPPBBPPP/R3K2R w KQkq -**


### 

![image](https://user-images.githubusercontent.com/60394642/178803159-4793edc8-286f-4a3f-b2d3-3bf20de0c614.jpeg)



**Figure 28: Perft - Position #2 -** 

**rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1**



![image](https://user-images.githubusercontent.com/60394642/178803210-b62b0d73-0913-4b33-9c4b-37ff020f86cd.jpeg)


**Figure 29: Perft - Position #3 - **

**r3k2r/Pppp1ppp/1b3nbN/nP6/BBP1P3/q4N2/Pp1P2PP/R2Q1RK1 w kq - 0 1**

The Perft tests use the Copy/Make approach discussed in the literature review section of this report. The macros that enable this approach have been implemented and are available in Appendix D

Position #1 shown in Figure 27 resulted in a number of nodes of **8,031,647,685** at depth 6. This is identical to the results reported at Chess Programming Wiki[19]. **Appendix E **shows the execution window of Monza, the name of the chess engine developed throughout this capstone project. **Appendices F** and **G** also show the perft results of the other two positions. Position 2 traverses **3,195,901,860** nodes at depth 7, and Position 3, which consists of a white king in check, traverses** 706,045,033 **nodes** **at depth 6 and returns all the legal moves. 

Through the Perft test, we can estimate how fast Monza really is. The speed determines how fast can the engine reach high search depths, which would ultimately lay the ground for potentially highly valued moves once solid evaluation methods are implemented. There are some caveats to keep in mind though when comparing one engine’s speed to another’s. Using compiler optimization flags like “-Ofast” can, if the code is stable, yield significant speed results[34] to C++ build files, especially the engine for this case.  Other engines may also use multithreading to speed up the search as well or report speed scores that were conducted using high-end machines.

It is worth noting that slow engine speed is not detrimental to its capabilities. Putting solid evaluations in place can allow the engine to search through much fewer nodes and provide an accurate result. However, it is favorable to at least have a solid search speed. Stockfish, currently the top engine in the world in terms of rating and users, runs at around 5000 kn/s for an average 4 CPU local machine[35]. A high-end machine can support up to 20.000kn/s, with local servers and cloud infrastructures being able to run at 50.000kn/s and beyond to even 1m kn/s, respectively.

The machine in which the Monza Perft Test was conducted used the -Ofast optimization flag, was developed and executed on an M1 Macbook Pro 2020 with 16Gb RAM, and no explicit threading instructions were implemented. As we can see from the Appendices E, F, and G, Position #1 ran at an average speed of  **8031647685 nodes / 184.310 seconds = 43,576,841.6527 n/s. **Which is about 43 million nodes per second. The other positions yielded **46,812,682.8768 n/s **and **41,666,865.329 n/s**, respectively. 

It is quite clear that these test numbers are impressive, given the limited time frame in which development has taken place. These numbers are also backed by the efficient utilization of bitboards and magic numbers for board representation and move generation. It also becomes much clearer than most, if not any sources of bottlenecks to the engine’s performance will be down to how good the search is, and most importantly, the evaluation methods and routines of the engine.


### 4.6	Search & Evaluation

The first search function that was implemented was Negamax Search. As explained earlier, this search function cannot be used alone due to the exponential branching factor in chess. The discussion in the literature review regarding the kind of optimizations which can be implemented has been used in Monza for the most part. The exact routines and methods used in the search are as follows:



* Negamax Search
* Alpha-Beta Pruning
* Principle Variation Search
* Quiescence Search
* Iterative Deepening
* Late Move Reductions
* Move Ordering
* Zobrist Hashing
* Transposition Tables

Notable evaluation techniques used for Monza, and as expanded on previously, are as follows:



* Piece Material Score
* Piece Positional Score
* Killer Moves / Heuristics
* MVV-LVA
* Passed Pawn and Open File Bonuses
* Isolated Pawns and Stacked Pawns Penalties
* Mate Bonuses
* Stalemate Detection
* Mobility Scoring
* King Safety
* Move Repetition Detection

The next portion of this chapter will discuss the improvements yielded from performing searches at different periods of the implementation. The aim behind this is an attempt at providing concrete information regarding search and evaluation optimizations that significantly improved the search.

Figure 27 is the chess position in which the testing and performance comparisons were conducted. Because we have information on the nodes from a Perft test point of view, it is interesting to look at it from the search and evaluation view as well.

For a more convenient visualization of search improvements, table 5 shows the point at which certain routines were introduced and their effect on the cumulative nodes, again keeping in mind that the position from figure 27 is the one being tested here.

**Table 5: Performance gains from different points of the Chess Engine Implementation**


<table>
  <tr>
   <td><strong>Milestone / Points of Implementation</strong>
   </td>
   <td><strong>Search Results</strong>
   </td>
  </tr>
  <tr>
   <td>Negamax with Alpha-Beta Pruning
   </td>
   <td>depth 7 nodes 180,149,650 - bestmove e2a6
   </td>
  </tr>
  <tr>
   <td>
<ul>

<li>Move Ordering & Iterative Deepening
</li>
</ul>
   </td>
   <td>depth 7 nodes 3,098,381 - bestmove e2a6
   </td>
  </tr>
  <tr>
   <td>
<ul>

<li>Killer Moves Ordering & PVS
</li>
</ul>
   </td>
   <td>depth 7 nodes 2,789,750
<p>
depth 8 nodes 12,211,778
   </td>
  </tr>
  <tr>
   <td>
<ul>

<li>LMR
</li>
</ul>
   </td>
   <td>depth 7 nodes 426,654
<p>
depth 8 nodes 2,559,833
   </td>
  </tr>
  <tr>
   <td>
<ul>

<li>Transposition Tables
</li>
</ul>
   </td>
   <td>depth 7 nodes 172,789
<p>
depth 8 nodes 1,323,587
   </td>
  </tr>
</table>


It is worth noting that the gains from these search and evaluation techniques can differ from position to another. Despite the significant savings that are noticed from the points of Negamax alone to the phase in which Transposition Tables were implemented, it does not mean that the engine will necessarily play the best move unless the evaluation is solid. This is something that cannot be necessarily conducted through number-crunching easily but rather through playing games, hundreds of games in fact. This means that despite the huge gains and speed numbers that make this comparable to many production engines, it should be no surprise if it cannot consistently beat said engines. Hence the earlier mention of why the biggest bottleneck of a bitboard engine is by far the implementation of its evaluation.

For instance, some chess engines with a relatively straightforward implementation of evaluation routines have seen a significant boost in their game performance, sometimes more than 80% (this jump in performance is similar to the jump from a chess rookie to a super grandmaster in chess), after the implementation of a third-party Neural Network evaluation library from Stockfish that is available publicly[36]. NNUEs are very much new, less than 5 years old from this report’s date. This remains something that is worth exploring as it also involves a different area of study involving Neural Networks. NNUEs have not been discussed nor implemented in this report due to the scale of such an area that can even warrant its standalone research topic.


### 4.7	Chess Interface / UCI Protocol Implementation

Thanks to the implementation of the UCI Protocol, a user can not only interact with the engine through a CLI but also through a third-party chess interface. A notable interface, known as Arena Chess[37] can be used to plug any engine with support for UCI or other protocols for analysis or to match one another. Figure 30 shows an Arena interface linked with the Monza Chess Engine.



<img width="460" alt="image" src="https://user-images.githubusercontent.com/60394642/178803274-39ceed68-e79c-4021-8116-5a6506a6f7a4.png">




**Figure 30: Arena Chess Interface connected to Monza Chess Engine**

UCI documentations are available across the web[38]. While the list is indeed exhaustive, a chess engine is not obliged to support all the listed commands. It may be favorable to the engine to support time controls too. Thanks to iterative deepening, the engine can give itself a time limit that can dynamically change based on how much time is left in a game, and return the best move found within that time window. This can allow for different configurations that include ideas where the engine can take its time to return a move at the beginning of the game but yield moves quicker when there is less time remaining. Depending on the length of the game (Bullet, Blitz, Rapid, etc.), the engine can calibrate itself to follow the pace of the match.

Note that Appendices H, I, and J contain PGN sequences of games played which either involve the engine against another chess engine rated around 1900 or against a human chess player, with a far less impressive rating of around 1000 (myself). A Stockfish analysis of the game, which is available in Appendix J, was conducted through the Chess dot com service which resulted in a move accuracy for Monza of about 90%[39]. Appendices K & L comprise of games played between Monza and versions of Komodo (1800) and (2000). Monza won the first game and drew the second. The games were conducted by manually inputting the board position to Monza, receiving the best move, and playing it on the website in which the version of Komodo was available. This was made simple through using FENs in the UCI protocol of Monza.


### 4.8	Open Sourcing the Project

The process of open sourcing the project is not in its final form. There is a long upcoming process of understanding engine weaknesses, improving code readability, cleaning unused aspects, and improving its overall presentation. The main aspects that make a project openly available are set through its availability (although yet to turn public as per the date of this report) on GitHub and overall version control mechanics that can easily convert this project, this report included, into a public contribution to the chess programming community.


<img width="453" alt="image" src="https://user-images.githubusercontent.com/60394642/178803308-6f699423-b19a-4557-b2c9-c81de7b629ad.png">


**Figure 31: Monza Chess Engine CLI**


## 


## 5   	STEEPLE ANALYSIS


### 5.1 	Societal Implications

The way this capstone project is laid out aims to involve more programmers in the world of chess programming, given the intention of converting this project into an open-source space where people can contribute and provide improvements and bug fixes to the codebase. It is also yet an additional source for players and programmers to learn from its implementation details and use it to improve their own play.


### 5.2	Technological Implications

Although the project uses numerous technologies and different adaptations that may not necessarily be manipulated and combined in the exact way this project does, it does not by any means imply that there would be a distinct technological impact on the technology being used itself. However, this does not discard the potential growth of an open-source project like this and the extent to which it can contribute, given the involvement of the chess programming community, to new implementations and ideas.


### 5.3	Economic Implications

Most powerful chess engine projects are free and open source. But they may not necessarily follow the best practices in terms of reachability and ease of access, unless using chess services that may or may not involve a subscription aspect. Seeing how big the current services are as players in the market and select open-source platforms, it is not expected that this project yields a significant economic impact if any.


### 5.4	Environmental Implications

The creation of the chess engine, its execution, or any of the technologies involved in its creation will not yield any environmental implications. Much of this project is considered an educational endeavor and it is beyond expectations that the scale of this project would yield any environmental implications.


### 5.5	Political Implications

As per the date of this report's publication, there are no political implications, restrictions, or other details that fall within this framework that would be affected by building and deploying a chess engine.


### 5.6	Legal Implications

Unlike other games like Uno, Monopoly, Scrabble, and other board games, there are no trademarks that tie the game of chess to a certain entity or organization. This means that the implementation of the chess engine does not by any means violate any legal aspects of the game or its open-source future. There is however one aspect that ties both legal and ethical aspects that are brought to attention in the next section of the STEEPLE analysis as a potential ethical implication.


### 5.7	Ethical Implications

One of the biggest aims behind this capstone is to shed more light on the world of chess programming and help newcomers to the field with an open-source and available source code of a modern chess engine. However, a typical application of this engine is also to use it for what it is, a chess engine that helps you find “the best next move” given a position, or help you solve a chess puzzle. There are however ethical implications that immediately arise from these applications, not only are they concerned with chess engines, but they include all different bots or helper tools that put one player at an unfair advantage. Service providers like Chess Dot Com do not tolerate the use of a chess engine during “live chess” but provide you access to an engine in order to help you learn from your game after its conclusion. But the engine can also be used during someone else’s live chess game provided that there is no way the players involved in the game get information from an engine or any people operating it at that time. An example of a service that bans the use of chess engines is Lichess given a section of their terms and services[40]: “We **prohibit** the use of any **external assistance** used whilst a game you are involved in is ongoing, which has the **effect of improving** your knowledge, calculation ability, or otherwise gives you an unfair advantage over your opponent. Examples of cheating include, but are not limited to, using a **chess engine,** opening books, endgame tables, receiving move recommendations from another person or software (including human commenters whilst streaming or social media services), and certain software or extensions at our discretion.”


## 6   	CONCLUSION

Most of the fundamental and crucial goals have been achieved successfully, with some aspects turning out to be better than expected, especially with regard to the search optimizations that the engine was able to achieve. It is a positive note to see how much knowledge and research goes into the development of a chess engine of this kind. In spite of the existence of numerous engines, the documentation is not as widely available with a lot of resources existing purely on Web Archives.

Of course, the engine is not perfect, it is far from that. But the amount of work that has gone into its development has laid the ground for a very promising future that can see the engine climbing up the ladder to impressive levels of performance and game accuracy. The amount of research that is upcoming is certainly far beyond what has been done to produce this project. Both the research and implementation process of this capstone started in mid-January, with a consistent number of hours per week (10-20 hours) going into its development. This can only show the scale of such a project, especially given minimal background knowledge regarding the inner workings of a chess engine, and a lot of interest. 

The next steps involve studying the engine itself in greater detail, especially by looking at game performance, understanding its evaluation weaknesses, and working to improve on them. It is also interesting to explore Tapered Evaluation. In the current version of the engine, positional and material scores are constant throughout the game phases. Tapered Evaluation however introduces in-game adjustments to said scores as the game phases move from the opening to the middle game, and towards the endgame[41]. It is also interesting to look at the implementation of an opening and an endgame database. One of the main reasons why these two aspects have not been implemented as of yet was down to some ambiguity with regards to whether it is ethical to embed an opening database directly into an engine, rather than keep it as a pluggable integration.

Finally, and for the learning purposes of the capstone, an off-the-shelf Stockfish NNUE was not implemented despite the significant performance impact it would have on the chess engine. This, however, does not prevent the possibility of exploring Neural Networks for chess evaluation, and even introducing them at the later stage of engine development.

The biggest challenges during the implementation were about understanding, which has not been fulfilled to a maximum extent, but enough to constitute fundamental understanding and an ability to explain these concepts to a certain level of depth to the uninitiated in chess programming. A growing collection of Monza games are documented on an archive in chess dot come website[42]. Some of the most impressive games include wins against two 1800 and 1900 rated engines, and a draw (from what was a winning position for Monza) against a 2000-rated engine that constitutes a particular version of Komodo. It is worth noting that later versions of Komodo have taken part and won multiple installments of the Top Chess Engine Championship, they are considered Commercial Engines (not free to use), and are backed by a chess grandmaster to examine and improve its evaluation.




## 7	REFERENCES


        [1] “Stockfish,” _Stockfish - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Stockfish#Board_Representation](https://www.chessprogramming.org/Stockfish#Board_Representation). [Accessed: 18-Apr-2022]. 


        [2] “Leela chess zero,” _Leela Chess Zero - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Leela_Chess_Zero#Board_Representation](https://www.chessprogramming.org/Leela_Chess_Zero#Board_Representation). [Accessed: 18-Apr-2022]. 


        [3] Jhonnold, “Jhonnold/Berserk: UCI Chess engine written in C,” _GitHub_. [Online]. Available: [https://github.com/jhonnold/berserk](https://github.com/jhonnold/berserk). [Accessed: 18-Apr-2022]. 


        [4] _Chess Program Board representations_. [Online]. Available: [https://web.archive.org/web/20130212063528/http://www.cis.uab.edu/hyatt/boardrep.html](https://web.archive.org/web/20130212063528/http://www.cis.uab.edu/hyatt/boardrep.html). [Accessed: 18-Apr-2022]. 


        [5] “0x88,” _Wikipedia_, 01-Jan-2022. [Online]. Available: [https://en.wikipedia.org/wiki/0x88](https://en.wikipedia.org/wiki/0x88). [Accessed: 18-Apr-2022]. 


        [6] “Bitboard,” _Bitboard - Rules and strategy of tabletop games_. [Online]. Available: [http://gambiter.com/tabletop/Bitboard.html](http://gambiter.com/tabletop/Bitboard.html). [Accessed: 18-Apr-2022]. 


        [7] “Encoding moves,” _Encoding Moves - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Encoding_Moves](https://www.chessprogramming.org/Encoding_Moves). [Accessed: 18-Apr-2022].


        [8] “Pseudo-legal move,” _Pseudo-Legal Move - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Pseudo-Legal_Move](https://www.chessprogramming.org/Pseudo-Legal_Move). [Accessed: 18-Apr-2022]. 


        [9] “Forsyth-Edwards notation,” _Forsyth-Edwards Notation - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Forsyth-Edwards_Notation#FEN_Syntax](https://www.chessprogramming.org/Forsyth-Edwards_Notation#FEN_Syntax). [Accessed: 18-Apr-2022].  


        [10] “Magic move-bitboard generation in computer chess - pradu.” [Online]. Available: [http://pradu.us/old/Nov27_2008/Buzz/research/magic/Bitboards.pdf](http://pradu.us/old/Nov27_2008/Buzz/research/magic/Bitboards.pdf). [Accessed: 18-Apr-2022]. 


        [11] R. Rustad-Elliott, “Fast chess move generation with magic bitboards,” _Rhys Rustad-Elliott – Fast Chess Move Generation With Magic Bitboards_. [Online]. Available: [https://rhysre.net/fast-chess-move-generation-with-magic-bitboards.html](https://rhysre.net/fast-chess-move-generation-with-magic-bitboards.html). [Accessed: 18-Apr-2022]. 


        [12] _Chess move generation with Magic Bitboards_. [Online]. Available: [https://essays.jwatzman.org/essays/chess-move-generation-with-magic-bitboards.html](https://essays.jwatzman.org/essays/chess-move-generation-with-magic-bitboards.html). [Accessed: 18-Apr-2022]. 


        [13] “Magic bitboards,” _Rival Chess Engine RSS_. [Online]. Available: [https://web.archive.org/web/20180109042730/http://www.rivalchess.com:80/magic-bitboards](https://web.archive.org/web/20180109042730/http://www.rivalchess.com:80/magic-bitboards). [Accessed: 18-Apr-2022]. 


        [14] “Magic bitboards,” _Magic Bitboards - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Magic_Bitboards](https://www.chessprogramming.org/Magic_Bitboards). [Accessed: 18-Apr-2022]. 


        [15] “Looking for magics,” _Looking for Magics - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Looking_for_Magics](https://www.chessprogramming.org/Looking_for_Magics). [Accessed: 18-Apr-2022]. 


        [16] “Talkchess.com,” _Magic Move Generation - Page 2 - TalkChess.com_. [Online]. Available: [http://www.talkchess.com/forum3/viewtopic.php?topic_view=threads&p=175834&t=19699](http://www.talkchess.com/forum3/viewtopic.php?topic_view=threads&p=175834&t=19699). [Accessed: 18-Apr-2022]. 


        [17] “Perft,” _Perft - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Perft](https://www.chessprogramming.org/Perft). [Accessed: 18-Apr-2022]. 


        [18] “An obvious place to start,” Min-Max Search. [Online]. Available: [https://web.archive.org/web/20071030220820/http://www.brucemo.com/compchess/programming/minmax.htm](https://web.archive.org/web/20071030220820/http://www.brucemo.com/compchess/programming/minmax.htm). [Accessed: 18-Apr-2022]. 


        [19] “Perft results,” _Perft Results - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Perft_Results](https://www.chessprogramming.org/Perft_Results). [Accessed: 18-Apr-2022]. 


        [20] “File:ab pruning.svg,” _Wikimedia Commons_. [Online]. Available: [https://commons.wikimedia.org/wiki/File:AB_pruning.svg](https://commons.wikimedia.org/wiki/File:AB_pruning.svg). [Accessed: 18-Apr-2022]. 


        [21] “The problem with Min-Max,” _Alpha-Beta Search_. [Online]. Available: [https://web.archive.org/web/20071030084528/http://www.brucemo.com/compchess/programming/alphabeta.htm](https://web.archive.org/web/20071030084528/http://www.brucemo.com/compchess/programming/alphabeta.htm). [Accessed: 18-Apr-2022]. 


        [22] L. Walker, “The anatomy of a chess ai,” _Medium_, 21-Aug-2020. [Online]. Available: [https://medium.com/@SereneBiologist/the-anatomy-of-a-chess-ai-2087d0d565](https://medium.com/@SereneBiologist/the-anatomy-of-a-chess-ai-2087d0d565). [Accessed: 18-Apr-2022]. 


        [23] “An enhancement to alpha-beta,” _Principal Variation Search_. [Online]. Available: [https://web.archive.org/web/20071030220825/http://www.brucemo.com/compchess/programming/pvs.htm](https://web.archive.org/web/20071030220825/http://www.brucemo.com/compchess/programming/pvs.htm). [Accessed: 18-Apr-2022]. 


        [24] “MVV/LVA,” _Quiescent Search_. [Online]. Available: [https://web.archive.org/web/20071027170528/http://www.brucemo.com/compchess/programming/quiescent.htm](https://web.archive.org/web/20071027170528/http://www.brucemo.com/compchess/programming/quiescent.htm). [Accessed: 18-Apr-2022]. 


        [25] “Late move reductions,” _Late Move Reductions - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Late_Move_Reductions](https://www.chessprogramming.org/Late_Move_Reductions). [Accessed: 18-Apr-2022]. 


        [26] “Fianchetto - chess terms,” _Chess.com_. [Online]. Available: [https://www.chess.com/terms/fianchetto-chess](https://www.chess.com/terms/fianchetto-chess). [Accessed: 18-Apr-2022]. 


        [27] U. Singh, “Zobrist hashing,” _OpenGenus IQ: Computing Expertise & Legacy_, 22-Jul-2018. [Online]. Available: [https://iq.opengenus.org/zobrist-hashing-game-theory/](https://iq.opengenus.org/zobrist-hashing-game-theory/). [Accessed: 18-Apr-2022]. 


        [28] “Zobrist hashing,” _Zobrist Hashing - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Zobrist_Hashing](https://www.chessprogramming.org/Zobrist_Hashing). [Accessed: 18-Apr-2022]. 


        [29] “A means of enabling position comparison,” _Zobrist Keys_. [Online]. Available: [https://web.archive.org/web/20071031100138/http://www.brucemo.com/compchess/programming/zobrist.htm](https://web.archive.org/web/20071031100138/http://www.brucemo.com/compchess/programming/zobrist.htm). [Accessed: 18-Apr-2022]. 


        [30] “A multi-purpose data structure,” _The Main Transposition Table_. [Online]. Available: [https://web.archive.org/web/20071031100051/http://www.brucemo.com/compchess/programming/hashing.htm](https://web.archive.org/web/20071031100051/http://www.brucemo.com/compchess/programming/hashing.htm). [Accessed: 18-Apr-2022]. 


        [31] “Transposition tables,” _Mediocre Chess_. [Online]. Available: [http://mediocrechess.sourceforge.net/guides/transpositiontables.html](http://mediocrechess.sourceforge.net/guides/transpositiontables.html). [Accessed: 18-Apr-2022]. 


        [32] “Transposition table,” _Transposition Table - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Transposition_Table#Aging](https://www.chessprogramming.org/Transposition_Table#Aging). [Accessed: 18-Apr-2022]. 


        [33] _UCI protocol_. [Online]. Available: [http://wbec-ridderkerk.nl/html/UCIProtocol.html](http://wbec-ridderkerk.nl/html/UCIProtocol.html). [Accessed: 18-Apr-2022]. 


        [34] _Optimize options (using the GNU compiler collection (GCC))_. [Online]. Available: [https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html). [Accessed: 18-Apr-2022]. 


        [35] “NPS - what are the ‘nodes per second’ in chess engine analysis,” _Chessify_. [Online]. Available: [https://chessify.me/blog/nps-what-are-the-nodes-per-second-in-chess-engine-analysis](https://chessify.me/blog/nps-what-are-the-nodes-per-second-in-chess-engine-analysis). [Accessed: 18-Apr-2022]. 


        [36] “Introducing NNUE evaluation,” _Stockfish_. [Online]. Available: [https://stockfishchess.org/blog/2020/introducing-nnue-evaluation/](https://stockfishchess.org/blog/2020/introducing-nnue-evaluation/). [Accessed: 18-Apr-2022]. 


        [37] “Features,” _Arena Chess GUI_. [Online]. Available: [http://www.playwitharena.de/](http://www.playwitharena.de/). [Accessed: 18-Apr-2022]. 


        [38] _UCI (=universal chess interface)_. [Online]. Available: [http://page.mi.fu-berlin.de/block/uci.htm](http://page.mi.fu-berlin.de/block/uci.htm). [Accessed: 18-Apr-2022]. 


        [39] “Chess Analysis Board and PGN editor,” _Chess.com_. [Online]. Available: [https://www.chess.com/analysis/game/pgn/3Zhhtky7EW](https://www.chess.com/analysis/game/pgn/3Zhhtky7EW). [Accessed: 18-Apr-2022]. 


        [40] “Lichess.org,” _Terms of Service • lichess.org_. [Online]. Available: [https://lichess.org/terms-of-service](https://lichess.org/terms-of-service). [Accessed: 18-Apr-2022]. 


        [41] “Tapered eval,” _Tapered Eval - Chessprogramming wiki_. [Online]. Available: [https://www.chessprogramming.org/Tapered_Eval](https://www.chessprogramming.org/Tapered_Eval). [Accessed: 18-Apr-2022]. 


        [42] “Monza | Game Library”. _Monza_ - _Chess.com. _[Online]. Available: [https://www.chess.com/library/collections/monza-2GVK9VSEa](https://www.chess.com/library/collections/monza-2GVK9VSEa). [Accessed: 28-Apr-2022]


## 
        Appendix A 


        **BISHOP MAGIC NUMBERS**


```
const Bitboard bishop_magics[64] = {
    0x420c80100408202ULL,
    0x1204311202260108ULL,
    0x2008208102030000ULL,
    0x24081001000caULL,
    0x488484041002110ULL,
    0x1a080c2c010018ULL,
    0x20a02a2400084ULL,
    0x440404400a01000ULL,
    0x8931041080080ULL,
    0x200484108221ULL,
    0x80460802188000ULL,
    0x4000090401080092ULL,
    0x4000011040a00004ULL,
    0x20011048040504ULL,
    0x2008008401084000ULL,
    0x102422a101a02ULL,
    0x2040801082420404ULL,
    0x8104900210440100ULL,
    0x202101012820109ULL,
    0x248090401409004ULL,
    0x44820404a00020ULL,
    0x40808110100100ULL,
    0x480a80100882000ULL,
    0x184820208a011010ULL,
    0x110400206085200ULL,
    0x1050010104201ULL,
    0x4008480070008010ULL,
    0x8440040018410120ULL,
    0x41010000104000ULL,
    0x4010004080241000ULL,
    0x1244082061040ULL,
    0x51060000288441ULL,
    0x2215410a05820ULL,
    0x6000941020a0c220ULL,
    0xf2080100020201ULL,
    0x8010020081180080ULL,
    0x940012060060080ULL,
    0x620008284290800ULL,
    0x8468100140900ULL,
    0x418400aa01802100ULL,
    0x4000882440015002ULL,
    0x420220a11081ULL,
    0x401a26030000804ULL,
    0x2184208000084ULL,
    0xa430820a0410c201ULL,
    0x640053805080180ULL,
    0x4a04010a44100601ULL,
    0x10014901001021ULL,
    0x422411031300100ULL,
    0x824222110280000ULL,
    0x8800020a0b340300ULL,
    0xa8000441109088ULL,
    0x404000861010208ULL,
    0x40112002042200ULL,
    0x2141006480b00a0ULL,
    0x2210108081004411ULL,
    0x2010804070100803ULL,
    0x7a0011010090ac31ULL,
    0x18005100880400ULL,
    0x8010001081084805ULL,
    0x400200021202020aULL,
    0x4100342100a0221ULL,
    0x404408801010204ULL,
    0x6360041408104012ULL
};

```



        


## 
        Appendix B 


        **ROOK MAGIC NUMBERS**


```
const Bitboard rook_magics[64] = {
    0xa8002c000108020ULL,
    0x6c00049b0002001ULL,
    0x100200010090040ULL,
    0x2480041000800801ULL,
    0x280028004000800ULL,
    0x900410008040022ULL,
    0x280020001001080ULL,
    0x2880002041000080ULL,
    0xa000800080400034ULL,
    0x4808020004000ULL,
    0x2290802004801000ULL,
    0x411000d00100020ULL,
    0x402800800040080ULL,
    0xb000401004208ULL,
    0x2409000100040200ULL,
    0x1002100004082ULL,
    0x22878001e24000ULL,
    0x1090810021004010ULL,
    0x801030040200012ULL,
    0x500808008001000ULL,
    0xa08018014000880ULL,
    0x8000808004000200ULL,
    0x201008080010200ULL,
    0x801020000441091ULL,
    0x800080204005ULL,
    0x1040200040100048ULL,
    0x120200402082ULL,
    0xd14880480100080ULL,
    0x12040280080080ULL,
    0x100040080020080ULL,
    0x9020010080800200ULL,
    0x813241200148449ULL,
    0x491604001800080ULL,
    0x100401000402001ULL,
    0x4820010021001040ULL,
    0x400402202000812ULL,
    0x209009005000802ULL,
    0x810800601800400ULL,
    0x4301083214000150ULL,
    0x204026458e001401ULL,
    0x40204000808000ULL,
    0x8001008040010020ULL,
    0x8410820820420010ULL,
    0x1003001000090020ULL,
    0x804040008008080ULL,
    0x12000810020004ULL,
    0x1000100200040208ULL,
    0x430000a044020001ULL,
    0x280009023410300ULL,
    0xe0100040002240ULL,
    0x200100401700ULL,
    0x2244100408008080ULL,
    0x8000400801980ULL,
    0x2000810040200ULL,
    0x8010100228810400ULL,
    0x2000009044210200ULL,
    0x4080008040102101ULL,
    0x40002080411d01ULL,
    0x2005524060000901ULL,
    0x502001008400422ULL,
    0x489a000810200402ULL,
    0x1004400080a13ULL,
    0x4000011008020084ULL,
    0x26002114058042ULL
};
```





## 
        Appendix C


        **FEN PARSER**


```
void parse_fen(char * fen_string) {

    memset(piece_bitboards, 0ULL, sizeof(piece_bitboards));
    memset(piece_occupancy, 0ULL, sizeof(piece_occupancy));
    
    castling_rights = 0;
    turn = -1;
    en_passant = -1;
    
    repetition_index = 0;
    memset(repetitions, 0, sizeof(repetitions));
    
    for (int square = 0; square < 64 && *fen_string && *fen_string!=' ';) {
        if (isalpha(*fen_string)) {
            int piece_index = find_piece_index(*fen_string++);
            set_bit(piece_bitboards[piece_index], square++);
        }
        else if (isdigit(*fen_string)) square += (*fen_string++ - '0');
        else if (*fen_string == '/') fen_string++;
        else memset(piece_bitboards, 0ULL, sizeof(piece_bitboards));
    }
    *(++fen_string) == 'b' ? (turn = black) : (turn = white);
    (fen_string += 2);
    while (*fen_string != ' ') {
        switch (*fen_string++) {
            case 'K': castling_rights |= wk; break;
            case 'Q': castling_rights |= wq; break;
            case 'k': castling_rights |= bk; break;
            case 'q': castling_rights |= bq; break;
            case '-': break;
            default: break;
        }
    }
    if (*(++fen_string) != '-') {
        int file = *fen_string++ - 'a';
        int rank = 8 - (*fen_string - '0');
        en_passant = rank * 8 + file;
    } else {
        en_passant = -1;
    }
    
    for (int piece = P; piece <= K; piece++) {
        piece_occupancy[white] |= piece_bitboards[piece];
    }
    
    for (int piece = p; piece <= k; piece++) {
        piece_occupancy[black] |= piece_bitboards[piece];
    }
    
    piece_occupancy[both] |= (piece_occupancy[white] | piece_occupancy[black]);
    
    hash_key = generate_hash();
}

```





## 
        Appendix D

**COPY AND TAKE-BACK MACROS FOR COPY/MAKE APPROACH IN MOVE GENERATION**


```
# define copy()                                                                 \
    Bitboard piece_bitboards_copy[12], piece_occupancy_copy[3];                 \
    int turn_copy, en_passant_copy, castling_rights_copy;                       \
    memcpy(piece_bitboards_copy, piece_bitboards, sizeof(piece_bitboards));     \
    memcpy(piece_occupancy_copy, piece_occupancy, sizeof(piece_occupancy));     \
    turn_copy = turn;                                                           \
    en_passant_copy = en_passant;                                               \
    castling_rights_copy = castling_rights;                                     \
    Bitboard hash_copy = hash_key;

# define take_back()                                                            \
    memcpy(piece_bitboards, piece_bitboards_copy, sizeof(piece_bitboards));     \
    memcpy(piece_occupancy, piece_occupancy_copy, sizeof(piece_occupancy));     \
    turn = turn_copy;                                                           \
    en_passant = en_passant_copy;                                               \
    castling_rights = castling_rights_copy;                                     \
    hash_key = hash_copy;

```





## 
        Appendix E

**POSITION #1 - PERFT(6) - RESULTS**


```
8   ♖ . . . ♔ . . ♖
7   ♙ . ♙ ♙ ♕ ♙ ♗ .
6   ♗ ♘ . . ♙ ♘ ♙ .
5   . . . ♟︎ ♞ . . .
4   . ♙ . . ♟︎ . . .
3   . . ♞ . . ♛ . ♙
2   ♟︎ ♟︎ ♟︎ ♝ ♝ ♟︎ ♟︎ ♟︎
1   ♜ . . . ♚ . . ♜

    A B C D E F G H

Turn:              White
En Passant:        No
Castling Rights:   KQkq
Hash Key:          b6a3e0ee0ff9bed8

     move: d5d6   nodes: 151133066
     move: d5e6   nodes: 203255191
     move: a2a3   nodes: 197413067
     move: a2a4   nodes: 183872225
     move: b2b3   nodes: 153953689
     move: g2g3   nodes: 141076301
     move: g2g4   nodes: 135208177
     move: g2h3   nodes: 158328615
     move: e5d7   nodes: 193856446
     move: e5f7   nodes: 176070755
     move: e5c6   nodes: 169836097
     move: e5g6   nodes: 165477768
     move: e5c4   nodes: 145182844
     move: e5g4   nodes: 144264874
     move: e5d3   nodes: 140737072
     move: c3b5   nodes: 166970874
     move: c3a4   nodes: 191260040
     move: c3b1   nodes: 165673862
     move: c3d1   nodes: 165415976
     move: d2h6   nodes: 161319567
     move: d2g5   nodes: 177883051
     move: d2f4   nodes: 165805784
     move: d2e3   nodes: 184114087
     move: d2c1   nodes: 158801466
     move: e2a6   nodes: 130642863
     move: e2b5   nodes: 158033152
     move: e2c4   nodes: 170094798
     move: e2d3   nodes: 167737155
     move: e2d1   nodes: 131348645
     move: e2f1   nodes: 174218453
     move: a1b1   nodes: 160413321
     move: a1c1   nodes: 159720218
     move: a1d1   nodes: 149265033
     move: h1f1   nodes: 154273720
     move: h1g1   nodes: 166086672
     move: f3f6   nodes: 146338070
     move: f3f5   nodes: 226135507
     move: f3h5   nodes: 197839051
     move: f3f4   nodes: 181938761
     move: f3g4   nodes: 189789456
     move: f3d3   nodes: 164583144
     move: f3e3   nodes: 189120807
     move: f3g3   nodes: 198078522
     move: f3h3   nodes: 210100865
     move: e1g1   nodes: 172063416
     move: e1c1   nodes: 148701308
     move: e1d1   nodes: 148612404
     move: e1f1   nodes: 139601450

     Depth: 6
     Nodes: 8031647685
     Time: 184310ms

```





## 
        Appendix F

**POSITION #2 - PERFT(7) - RESULTS**


```
8   ♖ ♘ ♗ ♕ ♔ ♗ ♘ ♖
7   ♙ ♙ ♙ ♙ ♙ ♙ ♙ ♙
6   . . . . . . . .
5   . . . . . . . .
4   . . . . . . . .
3   . . . . . . . .
2   ♟︎ ♟︎ ♟︎ ♟︎ ♟︎ ♟︎ ♟︎ ♟︎
1   ♜ ♞ ♝ ♛ ♚ ♝ ♞ ♜

    A B C D E F G H


Turn:              White
En Passant:        No
Castling Rights:   KQkq
Hash Key:          6ed57b118ae99580


     move: a2a3   nodes: 106743106
     move: a2a4   nodes: 137077337
     move: b2b3   nodes: 133233975
     move: b2b4   nodes: 134087476
     move: c2c3   nodes: 144074944
     move: c2c4   nodes: 157756443
     move: d2d3   nodes: 227598692
     move: d2d4   nodes: 269605599
     move: e2e3   nodes: 306138410
     move: e2e4   nodes: 309478263
     move: f2f3   nodes: 102021008
     move: f2f4   nodes: 119614841
     move: g2g3   nodes: 135987651
     move: g2g4   nodes: 130293018
     move: h2h3   nodes: 106678423
     move: h2h4   nodes: 138495290
     move: b1a3   nodes: 120142144
     move: b1c3   nodes: 148527161
     move: g1f3   nodes: 147678554
     move: g1h3   nodes: 120669525



     Depth: 7
     Nodes: 3195901860
     Time: 68270ms

```



## 
        


## 
        Appendix G

**POSITION #3 - PERFT(6) - RESULTS**


```
8   ♖ . . . ♔ . . ♖
7   ♟︎ ♙ ♙ ♙ . ♙ ♙ ♙
6   . ♗ . . . ♘ ♗ ♞
5   ♘ ♟︎ . . . . . .
4   ♝ ♝ ♟︎ . ♟︎ . . .
3   ♕ . . . . ♞ . .
2   ♟︎ ♙ . ♟︎ . . ♟︎ ♟︎
1   ♜ . . ♛ . ♜ ♚ .

    A B C D E F G H

Turn:              White
En Passant:        No
Castling Rights:   --kq
Hash Key:          43cb36c50fd0d6e3

     move: c4c5   nodes: 92063670
     move: d2d4   nodes: 124002076
     move: f3d4   nodes: 129579089
     move: b4c5   nodes: 87986826
     move: f1f2   nodes: 123078367
     move: g1h1   nodes: 149335005

     Depth: 6
     Nodes: 706045033
     Time: 16945ms

```





## 
        Appendix H

**ZIYAD MOURABITI (WHITE) X MONZA CHESS ENGINE (BLACK) PGN - GAME 1**


```
[Event "Computer chess game"]
[Site "VDI-VMLAB05-10"]
[Date "2022.04.17"]
[Round "?"]
[White "76650"]
[Black "Monza"]
[Result "0-1"]
[BlackElo "2000"]
[ECO "D00"]
[Opening "Queen's Pawn, Mason, Steinitz Countergambit"]
[Time "20:44:39"]
[Variation "Mason Variation"]
[WhiteElo "1000"]
[TimeControl "120+6"]
[Termination "normal"]
[PlyCount "64"]
[WhiteType "human"]
[BlackType "program"]





1. d4 d5 {(d7-d5 c2-c3 b7-b5 a2-a4 b5xa4 c3-c4 e7-e5 Ra1xa4 d5xc4 Ra4xc4)
0.00/10 9} 2. Bf4 c5 {(c7-c5 Bf4xb8 Ra8xb8 d4xc5 Qd8-a5+ Nb1-c3 Qa5xc5
Qd1xd5 e7-e5 Qd5xc5 Bf8xc5) -0.06/10 9} 3. Nf3 cxd4 {(c5xd4 Bf4xb8 Ra8xb8
Qd1xd4 a7-a5 Nf3-e5 f7-f5 c2-c3 b7-b5 Qd4xd5) -0.03/10 9} 4. Qxd4 Nc6
{(Nb8-c6 Qd4-a4 Qd8-d7 e2-e4 e7-e5 Nf3xe5 Nc6xe5 Qa4xd7+ Bc8xd7 Bf4xe5
d5xe4) +0.58/10 9} 5. Qd1 f6 {(f7-f6 e2-e4 d5xe4 Qd1xd8+) 0.00/10 9} 6. e3
e5 {(e7-e5 Bf4-g3 Qd8-a5+) +0.84/10 9} 7. Bg3 h5 {(h7-h5 Nb1-c3 Bf8-b4
Bf1-b5 g7-g5 Qd1-d2) +1.12/9 9} 8. h4 e4 {(e5-e4 Nf3-d4 a7-a5 Bf1-b5 Qd8-b6
Ke1-f1 Bc8-d7 c2-c3 Nc6xd4 Bb5xd7+) 0.00/10 9} 9. Bb5 exf3 {(e4xf3 g2xf3
a7-a6 Bb5-d3 Ke8-e7 a2-a4 d5-d4 e3xd4 Nc6xd4 c2-c4 Nd4xf3+) 0.00/11 9} 10.
Bxc6+ bxc6 {(b7xc6 g2xf3 Ng8-e7 c2-c4 g7-g5 a2-a4 a7-a5 c4-c5 Bc8-b7 h4xg5
f6xg5) 0.00/10 8} 11. Qxf3 Qb6 {(Qd8-b6 b2-b3 Bc8-g4 Qf3-f4 Qb6-a5+)
0.00/10 8} 12. b3 Bg4 {(Bc8-g4 Qf3-f4 O-O-O e3-e4 d5xe4 O-O Bf8-c5 Qf4xe4
Bc5xf2+) +4.00/11 8} 13. Qf4 O-O-O {(O-O-O Qf4-a4 g7-g5 h4xg5 f6xg5 Bg3-e5
Rh8-h7 c2-c3 Bf8-d6 Be5xd6 Rd8xd6) 0.00/11 8} 14. Nc3 Bb4 {(Bf8-b4 O-O
Bb4xc3 Ra1-e1 c6-c5 Re1-b1 a7-a5 a2-a3 Bg4-d7 Qf4-c7+ Qb6xc7 Bg3xc7)
+6.69/11 8} 15. O-O Bxc3 {(Bb4xc3 Ra1-b1 Bc3-e5 Qf4-a4 Be5xg3 f2xg3 a7-a5
Rb1-e1 Rd8-d7 c2-c3 Qb6xb3) +7.71/11 8} 16. Rad1 g5 {(g7-g5 h4xg5 Bc3-e5
Qf4-a4 Be5xg3 f2xg3 Bg4xd1 Rf1xd1 f6xg5 Rd1-d3 c6-c5 Rd3xd5) 0.00/12 8} 17.
Qa4 Be2 {(Bg4-e2 h4xg5 f6xg5 Rd1-d3 Be2xf1 Kg1xf1 Bc3-a1 b3-b4 c6-c5 b4xc5
Qb6-b1+ Kf1-e2 Qb1xa2) 0.00/12 8} 18. Rfe1 Bb5 {(Be2-b5 Qa4-a3 a7-a5 h4xg5
f6xg5 Re1-f1 c6-c5 Qa3-c1 Bb5xf1 Rd1xf1 Bc3-g7 e3-e4) +8.96/12 8} 19. Qa3
gxh4 {(g5xh4 Bg3xh4 a7-a5 e3-e4 Bc3xe1 Rd1xe1 d5xe4 Re1xe4 Rd8-d1+ Kg1-h2
c6-c5 f2-f4 a5-a4) 0.00/12 8} 20. Bxh4 a5 {(a7-a5 f2-f4 Bc3xe1 Bh4xe1
Qb6xe3+ Be1-f2 Qe3-e2 Rd1-c1 Qe2-d2 Rc1-e1 Qd2xf4 Qa3xa5) +8.66/11 8} 21.
e4 Bxe1 {(Bc3xe1 Rd1xe1 d5xe4 Qa3-c1 c6-c5 Qc1-e3 Bb5-a6 Qe3xe4 Kc8-b8
a2-a4 Kb8-a7) 0.00/12 8} 22. Rxe1 dxe4 {(d5xe4 b3-b4 a5xb4 Qa3xb4 Rd8-d4
Qb4-a3 Rd4-d2 Qa3-f8+ Qb6-d8 Qf8xd8+ Kc8xd8 Re1xe4 Rd2xc2) +8.18/11 7} 23.
Rxe4 Rd1+ {(Rd8-d1+) +9.37/10 7} 24. Kh2 c5 {(c6-c5 f2-f4 Bb5-c6 Re4-c4
Rd1-d5 Kh2-g3 Ng8-h6 Bh4xf6 Rh8-g8+ Kg3-h4 Rg8-g4+ Kh4-h3 Rg4xf4) 0.00/11
7} 25. Qb2 Bc6 {(Bb5-c6 Re4-c4 Bc6-d5 Rc4-c3 Qb6-b8+) 0.00/11 7} 26. Re6
Nh6 {(Ng8-h6 f2-f4 Nh6-g4+ Kh2-h1) +11.13/11 7} 27. Rxf6 Ng4+ {(Nh6-g4+)
0.00/11 7} 28. Kh3 Nxf6 {(Ng4xf6 f2-f3 Rd1-h1+ Bh4-g3 Bg3-h2 Bc6-d7+)
+16.35/10 7} 29. Qxf6 Rg8 {(Rh8-g8 Qf6-e6+ Bc6-d7 Qe6xd7+ Rd1xd7 f2-f3
Rd7-d2 g2-g4 Rd2xc2 Bh4-e7 h5xg4+ f3xg4 Qb6-h6+ Kh3-g3 Rg8xg4+) +18.24/11
7} 30. Qe6+ Bd7 {(Bc6-d7 Qe6xd7+ Rd1xd7 Kh3-h2 Rd7-d2 Kh2-g1 Qb6-b7 Kg1-f1
Rg8xg2 a2-a4 Rd2xc2 f2-f4 Qb7xb3) 0.00/11 7} 31. Kh2 Qxe6 {(Qb6xe6 Bh4-g5
Rg8xg5 b3-b4 Rg5xg2+ f2-f4) +M4/12 7} 32. g3 Qh3# {(Qe6-h3+) 0.00/17 7} 0-1


```





## 
        Appendix I

**ZIYAD MOURABITI (WHITE) X MONZA CHESS ENGINE (BLACK) PGN - GAME 2**


```
[Event "Computer chess game"]
[Site "VDI-VMLAB05-10"]
[Date "2022.04.17"]
[Round "?"]
[White "76650"]
[Black "Monza"]
[Result "0-1"]
[BlackElo "2000"]
[ECO "D02"]
[Opening "Queen's Pawn"]
[Time "21:52:03"]
[Variation "2.Nf3 Nc6 3.Bf4"]
[WhiteElo "1000"]
[TimeControl "120+6"]
[Termination "normal"]
[PlyCount "82"]
[WhiteType "human"]
[BlackType "program"]




1. d4 d5 {(d7-d5 c2-c3 b7-b5 a2-a4 b5xa4 c3-c4 e7-e5 Ra1xa4 d5xc4 Ra4xc4)
0.00/10 9} 2. Bf4 Nc6 {(Nb8-c6 Nb1-c3 e7-e6 Ng1-f3 Bf8-b4 h2-h4 e6-e5 d4xe5
Bb4xc3+ b2xc3 Nc6xe5) +0.11/10 9} 3. Nf3 f6 {(f7-f6 Nb1-c3 e7-e5 d4xe5
Nc6xe5 Nf3xe5 Bf8-b4 e2-e4 f6xe5) +0.06/9 9} 4. e3 a6 {(a7-a6 Nb1-c3 Bc8-g4
h2-h3 Bg4-h5 g2-g4 Bh5-f7 Nc3xd5 Qd8xd5 Bf4xc7) 0.00/10 9} 5. Bd3 g6
{(g7-g6 e3-e4 g6-g5 Nf3xg5 f6xg5 Bf4xg5 Nc6xd4 Qd1-h5+ Ke8-d7 e4xd5) 0.00/9
9} 6. c3 b5 {(b7-b5 a2-a4 g6-g5 a4xb5 g5xf4 b5xc6 e7-e5 e3xf4 e5xd4) 0.00/9
9} 7. O-O Bg7 {(Bf8-g7 e3-e4 g6-g5 Nf3xg5 f6xg5 Bf4xg5 Bc8-b7 e4xd5 Qd8xd5
Bg5xe7) 0.00/10 9} 8. Nbd2 Kf8 {(Ke8-f8 e3-e4 Bc8-g4 Bf4-e3) 0.00/9 9} 9.
Nb3 e5 {(e7-e5 d4xe5 f6xe5 Bf4-g5 Ng8-f6 Bg5xf6 Qd8xf6 h2-h4 a6-a5 Nb3xa5)
0.00/10 9} 10. dxe5 fxe5 {(f6xe5 Bf4-g5 Qd8-d7 e3-e4 h7-h6 Bg5-e3 d5xe4
Bd3xe4 Qd7xd1 Be3-c5+ Qd1-d6 Bc5xd6+) +0.57/11 8} 11. Bg3 e4 {(e5-e4 Bd3xe4
d5xe4 Qd1xd8+ Nc6xd8 Nf3-g5 Ng8-f6 Nb3-c5 h7-h6 Nc5xe4 Nf6xe4 Ng5xe4)
+1.32/11 8} 12. Bxe4 dxe4 {(d5xe4 Qd1xd8+) 0.00/12 8} 13. Qxd8+ Nxd8
{(Nc6xd8 Nf3-g5 Bc8-b7 Nb3-c5 h7-h6 Ng5xe4 Bb7xe4 Nc5xe4 a6-a5 Bg3xc7
Bg7xc3) +1.31/10 8} 14. Nfd4 Nb7 {(Nd8-b7 Bg3xc7 Bc8-d7 f2-f3 Ra8-c8 f3xe4+
Kf8-e8 Bc7-b6 a6-a5 e4-e5 Bg7xe5) 0.00/10 8} 15. f4 c5 {(c7-c5 f4-f5 c5xd4
f5xg6+ Kf8-e8 e3xd4 h7xg6 Ra1-e1 Ke8-d8 Re1xe4 Bg7xd4+) +3.53/10 8} 16. Ne2
Nf6 {(Ng8-f6 Nb3-d2 h7-h5 a2-a4 b5xa4 Ra1xa4 Bc8-d7 Ra4xe4 Nf6xe4 Nd2xe4)
+3.56/10 8} 17. Bh4 Ng4 {(Nf6-g4 Rf1-c1 c5-c4 Nb3-d2 a6-a5 Nd2xe4 Ng4xe3
b2-b3 c4xb3 a2xb3 Ne3xg2) +3.71/11 8} 18. f5 Nxe3 {(Ng4xe3 f5-f6 Bg7-h6
Rf1-f2 Ne3-g4 Nb3xc5 Nb7xc5 Ra1-d1 Ng4xf2 Rd1-d8+ Kf8-f7 Rd8xh8) +4.95/11
8} 19. Rf4 gxf5 {(g6xf5 Ne2-g3 Bg7-e5 Rf4-f2 Ne3-g4 Rf2-f1 Ng4xh2 Kg1xh2
h7-h5 Nb3xc5 Nb7xc5) +6.25/11 8} 20. c4 Bxb2 {(Bg7xb2 Ra1-b1 Bb2-e5 c4xb5
a6xb5 Bh4-f2 Ne3xg2 Kg1xg2 Be5xf4 Ne2xf4 Rh8-g8+ Kg2-h1 Ra8xa2) 0.00/12 8}
21. Rb1 Be5 {(Bb2-e5 c4xb5 a6xb5 Nb3xc5 Nb7xc5 Rb1xb5 Ne3xg2 Kg1xg2 Rh8-g8+
Kg2-h1 Be5xf4 Ne2xf4 Ra8xa2) +8.53/12 8} 22. Rf2 Nxc4 {(Ne3xc4 Rb1-f1 e4-e3
Rf2xf5+) +8.56/10 7} 23. Rd1 Ne3 {(Nc4-e3 Rd1-e1 Ne3-g4 Bh4-g3 Be5xg3
Rf2xf5+ Bc8xf5 Ne2xg3 Bf5-g6 Ng3xe4 Bg6xe4 Re1xe4) 0.00/11 7} 24. Rc1 Ng4
{(Ne3-g4 Rf2-f4 Be5xf4 Ne2xf4 e4-e3 Nb3xc5 Nb7xc5 Rc1xc5 Kf8-g8 h2-h3
a6-a5) +8.63/11 7} 25. Rff1 Nxh2 {(Ng4xh2 Rf1-d1 c5-c4 Nb3-d4 Nh2-g4 Nd4-c6
a6-a5 Nc6xe5 Ng4xe5 Ne2-f4 h7-h5) +9.07/11 7} 26. Kf2 Nxf1 {(Nh2xf1 Kf2xf1
c5-c4 Nb3-d4 h7-h5 Nd4-c6 Be5-b2 Rc1-d1 e4-e3 a2-a4) +10.96/10 7} 27. Kxf1
c4 {(c5-c4 Nb3-d4 Bc8-d7 Bh4-e1 h7-h5 Be1-g3 Be5xd4 Ne2xd4 Kf8-g8 Rc1-d1
f5-f4) +11.53/11 7} 28. Nbd4 Bd7 {(Bc8-d7 Rc1-d1 f5-f4 Rd1-e1 b5-b4 Ne2xf4
Be5xf4 Re1xe4 Bf4-d6 Bh4-e7+ Bd6xe7 Re4xe7) 0.00/11 7} 29. Rd1 h5 {(h7-h5
Nd4-c2 Kf8-e8 g2-g3 Bd7-e6 Ne2-d4 Be6-c8 Nd4-e2 a6-a5 a2-a4) +11.31/10 7}
30. Kf2 a5 {(a6-a5 Nd4xb5 Nb7-c5 Rd1-d5 Nc5-d3+ Kf2-g1 Bd7xb5 Rd5xb5 f5-f4
Bh4-e7+ Kf8xe7 Rb5xe5+) 0.00/10 7} 31. Bg3 a4 {(a5-a4 Bg3xe5 Rh8-g8 Kf2-g1
b5-b4 Be5-f4 Ra8-e8 a2-a3 b4xa3 Bf4-h6+ Kf8-e7 Nd4xf5+) 0.00/11 7} 32. Nc2
Bxg3+ {(Be5xg3+) +12.05/10 7} 33. Kxg3 Rg8+ {(Rh8-g8+ Kg3-h2 Bd7-c8 g2-g3
Rg8-g4 Nc2-e3 Rg4-g7 a2-a3 f5-f4 Ne2xf4 Rg7xg3) 0.00/10 7} 34. Kh2 Bc8
{(Bd7-c8 Nc2-d4 Ra8-a5 Ne2-f4 b5-b4 Nf4xh5 Rg8-h8 g2-g4 f5-f4 Kh2-g1)
+11.70/10 7} 35. Rd5 Ra6 {(Ra8-a6 Rd5xb5 Ra6-g6 g2-g3 h5-h4 Nc2-d4 h4xg3+
Kh2-g2 Rg6-d6 Nd4xf5 Bc8xf5 Rb5xf5+) 0.00/11 7} 36. Rxb5 Rag6 {(Ra6-g6
Nc2-e3 c4-c3 Ne2-f4 Rg6-c6 Nf4xh5 Nb7-d6 Rb5-b4 Kf8-f7 Rb4xa4 Rg8xg2+)
0.00/11 7} 37. g3 h4 {(h5-h4 Rb5-b4 h4xg3+ Kh2-g1 Rg6-d6 Ne2-c3 Rd6-d2
Rb4xc4 Bc8-d7 Rc4xa4 Bd7xa4 Nc3xa4) +11.95/11 7} 38. Rxf5+ Bxf5 {(Bc8xf5
Nc2-e3 h4xg3+ Kh2-g1 Bf5-d7 Ne3xc4 Bd7-b5 Nc4-e5 Bb5xe2 Ne5xg6+) +16.44/11
7} 39. gxh4 Rg4 {(Rg6-g4 Ne2-g3 Rg4xg3 Nc2-d4 Rg3-h3+) +M3/17 7} 40. Ng3
Rxg3 {(Rg4xg3 a2-a3 Rg3-h3+) +M2/18 7} 41. h5 Rh3# {(Rg3-h3+) 0.00/20 7}
0-1
```





## 
        Appendix J

**MONZA CHESS ENGINE (WHITE) X BBC_1.2 WITH TAPERED EVALUATION (BLACK) PGN**


<p id="gdcalert23" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: Long single-cell table. Check to make sure this is meant to be a code block. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert24">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>



```
[Event "BBCxMonza.at"]
[Site "VDI-VMLAB05-10"]
[Date "2022.04.02"]
[Round "6"]
[White "Monza_1.4.2"]
[Black "Bbc_1.2_64bit_windows"]
[Result "1-0"]
[BlackElo "2000"]
[ECO "D01"]
[Opening "Richter-Veresov Attack"]
[Time "21:18:40"]
[WhiteElo "?"]
[TimeControl "120+6"]
[Termination "time forfeit"]
[PlyCount "179"]
[WhiteType "program"]
[BlackType "program"]





1. d4 {(d2-d4 d7-d5 Nb1-c3 Ng8-f6 e2-e3 a7-a5 e3-e4 d5xe4 Bf1-b5+ c7-c6
Nc3xe4) +0.20/10 9} d5 {(d7-d5 Bc1-f4 Bc8-f5 e2-e3 e7-e6 Ng1-f3 Ng8-f6
Nb1-c3 Bf8-d6 Bf1-b5+ c7-c6 Bf4xd6) -0.15/11 9} 2. Nc3 {(Nb1-c3 c7-c6 a2-a4
Qd8-a5 Ng1-f3 e7-e5 Nf3xe5 c6-c5 b2-b4 c5xb4) 0.00/10 9} Bf5 {(Bc8-f5
Bc1-f4 Ng8-f6 e2-e3 e7-e6 Ng1-f3 c7-c6 Nf3-h4 Bf5-e4 Nc3xe4 Nf6xe4) 0.00/11
9} 3. h4 {(h2-h4 c7-c6 e2-e4 d5xe4 g2-g4 e7-e5 g4xf5 Qd8xd4 Qd1xd4 e5xd4)
0.00/10 9} e6 {(e7-e6 Bc1-f4 Nb8-c6 Ng1-f3 Ng8-f6 e2-e3 Bf8-d6 Bf4xd6 c7xd6
Bf1-d3 O-O) +0.32/11 9} 4. e4 {(e2-e4 d5xe4 g2-g4 Bf5xg4 Qd1xg4 c7-c6
Qg4xe4 Bf8-b4 f2-f4 Bb4xc3+) 0.00/10 9} Bxe4 {(Bf5xe4 f2-f3 Be4-f5 g2-g4
Bf8-e7 h4-h5 Be7-h4+ Ke1-e2 Bf5xg4 f3xg4 c7-c5 h5-h6) -0.39/11 9} 5. f3
{(f2-f3 Be4-f5 g2-g4 Bf5-g6 h4-h5 Nb8-c6 h5xg6 f7xg6 Bf1-b5 e6-e5) +1.33/10
9} Bf5 {(Be4-f5 g2-g4 Bf8-e7 h4-h5 Be7-h4+ Ke1-e2 Bf5xg4 f3xg4 c7-c5 h5-h6
g7-g6 d4xc5) -0.33/11 9} 6. g4 {(g2-g4 Bf8-e7 g4xf5 Be7xh4+ Ke1-e2 e6xf5
Ke2-d3 Nb8-c6 Nc3xd5 Nc6xd4 Nd5xc7+ Qd8xc7 Rh1xh4) +1.69/11 9} Be7 {(Bf8-e7
h4-h5 Be7-h4+ Ke1-e2 Bf5xg4 f3xg4 c7-c5 d4xc5 Nb8-d7 Bf1-g2 Nd7xc5 Bc1-f4)
-0.18/11 9} 7. gxf5 {(g4xf5 e6xf5 h4-h5 Ke8-f8 Ke1-f2 b7-b6 Bf1-d3 Be7-h4+
Kf2-g2 c7-c5 Bd3xf5 c5xd4) +1.51/11 9} Bxh4+ {(Be7xh4+ Ke1-e2 e6xf5 Nc3xd5
c7-c6 Nd5-e3 Bh4-f6 Bf1-h3 g7-g6 c2-c3 f5-f4 Ne3-c4) +0.17/11 9} 8. Ke2
{(Ke1-e2 e6xf5 Nc3xd5 Ke8-f8 Ke2-d3 c7-c5 Bc1-e3 c5-c4+ Kd3xc4 h7-h5 Rh1xh4
Qd8xh4) +1.44/10 9} exf5 {(e6xf5 Nc3xd5 c7-c6 Nd5-e3 Bh4-f6 Ne3xf5 g7-g6
Nf5-g3 Bf6xd4 Bc1-e3 Bd4xb2) 0.00/11 9} 9. Nxd5 {(Nc3xd5 Ke8-f8 Bf1-g2
Qd8xd5 Rh1xh4 h7-h5 Bc1-f4 c7-c5 Bf4xb8 Qd5-e6+ Ke2-d3 Ra8xb8) +1.38/11 9}
Bg3 {(Bh4-g3 c2-c4 Nb8-c6 Ke2-d3 Ng8-e7 Ng1-e2 Ne7xd5 Ne2xg3 Nc6-b4+ Kd3-e2
f5-f4) +0.17/10 9} 10. c4 {(c2-c4 c7-c6 Nd5-e3 f5-f4 Ne3-f5 Ke8-f8 b2-b4
a7-a5 Nf5xg3 f4xg3) +1.75/10 8} Ne7 {(Ng8-e7 Rh1-h3 Bg3-d6 Nd5xe7 Bd6xe7
Bc1-e3 Nb8-c6 Bf1-g2 O-O Ke2-f2) +0.30/10 8} 11. Rh3 {(Rh1-h3 Bg3-d6 Bc1-g5
f7-f6 Nd5xf6+ g7xf6 Bg5xf6 O-O Bf6xe7 Qd8xe7+ Ke2-f2 b7-b5 c4xb5) 0.00/11
8} Bd6 {(Bg3-d6 Ke2-f2 O-O Bc1-g5 c7-c6 Nd5xe7+ Bd6xe7 Bg5xe7 Qd8xe7 c4-c5
Rf8-e8 Bf1-c4) +0.25/11 8} 12. Nc3 {(Nd5-c3 Ne7-c6 Bf1-g2 O-O Ke2-f1 a7-a5
Nc3-b5 h7-h5 Nb5xd6 c7xd6) +2.03/10 8} Ng6 {(Ne7-g6 Ke2-f2 O-O Rh3-h5
Nb8-c6 Nc3-d5 Nc6-e7 c4-c5 Bd6-g3+ Kf2xg3 Qd8xd5) +0.38/10 8} 13. Bg2
{(Bf1-g2 O-O Ke2-f2 c7-c5 Nc3-d5 Ng6-e5 d4xc5 Bd6xc5+ Kf2-f1 Ne5xc4 Rh3xh7)
+2.22/10 8} O-O {(O-O Ke2-f2 Ng6-h4 c4-c5 Bd6-e7 Bc1-e3 Nb8-c6 f3-f4 Nh4-g6
Nc3-d5) +0.68/10 8} 14. Kf1 {(Ke2-f1 Rf8-e8 Rh3-h5 Qd8-f6 a2-a4 Qf6-e6
Nc3-d5 Qe6-e1+ Qd1xe1 Re8xe1+) +2.55/9 8} Nc6 {(Nb8-c6 Nc3-d5 Ng6-h4 c4-c5
Bd6-e7 Nd5xe7+ Qd8xe7 f3-f4 Nh4xg2 Kf1xg2) +0.70/9 8} 15. d5 {(d4-d5 Bd6-e5
d5xc6 Be5xc3 Qd1-e2 b7xc6 b2xc3 Ng6-h4 Bg2-h1 Nh4xf3) 0.00/10 8} Nce5
{(Nc6-e5 Qd1-c2 Ng6-h4 Nc3-b5 Ne5xf3 Ng1xf3 Nh4xg2 Kf1xg2 Qd8-f6 Bc1-e3)
+1.33/10 8} 16. Qb3 {(Qd1-b3 Ne5-g4 Qb3xb7 Ng4-h2+) 0.00/10 8} Re8 {(Rf8-e8
Rh3-h5 Qd8-c8 Bg2-h3 Ng6-e7 f3-f4 Ne5-g6 Ng1-e2 Ng6xf4) +1.52/9 8} 17. Rh5
{(Rh3-h5 Ne5-d3 Ng1-e2 Nd3-c5 Qb3-b5 Re8-e5 Rh5xf5 Re5xf5 Qb5xc5) 0.00/9 8}
f4 {(f5-f4 Bc1-d2 c7-c6 Ra1-e1 Ne5xf3 Ng1xf3 Re8xe1+ Kf1xe1 Ra8-b8) +1.39/8
8} 18. Qxb7 {(Qb3xb7 Ne5xc4 Nc3-e4 Nc4-e3+ Bc1xe3 f4xe3 a2-a4 Re8xe4 f3xe4
Qd8-f6+ Qb7xa8+) 0.00/10 8} Nxc4 {(Ne5xc4 Nc3-e4 Nc4-e3+ Bc1xe3 f4xe3
Ne4xd6 Qd8xd6 Ra1-c1 Ng6-f4 Rh5-f5 Ra8-c8) +1.55/10 8} 19. Ne4 {(Nc3-e4
Nc4-e3+ Bc1xe3 f4xe3 a2-a4 Ng6-f4 Ne4xd6 Nf4xh5 Nd6xe8 Nh5-g3+ Kf1-e1
Qd8xe8) +1.36/10 8} Ne3+ {(Nc4-e3+ Bc1xe3 f4xe3 Qb7-b3 Re8xe4 f3xe4 Ng6-f4
Rh5-f5 g7-g6 Qb3xe3 g6xf5) +1.74/10 8} 20. Bxe3 {(Bc1xe3 f4xe3 a2-a3 Ng6-f4
Rh5-f5 Ra8-b8 Qb7xa7 Nf4xg2 Ne4xd6 e3-e2+ Ng1xe2 c7xd6) +0.30/10 8} fxe3
{(f4xe3 Ng1-e2 Ng6-h4 Ra1-d1 Nh4xf3 Bg2xf3 Ra8-b8 Qb7xa7 Rb8xb2 Qa7xe3)
+1.68/10 8} 21. Re1 {(Ra1-e1 Ng6-f4 Rh5-g5 h7-h6 Rg5-f5 Ra8-b8 Qb7-c6
Nf4xg2 Ne4xd6 e3-e2+ Kf1xg2 c7xd6) 0.00/11 8} Nf4 {(Ng6-f4 Rh5-f5 Re8xe4
f3xe4 Ra8-b8 Qb7xa7 Rb8xb2 Ng1-e2 Nf4xg2 Kf1xg2) +1.94/10 8} 22. Rf5
{(Rh5-f5 Nf4xg2 Kf1xg2 Ra8-b8 Qb7xa7 Rb8xb2+) -1.16/11 7} Rb8 {(Ra8-b8
Qb7xa7 Re8xe4 f3xe4 Rb8xb2 Re1xe3 Nf4xg2 Re3-e2 Rb2xe2 Ng1xe2 Ng2-h4
Qa7-d4) 0.00/12 7} 23. Qxa7 {(Qb7xa7 Nf4xg2 Kf1xg2 Rb8xb2+) +0.34/11 7}
Rxe4 {(Re8xe4 f3xe4 Rb8xb2 Re1xe3 Nf4xg2 Re3-e2 Rb2xe2 Ng1xe2 Ng2-h4 Qa7-d4
Nh4xf5) +2.79/11 7} 24. fxe4 {(f3xe4 Rb8xb2 Re1xe3 Rb2-b1+ Re3-e1 Rb1xe1+
Kf1xe1 Bd6-c5 Qa7xc5 Nf4-d3+ Ke1-e2 Nd3xc5 e4-e5 h7-h5 Rf5xf7) +0.42/12 7}
Rxb2 {(Rb8xb2 Rf5xf4 Bd6xf4 Ng1-e2 Bf4-g5 Bg2-f3 Rb2-d2 a2-a4 Qd8-c8 Kf1-g2
Bg5-f4) +3.06/11 7} 25. Rxe3 {(Re1xe3 Nf4xg2) +0.42/11 7} Nxg2 {(Nf4xg2
Re3-e2 Rb2xe2 Ng1xe2 Ng2-h4 Rf5-f2 Qd8-e8 Qa7-e3 c7-c6 Ne2-f4 c6xd5)
+2.91/11 7} 26. Re2 {(Re3-e2 Rb2xe2 Ng1xe2 Qd8-h4 Qa7-d4 Qh4-h3 Kf1-f2
Qh3-h2 Kf2-f1 Qh2-h3 Rf5-g5) 0.00/13 7} Rxe2 {(Rb2xe2 Ng1xe2 Ng2-h4 Rf5-f2
Qd8-e8 Qa7-e3 c7-c6 Ne2-c3 c6xd5 Nc3xd5 Qe8-b5+ Kf1-g1 Bd6-e5) +2.94/12 7}
27. Nxe2 {(Ng1xe2) 0.00/11 7} Nh4 {(Ng2-h4 Rf5-f2 Qd8-e8 Ne2-c3 Bd6-e5
Nc3-e2 Qe8-c8 Qa7-e3 Qc8-g4 a2-a4 Nh4-g6) +2.94/11 7} 28. Rf2 {(Rf5-f2
Qd8-c8 Ne2-d4 g7-g6 Nd4-f3 c7-c5 Nf3xh4 Qc8-h3+ Kf1-e2 Qh3-g4+ Ke2-e3
Qg4xh4) +1.05/10 7} Qe8 {(Qd8-e8 Ne2-c3 Bd6-e5 Nc3-e2 Qe8-c8 Kf1-e1 Be5-d6
a2-a4 Bd6-b4+ Ke1-d1 Bb4-d6) +2.78/10 7} 29. Qe3 {(Qa7-e3 h7-h5 Ne2-c3
Bd6-e5 Qe3-h3 Be5xc3 Qh3xh4 f7-f5 Rf2xf5 Qe8-b5+ Kf1-g1 Qb5xd5) +0.67/11 7}
Qa4 {(Qe8-a4 Ne2-c3 Qa4-c4+ Rf2-e2 Nh4-g6 Kf1-e1 Bd6-e5 Re2-c2 c7-c6 d5xc6
Qc4xc6) +3.27/10 7} 30. Nc3 {(Ne2-c3 Qa4-c4+ Nc3-e2 Qc4-a4) 0.00/11 7} Qc4+
{(Qa4-c4+ Rf2-e2 Nh4-g6 Kf1-e1 Bd6-e5 Nc3-d1 Ng6-f4 Re2-d2 Qc4-a6 Nd1-c3
Qa6-g6 Rd2-c2) +3.43/11 7} 31. Ne2 {(Nc3-e2 Qc4xa2 Ne2-c1 Qa2-c4+ Rf2-e2
h7-h5 Qe3-g5 f7-f6 Qg5xh4 Qc4xc1+ Kf1-g2 Qc1-g5+ Qh4xg5 f6xg5) -0.45/10 7}
Qxa2 {(Qc4xa2 Ne2-f4 Qa2-b1+ Kf1-e2 Qb1-c2+ Ke2-f1 Qc2-c4+ Nf4-d3 Bd6-e5
Rf2-d2 Be5-d4 Qe3-e2 c7-c6 d5-d6) +3.97/11 7} 32. Nc1 {(Ne2-c1 Qa2-c4+
Nc1-d3 h7-h5 Rf2-b2 c7-c5 d5xc6/ep Nh4-g6 Rb2-b6 f7-f5 e4xf5 Qc4xd3+)
0.00/11 7} Qc4+ {(Qa2-c4+ Nc1-d3 c7-c6 d5xc6 Qc4xc6 e4-e5 Bd6-e7 Kf1-e2
Qc6-c4 Ke2-e1 Qc4-c3+ Ke1-e2 Nh4-g6) +3.76/11 7} 33. Nd3 c6 {(c7-c6 d5xc6
Qc4xc6 e4-e5 Bd6-e7 Qe3-f4 Qc6-h1+ Kf1-e2 Qh1-d5 Rf2-f1 Qd5-a2+ Ke2-e1
Qa2-d5) +3.72/11 7} 34. dxc6 {(d5xc6 Qc4xc6 Rf2-e2 Nh4-g6 Kf1-f2 Ng6-e5
Nd3xe5 Bd6xe5 Re2-d2 Qc6-f6+ Kf2-e2 h7-h5) 0.00/11 7} Qxc6 {(Qc4xc6 Kf1-g1
Qc6-c4 e4-e5 Bd6-e7 Qe3-f4 Qc4-d5 Qf4-e3 Nh4-g6 Rf2-f5) +3.69/10 7} 35. Rb2
{(Rf2-b2 Qc6-c8 Rb2-b6 Qc8-e6 Rb6-a6 h7-h5 Ra6-a8+ Kg8-h7 Kf1-f2 Qe6-f6+
Kf2-e2 g7-g5) -0.10/10 7} Qa4 {(Qc6-a4 Kf1-e2 Nh4-g6 Rb2-b6 Qa4-c2+ Qe3-d2
Ng6-f4+ Ke2-e3 Nf4-g2+ Ke3-e2 Qc2-c7 Qd2-b2 Ng2-f4+) +3.77/10 7} 36. Qe2
{(Qe3-e2 h7-h5 Rb2-a2 Qa4-d4 Ra2-a8+ Qd4xd3) 0.00/10 7} Qd7 {(Qa4-d7 Kf1-f2
Qd7-h3 e4-e5 Qh3-g2+ Kf2-e3 Qg2-g3+ Ke3-e4 Qg3-g6+ Ke4-f4 Qg6-f5+ Kf4-g3
Qf5-g5+ Kg3-h2 Bd6-e7) +3.92/10 7} 37. Nf2 {(Nd3-f2 Bd6-e5 Rb2-c2 g7-g5
Rc2-c5 Qd7-e7 Rc5-c8+ Kg8-g7 Rc8-c2 Nh4-g6 Rc2-c7) -0.13/10 7} Ng6 {(Bd6-e5
Rb2-d2 Qd7-c7 Rd2-d5 Be5-c3 e4-e5 Nh4-g6 e5-e6 Qc7-g3) +3.80/9 7} 38. Rd2
{(Rb2-d2 Qd7-c6 Qe2-d1 Qc6-b5+ Qd1-e2 Qb5-b8 Qe2-d1 Bd6-f8 Rd2-d3 Ng6-f4
Rd3-d8 f7-f5) 0.00/11 7} Qc6 {(Qd7-c6 Qe2-d3 Bd6-e5 Rd2-d1 Be5-f4 Qd3-d8+
Ng6-f8 Kf1-e2 Qc6-c2+ Ke2-f3 Bf4-e5) +3.67/9 7} 39. Qd3 {(Qe2-d3 Bd6-e5
Qd3-d5 Qc6-a6+ Qd5-d3 Qa6-e6 Qd3-b5 Qe6-c8 Rd2-d7 Qc8-c1+ Kf1-g2 h7-h5)
-0.29/10 7} Bf4 {(Bd6-f4 Qd3-d5 Qc6-a6+ Qd5-d3 Qa6-e6 Rd2-d1 Ng6-f8 Qd3-d8
Qe6-g6 Kf1-e1 Qg6-g3) +3.70/10 7} 40. Rd1 {(Rd2-d1 h7-h5 Qd3-h3 Qc6-a6+
Kf1-g1 Qa6-e2 Kg1-g2 Qe2-b5 Rd1-d8+) -0.40/10 7} Nf8 {(Ng6-f8 Qd3-d5 Qc6-c2
Qd5-d4 Bf4-c7 Qd4-d5 Qc2-c3 Nf2-d3 Nf8-e6 Kf1-g2) +3.61/10 7} 41. Qd5
{(Qd3-d5 Qc6-a6+) -0.37/10 7} Qg6 {(Qc6-g6 Kf1-e1 Qg6-g3 Qd5-f5 Bf4-e5
Rd1-d8 Be5-c3+ Ke1-e2 Bc3-f6 Rd8xf8+ Kg8xf8 Qf5xh7) +3.57/10 7} 42. Qc5
{(Qd5-c5 Qg6-f6 Qc5-f5 Qf6-a6+ Qf5-f6) 0.00/11 7} Qa6+ {(Qg6-a6+ Kf1-g2
Qa6-f6 Qc5-c8 Qf6-g6+ Qc8-g4 Qg6-h6 Nf2-d3 Bf4-e3 Qg4-f5 Nf8-e6 Nd3-e5)
+3.45/10 7} 43. Kg2 {(Kf1-g2 Qa6-f6 Qc5-f5 Qf6-h4 Qf5-h3 Qh4-g5+ Kg2-h1
h7-h5 Nf2-d3 Qg5-g3 Qh3xg3 Bf4xg3) 0.00/10 7} Ne6 {(Qa6-f6 Qc5-c8 Qf6-g6+
Qc8-g4 Qg6-h6 Nf2-d3 Bf4-e3 Nd3-e5 Nf8-e6 Rd1-d7 Ne6-f4+) +3.46/10 6} 44.
Rd7 {(Rd1-d7 Qa6-a8 Qc5-e7 Qa8-f8 Qe7xf8+) +0.04/11 6} Qa8 {(Qa6-a8 Qc5-e7
Qa8-f8 Nf2-d3 Qf8xe7 Rd7xe7 Bf4-d6 Re7-e8+ Bd6-f8 Re8-c8 Ne6-d4) +2.91/10
6} 45. Qe7 {(Qc5-e7 Qa8-f8 Qe7xf8+) 0.00/11 6} Qf8 {(Qa8-f8 Nf2-d3 Bf4-g5
Qe7xf8+ Kg8xf8 Kg2-f3 Kf8-e8 Rd7-d5 f7-f6 e4-e5 Ke8-f7 Kf3-e4 Kf7-g6)
+2.73/12 6} 46. Nd3 {(Nf2-d3 Qf8xe7 Rd7xe7 Bf4-d6 Re7-d7 Bd6-c7 Nd3-c5
Bc7-e5 Nc5xe6 f7xe6 Rd7-d8+ Kg8-f7 Kg2-g1) +0.23/12 6} Bg5 {(Bf4-g5 Qe7xf8+
Kg8xf8 Kg2-f3 Bg5-f6 e4-e5 Bf6-e7 Rd7-b7 f7-f5 e5xf6/ep Be7xf6 Nd3-f4
Ne6-c5) +2.65/12 6} 47. Qxf8+ {(Qe7xf8+ Kg8xf8 Rd7-a7 h7-h5 Ra7-a8+ Kf8-e7
Ra8-a7+ Ke7-f8 Ra7-a8+) 0.00/12 6} Kxf8 {(Kg8xf8 Kg2-f3 Bg5-e7 Kf3-e3
Kf8-e8 Rd7-b7 f7-f6 e4-e5 Ke8-f7 Ke3-e4 f6xe5 Nd3xe5+) +2.66/11 6} 48. Rb7
{(Rd7-b7 h7-h5 Rb7-b8+ Kf8-e7 Rb8-b7+ Ke7-f6 Kg2-f1 Ne6-f4 Rb7-b6+ Kf6-e7
Rb6-b7+ Ke7-f6) 0.00/12 6} Nf4+ {(Ne6-f4+ Nd3xf4 Bg5xf4 Kg2-f3 Bf4-d6
Rb7-d7 Bd6-e5 Kf3-g4 Be5-f6 Kg4-f5 Bf6-e7 Rd7-c7 Be7-d6) +2.68/12 6} 49.
Nxf4 {(Nd3xf4 Bg5xf4 Kg2-f3 g7-g5 Kf3-g4 Kf8-g7 e4-e5 Kg7-g6 Rb7-b6+ Kg6-g7
Rb6-b7 Bf4xe5) 0.00/12 6} Bxf4 {(Bg5xf4 Rb7-d7 Bf4-e5 Rd7-d5 f7-f6 Rd5-d7
Kf8-g8 Kg2-f3 Be5-c3 Kf3-e3 Kg8-f8 Ke3-f3 Bc3-b4 Kf3-e3 Bb4-c5+) +2.56/15
6} 50. Kf3 {(Kg2-f3 g7-g5 Kf3-g4 Kf8-g7 e4-e5 Bf4xe5 Kg4xg5 Kg7-g8 Rb7-a7
Kg8-g7 Ra7-b7) 0.00/14 6} Be5 {(Bf4-e5 Rb7-a7 Be5-d4 Ra7-d7 Bd4-c3 Rd7-d8+
Kf8-e7 Rd8-h8 h7-h6 Kf3-e3 Bc3-e5 Rh8-a8 Ke7-f6 Ra8-c8) +2.55/13 6} 51. Ra7
{(Rb7-a7 h7-h5 Ra7-a8+ Kf8-e7 Ra8-a6 g7-g6 Kf3-g2 Be5-d6 Ra6-a8 g6-g5
Ra8-a5 f7-f6 Ra5-a8 Bd6-f4 Kg2-f3) 0.00/14 6} f6 {(f7-f6 Kf3-e3 Be5-d6
Ra7-d7 Bd6-c5+ Ke3-f4 Bc5-b4 Rd7-d8+ Kf8-f7 Kf4-f5 Bb4-c3 Rd8-h8 g7-g6+
Kf5-f4 Bc3-e5+ Kf4-e3 Kf7-g7) +2.55/13 6} 52. Ra8+ {(Ra7-a8+ Kf8-f7 Ra8-h8
h7-h6 Kf3-e2 Kf7-g6 Ke2-d3 h6-h5 Kd3-e2 Kg6xh5) 0.00/14 6} Kf7 {(Kf8-f7
Ra8-c8 Be5-d6 Rc8-c6 Bd6-a3 Kf3-f4 Ba3-b2 Kf4-f5 Bb2-e5 Rc6-c8 Be5-d6
Rc8-a8 Bd6-c5 Ra8-h8 h7-h6) +2.60/14 6} 53. Rh8 {(Ra8-h8 Kf7-g6 Kf3-g4
h7-h6 Rh8-a8 h6-h5+ Kg4-h4 Be5-d4 Kh4-h3 Bd4-f2 Kh3-g2 Bf2-b6 Kg2-h3 h5-h4)
-0.24/13 6} Kg6 {(Kf7-g6 Rh8-c8 Be5-d6 Rc8-h8 Bd6-c5 Rh8-c8 Bc5-d4 Rc8-h8
Kg6-h6 Kf3-g4 Bd4-f2 Kg4-f5 Bf2-b6 Rh8-c8 Bb6-d4) +2.73/15 6} 54. Kg4
{(Kf3-g4 Be5-d6 Kg4-h4 h7-h6 Kh4-g4 Bd6-e5) -0.24/14 6} Bd6 {(Be5-d6 Rh8-d8
Bd6-b4 Rd8-c8 Bb4-a3 e4-e5 f6xe5 Rc8-c6+ Kg6-f7 Kg4-f5 Ba3-e7 Rc6-c7 e5-e4
Kf5xe4 Kf7-e6 Rc7-c8) +2.67/15 6} 55. Kh4 {(Kg4-h4 Bd6-c5 Kh4-g4 Bc5-e7
Kg4-f3 h7-h5 Rh8-a8 Be7-b4 Ra8-d8 Bb4-c5 Rd8-d5 Bc5-g1 Rd5-d7 Bg1-c5)
0.00/14 6} Bc7 {(Bd6-c7 Kh4-g4 Bc7-b6 Rh8-c8 Bb6-d4 Kg4-f3 Bd4-e5 Kf3-g4
Be5-d6 Kg4-f3 Kg6-f7 Kf3-g4 Bd6-b4 Kg4-f3 Kf7-g6 Kf3-e3) +2.79/16 6} 56.
Kh3 {(Kh4-h3 Bc7-b6 Kh3-g4 Bb6-d4 Kg4-h4 Bd4-f2+ Kh4-g4 Bf2-b6 Rh8-b8
h7-h5+ Kg4-f3) 0.00/14 6} Bb6 {(Bc7-b6 Rh8-c8 Bb6-d4 Kh3-g4 Bd4-b2 Rc8-a8
Bb2-c3 Ra8-c8 Bc3-b4 Rc8-c6 Bb4-a3 e4-e5 Ba3-e7 e5-e6 Be7-b4) +2.54/15 6}
57. Kg4 {(Kh3-g4 Bb6-d4 Kg4-h4 Bd4-c5) 0.00/15 6} Bc5 {(Bb6-d4 Kg4-f3
Bd4-c5 Rh8-c8 Bc5-d6 Rc8-h8 Bd6-h2 Rh8-c8 Bh2-e5 Rc8-h8 Be5-c7 Rh8-a8
Bc7-b6 Ra8-c8 Kg6-f7) +2.76/15 6} 58. Ra8 {(Rh8-a8 Bc5-d4 Ra8-h8 Bd4-e5
Kg4-f3 h7-h5 Kf3-e2 Be5-d4 Rh8-d8 Bd4-b6 Rd8-h8) -0.26/14 6} Bd4 {(Bc5-d4
Ra8-c8 Bd4-b2 Rc8-a8 Bb2-c3 Ra8-c8 Bc3-b4 Rc8-c6 Kg6-f7 Rc6-c8 Bb4-d2
Kg4-f5 Bd2-e3 Rc8-h8 g7-g6+) +2.46/15 6} 59. Rh8 {(Ra8-h8 Bd4-e5 Kg4-h3
Be5-c7 Kh3-g4 Bc7-b6 Kg4-f3 h7-h5 Kf3-e2 Bb6-d4 Rh8-d8 Bd4-e5) -0.26/14 6}
Be3 {(Bd4-e3 Rh8-c8 Be3-g1 Rc8-d8 Bg1-h2 Rd8-h8 h7-h6 Kg4-f3 Bh2-d6 Rh8-c8
Bd6-e5 Kf3-e3 Kg6-g5 Rc8-d8 Kg5-g4) +2.43/15 6} 60. Kf3 {(Kg4-f3 Be3-c5
Kf3-g4 Bc5-d4) -0.26/15 6} Bc5 {(Be3-c5 Rh8-a8 Bc5-d4 Ra8-h8 Bd4-b2 Kf3-g4
Bb2-c1 Rh8-c8 Bc1-e3 Kg4-f3 Be3-a7 Rc8-a8 Ba7-g1 Ra8-c8 Kg6-f7) +2.53/15 6}
61. Kg4 {(Kf3-g4 Bc5-d4 Rh8xh7 Kg4-f3) 0.00/15 6} Bb4 {(Bc5-b4 Rh8-c8
Bb4-d6 Rc8-h8 Bd6-a3 Rh8-b8 Ba3-c1 Kg4-f3 Kg6-h6 Kf3-g4 Bc1-e3 Kg4-f5
Be3-d4 Rb8-c8 Bd4-e5) +2.69/15 6} 62. Kh4 {(Kg4-h4 Bb4-d2 Kh4-g4 Bd2-e1
Rh8-a8 h7-h5+ Kg4-h3 Be1-d2 Ra8-d8 Bd2-f4 Kh3-g2 Kg6-h7 Rd8-d7 Bf4-e5
Kg2-f3) -0.26/14 6} Be7 {(Bb4-e7 Kh4-g4 Be7-a3 Rh8-c8 Ba3-d6 Kg4-f3 Bd6-e5
Kf3-e2 f6-f5 Rc8-e8 Be5-d4 Ke2-d3 Bd4-c5 Kd3-c4 Bc5-d6) +2.82/15 6} 63. Kg4
{(Kh4-g4 h7-h6 Rh8-a8 Be7-c5 Ra8-d8 h6-h5+ Rd8-d4) 0.00/14 6} Ba3 {(Be7-a3
Kg4-f3 Ba3-d6 Rh8-c8 Bd6-e5 Rc8-h8 Be5-c3 Rh8-c8 Bc3-d4 Rc8-h8 Bd4-g1
Rh8-c8 Bg1-b6 e4-e5 Kg6-f7) +2.66/15 6} 64. Kh4 {(Kg4-h4 h7-h6 Kh4-h3
Ba3-c5) -0.27/14 6} Bc1 {(Ba3-c1 Rh8-c8 Bc1-d2 Kh4-g4 Bd2-e3 Kg4-f3 Be3-d4
Kf3-g4 Kg6-h6 Rc8-c7 Bd4-e5 Rc7-c8 Be5-d6 Kg4-f5 Bd6-e5) +2.69/15 6} 65.
Kg4 {(Kh4-g4 Bc1-b2 Kg4-h4 h7-h6 Kh4-g4 Bb2-d4 Kg4-f3 Bd4-c5) -0.27/14 6}
Bb2 {(Bc1-b2 Kg4-f3 Bb2-a1 Kf3-g4 Ba1-c3 Rh8-c8 Bc3-b2 Rc8-a8 Kg6-h6 Ra8-d8
Bb2-e5 Kg4-f5 Be5-g3 Rd8-d7 Bg3-f2) +2.48/15 6} 66. Kh4 {(Kg4-h4 h7-h6
Rh8-a8 Bb2-d4 Kh4-g4 Bd4-e5 Ra8-h8 Be5-c3 Rh8-a8 h6-h5+ Kg4-h4 Bc3-d4)
0.00/15 6} Bc3 {(Bb2-c3 Kh4-g4 Bc3-d2 Rh8-c8 Bd2-b4 Rc8-c6 Kg6-f7 Kg4-f5
Bb4-a5 Rc6-c8 Ba5-b6 Rc8-h8 g7-g6+ Kf5-f4 Kf7-g7) +2.44/14 6} 67. Kg4
{(Kh4-g4 h7-h6 Rh8-a8 Bc3-e5 Ra8-h8 Be5-d4 Rh8-a8 g7xh6) 0.00/14 6} Bd2
{(Bc3-d2 Rh8-c8 Bd2-b4 Rc8-c6 Kg6-f7 Rc6-c7+ Bb4-e7 Rc7-c6 Be7-a3 Kg4-f5
Ba3-b4 Rc6-c7+ Bb4-e7 Rc7-b7 Kf7-f8 Rb7-c7) +2.40/14 6} 68. Rc8 {(Rh8-c8
h7-h5+ Kg4-f3 Bd2-b4 Rc8-c6 Kg6-h7 Rc6-c8 h5-h4 Kf3-g4 Bb4-e1 Rc8-c7 Be1-g3
Rc7-c8 Bg3-f2) -0.29/14 6} Bb4 {(Bd2-b4 Rc8-c6 Kg6-f7 Rc6-c8 Bb4-d6 Kg4-h5
Bd6-f8 Rc8-c7+ Bf8-e7 Rc7-c8 Be7-a3 Rc8-h8 h7-h6 Rh8-d8 Kf7-e7) +2.19/14 6}
69. Kf3 {(Kg4-f3 h7-h5 Rc8-c6 Kg6-g5 Rc6-c7 g7-g6 Rc7-b7 Bb4-d6 Rb7-b5+
Bd6-e5 Kf3-e3 Kg5-h6 Ke3-f3 Be5-d4 Rb5-b8) 0.00/14 6} Bd6 {(Bb4-d6 Rc8-c2
Bd6-e5 Rc2-g2+ Kg6-f7 Kf3-g4 Be5-d6 Rg2-c2 Bd6-b4 Rc2-c8 Bb4-e7 Kg4-f5
Be7-d6 Rc8-h8 g7-g6+) +2.54/14 6} 70. Kg4 {(Kf3-g4 h7-h6 Rc8-h8 Bd6-e5
Rh8-c8 Be5-d4 Rc8-h8 Bd4-b2 Kg4-h3 Bb2-e5 Kh3-g4 Be5-d4 Rh8-f8 h6-h5+)
0.00/14 6} Bh2 {(Bd6-h2 Rc8-d8 Bh2-g1 Rd8-c8 h7-h6 Kg4-f3 Kg6-f7 Rc8-d8
Bg1-h2 Rd8-d2 Bh2-e5 Rd2-d7+ Kf7-g6 Kf3-g4 Be5-c3 Kg4-f4) +2.39/15 6} 71.
Kh4 {(Kg4-h4 Bh2-e5 Rc8-f8 Be5-f4 Rf8-h8 h7-h6 Kh4-g4 Bf4-e5) -0.35/14 6}
Bf4 {(Bh2-f4 Rc8-c6 Bf4-e5 Kh4-g4 Be5-d4 Rc6-c7 Kg6-h6 Rc7-c6 Bd4-e5 Rc6-c2
Be5-b8 Rc2-c8 Bb8-d6 Kg4-f5) +2.69/14 6} 72. Kg4 {(Kh4-g4 Bf4-d6 Rc8-h8
Bd6-e5 Rh8-d8 h7-h6 Rd8-h8 Be5-b2 Rh8-b8) -0.35/14 6} Be3 {(Bf4-e3 e4-e5
Be3-d4 e5-e6 f6-f5+ Kg4-f3 Kg6-f6 Rc8-c6 Bd4-e5 Kf3-e2 Kf6-e7 Rc6-b6 Be5-d4
Rb6-c6) +2.12/13 6} 73. Rd8 {(Rc8-d8 h7-h5+) -0.29/13 6} Bg1 {(Be3-g1
Rd8-h8 Bg1-f2 Rh8-a8 Bf2-e1 Ra8-h8 Kg6-h6 Rh8-c8 Be1-f2 Rc8-c4 Bf2-g1
Kg4-f3 Bg1-b6 Rc4-c8) +2.64/14 6} 74. Rd2 {(Rd8-d2 h7-h5+ Kg4-f3 Bg1-c5
Rd2-d8 h5-h4 Rd8-d7 Bc5-b6 Kf3-g4) -0.29/13 6} Bc5 {(Bg1-c5 Kg4-f3 Bc5-b4
Rd2-g2+ Kg6-f7 Rg2-h2 Kf7-g8 Rh2-g2 Bb4-a5 Rg2-a2 Ba5-e1 Kf3-e3 Be1-b4
Ra2-a8+) +2.57/13 6} 75. Rd8 {(Rd2-d8 h7-h5+ Kg4-f3 Bc5-b6 Rd8-d7 h5-h4
Kf3-g4 Bb6-f2 e4-f5+) -0.29/13 6} Bf2 {(Bc5-f2 Rd8-c8 h7-h6 Kg4-f3 Bf2-d4
Rc8-h8 Bd4-e5 Rh8-d8 Kg6-g5 Rd8-d7 f6-f5 e4xf5 Kg5xf5 Kf3-e3) +2.44/14 6}
76. Kf3 {(Kg4-f3 Bf2-b6 Rd8-d7 Bb6-c5 Kf3-f4 h7-h5 Rd7-d8 h5-h4 Kf4-f3)
-0.29/14 6} Bb6 {(Bf2-b6 Rd8-c8 Bb6-d4 Kf3-g4 Bd4-g1 Rc8-d8 Bg1-a7 e4-e5
Ba7-c5 Rd8-c8 Bc5-b4 e5-e6 Bb4-d6 Kg4-f3 Bd6-e5) +2.49/15 6} 77. Rd7
{(Rd8-d7 h7-h5 Kf3-g3 Bb6-a5 Rd7-d5 Ba5-c7+ Kg3-h4 Bc7-e5 Rd5-d8 Be5-c3)
0.00/14 6} Ba5 {(Bb6-a5 Kf3-e3 Ba5-c3 Ke3-f4 Bc3-b4 Kf4-f3 Bb4-a3 Kf3-e3
Ba3-c1+ Ke3-f3 Bc1-g5 Rd7-d8 Bg5-h4 Kf3-f4 Bh4-e1 Kf4-f3) +2.65/15 6} 78.
Kg3 {(Kf3-g3 h7-h5 Rd7-d5 Ba5-b6 Rd5-d7) -0.36/13 6} Bb4 {(Ba5-b4 Kg3-f3
Bb4-c3 Rd7-d8 Bc3-e5 Kf3-g4 Be5-b2 Kg4-f3 Bb2-a3 Rd8-c8 Kg6-h6 Kf3-f4
Ba3-b4 Rc8-d8) +2.68/14 6} 79. Rd8 {(Rd7-d8 h7-h5 Kg3-g2 Bb4-c3 Rd8-h8
Bc3-e5 Kg2-h1 Be5-a1 Rh8-a8 Ba1-c3 Ra8-c8 Bc3-b2 Kh1-g1 h5-h4) 0.00/14 6}
Bc3 {(Bb4-c3 Kg3-f3 Bc3-e1 Rd8-c8 Be1-a5 Kf3-g4 Kg6-h6 Kg4-f5 Ba5-b6 Rc8-c6
Bb6-d4 Rc6-c7 Bd4-e5) +2.65/13 6} 80. Rc8 {(Rd8-c8 Bc3-d4 Kg3-g4 h7-h5+
Kg4-h4 Bd4-f2+ Kh4-h3 Kg6-h6 Rc8-h8+ Kh6-g5 Rh8-h7 Kg5-g6 Rh7-h8) 0.00/15
6} Bd4 {(Bc3-d4 Kg3-g4 Bd4-g1 Rc8-d8 Bg1-h2 Rd8-c8 Kg6-h6 Kg4-f5 Bh2-d6
Rc8-d8 Bd6-e5 Rd8-d7 Be5-c3) +2.57/13 6} 81. Rd8 {(Rc8-d8 Bd4-e5+) 0.00/15
6} Bb6 {(Bd4-b6 Rd8-h8 Kg6-h6 Kg3-g4 Bb6-d4 Rh8-c8 Bd4-e5 Kg4-f5 Be5-b2
Rc8-c6 Bb2-d4 Rc6-c1 g7-g6+ Kf5-f4 Bd4-e5+) +2.35/14 6} 82. Rd5 {(Rd8-d5
h7-h5 Rd5-d7 Bb6-a5 Kg3-f3 Kg6-h6 Rd7-d6 Ba5-c7 Rd6-c6 Bc7-e5 Rc6-c8 Kh6-g6
Rc8-d8) 0.00/14 6} Bc7+ {(Bb6-c7+ Kg3-g4 Bc7-e5 Rd5-d8 Be5-b2 Rd8-d3 Bb2-c1
Rd3-c3 Bc1-g5 Rc3-c8 Kg6-h6 Kg4-f5 Bg5-e3 Rc8-c4 Be3-b6) +2.63/14 6} 83.
Kg4 {(Kg3-g4 Bc7-e5 Rd5-d8) -0.36/14 6} Be5 {(Bc7-e5 Rd5-d8 Be5-b2 Rd8-h8
h7-h6 Rh8-d8 Bb2-e5 Rd8-d7 Be5-c3 Kg4-f3 Bc3-b4 Kf3-e3 Bb4-c5+ Ke3-f3
h6-h5) +2.39/14 6} 84. Rd8 {(Rd5-d8 h7-h5+ Kg4-h4 Be5-c3 Rd8-c8 Bc3-d4
Rc8-d8 Bd4-f2+ Kh4-h3 Kg6-h6 Rd8-d7 Kh6-g5 h5-h4) 0.00/16 6} Bb2 {(Be5-b2
Rd8-b8 Bb2-a3 Rb8-d8 h7-h6 Kg4-f3 Ba3-b4 Rd8-d7 Bb4-c5 Kf3-f4 Bc5-f2 Kf4-f3
Bf2-b6) +2.37/13 6} 85. Rh8 {(Rd8-h8 h7-h6 Rh8-a8 Bb2-e5 Kg4-h3 h6-h5
Kh3-h4 Be5-d4 Ra8-d8 Bd4-f2+ e4-f5+) -0.36/14 6} h6 {(h7-h6 Rh8-c8 Bb2-d4
Rc8-d8 Bd4-c3 Kg4-f3 Bc3-e5 Rd8-c8 Be5-d4 Kf3-g4 Bd4-b6 Kg4-f3 Kg6-g5
Rc8-c4 f6-f5) +2.30/15 6} 86. Ra8 {(Rh8-a8 Bb2-e5 Ra8-d8 h6-h5+ Kg4-h4)
0.00/15 6} Be5 {(Bb2-e5 Ra8-d8 h6-h5+ Kg4-h4 Be5-c3 Kh4-h3 Bc3-e1 Kh3-g2
Be1-b4 Kg2-f3 Bb4-c5 Rd8-d5 Bc5-a7 e4-e5 f6xe5) +2.14/14 6} 87. Rd8
{(Ra8-d8 f6-f5+) -0.36/13 6} Ba1 {(Be5-a1 Kg4-f3 Ba1-c3 Rd8-d7 Bc3-b4
Rd7-d5 Bb4-e7 Kf3-e2 Be7-a3 Ke2-f3 Kg6-f7 Kf3-e3 Ba3-c1+ Ke3-f3 Bc1-b2)
+2.32/14 6} 88. Rc8 {(Rd8-c8 Ba1-d4 Rc8-d8 h6-h5+ Kg4-h3 Bd4-e5 Kh3-h4
Be5-c3) 0.00/15 6} Bd4 {(Ba1-d4 Kg4-f3 Bd4-e5 Kf3-g4 Be5-d6 Kg4-f3 Kg6-f7
Rc8-c6 Bd6-e5 Rc6-c8 Kf7-e7 Kf3-g4 Ke7-d7 Rc8-a8) +2.30/14 6} 89. Rd8
{(Rc8-d8 h6-h5+ Kg4-h4 Bd4-e3 Rd8-h8 Be3-f2+ Kh4-h3 Bf2-d4 Rh8-d8 Bd4-e5)
0.00/15 6} Bc5 {(Bd4-b6 Rd8-d7 Bb6-e3 Kg4-f3 Be3-c5 Kf3-f4 Bc5-b4 Kf4-f3
Bb4-c3 Kf3-f4 Bc3-e5+ Kf4-g4 h6-h5+ Kg4-f3 f6-f5 e4xf5+) +2.28/14 6} 90.
Rd5 {(Rd8-d5 Bc5-g1 Rd5-d7 h6-h5+ Kg4-h3 Bg1-f2 Rd7-d8 Bf2-e3 Kh3-g2 Be3-f4
Kg2-h3 Kg6-h7 Kh3-h4 Kh7-g6) -0.36/13 6} ... {Black forfeits on time} 1-0

```



## 
        


## 
        Appendix K

**MONZA CHESS ENGINE (WHITE) X KOMODO14 (BLACK) - 1800 RATED**


```
[Event "vs Computer"]
[Site "Chess.com"]
[Date "2022.04.26"]
[Round "-"]
[White "Monza"]
[Black "Komodo14"]
[Result "1-0"]
[CurrentPosition "R7/1pQ5/k1p5/p5Pp/2PP3P/PP6/3K2B1/8 b - - 4 39"]
[Timezone "UTC"]
[ECO "D00"]
[ECOUrl "https://www.chess.com/openings/Queens-Pawn-Opening-Chigorin-Variation-2...Nf6"]
[UTCDate "2022.04.26"]
[UTCTime "05:37:50"]
[WhiteElo ""]
[BlackElo "1800"]
[TimeControl "1/0"]
[Termination "Monza won by checkmate"]
[StartTime "05:37:50"]
[EndDate "2022.04.26"]
[EndTime "06:13:53"]
[Link "https://www.chess.com/game/computer/10299027"]



1. d4 Nf6 2. Nc3 d5 3. h4 Qd6 4. f4 Bd7 5. Nf3 Ne4 6. Nxe4 dxe4 7. Ne5 f6 8.
Nxd7 Nxd7 9. e3 e5 10. g4 exf4 11. exf4 g5 12. Bg2 e3 13. Bxe3 Qe7 14. Kf2 Rd8
15. Re1 c6 16. Bc1 Ne5 17. fxe5 fxe5 18. Bxg5 Qb4 19. Rxe5+ Kd7 20. b3 Bd6 21.
Bxd8 Rxd8 22. a3 Qc3 23. Re3 Rf8+ 24. Ke2 Qa5 25. c4 Qd8 26. g5 Kc7 27. Qd2 Qd7
28. Re4 Kb8 29. Qe3 Qf7 30. Rf1 Qg8 31. Rxf8+ Bxf8 32. Qf4+ Bd6 33. Qxd6+ Ka8
34. Rf4 Qe8+ 35. Kd2 h5 36. Rf8 a5 37. Rxe8+ Ka7 38. Qc7 Ka6 39. Ra8# 1-0

```





## 
        Appendix L

**MONZA CHESS ENGINE (WHITE) X KOMODO16 (BLACK) - 2000 RATED**


```
[Event "vs Computer"]
[Site "Chess.com"]
[Date "2022.04.26"]
[Round "-"]
[White "Monza"]
[Black "Komodo16"]
[Result "1/2-1/2"]
[CurrentPosition "6n1/6P1/3p2K1/2k5/2P5/8/8/8 w - - 11 87"]
[Timezone "UTC"]
[ECO "A45"]
[ECOUrl "https://www.chess.com/openings/Indian-Game-2.Nc3"]
[UTCDate "2022.04.26"]
[UTCTime "12:11:07"]
[WhiteElo ""]
[BlackElo "2000"]
[TimeControl "1/0"]
[Termination "Game drawn by stalemate"]
[StartTime "12:11:07"]
[EndDate "2022.04.26"]
[EndTime "13:07:46"]
[Link "https://www.chess.com/game/computer/10313497"]


1. d4 Nf6 2. Nc3 e6 3. Bg5 h6 4. Bxf6 Qxf6 5. e4 Bb4 6. e5 Qf5 7. a3 Bxc3+ 8.
bxc3 Qg5 9. h4 Qf4 10. Ne2 Qe4 11. Rb1 b6 12. c4 Bb7 13. c5 bxc5 14. dxc5 Bd5
15. f4 Na6 16. Qd4 Qxd4 17. Nxd4 Nxc5 18. Nb5 Kd8 19. c4 Be4 20. Rd1 a5 21. Nc3
Bf5 22. Be2 Ke7 23. g4 Bc2 24. Rd2 Be4 25. O-O Rhb8 26. Rfd1 d6 27. exd6+ cxd6
28. Nxe4 (28. Nxe4 Nxe4 29. Rd4 Nc3 30. R1d2 Rb1+) 28... Nxe4 29. Rd3 Rc8 30.
Re3 Nc5 31. f5 Rab8 32. Re1 e5 33. g5 hxg5 34. hxg5 Rb2 35. Bg4 Rh8 36. Bf3 f6
37. g6 Rh4 38. R3e2 Rb3 39. Bd5 Rxa3 40. Rh2 Rxh2 41. Kxh2 a4 42. Rh1 Rc3 43.
Ra1 (43. Ra1 Rb3 44. Kg1 a3 45. Kf1 e4) 43... a3 44. Bg2 e4 45. Kg1 Kd7 46. Kh2
Kc6 47. Kg1 Rb3 48. Kf1 Rc3 49. Ra2 Rb3 50. Kg1 Rc3 51. Kh2 Rb3 52. Ra1 Rc3 53.
Kg1 Kd7 54. Bf1 e3 55. Ra2 Rc1 56. Kg2 Rc3 57. Kg1 Rb3 58. Ra1 Ke7 59. Ra2 Kd7
60. Ra1 Ke7 61. Ra2 Kf8 62. Ra1 Rc3 63. Be2 Rc2 64. Rxa3 Rxe2 65. Ra8+ Ke7 66.
Ra3 Re1+ 67. Kg2 Ne4 68. Ra7+ Kd8 69. Ra8+ Kd7 70. Ra7+ Kc6 71. Re7 Nd2 72. Rxg7
Re2+ 73. Kh3 Rf2 74. Re7 Rxf5 75. Rxe3 Rh5+ 76. Kg2 f5 (76... f5 77. g7 Rg5+ 78.
Rg3 Rxg7 79. Rxg7) 77. g7 (77. g7 Rg5+ 78. Rg3 Rxg7 79. Rxg7 Kc5) 77... Rg5+ 78.
Rg3 Rxg3+ 79. Kxg3 Ne4+ 80. Kf4 Nf6 81. Kxf5 Ng8 82. Kg6 Kc5 83. Kf7 Nh6+ 84.
Kg6 Ng8 85. Kf7 Nh6+ 86. Kg6 Ng8 1/2-1/2

```

