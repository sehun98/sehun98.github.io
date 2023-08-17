---
title: "C Language : Install2"
excerpt: "Visual studio Code에서 C Language 사용하기"
categories:
  - C Language
---

<br>

<br>

## ⭐ Visual Studio Code에서 C Language 사용하기 ⭐

<br>

## Visual Studio Code Extension `C/C++ Extension pack` 설치하기

<img width="716" alt="15" src="https://github.com/sehun98/TIL/assets/100746863/d2b996ec-e68b-4c3b-9615-fbb2296980bd">

## 윈도우 C 컴파일러 gcc를 사용하기 위한 MinGW 설치하기

<img width="624" alt="16" src="https://github.com/sehun98/TIL/assets/100746863/f5e4a8b1-56b7-4478-b3d8-13f58a7c9ab8">
<img width="443" alt="17" src="https://github.com/sehun98/TIL/assets/100746863/f108b29c-2025-481a-8905-493e779b0c2f">
<img width="946" alt="18" src="https://github.com/sehun98/TIL/assets/100746863/595a9a9a-732f-493b-a09d-50f6e7abb858">
<img width="945" alt="19" src="https://github.com/sehun98/TIL/assets/100746863/f881ae71-bcb7-42e4-b49e-da0261bccf2d">
<img width="282" alt="20" src="https://github.com/sehun98/TIL/assets/100746863/3268e8b9-2c9e-4b7d-b488-581fb913bbc2">

<br>

## MinGW path 설정하기 

path : `C:\MinGW\bin` 

<img width="822" alt="21" src="https://github.com/sehun98/TIL/assets/100746863/7c02b2f8-ee1e-42fa-85fc-ff020b520591">
<img width="726" alt="22" src="https://github.com/sehun98/TIL/assets/100746863/1065d23a-0e40-4b58-853a-22c5ffd6fbf6">

<br>

Visual Studio Code에서 코드 작성 후 `Terminal > Configure Default Build Task`

<img width="640" alt="23" src="https://github.com/sehun98/TIL/assets/100746863/41889e06-7f18-44a5-8ee2-fd6f1c2070fe">

Task에 다음 코드 붙혀넣기

```yaml
{
    "version": "2.0.0",
    "runner": "terminal",
    "type": "shell",
    "echoCommand": true,
    "presentation": {
        "reveal": "always"
    },
    "tasks": [
        {
            "label": "save and compile for C++",
            "command": "g++",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "group": "build",
            "problemMatcher": {
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}"
                ],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
        {
            "label": "save and compile for C",
            "command": "gcc",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": {
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}"
                ],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
        {
            "label": "execute",
            "command": "cmd",
            "group": "test",
            "args": [
                "/C",
                "${fileDirname}\\${fileBasenameNoExtension}"
            ]
        },
        {
            "type": "cppbuild",
            "label": "C/C++: gcc.exe 활성 파일 빌드",
            "command": "C:\\MinGW\\bin\\gcc.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": "build",
            "detail": "디버거에서 생성된 작업입니다."
        },
        {
            "type": "cppbuild",
            "label": "C/C++: g++.exe 활성 파일 빌드",
            "command": "C:\\MinGW\\bin\\g++.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": "build",
            "detail": "디버거에서 생성된 작업입니다."
        },
        {
            "type": "cppbuild",
            "label": "C/C++: gcc.exe 활성 파일 빌드",
            "command": "C:\\MinGW\\bin\\gcc.exe",
            "args": [
                "-g",
                "${file}",
                "-o",
                "${fileDirname}\\${fileBasenameNoExtension}.exe"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": "build",
            "detail": "컴파일러: C:\\MinGW\\bin\\gcc.exe"
        }
    ]
}
```

<br>

## 단축키 설정하기

<img width="460" alt="25" src="https://github.com/sehun98/TIL/assets/100746863/152f9d7b-f20a-48db-b478-46c59e78f318">
<img width="412" alt="26" src="https://github.com/sehun98/TIL/assets/100746863/140d07b2-d183-4739-98c7-24628c56f2c9">

```yaml
// Place your key bindings in this file to override the defaults
// 아래 키 바인딩을 파일에 넣어서 기본값을 덮어 씁니다.


[
    // 컴파일
    {
        "key": "ctrl+alt+c",
        "command": "workbench.action.tasks.build"
    },
    // 실행
    {
        "key": "ctrl+alt+r",
        "command": "workbench.action.tasks.test"
    }
]

```

<br>

## 실행하기

ctrl + alt + c : 컴파일하기

ctrl + alt + r : 실행하기

<img width="639" alt="24" src="https://github.com/sehun98/TIL/assets/100746863/3ffa179b-058a-4988-89c5-3ee6ba91ee20">

<br>

<br>
