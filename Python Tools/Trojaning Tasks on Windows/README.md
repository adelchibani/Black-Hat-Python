**When you deploy a trojan, you want to perform a few
common tasks: grab keystrokes, take screenshots, and
execute shellcode to provide an interactive session to
tools like CANVAS or Metasploit. We’ll wrap things up with some sandbox detection techniques to determine if we are running within an antivirus or forensics sandbox. These
modules will be easy to modify and will work within our trojan framework.
We’ll explore man-in-the-browser-style attacks and privilege escalation techniques that you can deploy with your trojan. Each technique comes with its own challenges and probability of being caught by the
end user or an antivirus solution.**


# Notes for the reader

keylogger.py

This script requires pyHook library, that is not compatible with newer versions of Python.

Check for details (and, in the case, updated answers on Stack Overflow - pyHook issues.)

You have two ways ahead:

Search for a wheel file appropriate for the Python version you are running here https://www.lfd.uci.edu/~gohlke/pythonlibs/#pyhook
Use pyWinhook, a pyHook fork with some updates for support latest Visual Studio compilers.
Two methods here:

____ a) pip install pyWinhook==1.6.2

____ b) python -m pip install pyWinhook-1.6.2-cp38-cp38-win_amd64.whl


I would like to switch to keyboard module in order to bypass all this mess, but at the moment I am not able to reproduce the exact workflow offered by the book without going thru pyHook.


ps. if the topic is of your interest, check my keylogger for Power Shell here: https://gist.github.com/carloocchiena/316234e45f67ca63f07620e15e7dfaef

shell_exec.py
Be carefull to base64 encode your raw shellcode script before hosting it on localhost
Store the raw shellcode in /tmp/shellcode.raw
then run (on your linux shell):
user$ base64 -i shellcode.raw >
shellcode.bin
user$ python -m http.server 8000

screenshotter.py
the win32 import issues solved thanks to this answer: https://stackoverflow.com/questions/44063350/python-no-module-named-win32gui-after-installing-pywin32?rq=1
