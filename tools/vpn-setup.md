# Setting up a VPN server

https://github.com/kylemanna/docker-openvpn

```
# create volume to store vpn data persistently
OVPN_DATA="ovpn-data-example"
docker volume create --name $OVPN_DATA

# Setup VPN config ( passphrase required for protecting private key )
docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm kylemanna/openvpn ovpn_genconfig -u udp://<IP address or hostname>
docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm -it kylemanna/openvpn ovpn_initpki

# start server
docker run -v $OVPN_DATA:/etc/openvpn -d -p 1194:1194/udp --cap-add=NET_ADMIN kylemanna/openvpn

# generate client certificate
docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm -it kylemanna/openvpn easyrsa build-client-full CLIENTNAME nopass
docker run -v $OVPN_DATA:/etc/openvpn --log-driver=none --rm kylemanna/openvpn ovpn_getclient CLIENTNAME > CLIENTNAME.ovpn

# SCP ovpn file over to the client machine

# Client setup [ Mac ]
brew install openvpn
export PATH=$(brew --prefix openvpn)/sbin:$PATH

# Connect to vpn server
openvpn --config CLIENTNAME.ovpn

# Note: this will connect to UDP port 1194 on the VPN machine. Make sure the security group allows this port 
```
