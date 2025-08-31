#!/bin/bash
set -xe
exec > /var/log/user-data.log 2>&1
apt-get update -y || true
chown -R ubuntu:ubuntu /home/ubuntu || true
su - ubuntu -c '
  set -xe
  export NVM_DIR="$HOME/.nvm"
  [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
  nvm use 20 || (nvm install 20 && nvm alias default 20)
  npm i -g pm2
  cd "$HOME/week-22" || exit 1
  if [ -f package-lock.json ]; then
    npm ci
  else
    npm i
  fi
  export NODE_ENV=production
  export PORT=3000
  pm2 start npm --name week-22 -- start
  pm2 save
  pm2 startup systemd -u ubuntu --hp "$HOME"
'
systemctl enable pm2-ubuntu || true
systemctl start pm2-ubuntu || true