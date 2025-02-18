---
title: "Portal Listing"
slug: "portal-listing"
---

Now that we have a RollApp deployed, we can list it on the [Dymension Portal](https://portal.dymension.xyz). This will allow other users to discover and interact with the RollApp.

:::info NOTE:
Only developers with the `RollApp-fam` discord role are eligible for listing their RollApp on the portal.
:::

### Interacting with the RollApp

Developers are expected to provide the following end-points under either [http](https://en.wikipedia.org/wiki/HTTP) or [https](https://en.wikipedia.org/wiki/HTTPS). This will allow for users to be able to interact with your RollApp:

1. RollApp RPC Endpoint (default port `26657`)
2. Rest Endpoint (default port `1317`)
3. JSON RPC Endpoint (default port `8545`. Only relevant for EVM RollApps)

:::info NOTE:
If you are using a self-signed certificate for [https](https://en.wikipedia.org/wiki/HTTPS), please add it to your browser's trusted certificates.
:::

## List Your RollApp

The following steps are required for listing a RollApp on the Portal:

1. Make sure to have successfully deployed and are running a RollApp instance.

2. Fund the Faucet and test the IBC connection by submitting an IBC transfer of your RollApp token to the Dymension Hub faucet with the following command:

    ```
    roller tx fund-faucet
    ```

    Subsequently, check the balance of the RollApp token on the Dymension Hub faucet which should arrive within 15 minutes:

    ```
    $balance dym1g8sf7w4cz5gtupa6y62h3q6a4gjv37pgefnpt5 <RollApp-ID>
    ```

3. Fork the RollApp-registry [repo](https://github.com/dymensionxyz/rollapp-registry) into your GitHub account:

<img class="image--primary" loading="eager" src={require('@site/static/img/fork.png').default} alt="background" />

4. Clone it by running the following command:

    ```bash
    git clone https://github.com/<your-github-username>/rollapp-registry
    ```

5. CD into the cloned repo:

    ```bash
    cd rollapp-registry
    ```

6. Retrieve your generated rollapp id with `roller config show` and save it as an environment variable:

    ```
    export ROLLAPP_ID=<RollApp-ID-HERE>
    ```

7. Create the appropraite folders and files:

    ```
    cd devnet
    mkdir -p $ROLLAPP_ID/logos
    cd $ROLLAPP_ID && touch $ROLLAPP_ID.json
    ```

    This should create a folder for your RollApp logo and config information.

8. Add your RollApp logo to the `logos` folder. Logo file name: `<RollApp-ID>.<format>`. This can be SVG, PNG, or JPG format.

:::warning NOTE:
Please make sure the file doesn't exceed 50KB.
::: 

9. Export the RollApps configuration JSON by running:

    ```
    roller config export
    ```

10. Copy paste the JSON output to the `<RollApp-ID>.json` and fill in the following fields:

    a. RPC: `"http://<your-ip-or-domain>:<port>" (default port 26657)`

    b. REST: ` "http://<your-ip-or-domain>:<port>" (default port 1317)`

    c. EVM RPC \*(ONLY FOR EVM ROLLAPPS): `"http://<your-ip-or-domain>:<port>" (default port 8545)`

    d. Logo path: `"/logos/<RollApp-ID>.<format>"`

    Optinal fields:

    e. chainName: switch `<RollApp-ID>` to your RollApp's name as it will appear on the Portal

    f. description: add `"<Your RollApp description>",` to be displayed on the portal

    g. website: add `"<your-RollApp's-url>",` to be displayed on the portal

11. Add and commit your changes:

```
git add .
git commit -m "added RollApp"
git push -u origin main
```

12. Create a PR to https://github.com/dymensionXYZ/rollapp-registry. 

:::info NOTE:
For a demonstration of a step-by-step guide to creating a PR please follow the [GitHub documentation](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork) or watch this helpful [youtube video](https://www.youtube.com/watch?v=a_FLqX3vGR4).
:::

13. Pair the RollApp on the [Discord channel](https://discord.com/channels/956961633165529098/1140590139022782474) by entering the following command:

:::warning NOTE:
In the following command replace `<RollApp-ID>` with your customized RollApp ID.
:::

```bash
 $pair <RollApp-ID>
```

A community moderator will then begin a conversation with you in Discord. Please follow attentively to get the listing process fulfilled quickly. 

If you have any question please feel free to reach out to the coreteam and community on Discord. We're here for you!
