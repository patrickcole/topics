# Ports

## Closing a Port

You'll need to figure out what process is using that port. You can do so by finding the PID of the port and eventually kill that PID.

```bash
# First, obtain the PID using the port you want to close
# NOTE: replace the ${} with the actual port
sudo lsof -i :${PORT}
# example: get PID of port 3000:
sudo lsof -i :3000

# now kill that PID
kill ${PID}
# example: let's say the PID of :3000 was 57
kill 57
```

If you are still having trouble killing the process or closing the port, there's a few additional commands you can try:

```bash
kill -9 ${PID}
sudo kill -9 ${PID}
```

## Sources

- [How to properly close a port?](https://dev.to/sylwiavargas/how-to-properly-close-a-port-2p36)
