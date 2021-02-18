---
title: VS code - Module 'torch' has no 'xxx' member
date: 2020-09-04 11:05:05
tags: 
	- VS code
categories: 
	- VS code
abbrlink: '20200904a' 
---
# vscode  'torch' has no 'xxx' member

vscode User settings中加上

    "python.linting.pylintArgs": [
        "–errors-only",
        "–generated-members=numpy.* ,torch.* ,cv2.* , cv.*",
    ]