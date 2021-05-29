---
layout: page
title: elementary os notlarım
---

- Kaldırdığım uygulamalar:
  
  ```console
  # apt remove --purge pantheon-mail audience  noise  epiphany
  ```

- Yüklediğim uygulamalar:
  
  ```console
  # apt install firefox firefox-locale-tr thunderbird thunderbird-locale-tr vlc transmission
  ```
- Terminal ayarlarım:
  
  ```console
  $ gsettings set io.elementary.terminal.settings tab-bar-behavior 'Never Show Tabs'
  $ gsettings set io.elementary.terminal.settings remember-tabs false
  ```
  ```console
  # cat <<EOF > /usr/local/bin/queeup_io.elementary.terminal
  #!/bin/bash
  
  # Always reset terminal window states.
  gsettings reset io.elementary.terminal.saved-state window-size
  gsettings reset io.elementary.terminal.saved-state window-position 
  gsettings reset io.elementary.terminal.saved-state window-state
  
  # Open in a new window
  # io.elementary.terminal -n -e tmux "@"
  io.elementary.terminal -n "$@"
  EOF
  
  # chmod +x /usr/local/bin/queeup_io.elementary.terminal
  $ gsettings set org.gnome.desktop.default-applications.terminal exec 'queeup_io.elementary.terminal
  ```

- Dosyalar (Files) ayarlarım:
  
  ```
  $ gsettings set io.elementary.files.preferences show-remote-thumbnails true
  $ gsettings set io.elementary.files.preferences single-click false
  ```
  
  
