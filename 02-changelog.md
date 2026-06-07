# Changelog

### Jellyfin module **[WHMCS](https://puqcloud.com/link.php?id=77)**
#####  [Order now](https://puqcloud.com/whmcs-module-jellyfin.php) | [Download](https://download.puqcloud.com/WHMCS/servers/PUQ_WHMCS-Jellyfin/) | [Community](https://community.puqcloud.com/)

## v3.0 — 2026-06-06

**Added**
- AJAX, card-based client area with a gradient status hero, a two-column account/usage layout, usage progress bars (sessions, failed logins), library chips and an active-devices table — plus toast notifications and confirm dialogs.
- Self-service **Drop all devices** and **Unblock** actions in the client area (no page reload).
- **Dynamic library picker** in the product configuration form: the library list is loaded live from the assigned Jellyfin server as checkboxes, with a *Select all* toggle and a *Reload* button (with a manual text-box fallback when the server is unreachable). The separate *Use all libraries* switch is kept.
- Product configuration form injected on the WHMCS product page via `AdminAreaFooterOutput`.
- Admin homepage license alert listing products with invalid or missing licenses.
- Schema migration runner (`puqJellyfinMigrations`).
- **Diagnostic logging throughout.** Every lifecycle action, hook and AJAX call records its result and any exception to the WHMCS Module Log; all Jellyfin API calls log their request/response on error (and every write call on success), with the HTTP status code and the real Jellyfin message. Passwords are redacted in the log.

**Changed**
- **Jellyfin 10.11.10+ compatibility.** Switched to the modern `Authorization: MediaBrowser` header (with `Version`) as the primary scheme and dropped the deprecated `X-Emby-Token` / `X-MediaBrowser-Token` headers that Jellyfin removes in 10.12/10.13. The password endpoint now uses the current route `Users/Password?userId=` instead of the deprecated `Users/{id}/Password`.
- `CreateAccount` now reads the new user's `Id` directly from the `Users/New` response instead of re-listing all users and matching by name (faster and robust against special characters).
- API error handling now inspects the HTTP status code and extracts the real Jellyfin error message (ProblemDetails / validation errors) instead of occasionally treating a 4xx as success.
- All product settings are now stored as a single JSON document in `configoption24`. Existing v2 installs are read transparently from the legacy `configoption3`–`configoption8` slots, so **no reconfiguration is required** after upgrading.
- License verification moved to a block-based hash with online/offline caching.
- Jellyfin admin API token is cached per instance instead of re-authenticating on every call.
- PHP **7.4 / 8.1 / 8.2+** compatible source; hardened with null-safe reads, `try/catch` around all external calls, and `htmlspecialchars` on every API-sourced string.

**Fixed**
- Web-interface URL no longer mishandled the plain-HTTP/port-80 case (operator-precedence bug in the default-port check).
- Empty text fields (e.g. an intentionally blank username suffix) are now preserved instead of reverting to their default on save.

-----------

## v2.1.1

- Maintenance release (last public v2.x build).

## v2.1 — 2025-10-03

- Added a configurable rule for **custom usernames**.
- Added a configurable rule for **custom passwords**.
- Added support for **PHP 8.2+**.

## v2.0.1 — 2024-12-19

- Added a validation check in the Client Area Primary Sidebar hook.

## v2.0 — 2024-09-24

- Module compiled with **ionCube v13**.
- Supported PHP versions:
  - PHP 7.4 — WHMCS 8.11.0 and below
  - PHP 8.1 — WHMCS 8.11.0 and above
  - PHP 8.2 — WHMCS 8.11.0 and above

## v1.5.1 — 2024-08-13

- Fixed a password bug when **Show password** is set to *no*.

## v1.5 — 2023-07-12

- Client area better adapted for mobile.
- Added buttons to copy the login and password in the client area.

## v1.4 — 2023-12-21

- Client area enhancements:
  - Option to hide service passwords by default.
  - Added a **Show** button to reveal the service password in the client area.
  - Option to display the service password in plain text.
- Note: save the product's *Module Settings* for the module to function correctly.

## v1.3 — 2023-12-18

- Various bug fixes.
- Fixed the session-count display in the client area.
- Support for Jellyfin 10.8.13.

## v1.2 — 2023-11-17

- Fixed incorrect library-selection behaviour (**CRITICAL**).
- Fixed bugs in the change-password feature.
- New **Use All Libraries** checkbox on the Module Settings page.
- Client-area changes and optimizations.
- Note: reconfigure the product's *Module Settings* and run **Change Package** on customer services.

## v1.1 — 2023-11-09

- Reworked library handling: `-` means *no libraries selected*, an empty field means *select all libraries*.
- Bug fixes.

## v1.0 — 2023-11-03

- First version.
