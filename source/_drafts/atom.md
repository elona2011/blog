# Packages
Project Manager 快速打开项目

# 快捷键
ctrl-tab
Add the following to your keymap.cson:
'body':
  'ctrl-tab ^ctrl': 'unset!'
  'ctrl-tab': 'pane:show-next-item'
  'ctrl-shift-tab ^ctrl': 'unset!'
  'ctrl-shift-tab': 'pane:show-previous-item'
