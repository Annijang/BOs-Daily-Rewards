# Daily Rewards (1.16.5)

[![Daily Rewards Downloads](http://cf.way2muchnoise.eu/full_628798_downloads.svg)](https://www.curseforge.com/minecraft/mc-mods/daily-rewards)
[![Daily Rewards Versions](http://cf.way2muchnoise.eu/versions/Minecraft_628798_all.svg)](https://www.curseforge.com/minecraft/mc-mods/daily-rewards)

**Note: This version will only receive maintenance updates!**

Daily rewards is a very lightweight and simple Forge mod that rewards players daily.

![Daily Rewards Screenshot](examples/daily_rewards_screen.png)

## Features

- Server and client friendly
- Easy Customization over configuration file
- Extra UI to collect rewarded items and to see upcoming rewards
- Grant daily rewards after some minutes online and not immediately
- Supports mod items and loot bags

## Report Issues

Please report issues over the issue link above.

## Daily Rewards Configuration

All rewards could be customized over the configuration file under `config/daily_rewards_common.toml`.

### Preview reward data

You can preview the configured rewards for each month based on the configuration over the `/DailyRewards preview ...` command.
Example: `DailyRewards preview April`

Please keep in mind that the preview could be different from the actually result if you haven't define a reward for each single day.

### Reset reward data

If you want to reset the rewards for the current month, the easiest way is to delete the reward data files inside your world folder under:

- `data/daily_rewards_user.dat`
- `data/daily_rewards.dat`

Alternative you could use an NBT editor to directly edit the files for a specific day.
After the change you need to restart the server, to re-calculate the current daily rewards based on your configuration.

## Internal Data Structure

This section covers the internal data structure used inside the corresponding .dat files.

### Reward Data (daily_rewards.dat)

The reward data are separated by year month and will be calculated at the beginning of the month based on the provided config.

Data structure:

- Rewards
  - Year - Month (key)
  - Rewards 1-31 [ItemStack ...]

### Reward User Data (daily_rewards_user.dat)

The reward user data tracking the given rewards to the user, they have no direct relationship to the reward data to make sure updates will not make former rewards invalid and are only relevant for further items.

Data structure:

- Rewards User
  - Year - Month - UUID (key)
  - Rewards 1-31 (takeable) [ItemStack ...]
  - Last rewarded day (String)
  - Number of rewarded days (int)

## Using with Quark 1.16.5

The inventory sort feature from Quark 1.16.5 is not handling the corresponding slot information correctly like locked slots.
This could be miss-used to cheat, for this reason you should deactivate the feature or adding the following change to your `quark-common.toml` file:

```toml
  #A list of screens that don't play well with quark's buttons. Use "Print Screen Classnames" to find the names of any others you'd want to add.
  "Ignored Screens" = ["de.markusbordihn.dailyrewards.client.screen.RewardScreen"]
```

## Version Status Overview 🛠️

| Version        | Status                |
| -------------- | --------------------- |
| Fabric Version | ❌ Not planned        |
| Forge 1.16.5   | ⚠️ Deprecated         |
| Forge 1.17.1   | ❌ Not planned        |
| Forge 1.18.1   | ❌ Not planned        |
| Forge 1.18.2   | ⚠️ Maintenance only   |
| Forge 1.19     | ⚠️ Deprecated         |
| Forge 1.19.1   | ⚠️ Deprecated         |
| Forge 1.19.2   | ✔️ Active development |

## License

The MIT [LICENSE.md](LICENSE.md) applies only to the code in this repository. Images, models and other assets are explicitly excluded.

## Note

Please only download the mod from the official CurseForge page or with the official CurseForge launcher like:

🚀 <https://www.curseforge.com/minecraft/mc-mods/daily-rewards>

If you are downloading this mod from other sources we could not make sure that it works as expected or does not includes any unwanted modification (e.g. adware, malware, ...).
