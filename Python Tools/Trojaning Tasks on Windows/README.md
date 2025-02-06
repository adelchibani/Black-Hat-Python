**When you deploy a trojan, you want to perform a few
common tasks: grab keystrokes, take screenshots, and
execute shellcode to provide an interactive session to
tools like CANVAS or Metasploit. This chapter focuses
on these tasks. We’ll wrap things up with some sandbox detection techniques to determine if we are running within an antivirus or forensics sandbox. These
modules will be easy to modify and will work within our trojan framework.
In later chapters, we’ll explore man-in-the-browser-style attacks and privilege escalation techniques that you can deploy with your trojan. Each technique comes with its own challenges and probability of being caught by the
end user or an antivirus solution. I recommend that you carefully model
your target after you’ve implanted your trojan so that you can test the modules in your lab before trying them on a live target. Let’s get started by creating a simple keylogger.**
