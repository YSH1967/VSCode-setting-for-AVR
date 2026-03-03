## **1. ATmega328p 개발에 필요한 toolchain 설치**

## ✅ 1. avr-gcc 를 설치하기 위해 microchip 사이트로 가자 !!

https://www.microchip.com/en-us/tools-resources/develop/microchip-studio/gcc-compilers

- **Linux 버전을 다운받자**

![마이크로칩 사이트](images/image1.png)

- **다운받은 후 터미널에서**

```bash
cd ~/Downloads
tar -xf avr8-gnu-toolchain-*-linux.any.x86_64.tar.gz
sudo mkdir -p /opt/microchip/avr-gcc
sudo mv avr8-gnu-toolchain-linux_x86_64/* /opt/microchip/avr-gcc/
```

![bash](images/image01.png)

![bash](images/image2.png)

![bash](images/image03.png)

## ✅ 2. 환경변수 설정 (`~/.bashrc` 또는 `~/.zshrc`)

```bash
export PATH=/opt/microchip/avr-gcc/bin:$PATH
```

![image.png](attachment:3c0feb33-8d22-4773-8a2a-f4118a03edda:image.png)

- **설정 반영**

```bash
**source ~/.bashrc   # 또는 source ~/.zshrc**
```

![image.png](attachment:09fab41b-9f47-4203-bbad-96359699045d:image.png)

---

## ✅ 3. 설치 확인

```bash
**avr-gcc --version**
```

- **정상 출력되면 설치 성공!**

![image.png](attachment:85155bc5-5b67-43d1-9f15-96c3720c4696:image.png)

---

### ➡️**나머지 설치 정리: 한방에 설치**

```bash
**sudo apt update**
```

![image.png](attachment:9b80fb67-5b03-47d0-8800-80c2bde30a1a:image.png)

```bash
**sudo apt install -y avrdude cmake make**
```

- **`avrdude`: 업로드 도구**
- **`cmake`, `make`: 빌드 도구**

![image.png](attachment:9a965ee7-5bb0-40fd-8923-4d6c1b430022:image.png)

### ➡️ **설치 버전 확인 및 위치 확인**

- **avrdude**

![image.png](attachment:2fad450c-2e15-4b7a-a275-6a6394e3f25d:image.png)

![image.png](attachment:bad51429-48fb-4099-a0d9-db740ece9d22:image.png)

- **cmake**

![image.png](attachment:47430276-c114-4f05-b49f-a7855e156594:image.png)

- **make**

![image.png](attachment:68e629ee-1516-4d51-910f-0048add17728:image.png)

## **✅ 4**. VScode 확장 모듈 설치

- **C/C++**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/0a826f10-29c2-4cf8-bcdf-0a1a34fa435c/Untitled.png)

- **CMake**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/21862217-2120-4985-93bf-172730a86d24/Untitled.png)

- **CMake Tools**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/0de4b1fc-8452-49fc-b103-f7ab1f76921a/Untitled.png)

## **✅ 5. 작업영역(workspace)생성**

```bash
**mkdir ~/arduino328p**
```

![image.png](attachment:1516bbf3-7a98-489f-9081-2934ca216164:image.png)

### ➡️ vscode 를 실행

- **File->Save Workspace As... 를 선택**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/752b60d0-f5bc-49e3-9895-e220775057ab/Untitled.png)

- **arduino328p 선택하고**
- **워크스페이스 이름을 정함**

![image.png](attachment:fdf91e35-edca-4521-a2d3-bd34ca17d06c:efe2a3db-eaa1-4a5b-9a74-e77d6de5ed9d.png)

- **vscode 상단을 보면 워크페이스 이름이 바뀜**

![image.png](attachment:73945087-156b-4f46-abe4-8bff6ac00013:image.png)

![image.png](attachment:6b7c6b9f-b360-4a7f-94a6-b39c848b67e0:image.png)

## **✅ 6. 프로젝트 폴더 선택(또는 생성)**

- **testexam 폴더를 arduino328p 폴더내에 생성한다**

```bash
**mkdir arduino328p/testexam
cd arduino328p
ls -l**
```

![image.png](attachment:8a5b4652-d891-4b75-8c33-4a76d970b546:image.png)

- **vscode : File → Add Folder to Workspace… 선택**

![image.png](attachment:6fc56066-53d9-4ee7-a292-4a73044cb2c2:image.png)

- **testexam 폴더를 찾아가 Add 시킨다**

![image.png](attachment:6d3d98b6-11b1-481c-abc8-eddee9e1e32d:f086c1a7-c903-48c8-9e2d-ab2ead5434af.png)

- **Yes 클릭**

![image.png](attachment:440780e6-02e4-480c-a312-660a50dedfd5:image.png)

- **좌측 상단의 Explorer 클릭**

![image.png](attachment:0c9ad783-efde-4321-ae7c-3a6367015f45:image.png)

- testexam 폴더가 추가된것을 볼수 있음

![image.png](attachment:d2a89f40-b6bc-4e77-b5f8-50c9ff12376d:image.png)

## **✅ 7**. CMake Tools 설정

- **Visual Studio Code의 확장모듈 중에 CMake Tools를 선택하고 톱니바퀴를 누르면 나오는 메뉴중에 Extension Settings를 선택**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/48712e12-5844-45c8-84ba-30a8b598d0a4/Untitled.png)

- **설정값을 어느범위로 할 것이냐를 선택해야 하는데 User를 선택하면 항상 적용이 되고,**
- **Workspace를 적용하면 현재 Open한 워크스페이스에 저장이 되어서 워크스페이스별로 설정을 달리 하고자 할때는 Workspace로 설정한다**
- **우리는 Workspace를 선택**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/e227137d-64d5-41ea-ae9f-744e26f85719/431710dd-9679-4d16-b067-503f8729325c/Untitled.png)

- **Cmake: Configure Args**
    - **옵션 중에 Configure Args를 아래 2개의 정의값을 추가한다.**
    - **AVR_TOOLCHAIN_DIR은 이전에 다운로드 받은 AVR GCC 컴파일러의 실행파일 위치임**
    - **CMAKE_MAKE_PROGRAM은 make 실행파일의 위치임**
    - **주의 할 것은 폴더의 슬래시문자를 리눅스에서 사용하는 슬래시로 입력해야 한다.**
    - **윈도우타입인 역슬래시를 입력하면 안됨**

```c
**-DAVR_TOOLCHAIN_DIR=/opt/microchip/avr-gcc
-DCMAKE_MAKE_PROGRAM=/usr/bin/make**
```

![image.png](attachment:6ee16c18-5a9d-4f3d-9c94-71cec3727474:image.png)

- **Cmake: Generator**
    - **빌드프로그램을 make를 사용하기 때문에 Generator 옵션에 Unix Makefiles로 입력**

```bash
**Unix Makefiles**
```

![image.png](attachment:ff59650e-dee8-4248-bb4e-a2107d296afe:image.png)

- **Toolchain Kit 설정**
    - **이제는 빌드를 위한 Toolchain Kit을 설정해야 한다**
    - **먼저 펌웨어 폴더 아래에 tools 폴더를 생성한다**

![image.png](attachment:db38ecd5-69e5-46f2-a78a-06bee70c0336:image.png)

- **CMake의 툴체인 설정 파일을 생성함 →avr-toolchain.cmake**
- **어떤 컴파일러, 링커, 아키텍처를 사용할지 지정하는 설정 파일**

![image.png](attachment:703c0c31-9657-49ab-a5c4-a71bf2b3742a:image.png)

```bash
**# CMake 프로젝트에 AVR 플랫폼 설정
set(CMAKE_SYSTEM_NAME Generic)  # 시스템 이름을 'Generic'(범용)으로 설정
set(CMAKE_SYSTEM_PROCESSOR AVR) # 프로세서를 AVR 마이크로컨트롤러로 설정

# 타겟 MCU 설정 (2025.04.11 수정 사항)
set(MCU atmega328p) # 사용할 마이크로컨트롤러를 ATmega128A로 설정
set(CMAKE_C_FLAGS "-mmcu=${MCU} -DF_CPU=16000000UL -Os")    # MCU 설정 + F_CPU + 최적화
set(CMAKE_CXX_FLAGS "-mmcu=${MCU}") # C++ 컴파일러에 MCU 설정 플래그 전달

# AVR Toolchain 경로 설정
set(BINUTILS_PATH ${AVR_TOOLCHAIN_DIR}) # AVR 도구체인 루트 디렉토리 지정

# AVR Toolchain 실행 파일 경로 설정
set(TOOLCHAIN_PREFIX ${AVR_TOOLCHAIN_DIR}/bin/avr-) # AVR 컴파일러 및 유틸리티 파일 경로 접두사 설정

# CMake 테스트 빌드 대상 유형 설정
set(CMAKE_TRY_COMPILE_TARGET_TYPE STATIC_LIBRARY) # CMake의 테스트 컴파일을 정적 라이브러리로 제한

# 컴파일러 경로 설정
set(CMAKE_C_COMPILER "${TOOLCHAIN_PREFIX}gcc" CACHE FILEPATH "C Compiler path") # C 컴파일러 경로
set(CMAKE_ASM_COMPILER ${CMAKE_C_COMPILER}) # ASM(어셈블리) 컴파일러를 C 컴파일러와 동일하게 설정
set(CMAKE_CXX_COMPILER "${TOOLCHAIN_PREFIX}g++" CACHE FILEPATH "C++ Compiler path") # C++ 컴파일러 경로

# AVR에서 사용하는 추가 유틸리티 경로 설정
set(CMAKE_OBJCOPY ${TOOLCHAIN_PREFIX}objcopy CACHE INTERNAL "objcopy tool") # 바이너리 변환 유틸리티 설정
set(CMAKE_SIZE_UTIL ${TOOLCHAIN_PREFIX}size CACHE INTERNAL "size tool") # 바이너리 크기 확인 유틸리티 설정

# C/C++ 표준 버전 설정
set(CMAKE_C_STANDARD    11) # C 언어 표준을 C11로 설정
set(CMAKE_CXX_STANDARD  11) # C++ 언어 표준을 C++11로 설정

# 컴파일러 확인 단계 비활성화
set(CMAKE_C_COMPILER_FORCED TRUE) # C 컴파일러 강제 사용 (검사 생략)
set(CMAKE_CXX_COMPILER_FORCED TRUE) # C++ 컴파일러 강제 사용 (검사 생략)

# 컴파일 및 링크 시 사용할 검색 경로 설정
set(CMAKE_FIND_ROOT_PATH ${BINUTILS_PATH})   # 검색 루트 경로를 도구체인 경로로 설정
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER) # 프로그램 검색 시 루트 경로 사용 안 함
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY) # 라이브러리 검색 시 루트 경로만 사용
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY) # 헤더 파일 검색 시 루트 경로만 사용
set(CMAKE_FIND_ROOT_PATH_MODE_PACKAGE ONLY) # 패키지 검색 시 루트 경로만 사용**
```

- **Toolchain Kit 설정파일을 만들기 위해서 testexam폴더 밑에 .vscode 폴더를 생성하고**
- **그 아래에 cmake-kits.json 이름으로 새로운 파일을 생성**

```
**🧩 cmake-kits.json이란?

	- VSCode의 CMake Tools 확장 기능에서 사용하는 설정 파일
	- CMake에서 사용할 툴체인이나 컴파일러 환경(KIT)을 VSCode에 알려주는 역할을 함
	- 이 파일은 보통 .vscode/ 폴더 안에 있고, 여러 개의 빌드 환경을 저장해두고 선택할 수 있도록 도와줌

✅ 왜 필요해?
	- avr-toolchain.cmake는 CMake 자체에 알려주는 설정이고,
	- cmake-kits.json은 VSCode에서 툴체인을 선택할 수 있도록 UI에 보여주는 용도임
	
👉 즉, cmake-kits.json을 쓰면 VSCode에서 "이 툴체인 쓸래!" 하고 툴체인을 클릭해서 선택할 수 있음**
```

```json
**주석지원 안함 !!!!

[
    {
        "name": "AVR-GCC Embedded",     // VSCode에서 선택할 이름-> 지워야 함
        "toolchainFile": "${workspaceFolder}/tools/avr-toolchain.cmake"  //툴체인 파일 경로-> 지우셈
    }
]**
```

## **✅ 8. CMake Configuration**

- **CMake : Quick Start 를 선택**

![image.png](attachment:9cde0d43-a7f0-4144-b9d0-f1aa0e5abcb3:image.png)

- **프로젝트 이름을 넣음**

![image.png](attachment:e920ad81-7fcb-4f92-a57f-07a4c9bd60e7:image.png)

- **C Create C project 선택**

![image.png](attachment:18743bd0-e862-494d-a555-42ec65457784:image.png)

- **실행파일 만들꺼니까.. Executable 선택**

![image.png](attachment:b08bec30-d53e-40e6-84d1-76d341e20c49:image.png)

- **그냥 OK 선택**

![image.png](attachment:2eb881fe-9c87-4486-8114-e3fc7d7ce0b0:image.png)

### 🔍 의미는?

- 이건 CMake에서 제공하는 **추가 옵션 선택 화면**

| **옵션** | **설명** |
| --- | --- |
| **CPack** | **CMake 프로젝트에서 **설치/배포 패키지 (ex: .deb, .rpm 등)**를 만들 수 있게 해주는 모듈** |
| **CTest** | **CMake에서 **테스트 프레임워크 (ex: 단위 테스트)**를 사용할 수 있게 해주는 모듈** |

---

### 🔍 AVR 프로젝트에서는?

- AVR 마이컴 프로젝트에서는 **둘 다 필요 없음** (우노에서는 테스트 자동화나 패키징이 거의 없음)
- 그냥 **선택 안 하고 OK 눌러도 전혀 문제 없음**

---

### 🛠 트러블이 생기면….

![image.png](attachment:58e27a79-6e99-4a9b-aa22-5723ab997958:image.png)

![image.png](attachment:93d01a37-f069-47a2-8c4c-ddf11d045b48:image.png)

---

- **F1 키를 누르고 CMake: Configure를 선택**
- **CMake Configuration을 실행하면 CMakeLists.txt 파일이 생성이 되고 기본적인 main.c 파일이 생성이 된다**

![image.png](attachment:460a9d2a-67aa-407e-983c-fc005d4d5133:image.png)

- **Select a Kit 메뉴가 나오면 이전에 추가했던 AVR-GCC 툴킷을 선택**

![image.png](attachment:e7d292ce-3416-40e3-ad70-5cae97da4922:image.png)

- **기본적인 CmakeList.txt 가 생성됨**

![image.png](attachment:a3adb5dd-b5aa-48d8-9c8c-d4cdc8ed6159:image.png)

![image.png](attachment:3301d9e9-3709-48c7-95e2-728c83f64c4d:image.png)

- **main.c 파일을 아래와 같이 변경**

![image.png](attachment:e2020321-cf09-4ce0-b2ff-a88f7426fca9:image.png)

- **다시 F1을 눌러 CMake:Configure를 실행**

![image.png](attachment:460a9d2a-67aa-407e-983c-fc005d4d5133:image.png)

- **이번에 실행을 하면 Toolchain Kit과 CMakeLists.txt 기반으로 빌드환경이 만들어 짐**

![image.png](attachment:ebf464e3-93a2-42f5-bd6f-4ff9e07d22d9:image.png)

- **build 폴더가 생성되고 이곳에 빌드와 관련된 파일들이 생성된 것을  볼수 있다**

![image.png](attachment:1ba08743-ae7d-45b9-9541-c2cdda3a79ba:image.png)

## **✅ 9. CMake Build**

- **이제 빌드 환경은 다 만들어 졌고 실제로 빌드를 함**
- **F1을 눌러서 CMake: Build를 실행하거나 하단의 Build 아이콘을 누르면 빌드가 진행됨**

![image.png](attachment:ee083a26-ed9b-4af9-b328-eeea4225c1a4:image.png)

- **빌드완료**

![image.png](attachment:cb79a383-2afe-47cc-9c8e-d81f75c40241:image.png)

## **✅ 10. CMakeList.txt 파일을 아래 내용으로 수정**

- **CMakeList에는 컴파일/링커 옵션과 hex파일을 생성하는 부분까지 추가**

```c
**cmake_minimum_required(VERSION 3.10.0)

project(atmega328p
  LANGUAGES ASM C CXX
)

set(EXECUTABLE ${PROJECT_NAME}.elf)

# 소스 파일 수집
file(GLOB SRC_FILES CONFIGURE_DEPENDS
  *.c
  *.cpp
)

file(GLOB_RECURSE SRC_FILES_RECURSE CONFIGURE_DEPENDS
  src/*.c
  src/*.cpp
)

# 실행 파일 생성
add_executable(${EXECUTABLE}
  ${SRC_FILES}
  ${SRC_FILES_RECURSE}
)

# 컴파일 타임 매크로
target_compile_definitions(${EXECUTABLE} PRIVATE
  -DF_CPU=16000000UL
)

# include 디렉토리 설정
target_include_directories(${EXECUTABLE} PRIVATE
  src 
  src/ap
  src/bsp
  src/hw
  src/common
  src/common/hw/include
)

# 컴파일러 옵션
target_compile_options(${EXECUTABLE} PRIVATE
  -fdata-sections
  -ffunction-sections
  -MMD
  -flto
  -fno-fat-lto-objects

  -Wall
  -Os
  -g3
)

# 링커 옵션
target_link_options(${EXECUTABLE} PRIVATE
  -flto 
  -fuse-linker-plugin

  -lm
  -Wl,-Map=${CMAKE_BINARY_DIR}/${PROJECT_NAME}.map,--cref
  -Wl,--gc-sections
  -Xlinker -print-memory-usage -Xlinker
)

# 바이너리 파일 생성 (.hex)
add_custom_command(TARGET ${EXECUTABLE}
  POST_BUILD
  COMMAND ${CMAKE_OBJCOPY} -O ihex -R .eeprom ${EXECUTABLE} ${CMAKE_BINARY_DIR}/${PROJECT_NAME}.hex
  COMMENT "Generating HEX file"
)

# EEPROM 파일 생성 (.eep)
add_custom_command(TARGET ${EXECUTABLE}
  POST_BUILD
  COMMAND ${CMAKE_OBJCOPY} -O ihex -j .eeprom --set-section-flags=.eeprom=alloc,load --no-change-warnings --change-section-lma .eeprom=0 ${EXECUTABLE} ${CMAKE_BINARY_DIR}/${PROJECT_NAME}.eep
  COMMENT "Generating EEPROM file"
)

# 바이너리 사이즈 출력
add_custom_command(TARGET ${EXECUTABLE}
  POST_BUILD
  COMMAND ${CMAKE_SIZE_UTIL} ${EXECUTABLE}
  COMMENT "Firmware Size:"
)**
```

- **다시 빌드를 하면 이제는 펌웨어 섹션별로 용량이 표시되고  hex파일도 생성되는 것을 볼 수 있다**

![image.png](attachment:b87a9cc5-82cb-4acd-8217-602f622dcd9e:image.png)

## **✅ 11. 다운로드 하기**

- **Arduino 를 컴퓨터에 연결한다**
- **우분투 터미널에서 접속된 포트를 확인**

![image.png](attachment:ed41ca7e-9698-4bf7-8bcb-37eb7c79be09:18ae100d-9c13-4571-a9ba-c2d902c1c898.png)

- **/dev/ttyACM0 의 권한 확인**

![image.png](attachment:e363f57a-971c-46e1-851a-ea12b57990fe:image.png)

- **쓰기 권한이 없으로 쓰기 권한을 추가한다**

![image.png](attachment:2b3ae966-f04a-4fb2-b03d-32cd35138827:image.png)

- **Terminal → Run Task..를 실행**
- **Tasks는 이클립스에서 External Tools와 비슷한 기능으로 외부의 프로그램을 연결해서 실행 할 수 있는 기능이다**

![image.png](attachment:15c9cd8a-6c56-4e43-a02f-57641593ef00:image.png)

- **Configure a Task 선택**

![image.png](attachment:11484a1a-d1f7-4703-9612-159ee8737f31:image.png)

- **하단의 Create tasks.json file template → 선택**

![image.png](attachment:eca81808-799c-43d3-80ff-3d33796618b5:image.png)

- **Other → 선택**

![image.png](attachment:e8d07e72-5fea-4fd0-ad62-855734534462:image.png)

- **아래 그림처럼 .vscode 폴더에 tasks.json 파일이 생성되고 기본적인 템플릿 내용이 보인다**

![image.png](attachment:86324c3b-06a4-47c3-b79b-ee79a94149d1:image.png)

- **avrdude 의 위치를 확인**

![image.png](attachment:82552471-ee32-4444-ad04-50c01c5a0989:image.png)

- **task.json 내용을 변경**

```json
**{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Upload to Arduino Uno",
      "type": "shell",
      "command": "/usr/bin/avrdude",
      "args": [
        "-C", "/etc/avrdude.conf",
        "-v",
        "-u",
        "-p", "atmega328p",
        "-c", "arduino",
        "-P", "/dev/ttyACM0",
        "-b", "115200",
        "-D",
        "-U", "flash:w:build/atmega328p.hex:i"
      ],
      "group": "build"
    }
  ]
}**

```

- **Teminal → Run Task 선택**

![image.png](attachment:bab85d6b-8343-43bd-b904-f3d47ca8506a:image.png)

- **완료**

![image.png](attachment:36aa18e2-8232-4049-a754-ccd9822846df:image.png)

====

====

### Task Explorer 에서 사용

```json
**{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "CMake Build",
            "type": "process",
            "command": "cmake",
            "args": [
                "--build",
                "${workspaceFolder}/build",
                "--target",
                "all"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        },
        {
            "label": "CMake Clean",
            "type": "process",
            "command": "cmake",
            "args": [
                "--build",
                "${workspaceFolder}/build",
                "--target",
                "clean"
            ],
            "problemMatcher": []
        },
        {
            "label": "avrdude",
            "type": "shell",
            "command": "/usr/bin/avrdude",
            "args": [                
                "-v",
                "-u",
                "-p", "atmega328p",
                "-c", "arduino",
                "-P", "/dev/ttyACM0",
                "-b", "115200",
                "-D",
                "-U", "flash:w:build/atmega328p.hex:i"
            ],
            "problemMatcher": []
        },
        {
            "label": "Build",
            "dependsOrder": "sequence",
            "dependsOn": [
                "CMake Build",
                "avrdude"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        },
        {
            "label": "Clean",
            "dependsOrder": "sequence",
            "dependsOn": [
                "CMake Clean"
            ]
        }
    ]
}**
```
