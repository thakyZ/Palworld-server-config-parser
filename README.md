# Palworld config parser tool

A simple tool that replaces values in the Palworld dedicated server config file based on environment variables

This tool was made with Pterodactyl in mind but does work outside of it.

![afbeelding](https://github.com/QuintenQVD0/Palword-server-config-parser/assets/67589015/1006e731-b397-4f39-9bca-69cfee4fd2f2)

Yes, this tool can also work on the windows dedicated server but it has a know bug with not clearning variables that are empty, This does work on linux.


If you want to support my work:
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/J3J2HGECS)


## Key with variables

| Config keyword                          | ENV variable                              | Pterodactyl stock  |
|-----------------------------------------|-------------------------------------------|---|
| Difficulty                              | DIFFICULTY                                |   |
| DayTimeSpeedRate                        | DAY_TIME_SPEED_RATE                       |   |
| NightTimeSpeedRate                      | NIGHT_TIME_SPEED_RATE                     |   |
| ExpRate                                 | EXP_RATE                                  |   |
| PalCaptureRate                          | PAL_CAPTURE_RATE                          |   |
| PalSpawnNumRate                         | PAL_SPAWN_NUM_RATE                        |   |
| PalDamageRateAttack                     | PAL_DAMAGE_RATE_ATTACK                    |   |
| PalDamageRateDefense                    | PAL_DAMAGE_RATE_DEFENSE                   |   |
| PlayerDamageRateAttack                  | PLAYER_DAMAGE_RATE_ATTACK                 |   |
| PlayerDamageRateDefense                 | PLAYER_DAMAGE_RATE_DEFENSE                |   |
| PlayerStomachDecreaseRate               | PLAYER_STOMACH_DECREACE_RATE              |   |
| PlayerStaminaDecreaseRate               | PLAYER_STAMINA_DECREACE_RATE              |   |
| PlayerAutoHPRegeneRate                  | PLAYER_AUTO_HP_REGENE_RATE                |   |
| PlayerAutoHpRegeneRateInSleep           | PLAYER_AUTO_HP_REGENE_RATE_IN_SLEEP       |   |
| PalStomachDecreaseRate                  | PAL_STOMACH_DECREACE_RATE                 |   |
| PalStaminaDecreaseRate                  | PAL_STAMINA_DECREACE_RATE                 |   |
| PalAutoHPRegeneRate                     | PAL_AUTO_HP_REGENE_RATE                   |   |
| PalAutoHpRegeneRateInSleep              | PAL_AUTO_HP_REGENE_RATE_IN_SLEEP          |   |
| BuildObjectDamageRate                   | BUILD_OBJECT_DAMAGE_RATE                  |   |
| BuildObjectDeteriorationDamageRate      | BUILD_OBJECT_DETERIORATION_DAMAGE_RATE    |   |
| CollectionDropRate                      | COLLECTION_DROP_RATE                      |   |
| CollectionObjectHpRate                  | COLLECTION_OBJECT_HP_RATE                 |   |
| CollectionObjectRespawnSpeedRate        | COLLECTION_OBJECT_RESPAWN_SPEED_RATE      |   |
| EnemyDropItemRate                       | ENEMY_DROP_ITEM_RATE                      |   |
| DeathPenalty                            | DEATH_PENALTY                             |   |
| bEnablePlayerToPlayerDamage             | ENABLE_PLAYER_TO_PLAYER_DAMAGE            |   |
| bEnableFriendlyFire                     | ENABLE_FRIENDLY_FIRE                      |   |
| bEnableInvaderEnemy                     | ENABLE_ENEMY                              | ✅ |
| bActiveUNKO                             | ACTIVE_UNKO                               |   |
| bEnableAimAssistPad                     | ENABLE_AIM_ASSIST_PAD                     |   |
| bEnableAimAssistKeyboard                | ENABLE_AIM_ASSIST_KEYBOARD                |   |
| DropItemMaxNum                          | DROP_ITEM_MAX_NUM                         |   |
| DropItemMaxNum_UNKO                     | DROP_ITEM_MAX_NUM_UNKO                    |   |
| BaseCampMaxNum                          | BASE_CAMP_MAX_NUM                         |   |
| BaseCampWorkerMaxNum                    | BASE_CAMP_WORKER_MAX_NUM                  |   |
| DropItemAliveMaxHours                   | DROP_ITEM_ALIVE_MAX_HOURS                 |   |
| bAutoResetGuildNoOnlinePlayers          | AUTO_RESET_GUILD_NO_ONLINE_PLAYERS        |   |
| AutoResetGuildTimeNoOnlinePlayers       | AUTO_RESET_GUILD_TIME_NO_ONLINE_PLAYERS   |   |
| GuildPlayerMaxNum                       | GUILD_PLAYER_MAX_NUM                      |   |
| PalEggDefaultHatchingTime               | PAL_EGG_DEFAULT_HATCHING_TIME             |   |
| WorkSpeedRate                           | WORK_SPEED_RATE                           |   |
| bIsMultiplay                            | IS_MULTIPLAY                              |   |
| bIsPvP                                  | IS_PVP                                    |   |
| bCanPickupOtherGuildDeathPenaltyDrop    | CAN_PICKUP_OTHER_GUILD_DEATH_PENALTY_DROP |   |
| bEnableNonLoginPenalty                  | ENABLE_NON_LOGIN_PENALTY                  |   |
| bEnableFastTravel                       | ENABLE_FAST_TRAVEL                        |   |
| bIsStartLocationSelectByMap             | IS_START_LOCATION_SELECT_BY_MAP           |   |
| bExistPlayerAfterLogout                 | EXIST_PLAYER_AFTER_LOGOUT                 |   |
| bEnableDefenseOtherGuildPlayer          | ENABLE_DEFENSE_OTHER_GUILD_PLAYER         |   |
| CoopPlayerMaxNum                        | COOP_PLAYER_MAX_NUM                       |   |
| ServerPlayerMaxNum                      | MAX_PLAYERS                               | ✅ |
| ServerName                              | SERVER_NAME                               | ✅ |
| ServerDescription                       | SERVER_DESCRIPTION                        | ✅ |
| ServerPassword                          | SERVER_PASSWORD                           | ✅ |
| AdminPassword                           | ADMIN_PASSWORD                            | ✅ |
| PublicIP                                | PUBLIC_IP                                 | ✅ |
| PublicPort                              | SERVER_PORT                               | ✅ |
| RCONPort                                | RCON_PORT                                 | ✅ |
| RCONEnabled                             | RCON_ENABLE                               | ✅ |
| bUseAuth                                | USE_AUTH                                  |   |
| BanListURL                              | BAN_LIST_URL                              |   |
| Region                                  | SERVER_REGION                             |   |


# Notes

- If a variable does not exists the parser will not try to change that value in the configuration file.
- If a `DefaultPalWorldSettings.ini` exists but a `PalWorldSettings.ini` does not, it will try to copy it to the right directory.
- If a `DefaultPalWorldSettings.ini` exists and a `PalWorldSettings.ini` exits, but it is empty, then it will try to copy the contents over to the settings file.
- There is some very basic validation on the variables.

|Rule|Value|Example|
|-----|-----|-----|
|Numeric|Allows only positive numeric values|"123" or "25565"|
|Floating|Allows only positive floating-point values|"0.005" or "3.14"|
|TrueFalse| Allows values "True" or "False"|True" or "False"|
|String|Everything|"this is a test" or "test"|
|AlphaDash|Allows only alphanumeric characters and dashes|"abc123" or"test-123"|
