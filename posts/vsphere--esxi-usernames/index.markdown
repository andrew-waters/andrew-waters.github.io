---
layout: post
title:  vSphere / ESXi Usernames
date:   2012-07-24 00:00:00 +0000
category: Posts
---

When adding users to ESXi 4.1 you can sometimes get the error "User name or password has an invalid format".

This is fixable by checking the following:

 - Your password is at least eight characters in length.
 - Your password or username entered contained characters outside of the character types allowed.

Allowed characters:

 - Numbers, uppercase alphabetic characters, and lowercase alphabetic characters
 - Special Characters ``~!@#$%^&*()_+{}|:"<>?/.,';\][=-`)``