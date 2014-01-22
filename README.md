# Scout Realtime Role for Ansible

This role installs [Scout Realtime](http://scoutapp.github.io/scout_realtime/) which provides easy, beautiful, and free real-time server metrics.

## Requirements

This role requires [Ansible](http://www.ansibleworks.com/) version 1.4 or higher and the Debian/Ubuntu platform and Ruby 1.8.7 or higher.

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows:

```yaml
# The default port used for the metrics web interface
scout_port: 5555

# The default path for the service's log file
scout_logpath: '/var/log/scout_realtime.log'

# The default path for the service's PID
scout_pidpath: '/root/.scout/scout_realtime.pid'
```

__Note:__ Scout Realtime is currently in beta. Currently if you change the PID path, the daemon will no longer stop properly and the process must be manually killed.

## Examples

1. Install Scout Realtime and view server stats from your local computer

    ```yaml
    ---
    # This playbook bootstraps machines with common users

    - name: Apply Scout Realtime role to metrics nodes
      hosts: metrics
      roles:
        - scout-realtime
    ```

2. View server stats from your local computer

    * Create an SSH tunnel to your server running Scout Realtime

        `ssh -NL 5555:localhost:5555 user@ip_or_hostname`

    * Point your browser to: [http://localhost:5555](http://localhost:5555)

3. View server stats from any computer

    * Open a port in the firewall on your server running Scout Realtime

        `sudo iptables -A INPUT -p tcp --dport 5555 -j ACCEPT`

    * Point your browser to: [http://ip_or_hostname:5555](http://ip_or_hostname:5555)

## Dependencies

None.

## License

MIT.
