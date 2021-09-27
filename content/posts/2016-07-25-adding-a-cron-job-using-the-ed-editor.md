---
title: Adding a Cron job using the ed editor
author: Riinu Ots
date: '2016-07-25'
categories:
  - Unix
slug: adding-a-cron-job-using-the-ed-editor
---

These commands (after the first one) work in the ed editor. ed editor is used in the RStudio server shell.

    sudo crontab -e                                     #opens crontab file in chosen editor

    a                                                   #add to file
    0,30 * * * * Rscript /home/user/folder/script.R     #command to add
    .                                                   #finished editing
    ,p                                                  #print file content to check
    w                                                   #save changes
    Q                                                   #quit

In this example the script will run every 0 hours, 30 minutes, see [Ubuntu: How do I set up a CRON job](http://askubuntu.com/questions/2368/how-do-i-set-up-a-cron-job) for other options.
