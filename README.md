# number-of-rounds-expected-until-one-coin-remains
You have n fair coins and you flip them all at the same time. Any that come up tails you set aside. The ones that come up heads you flip again. How many rounds do you expect to play before only one coin remains?  Write a function that, given n, returns the number of rounds you'd expect to play until one coin remains.


#include <iostream>

using namespace std;

enum Coin { heads, tails };

Coin flip()

{

    return (rand() % 100) > 49 ? Coin::heads : Coin::tails;

}

int coinCounter(int totalCoins)

{

    int totalRounds = 0;

    int coinsToFlip = totalCoins;

    while (coinsToFlip > 1)

    {

        int coins = coinsToFlip;

        for (int i = 0; i < coins; ++i)

        {

            if (flip() == tails)

            {

                --coinsToFlip;

            }

        }

        ++totalRounds;

    }

    return totalRounds;

}

int main()

{

    int numCoins = 100;

    auto result =  coinCounter(numCoins);

    cout << "Expected rounds to play: " << result << endl;

    return 0;

}
