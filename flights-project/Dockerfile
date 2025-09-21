# Ξεκινάμε από την επίσημη εικόνα του Node-RED
FROM nodered/node-red:4.0

# Τρέχουμε εγκαταστάσεις ως root
USER root
WORKDIR /data

# Εξαρτήσεις παλετών (worldmap, minio κλπ.) — caching friendly
COPY package.json /data/package.json
RUN npm install --unsafe-perm --no-update-notifier --no-fund

# Η ροή 
COPY flows.json /data/flows.json

# 🔧 ΣΗΜΑΝΤΙΚΟ: δικαιώματα για να μπορεί να γράψει ο Node-RED
RUN chown -R node-red:node-red /data

# Επιστροφή στον default χρήστη του image
USER node-red
WORKDIR /usr/src/node-red