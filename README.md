# windowsterminal
My Windows Terminal settings.

## Usage

### Background image

* Copy cloned background image to location in `[user-dir]\Pictures\`
  * If needed, fix-up hardwired path to user-dir in `settings.json`-file

### Font

I like the [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/), and use one of them in Terminal. For the font, I use "FuraCode Nerd Font Mono" (in the bundle "FiraCode Nerd Font"), because it has nordic characters; get it (or other Nerd Fonts) here: <https://www.nerdfonts.com/font-downloads>.

The `settings.json` file assumes that the given Nerd font is installed. If not, your Windows Terminal will probably render certain characters weirdly.

### settings.json

Clone, and do one of the following:

#### 1. Setup hardlink to Terminal config settings file

Setup a hardlink to the directory where Terminal looks for its config file:

* `git clone` repo - in the following, we assume cloned into `C:\src\windowsterminal`
* Locate current `settings.json` in `[user-dir]\AppData\Local\Packages\Microsoft.WindowsTerminal[...]\LocalState`
* Rename current `settings.json` to `settings.json.bak` (make sure to delete original; from a non-Terminal shell, else it will recreate)
* Setup hardlink from cloned `settings.json` to where Terminal looks for it's settings - i.e., do something like the following - making sure to replace strings in `[...]`

```cmd
mklink /H [user-dir]\AppData\Local\Packages\Microsoft.WindowsTerminalPreview_[somestring]\LocalState\settings.json C:\src\windowsterminal\settings.json
```

* Open Terminal, and check that it loads the profile without error

_(Note - as of Oct. 2021, have seen cases, where WindowsTerminal overwrites the settings.json file, reverting that it's a hardlink. See [#1](/../../issues/1).)_

#### 2. Manual deploy of settings.json

Manually copy the `settings.json` file to the directory where Terminal looks for its config file.

* `git clone` repo
* Locate current `settings.json` in `[user-dir]\AppData\Local\Packages\Microsoft.WindowsTerminal[...]\LocalState`
* Rename current `settings.json` to `settings.json.bak`
* Copy cloned settings to `settings.json` in said dir.

