# MC-Casino
using the mod CC: tweaked (without using turtles or commands and command blocks) for my friends server

ASCII LEGEND:
C - Advanced Computer
M - Advanced Monitor
P - Printer
D - Disk Drive
W - Wireless Modem
X - Chest


1. Developer Console Computer:
This computer is for managing the system’s settings and monitoring activity. It has several functionalities aimed at administrating the slot machines and other computers in the system.
Features:

	•	Game Settings Management:
The developer can adjust various game settings such as the payout rates, the jackpot cap, and the bet limits. This provides flexibility to change game dynamics on the fly.

	•	Progressive Jackpot Control:
The developer has the ability to toggle the progressive jackpot on/off and set a cap on the jackpot, ensuring it doesn’t grow indefinitely.

	•	Win/Loss Ratio Adjustments:
The developer can change the likelihood of the house winning in the slot machine, adjusting the odds to ensure the game remains balanced.

	•	VIP Management:
The developer can assign or revoke VIP status from players. VIPs receive special privileges, such as higher payout rates or exclusive bonus rounds.

	•	Transaction Logging:
The developer can view logs of all transactions in real-time. This includes bets placed, wins/losses, jackpot contributions, and withdrawals from the ATM.

	•	Detailed Activity Log:
The developer can view a detailed log that tracks every action, including which players interacted with the system, the amount they bet, and the payouts they received.

	•	Adjustable Settings:
Through a UI with sliders, the developer can adjust the house’s winning percentage, set bet increments, and modify jackpot size.

	•	Live Feed to Leaderboard:
The developer’s console is integrated with the leaderboard computer, displaying real-time updates of the top players, their scores, win/loss ratios, and the biggest bet.

	•   UI:
The Developer Computer does not need to look as fancy as the other computers but all settings and options should be easily usable with either “on/off” inputs, or editable “50%” digits for chances and the alike, as well as separate sections for viewing the Activity Log.

Blocks used (orientations and block placement in ASCII):
Front view; 
M
D
Side view;
        M
W   C   D

Images:


2. Leaderboard Computer:
This computer displays the top players based on various metrics, allowing players to see who is doing the best in the casino.
Features:

	•	Leaderboard Display:
The leaderboard shows the top players with their respective stats: balance, win/loss ratio, and biggest bet. Players can check their rankings against others.The leaderboard highlights the top player with a gold color, second place with silver, and third place with bronze

	•	Win/Loss Ratio:
Each player’s win/loss ratio is displayed on the leaderboard. With the ratio being either in green or red colour depending if the ratio is more wins then losses, and red if more losses then wins

	•	Progressive Jackpot Tracker:
The leaderboard also shows the current progressive jackpot value, which is constantly updated in real-time.

	•	Real-Time Updates:
The leaderboard is updated live with each spin, showing the latest winners and changes in player rankings.


Blocks used (orientations and block placement in ASCII):
Front View;
MMM
MMM
MMM
MMM
Side View;
        M
        M
        M
W   C   M

Images:

3. ATM Computer:
The ATM allows players to deposit and withdraw items based on their disk drive balance. This is where players manage their funds and interact with the economy of the casino.

Features:
	•	Deposit & Withdrawal:
Players can deposit items (gold nuggets, iron nuggets, emeralds and diamonds, each with editable values in the developer computer) into their disk drives and withdraw from them. The ATM works in tandem with the disk drive to manage balances.

	•	Transaction Fees & Bonuses:
Every deposit and withdrawal can have an associated fee or bonus, which is configurable by the developer. This adds an extra layer of complexity to the economy.

	•	Transaction History:
The ATM logs every deposit and withdrawal action for transparency, allowing both the player and the developer to see past transactions

	•	Item Storage:
Deposited items are held in a separate storage chest. Players can only withdraw items they have previously deposited. This prevents players from exploiting the system.

	•	Customizable Currency & Rates:
The ATM allows the developer to set the value of each item, giving them control over the in-game economy. The value of currency can fluctuate based on game events or developer input.

	•	Transaction Bonuses:
Players may receive bonuses based on their transactions (e.g., a percentage of the amount deposited as a bonus). These bonuses are adjustable by the developer.

	•	VIP-Only Features:
VIP players can access special withdrawal limits or get higher bonus rates when using the ATM. This adds an extra incentive for players to become VIP members.


Security measures:
Drives for the casino can only be made by the developer computer and drives made by the developer computer are the only drives that can be used within the casino, to stop people from artificially adding to their drives. Casino drive creation should be a section in the developer computer where we can set the players name and open their account if needed.

Blocks used (orientations and block placement in ASCII):
Front View;
    M
X   D   X
Side VIew:
    D
W   C  X

Images:

4. VIP Management and Benefits:
The VIP system gives special perks to high-level or frequent players. VIPs receive enhanced benefits that make the game more rewarding.

Features:
	•	VIP Status Assignment:
The developer can assign VIP status to players. This status can be toggled on and off at any time.

	•	VIP-Only Payouts:
VIPs can receive better payouts on the slot machines. For example, they may get a higher payout percentage or access to exclusive game features.

	•	VIP Access to Special Bonuses:
VIP players can receive bonus items, higher withdrawal limits at the ATM, and other in-game advantages.

	•	Leaderboard VIP Tag:
VIP players are tagged with a “VIP” status on the leaderboard and other interfaces, making them stand out among the other players.


5. Slot Machine Computer:
This is the core machine where players interact with the slot game. It allows players to place bets, spin the reels, and view their results.

Features:
	•	Reels & Symbols:
The machine has three spinning reels with a variety of symbols. Players can bet on the outcome of the spin. The possible symbols include “cherry,” “lemon,” “orange,” “plum,” “bar,” and “seven.”

	•	Betting:
Players can place bets ranging from a set minimum to a maximum limit. The bet amount determines the potential payout.

	•	Partial Match Payouts:
If two of the three symbols match, players can win a small payout. This incentivizes players to play even when they don’t hit the jackpot.

	•	Progressive Jackpot:
A portion of each bet contributes to a progressive jackpot. If the player wins the jackpot, the total jackpot prize is awarded. However, the jackpot has a cap that can be set and toggled by the developer.

	•	Animation of Spinning Reels:
The slot machine features smooth animations of the reels spinning, providing a more immersive gaming experience.

	•	Dynamic Payouts:
The payout for each symbol is dynamically calculated based on the bet. Higher bets yield higher rewards for matching symbols.

	•	User Interface (UI):
The machine has an intuitive UI, displaying the reels, bet amount, and spin button. Players can interact directly with the screen to place bets and spin the reels.

Player Control:

Players should never need or be able to interact with the computer or command line its self, all interaction (besides with the developer computer) should be through buttons on the displays as to not allow for players to bypass the code.


Blocks used (orientations and block placement in ASCII):
Front View;
 M
D 
Side VIew:
        M
W   C  D

Images:


6. Game Balancing:
To ensure fairness and maintain the longevity of the game, the following balancing features are implemented:
Features:

	•	Adjustable Odds for House Edge:
The developer can adjust the odds for the house to win. This allows for fine-tuning of the system to ensure that the casino has a built-in advantage but still allows players to have fun.

	•	Randomized Outcomes:
The system uses a random number generator (RNG) for the outcomes of the slot machine spins, ensuring fairness.

	•	Customizable Bet Increments:
Players can choose to increase or decrease their bet in increments defined by the developer. This provides flexibility for the player and ensures that they can manage their funds.

