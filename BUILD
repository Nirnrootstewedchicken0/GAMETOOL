name: Build EXE with PyInstaller

on:
  workflow_dispatch:  # 允许你手动触发这个打包流程

jobs:
  build:
    runs-on: windows-latest  # 在 Windows 环境里打包，确保生成的 EXE 能直接在 Windows 上运行

    steps:
      # 1. 把你的代码从仓库里拉取到虚拟机上
      - name: Checkout code
        uses: actions/checkout@v4

      # 2. 在虚拟机上安装 Python 环境
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'

      # 3. 安装 PyInstaller
      - name: Install PyInstaller
        run: pip install pyinstaller

      # 4. 执行打包命令，生成 EXE
      # 如果你的代码里有其他依赖（例如 pyautogui），需要先执行 pip install -r requirements.txt
      - name: Build EXE
        run: |
          pyinstaller --onefile --windowed --name=键鼠自动化工具 SKIPCLICK.py

      # 5. 把生成的 EXE 文件上传到工作流运行结果里，供你下载
      - name: Upload EXE artifact
        uses: actions/upload-artifact@v4
        with:
          name: 键鼠自动化工具
          path: dist/键鼠自动化工具.exe
