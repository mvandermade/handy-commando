# tmux
Easier to get up and running with Linux systems...
https://github.com/tmux/tmux/wiki

## Good to know
Common abbreviations:
- ```C``` : Ctrl
- ```S``` : Shift
- ```M``` : Alt / Option
- ```-``` : Hold down together
- ```prefix``` / ```prefix mode``` : a sticky key

### Prefix key:

The prefix key (default) = ```C-b``` which enables control of ```tmux```. So when in ```tmux```, hold down ```C-b``` together and let go enable it.
There is no visual cue that anything happens when you press both keys and let go, but it's a sticky key-combination which you can follow up to.

It might feel familiar as typing the letter é.

Windows:
- ```'``` -> ```prefix mode``` + ```e``` -> é
- ```'``` -> ```prefix mode``` + ```'``` -> '

OSX:
- ```M-e``` -> ```prefix mode``` + ```e``` -> é 
- ```M-e``` -> ```prefix mode``` + ```M-e``` -> '

tmux:
- ```C-b``` -> ```prefix mode``` + ```prefix-cmd``` -> outcome
- ```C-b``` -> ```prefix-mode``` + ```C-b``` -> ```C-b```
So, if you want to pass ```C-b``` to an open terminal, simply repeat it: ```C-b C-b```.


## Prefix Commands
```C-b``` followed by:

| prefix-cmd  | Outcome       | How to undo, type: |
| ------------- |-------------| -------------|
| ```d```       | Detach tmux session, keeps processes up                                 |
| ```S-5```     | Split screen and spawn new terminal like the o-positions to / as % sign | ```exit ```
| ```S-'```     | Split screen and spawn new terminal like the positions " above ' key    | ```exit ```
| ```[```       | Enter scroll mode (right top shows row counter)                         | ```q```
| ```arrow```   | Jump in the arrow direction                                             | ```C-b arrow```

## Configuration
It is possible to add mouse support to tmux, but I don't recommend changing the default behaviour.
Use the config files in your home dir to change it.

## Using tmux
### Start new
```sh
tmux
```

### Start new with alias
```sh
tmux new -s myname
```

### Detach 
Detach is not reboot persistent... But keeps all processes spawned running while the machine is up. Could come in handy when you run blocking commands without using ```&```.

```C-b d```

### Show all open tmux'
```sh
tmux ls
```

### Attach
Each session spawned by ```tmux``` gets a number. After a detach, you can attach using:
```sh
tmux attach -t 1
```
The aliased "myname" is reattached via:
```sh
tmux attach -t myname
```
