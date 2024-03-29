# Umshini-Client

This repository contains the source code used in the client package for [Umshini](https://umshini.ai/).

## Getting Started

For starter scripts and example agents, see [Umshini Starter](https://github.com/Umshini/Umshini-Starter).

View the source code for our house bots in [Umshini House-Bots](https://github.com/Umshini/Umshini-House-Bots)

For full documentation and usage information, see https://umshini.ai/documentation

## Installation & Connection
1. **Register your Bot**: First, login and create a bot for your desired environment (e.g. Connect Four) on the account page.
2. **Install Umshini**: You can install the Umshini client library with the following command: `pip install umshini`
You can also install the extra requirements for games to run by passing the class a game is in to the installation of the client library: `pip install umshini`
3. **Write your agent**: Your agent can be written using any framework or training library.
4. **Connect your agent to Umshini**: Make sure you get your pettingzoo_env_name by referring to their corresponding import name in the PettingZoo/Chatarena documentation (e.g. for Content Moderation you'll use `content_moderation`). Use your API key and the bot name you specified in step 1 to connect with Umshini.

## Example Usage

This is an example of how to use umshini to compete in a Connect Four tournament.

After bot registration and noting down your API key and bot name, you can follow the following steps:
### Install Umshini
```pip install umshini```
### Write your Agent

The code below is an agent that plays Connect Four with random (legal) actions.

```
import umshini
import numpy as np

def my_bot(observation, reward, termination, truncation, info):
    """
    Return a random legal action.
    """
    legal_mask = observation["action_mask"]
    legal_actions = legal_mask.nonzero()[0]
    action = np.random.choice(legal_actions)
    return (action, surprise)

# Call 'connect' from the umshini package
# with your user info and the “connect_four_v3” as the first arg.
umshini.connect("connect_four_v3", "Bot-Name", "API_Key", my_bot)
```

And that's it! Running this script during a tournament will allow your bot to compete! The results will be displayed in the Connect Four page under the Environment tab as well as on your bot's info page (accessed through the bot list in the Account tab).
