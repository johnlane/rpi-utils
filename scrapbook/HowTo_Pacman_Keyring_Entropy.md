# Pacman Keyring Entropy

Setting up the Pacman keyring requires "entropy" (randomness) in order to compute its keys.

This is one way to quickly provide this entropy on a new system that has not been running
long enough to do this on its own. (Such a system could otherwise take hours to complete
"pacman-key --init")

    $ pacman -S haveged
    $ haveged -w 1024
    $ pacman-key --init
    $ pkill haveged
    $ pacman -Rs haveged


