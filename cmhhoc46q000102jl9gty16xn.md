---
title: "Claude Code 기본 사용법"
datePublished: Sun Nov 02 2025 12:15:10 GMT+0000 (Coordinated Universal Time)
cuid: cmhhoc46q000102jl9gty16xn
slug: claude-code
tags: claude, claude-code

---

Claude Code를 업무에 활용한지 이제 약 5개월쯤 되었다.  
**Github Copilot → Cursor → Claude Code → Codex** 순으로 나왔던 것 같은데, Cursor를 1년정도 사용하다가, Claude Code가 좋다는 말에 한번 써보다가 갈아탔다.  
요즘 Codex도 서브로 사용해보고 있는데, 똑똑하긴하지만 속도가 느려서 손이 자주가진 않는 듯! Claude Code 리밋 걸렸을 때 잘 사용하고 있다.

Claude Code 관련 문서는 많지만… 최근에 친구가 Cursor를 오래 쓰다가 Claude Code를 써보니 편하다고 해서, 간단한 팁들을 공유해보고자? 친구한테 알려준다는 생각으로 한번 정리해보려고 한다.  
(Claude Code 어느정도 써보신 분들은 다 아는 내용일 듯)

## 터미널 환경 & Extension

Claude Code가 Cursor보다 좋다고 생각한 가장 큰 이유가 터미널 기반이었던 것 같다. (지금은 Cursor도 CLI 환경이 나온걸로 알고있음)  
터미널 기반이다보니 IDE에 국한되지 않고, 여러 환경에서 사용하기 편해서 VSCode 기반인 Cursor환경에 익숙하지 않은 사람들도 사용하기 편한 듯

나는 일반 터미널에서도 사용하고, 대부분은 **VSCode Extension**으로 열어서 사용한다. 이렇게 사용하면 Cursor와 크게 다르게 느껴지진 않는다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762083209096/46201038-bea7-4649-bfd6-acf8a4d27d6d.png align="center")

이 Extension을 설치해주면 VSCode 우측 상단에 클로드 아이콘이 생겨서 열어서 사용하면 된다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762083280328/c2e8a5d3-f4fc-4e3c-af1b-515104c934a6.png align="center")

### Mode

* 3가지 모드가 있다. **Plan mode, edit automatically, Ask before edits**
    
* Plan mode는 코드를 수정하지 않고, 설계만 해서 제안하는 형식이고,
    
* 뒤에 2개는 설계도 하고, 그대로 코드 수정도 하는 모드이다.
    
* 오래걸리는 작업의 경우 plan mode로 설계를 해서, 원하는 설계가 완성되면 그대로 코드를 수정시키는 것도 좋다. (귀찮을 땐 바로 수정모드로 작업함)
    
* UI에서도 설정가능하고, 단축키는 **Shift + Tab**
    

### 파일

* 어느 파일을 봐야하는지 지정할 때는 **@를 쓰고, 그 뒤에 파일명**을 적어주면 된다.
    
* 파일을 잘 명시해주면 클로드가 파일 찾는 시간 및 토큰을 줄일 수 있어서 좋다.
    
* 명시한 파일만 보는건 아니고, 그 안에 요청한 내용이 없으면 알아서 연관된 파일도 찾아서 작업한다.
    
* 명시하지 않아도 알아서 검색을 잘해주긴한다. (클로드가 잘하는게 코드, 파일 검색인 듯?)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762083521117/2476a672-fd4d-4a62-a04a-0fe163483075.png align="center")

### 토큰 Limit

* **세션 한도**와 **주간 한도**가 있다.
    
* 세션 한도는 클로드코드 세션 **5시간동안 토큰 사용량이 소진되면, 세션 이후에 다시 리셋된다.**
    
* 예를들어 8시부터 사용시작 → 이 세션의 종료시간은 13시 → 13시전에 토큰 소진 시 13시에 리셋되어 다시 사용가능
    
* 주간한도는 일주일단위로 클로드가 돌아간 시간에 해당되는 Limit이다.
    

### 그 외

* 클로드와 대화를 종료할 때는 `ctrl + c`가 아닌, `ESC`를 누르면 된다.
    
* 대화를 초기화 하고 싶을 땐 `/clear`
    
* 또 생각나면 추가해보겠음…
    

## CLAUDE.md

* 클로드 코드를 사용하기 시작할 때 가장먼저 설정 해야하는 것
    
* **CLAUDE.md는 클로드가 작업을 할 때 항상 먼저 참고하는 문서이다.**
    
* **프로젝트 설명, 코드 컨벤션, 기술스택 등등 프로젝트 작업할 때 참고하면 좋은 내용이 들어가있으면 된다.**
    
* 프로젝트 루트 경로에 위치한다. (클로드용 리드미라고 생각하면 됨)
    
* `/init` 커맨드를 실행하면 클로드가 현재 프로젝트 코드를 기반으로 CLAUDE.md를 써준다!
    
* 작성된 CLAUDE.md에 내용을 추가하거나 커스텀 해서 사용하면 된다.
    

## Commands

* 가장 잘 쓰고 있는 기능!
    
* 클로드는 `/clear`, `/compact` 등 기본으로 제공되는 커맨드가 있는데, **커스텀으로 커맨드**를 만들어 사용할 수도 있다.
    
* **자주 사용하는 프롬프트**를 좀 더 구조적이고 자세히 md 파일로 만들면 같은 작업을 할 때 커맨드 사용만하면 되므로 왕 편하다!
    
* `.claude` 폴더 안에 `commands` 폴더 안에 md 파일을 넣어주면 사용할 수 있다.
    
* 어떻게 작성해야할지 모르겠다면 원하는 작업을 클로드한테 말하고 commands를 만들어달라고하면 잘 작성해줄거다~
    

### 내가 사용하는 커스텀 커맨드들

* `/pr-description` - pr description 작성해주는 커맨드. pr을 올리고 pr 번호를 쓰면 코드 변경사항을 보고 pr description을 작성해서 실제 업데이트까지 해준다. (github cli 활용)
    
* `/review` - 코드 리뷰를 써주는 커맨드. pr 번호를 쓰면 코드 변경사항을 보고 코드 리뷰를 써서 올려준다. (github cli 활용)
    
* `/test` - 테스트코드 작성 지침을 넣어서 사용
    
* `/optimize` - 최적화 포인트를 찾아주는 커맨드
    

\=&gt; 위 커맨드 마크다운 파일들은 [클로드 커스텀 커맨드 레포 (내가 사용하는거 정리)](https://github.com/suyeoniii/claude-code)에 정리되어있다.

## Hooks

* hooks는 많이 활용하고 있지는 않은데, 잘 활용하면 도움이 되는 기능이다.
    
* **클로드가 어떤 작업을 하기 전/후로 특정 작업 (명령 실행 등) 이 실행되도록 할 수 있다.**
    
* 예를들어 클로드가 수정한 코드가 컴파일 오류가 날수도 있고, 테스트에 실패할 수도 있는데, 코드를 수정한 뒤에 빌드&테스트 커맨드가 실행해서 오류를 고치도록 할 수 있다.
    
* 나는 클로드가 수정한 코드 포맷팅인 내 설정과 맞지 않는 경우가 종종 있어서, 수동으로 저장을 해서 포맷팅을 맞춰줬었는데, 아래 **hooks를 통해 클로드가 코드를 수정한 뒤 prettier (코드 포맷팅 도구) 명령어가 실행되도록** 해서 따로 포맷팅을 안해줘도 되게 되었다! (편함)
    

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|MultiEdit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | { read file_path; if echo \"$file_path\" | grep -q '\\.ts$'; then npx prettier --write \"$file_path\"; fi; }"
          }
        ]
      }
    ]
  }
}
```

위 hooks를 간단히 뜯어보면,

* `PostToolUse` = 도구 사용 이후
    
* `Edit|MultiEdit|Write` = 코드 수정 이후
    
* `type: command` = 커맨드 실행
    
* `command` 부분 = 클로드가 수정한 파일명을 찾아서, 해당 파일들에 npx prettier 실행
    

hooks에 대한 자세한 내용은 [Claude Code In Action](https://anthropic.skilljar.com/claude-code-in-action)에 잘 나와있다!

## Agent

* Agent 기능은 업무할 때 사용하고 있지는 않은데, 내가 알기로는 ‘너는 시니어 백엔드 개발자야. 어떤어떤 작업을 하고 어떤어떤거를 신경써서 작업해야해’. 이렇게 역할을 부여하는 기능으로 알고있다.
    
* 예시로는 **TDD 작업**을 할 때
    
    1. 처음에 테스트 코드를 작성하는 Agent
        
    2. 실제 코드를 작성하는 Agent
        
    3. 리팩토링하는 Agent
        
* 이렇게 3개의 Agent가 실행되도록해서 역할을 분리해서 작업할 수 있다.
    
* 이렇게 작업할만한게 잘 없기도하고 토큰도 많이 쓸 것 같아서 나는 잘 사용하고 있진 않다..
    

## MCP

* MCP에 대해서 잘 모르겠다면 내가 예전에 쓴 MCP 포스팅 보고 오기.. [MCP란 무엇인가?](https://medium.com/ne-o-rdinary-tech/ai%EC%99%80-%EC%99%B8%EB%B6%80%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%84-%EC%97%B0%EA%B2%B0%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-mcp%EA%B0%80-%EB%A7%8C%EB%93%9C%EB%8A%94-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B0%9C%EB%B0%9C-%ED%99%98%EA%B2%BD-2575804d176c)
    
* `claude mcp add` 커맨드로 mcp 서버 연결을 할 수 있다.
    
* 주변에서 가장 많이 사용하는 mcp는 serena mcp인 것 같다. 내부 캐싱을 통해 토큰 사용량을 줄여준다고 함! 관심있으면 한번 써보기~ [Serena MCP 레포](https://github.com/oraios/serena)
    

## Skills

* 비교적 최근에 나온 기능인데, 나도 한번 찾아보고 써봐야한다..! 요건 다음 포스팅에서 공부하고 써보고 정리해볼 예정~
    

## 폴더 구조

위 내용들 중 commands, hooks가 적용된 프로젝트 구조 예시는 아래와 같다.  
프로젝트 루트 경로에 `.claude` 아래에 commands, settings를 넣어주면 되고,  
hooks의 경우 `settings.json`에 위에 작성한 json형태로 넣어주면 된다.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1762085544413/bd36cfc5-8d21-45b8-a0ff-160f5ca98e90.png align="center")

잘 모르겠는 부분이 있다면 질문주세요~ 읽어주셔서 감사합니다^-^

## 자료

* [Claude Code In Action](https://anthropic.skilljar.com/claude-code-in-action) - 앤트로픽에서 공식으로 제공하는 튜토리얼, 한번 쭉 읽어보면 도움됨
    
* [클로드 커스텀 커맨드 레포](https://github.com/suyeoniii/claude-code) \- 내가 사용하는 것들 정리