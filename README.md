# LB Chess Extension
A LioranBoard extension to play chess with your viewers or between them.

The extension includes a pretty complex deck to play, fully controllable with chat commands. Also allows an easy translation to your language.

Read carefully the documentation on how to set up the game and how to use it.

# Set up
1. [Download the zip file from releases](https://github.com/SebasF1349/LB-Chess-Extension/releases/). The file contains a .lbe file (the extension) and 13 pgn files (the 12 pieces and the chessboard).

2. Place the pgns in any folder where they will be safe (if you delete those files the game will not work).

3. Install the lbe extension. [Check this documentation if you don't know how](https://christinna9031.github.io/LBDocumentation/setup.html#extensions). It will install a new deck called "ChessGame by SebasF". The next steps will use buttons of this deck.

4. Buttons in the deck have 4 different colors:

    * **Black buttons**: Used for the setup. The one at the bottom opens the documentation (this site) for you, in case you need it to reinstall or make some changes.

    * **Red buttons**: Buttons you can use in your streamdeck (although it's better to use chat commands).

    * **Green buttons**: Buttons that are executes by the players. Don't press them in the streamdeck.

    * **Blue buttons**: Just titles so you know what the green buttons in the left do. They don't do anything.

5. First you need to fill information in the "Messages and Translation" button. Open it in the receiver (right click -> edit commands). Although the Math: Change Variable commands are already prefill with messages (in English) you may want to edit them for a more personalized experience (also, it's a good idea to translate it to your language if it's not English). Remember to use "" in the boxes. __*The first two Math: Change Variable (chessPath and username) MUST BE FILLED*__. The button has a lot of comments to understand where each word or phrase will be used. But some may need more clarification:

    * **chessPath**: The file path of the folder containing the pgn files downloaded with the extension. Remember to change / to \ (for example, "C:/Users/SebasF/Documents/LioranBoard Receiver(PC)/Chess").

    * **Username**: Your Twitch username, in lowercase.

    * **Resign command (all lower case)**: This will be the chat command to let the players resign. By default, is "resign", which means that if a player types $resign he/she is resigning (or is voting for resigning in the group votation). You can change it to whatever you want, but it must be in lowercase.

    * **chessPiecesTranslation variable**: Type 0 if you want to use the name pieces in English (q for queen, k for king, and so on). If you want to translate them to your language, type 1 and rewrite the letters inside the if below (always in uppercase).

        ***BE CAREFUL***: If one of the name pieces in your language is K, Q, R, B or K, it can have unexpected consequences. The extension works in English, so when you translate you are replacing letters. For example, in Icelandic the knight is called riddari, so when translating from English it will change the N to a R, and then the R (rook) to H (Hrkur) , transforming a knight into a rook. To avoid that, you will need to manually change the order of the translation in the green Move Input button (search two if statements chessPiecesTranslation == 1)

6. Open the StreamDeck and press the black "Create Chess Scene" button. It will create the "ChessGame by SebasF" scene in OBS. If it's not created or it's created but you can't see the chessboard and pieces in the starting position, check if LB is connected to OBS or if you complete correctly the chessPath in the step 5.

7. The scene has 2 text sources. "ChessMoves" will show the votes in any group. "ChessAlerts" will show any notification, like "Check", "Stalemate" or "White lost on time". They are very basic text sources at creation. You can edit them in OBS, like moving them, changing fonts, size, colour or even some animation. Let your imagination fly.

8. The board and pieces use very precise numbers for the movement and placement, so DON'T MOVE, SCALE OR CHANGE THE IMAGE SOURCES. My advice is to use the scene as a nested scene to fit it with your layout.

9. Set up is completed! You can now play with your viewers.

# How to Play

There are 3 different ways to play.

* **"One vs One"**: Self explanatory. You choose who play. Can be two viewers or you against one of them.

* **"One vs Public"**: You play against the viewers. The viewers vote the moves and the move with more votes it's played.

* **"Public vs Public"**: The viewers play between them. The green  Colour Division button gives every viewer (that want to play) a colour "group" (white or black).

In every move, the players have only 1 minute to play. If it's a group vote, then after 1 minutes you can't vote anymore and the move with more votes will be played. If there is no move in 60 seconds, then you lose on time!

The best way to play is using the chat commands.

## Chat Commands

* **$chessng** (chess new game): To start a new game. Only the broadcaster can use it. There are 3 ways of using it, depending on what game mode you want:

    * **$chessng diplayname1 displayname2**: This will start a "One vs One" between diplayname1 (white) and displayname2 (black). Use the Display Name (with uppercase letters). All the other viewers will not be able to play while the game is in progress.

    * **$chessng w** or **$chessng b**: Starts a "One vs Public" game. w means the broadcaster will play with the white pieces, b for the black pieces.

    * **$chessng**: Starts a "Public vs Public" game. The viewers will have 1 minute to join the game (check **$playchess**), and the deck will decide which color they are assigned. After the game is started, they can still join. As the viewers play between them, you can now relax and what the game.

* **$chessnb** (chess new board): Another "only broadcaster" command. Resets the chessboard and the game. Useful to finish the game or move the pieces to the initial position. If you use **$chessng** it will reset automatically, so there is no need to use **$chessnb** before starting a game.

* **$playchess**: Let the viewers join a "Public vs Public" game. The deck will decide with which colour they will play. If they use the command before starting the game, all the "inscriptions" will be split between white and black. If the game is in progress, they still can join and the deck will decide the color with a chat message.

* **$[chessmove]**: The key command to move! If you are playing alone, doing $e4 will move the pawn to e4 in the board. If the viewers are playing as a team, each vote will be shown in the screen and the move with more votes will be played. The extension will not allow illegal moves. All legal moves are possible, even castling (O-O), promoting (c8Q) or en passant! But be careful, you need to know the algebraic notation very well! You can also vote for resigning with **$resign** (or what you decided in step 5 of set up).

## The Game Flow

To start a new game, you need to use the **$chessng** as explained before. If you press the button on the deck it will default to "Public vs Public" mode.

In each step there will be chat messages from LB explaining what to do. Some messages will let you know how much time is left to move or join a group, others when you can play.

After making a move, you have 10 seconds to think about the position before you can vote (again, a chat message will let you know when you can play).

Of course, the deck will recognise each player and will avoid someone to play if it's not his/her turn. If it's a "Public vs Public", viewers can always use the command **$playchess** to join a group.

## The End of the Game

The extension recognizes all the possible ends of a game, except draw offers (can be added in a future release if requested). In case of mate, stalemate, repetition or 50 moves rules, it will show a screen message in the ChessAlerts text source.

# Miscellaneous

* The deck will create a file called game.ini in the Receiver's folder with the pgn of the game. Can be useful if you plan to analyze the game afterwards in lichess or another website. You can change the name of the file, it's saved at the end of the green "Movement" button. If you play more than one game, all the games will be saved. But in your next stream the old pgns will be replaced. If you want to keep them all you can save them somewhere else after the stream or edit the button to use the date as the name file.

* Clear All Button: This button will clear all the variables and stacks that the extension uses. There are lots of them, but most are auto-deleted after using them. Useful if you want to clean LB, but not important for the game to work.

* Don't edit the deck! Only the black "Messages and Translation" button should be edited. The game is pretty complex and you have to be an advanced LB user to tweak it. It has many comments to help you with that. But, as I said, better to don't do it.

* I think the extension should work with LB 1.43. But I force the 1.44 version because new is better. Always keep LB updated, new cool features are introduced in every new version!

* There are many improvements to be made to the extension, but it works as it is. If you have any suggestion you can ping me in the [LioranBoard discord server](https://discord.gg/dXez8Zh).
