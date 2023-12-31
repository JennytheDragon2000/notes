###### Answer | gpt-3.5 Model

To change your DNS settings on Fedora, you have a few options depending on your specific needs and preferences. Here are some approaches you can consider:

1. Using Network Manager:
    - Open the Network Manager settings by clicking on the gearwheel icon.
    - Select the network device (wired or wireless) that you want to modify.
    - In the IPv4 tab, enter the DNS servers you want to use in the "DNS" field. For example, you can set it to "8.8.8.8 8.8.4.4" for Google DNS.
    - Save the changes and restart your PC for the new DNS settings to take effect. [[0]](https://www.reddit.com/r/Fedora/comments/tatsjs/fedora_dns/)

2. Using systemd-resolved:
    - Fedora since version 33 defaults to systemd-resolved for DNS management.
    - Edit the `/etc/systemd/resolved.conf` file to set the DNS addresses. You can uncomment the `DNS` option and add the IP addresses of the DNS servers you want to use. For example:

     ` DNS=9.9.9.9 149.112.112.112     ``` `

[

](https://www.phind.com/search?cache=97ee9c31-a0f8-44b7-a814-94223257681f)

- Optionally, you can enable DNS over TLS by uncommenting the `DNSOverTLS` option.
    - Save the changes and restart the systemd-resolved service with the command `systemctl restart systemd-resolved`. [[0]](https://www.reddit.com/r/Fedora/comments/tatsjs/fedora_dns/) [[7]](https://medium.com/@isharamalaviarachchi/how-to-configure-dns-server-on-fedora-4cabbbfade6d)

3. Manually configuring `/etc/resolv.conf`:
    - Fedora's `/etc/resolv.conf` is usually automatically created and maintained by systemd. Modifying it directly may not persist across system reboots.
    - If you still want to manually configure `/etc/resolv.conf`, you can try removing the symbolic link to `/etc/resolv.conf` and creating a new file with the same name. For example:

     ` sudo rm /etc/resolv.conf     sudo nano /etc/resolv.conf     ``` `

[

](https://www.phind.com/search?cache=97ee9c31-a0f8-44b7-a814-94223257681f)

- In the new file, you can add your DNS server addresses. For example:

     ` nameserver 8.8.8.8     nameserver 8.8.4.4      ``` `

[

](https://www.phind.com/search?cache=97ee9c31-a0f8-44b7-a814-94223257681f)

- Save the file and restart your networking service. Keep in mind that this approach may not be recommended as it may conflict with systemd's management of `/etc/resolv.conf`. [[3]](https://forums.fedoraforum.org/showthread.php?328941-changing-DNS-Server&p=1861333)

It's important to note that changing DNS settings at the router level will only affect devices within your home network. If you want to change the DNS settings for your Fedora PC specifically, you should follow one of the methods mentioned above. [[0]](https://www.reddit.com/r/Fedora/comments/tatsjs/fedora_dns/)

Each approach has its pros and cons:

- Using Network Manager:
    - Pros:
        - Easy to use and configure through the graphical interface.
        - Changes can be made per network device, allowing for more flexibility.
    - Cons:
        - The changes may not persist after system reboots in some cases.
        - Limited customization options compared to other methods.

- Using systemd-resolved:
    - Pros:
        - Default DNS management solution in Fedora.
        - Supports DNSSEC and DNS over TLS.
        - Changes persist across system reboots.
    - Cons:
        - Requires manual editing of configuration files.
        - Limited GUI options for configuration.

- Manually configuring `/etc/resolv.conf`:
    - Pros:
        - Provides direct control over DNS server settings.
        - Changes persist across system reboots.
    - Cons:
        - May conflict with systemd's management of `/etc/resolv.conf`.
        - Requires manual maintenance and may not be recommended.

It's worth exploring each method and choosing the one that best suits your needs and preferences.