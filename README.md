# Steamodded - A Balatro ModLoader

## Introduction

Steamodded is a mod loader and injector for the game Balatro. It is developed using Lua for the injected code and Python for additional tools. Currently, Steamodded focuses on basic mod loading and injection functionalities and does not include a modding API.

## Features

- **Mod Loader:** Loads mods into the game.

It will load every mods located at the path `C:\Users\<USER>\AppData\Roaming\Balatro` (or `%appdata%\Balatro\Mods`) into the game.
If it's for now very simple, it will seach for an header at the top of the file that looks like this:

```text
--- STEAMODDED HEADER
--- MOD_NAME: Your Mod Name
--- MOD_ID: YourModID
--- MOD_AUTHOR: [You, AnotherDev, AnotherOtherDev]
--- MOD_DESCRIPTION: The Description of your Mod
```

This header is mandatory and the mod loader will not load the mod without it.

The `MOD_ID` must be unique and without spaces. The `MOD_AUTHOR` mus be an array. Every part of the Header must be present.

After the Header validation, the lua code of your mod will be loaded.

- **Core Management:** Handles the overall management of mods.

This is the hearth of the project, every parts depend on it.

For now it's not doing much outside of displaying basic informations and offering a basic GUI for Steamodded. In the future it will be the most important part of the project.

- **Debug Socket:** Provides a way to output debug data.

The debug Socket is used to send debug informtions from the Game and the Mods outside of the Game. Since we can't launch Balatro linked with a console interface, it's the most efficient way to provide debug data.

- **Injector:** Injects Steamodded into Balatro.

The injector is coded in Python. It's used to inject every other parts of Steamodded into the base game.

It use 2 external tools: [7zip](https://www.7-zip.org/) for is extreme capability in term of SFX ZIP, permiting Steamodded to modify the executable without breaking it, and [luajit-decompiler-v2](https://github.com/marsinator358/luajit-decompiler-v2) that is used for decompiling the code before reinjection. Big thanks to them, they made this project way easier to do.

The code is NOT recompiled after injection. It might change in the future but it will stay like that for now.

## Installation

### How to Install Steamodded

#### Windows

- **CLOSE THE GAME !**
- Go to the [release page](https://github.com/Steamopollys/steamodded/releases) and download the latest or nightly release (Your aiming for the ".exe" download)
- Drag and Drop your "Balatro.exe" to the executable
- Wait for it to finish
- And that's it! Balatro is now ready to be Modded.

#### Linux

- **CLOSE THE GAME !**
- Make sure you have python3, pip3, MPocate/PLocate, 7zip-full, and the python requests library.
- run `git clone https://github.com/Steamopollys/Steamodded.git && cd Steamodded && python3 steamodded_injector.py $(/common/Balatro/Balatro.exe | head -n 1)`
- Wait for it to finish
- And that's it! Balatro is now ready to be Modded.

#### Mac

- **CLOSE THE GAME !**
- Make sure you have python3, pip3, MPocate/PLocate, 7zip-full, and the python requests library.
- run `git clone https://github.com/Steamopollys/Steamodded.git && cd Steamodded && python3 steamodded_injector.py` and drag in the Balatro.exe before hitting enter!
- Wait for it to finish
- And that's it! Balatro is now ready to be Modded.

### How to Install a Mod

- Go to `C:\Users\<USER>\AppData\Roaming\Balatro\Mods` (or `%appdata%\Balatro\Mods`) (Create the "Mods" directory if necessary)
- On Linux it is typically `/home/$USER/.local/share/Steam/steamapps/compatdata/2379780/pfx/drive_c/users/steamuser/AppData/Roaming/Balatro/Mods`
- Put the mod into the directory (only the Mod File if there is only one file provided or all the files in a subdirectory)
- Launch the Game and enjoy!

## Dependencies

- [7zip](https://www.7-zip.org/) - Used by the Injector (A gpg pubkey signed repack is used as a better alternative has not been found yet. You can get the pubkey with `gpg --keyserver hkp://keys.openpgp.org --recv-keys 77317C3B9C73D835B9312414D5C9523EBB5CC15B`)

- [luajit-decompiler-v2](https://github.com/marsinator358/luajit-decompiler-v2) - Used by the Injector

All the previous depencies are automaticaly downloaded during the injection.

- [Nuitka](https://pypi.org/project/Nuitka/) - Used to compile the injector

## Contributing

This project is open for contribution. Please, feel free to open a merge request to do so.

Instruction to compile the injector are provided into is dedicated directory.

## License

This project is licensed under the GNU General Public License. This ensures that the software is free to use, modify, and distribute. For more details, see the LICENSE file in the repository.
