# Specter HWIBridge
If you are running your Bitcoin Core on a remote machine,
such as an AWS or Heroku machine, or if you are using a separate hardware like [RaspiBlitz](https://github.com/rootzoll/raspiblitz), [myNode](https://mynodebtc.com), or [Nodl](https://www.nodl.it),
you may also prefer to run Specter on that same remote machine.

In such case, Specter will not be able to connect to USB devices connected to the local machine you use to access Specter.
This is because Specter uses HWI for hardware wallets integration, which can only access devices connected directly to the machine it is running on.

If you have physical access to the machine Specter is running on, like with RaspiBlitz or myNode, the easiest solution is to connect your hardware wallet by USB directly to that machine's USB port.
This will allow Specter to detect the device and continue normally.

However, if you don't have physical access to the machine Specter is running on, you will need to set up a `Specter HWIBridge`.
The following steps will help you set up a local `Specter HWIBridge`, which you could connect to the remote server and will allow it to detect devices connected to your local machine:

1. On the local machine you are accessing Specter from, [install Specter](../README.md#how-to-run) and run it with the `--hwibridge` flag.
<br><b>You could do that by downloading the binary from the [Specter's GitHub releases page](https://github.com/cryptoadvance/specter-desktop/releases), and double clicking it.</b>
2. Then open `http://127.0.0.1:25441/hwi/settings` in your browser.
3. In the `Whitelisted domains` form field, enter the domain of your remote Specter server you are connecting to and click update.
4. Now open the remote Specter server you wish to use and go to settings.
5. In the bottom, find `HWI Bridge URL`, and enter there the URL of your local Specter HWIBridge along with `/hwi/api/` (i.e. `http://127.0.0.1:25441/hwi/api/`), then click save.

Now you should now be able to use hardware wallets connected via USB to your local node with the Specter running on the remote server.

We are currently working to make this process much easier and simpler.
In the meantime, if you have any further questions or need help, please either open a GitHub issue, or ask in the [Specter Telegram group](https://t.me/spectersupport).

<i>(Note, if you are running Specter as a Tor hidden service and want to use HWIBridge, you will have to set up the HWIBridge as a [Tor hidden service](tor.md) as well).<i>
