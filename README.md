# Greedy Mods

The existing list of [greedy](https://github.com/VoltCruelerz/Greed) mods available for download.

To contribute, merely open a pull request for the repo to change `catalogs/<schemaVersion>.json`.

## Schema

### Catalog Object

| Field | Type | Description |
|:------|:-----|:------------|
| `id`* | `string` | This name of the folder your mod will occupy once installed in the `mods` folder. |
| `name`* | `string` | The human-readable name of the mod. |
| `author`* | `string` | Your name/username. |
| `description`* | `string` | A brief summary of your mod. Save details for the readme. |
| `url`* | `url` | The URL to your thread or repo where you give greater details about your mod. Details beyond what is covered in the description should be covered here. |
| `versions`* | `dictionary<version,versionDetails>` | A dictionary mapping versions of your mod to version detail objects. |
| `latest`* | `version` | The most recent version of your mod that will be the default download for it. |

### Version Detail Object

| Field | Type | Description |
|:------|:-----|:------------|
| `download` | `url` | A link to a publicly-available `.zip` file somewhere on the internet. (I recommend a GitHub release.) If you want users to download manually, rather than through the auto-downloader, provide the instructions to download it in your `url` link above and leave this field undefined. |
| `sinsVersion`* | `version` | The minimum compatible Sins version. |
| `greedVersion`* | `version` | The minimum compatible Greed version. |
| `dependencies`* | `dependency[]` | An array of dependencies. |
| `conflicts`* | `string[]` | An array of mod ids with which this mod is incompatible. |
| `date`* | `MM/DD/YYYY` | The date on which you published your mod. |

### Dependency Object

| Field | Type | Description |
|:------|:-----|:------------|
| `id`* | `string` | The id of the mod on which this mod depends. |
| `version`* | `version` | The minimum required version of the dependency. |

### Examples

#### Standard Mod

```json
        {
            "id": "constituent-components",
            "name": "Constituent Components",
            "author": "Volt Cruelerz",
            "description": "Improves the roster of ship components.",
            "url": "https://github.com/VoltCruelerz/constituent-components",
            "versions": {
                "1.3.0": {
                    "download": "https://github.com/VoltCruelerz/constituent-components/archive/refs/tags/1.3.0.zip",
                    "sinsVersion": "1.15.1.0",
                    "greedVersion": "1.7.0",
                    "dependencies": [],
                    "conflicts": [],
                    "date": "09/04/2023"
                },
                "1.2.0": {
                    "download": "https://github.com/VoltCruelerz/constituent-components/archive/refs/tags/1.3.0.zip",
                    "sinsVersion": "1.15.1.0",
                    "greedVersion": "1.4.0",
                    "dependencies": [],
                    "conflicts": [],
                    "date": "09/04/2023"
                }
            },
            "latest": "1.3.0"
        }
```

#### Mod With Dependencies

```json
        {
            "id": "b_dependent",
            "name": "B Dependent",
            "author": "TEST",
            "description": "Child of the chain",
            "url": "https://github.com/VoltCruelerz",
            "versions": {
                "1.0.0": {
                    "download": "https://raw.githubusercontent.com/League-of-Greedy-Modders/Greedy-Mods/main/beta/b_dependent.zip",
                    "sinsVersion": "1.15.1.0",
                    "greedVersion": "1.7.0",
                    "dependencies": [
                        {
                            "id": "a_dependency",
                            "version": "1.0.0"
                        }
                    ],
                    "conflicts": [],
                    "date": "09/04/2023"
                }
            },
            "latest": "1.0.0"
        }
```

#### Mod With No Download

```json
        {
            "id": "Gauss Weapon Rework",
            "name": "Gauss Weapon Rework",
            "author": "Shrimple",
            "description": "This mod reworks the Gauss weapon type for the TEC Loyalists and TEC Rebels.",
            "url": "https://discord.com/channels/266693357093257216/1148026045124059247",
            "versions": {
                "1.2.0": {
                    "sinsVersion": "1.15.1.0",
                    "greedVersion": "1.5.0",
                    "dependencies": [],
                    "conflicts": [],
                    "date": "09/04/2023"
                }
            },
            "latest": "1.2.0"
        }
```
