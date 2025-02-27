# VS Code 設定說明文件

此文件包含 VS Code 編輯器的完整設定配置,主要包含以下幾個主要部分:

## 基本設定

- 視窗縮放級別設定為 1.0
- macOS 終端機預設使用 zsh
- 使用 vscode-icons 作為檔案圖示主題
- 使用 Default Dark+ 作為色彩主題
- 自動儲存模式設為切換焦點時儲存

```json
{
  "window.zoomLevel": 1.0,
  "terminal.integrated.defaultProfile.osx": "zsh",
  "workbench.iconTheme": "vscode-icons",
  "workbench.colorTheme": "Default Dark+",
  "files.autoSave": "onFocusChange"
}
```

## 編輯器設定

- 字體大小: 14px
- 字體: Fira Code, Source Code Pro 等
- 開啟連字符號(Font Ligatures)
- 自動刪除行尾空白
- 顯示 80 和 120 字元的垂直尺規線
- 自動換行
- Tab 縮排設為 2 空格
- 關閉自動偵測縮排

```json
{
  "editor.fontSize": 14,
  "editor.fontFamily": "Fira Code, Source Code Pro, 'Courier New', monospace",
  "editor.fontLigatures": true,
  "editor.trimAutoWhitespace": true,
  "editor.rulers": [80, 120],
  "editor.wordWrap": "on",
  "editor.tabSize": 2,
  "editor.detectIndentation": false
}
```

## 格式化設定

- 預設使用 Prettier 作為格式化工具
- 儲存時自動格式化
- 為不同語言(JavaScript, JSON, Vue, CSS, Sass, SCSS)設定專用格式化工具
- ESLint 設定支援 .js, .ts, .vue, .html 檔案

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "eslint.format.enable": true,
  "eslint.options": {
    "extensions": [".js", ".ts", ".vue", ".html"]
  }
}
```

## Sass 編譯設定

- 自動前綴(Autoprefix)設定
- 排除 node_modules 和 .vscode 目錄
- 產生 source map
- 輸出壓縮和展開兩種 CSS 格式

```json
{
  "liveSassCompile.settings.autoprefix": ["> 1%", "last 2 versions"],
  "liveSassCompile.settings.excludeList": ["**/node_modules/**", ".vscode/**"],
  "liveSassCompile.settings.generateMap": true,
  "liveSassCompile.settings.formats": [
    {
      "format": "compressed",
      "extensionName": ".min.css",
      "savePath": "/public/styles"
    },
    {
      "format": "expanded",
      "extensionName": ".css",
      "savePath": "/dist//public/styles"
    }
  ]
}
```

## Git 與版本控制

- 啟用 Git 自動抓取
- TypeScript/JavaScript 檔案移動時自動更新引用路徑

```json
{
  "git.autofetch": true,
  "typescript.updateImportsOnFileMove.enabled": "always",
  "javascript.updateImportsOnFileMove.enabled": "always"
}
```

## 終端機設定

- Windows 預設使用 Command Prompt
- Linux 預設使用 bash
- 終端機字體大小: 14px

```json
{
  "terminal.integrated.defaultProfile.windows": "Command Prompt",
  "terminal.integrated.defaultProfile.linux": "bash",
  "terminal.integrated.fontSize": 14
}
```

## 智慧提示與驗證

- 字串中啟用快速建議
- 停用 CSS 相關驗證
- 設定 Tailwind CSS 語言支援
- GitHub Copilot 自動完成啟用

```json
{
  "editor.quickSuggestions": {
    "strings": true
  },
  "css.validate": false,
  "less.validate": false,
  "scss.validate": false,
  "tailwindCSS.includeLanguages": {
    "plaintext": "html"
  },
  "github.copilot.editor.enableAutoCompletions": true
}
```

## Better Comments 設定

配置了特殊註解標記:

- ! (紅色): 重要警告
- ? (藍色): 問題標記
- // (灰色): 註解刪除線
- todo (橘色): 待辦事項
- - (綠色): 一般註解

```json
{
  "better-comments.tags": [
    {
      "tag": "!",
      "color": "#FF2D00"
    },
    {
      "tag": "?",
      "color": "#3498DB"
    },
    {
      "tag": "//",
      "color": "#474747",
      "strikethrough": true
    },
    {
      "tag": "todo",
      "color": "#FF8C00"
    },
    {
      "tag": "*",
      "color": "#98C379"
    }
  ]
}
```

## 檔案巢狀顯示

設定相關檔案的巢狀顯示規則，如:

- TypeScript/JavaScript 相關檔案
- 設定檔案
- 套件相依性檔案

```json
{
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.patterns": {
    "*.ts": "${capture}.js, ${capture}.typegen.ts",
    "*.js": "${capture}.js.map, ${capture}.min.js, ${capture}.d.ts",
    "tsconfig.json": "tsconfig.*.json",
    "package.json": "package-lock.json, yarn.lock, pnpm-lock.yaml, bun.lockb"
  }
}
```
