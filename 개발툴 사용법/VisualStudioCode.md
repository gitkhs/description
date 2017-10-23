## Visual Studio Code

### 단축키
* 다중 셀 선택: `ctrl`+`alt`+`shift`+`down,up`

커스텀 설정(keybindings.json)
```javascript
[
	{	// 깃허브 푸시
		"key": "alt+enter",
		"command": "git.push"
	},
	{	// 터미널에 포커싱
		"key": "ctrl+shift+down",
		"command": "workbench.action.terminal.focus"
	},
	{	// 에디터에 포커싱
		"key": "ctrl+shift+up",
		"command": "workbench.action.focusActiveEditorGroup"
	},
	{	// 대문자 변환
		"key": "ctrl+shift+u",
		"command": "editor.action.transformToUppercase"
	},
	{	// 소문자 변환
		"key": "ctrl+shift+l",
		"command": "editor.action.transformToLowercase"
	}
]
```