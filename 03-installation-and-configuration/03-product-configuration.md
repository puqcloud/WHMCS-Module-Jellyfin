# Product configuration

### Jellyfin module **[WHMCS](https://puqcloud.com/link.php?id=77)**
#####  [Order now](https://puqcloud.com/whmcs-module-jellyfin.php) | [Download](https://download.puqcloud.com/WHMCS/servers/PUQ_WHMCS-Jellyfin/) | [Community](https://community.puqcloud.com/)

Create a product of type **PUQ Jellyfin** (Setup → Products/Services), assign the Jellyfin server on the **Module Settings** tab, then configure the access policy in the injected configuration panel.

![Product configuration](../img/01-product-config.png)

## Libraries Configuration
- **Use all libraries** — grant access to every library on the server (overrides the selection below).
- **Libraries** — the list of libraries is loaded live from the Jellyfin server assigned to the product's Server Group. Tick the libraries this product grants; use **Select all** to toggle everything, or **Reload** to refresh the list. Leaving everything unticked grants no library. If the server cannot be reached, a manual text box appears as a fallback (one library name per line). Ignored when "Use all libraries" is ON.

> The dynamic list requires the product to be saved with a Server Group that contains a reachable Jellyfin server. Until then the panel shows a hint to select and save a Server Group.

![Libraries — dynamic checkbox picker](../img/02-libraries.png)

## User Configuration
- **Streaming bitrate limit** — 1–60 Mbps (empty = unlimited).
- **SyncPlay access** — create & join groups / join groups / disabled.
- **Remote control of shared devices**, **Media downloads** — on/off.
- **Max user sessions** — `0` disables the limit.
- **Failed login attempts** — lockout threshold; `-1` disables it.
- **Username prefix / suffix** — wrap the generated username.

![User Configuration](../img/05-user-configuration.png)

## Allow Playback
Toggle media playback, audio transcoding, video transcoding and video conversion without re-encoding.

![Allow Playback](../img/03-allow-playback.png)

## Feature Access
Live TV access, Live TV recording management, and force transcoding of remote media sources.

![Feature Access](../img/04-feature-access.png)

## Links
- **Instruction / manual URL** — shown as the *User manual* link in the client area.

![Links](../img/07-links.png)

## Client Area
- **Show password** — show button / plain text / hidden.
- **Password generation** — `length:characters`, e.g. `8:23456789abcdABCD`.
- **Username format** — `standard` (`prefix<client_id>-<service_id>suffix`) or `custom`.
- **Custom username** — macro template: `{user_id}`, `{service_id}`, `{random_digit_x}`, `{random_letter_x}`, `{unixtime}`, `{year}`, `{month}`, `{day}`, `{hour}`, `{minute}`, `{second}`.

![Client Area settings](../img/06-client-area-settings.png)

Settings are stored as a single JSON document in `configoption24`. After saving, **Create/Change** actions push the resulting policy to Jellyfin.
