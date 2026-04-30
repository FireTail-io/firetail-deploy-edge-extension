# FireTail Deploy Edge Extension

This GitHub Action publishes your Edge add-on onto [Microsoft Edge Add-ons](https://microsoftedge.microsoft.com/addons/Microsoft-Edge-Extensions-Home)
using the [Microsoft Edge Add-ons API v1.1](https://learn.microsoft.com/en-us/microsoft-edge/extensions-chromium/publish/api/using-addons-api).

> [!NOTE]
> This action can only publish a new version of an existing add-on. Publishing a new add-on is not
> supported.

## Prerequisites

The following items are required before publishing your Edge add-on:

- A zip file to upload.
- An API key and a client ID.

Please refer to this [tutorial](https://learn.microsoft.com/en-us/microsoft-edge/extensions-chromium/publish/api/using-addons-api#before-you-begin)
for how to generate an API key and a client ID.

## Usage

### Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `product-id` | **Yes** | — | The product ID of your add-on. |
| `zip-path` | **Yes** | — | Path to the zip file to upload. May include a glob pattern (only one file must match). |
| `api-key` | **Yes** | — | Your Edge publish API key. |
| `client-id` | **Yes** | — | Your Edge publish API client ID. |
| `upload-only` | No | `"false"` | Set to `"true"` to upload without publishing (you must publish manually). |
| `notes-for-certification` | No | — | A secret text to Microsoft reviewers. |

### Example

```yaml
steps:
  - uses: FireTail-io/firetail-deploy-edge-extension@v2
    with:
      product-id: your-addon-product-id
      zip-path: your-addon.zip
      api-key: ${{ secrets.EDGE_API_KEY }}
      client-id: ${{ secrets.EDGE_CLIENT_ID }}
```

### Upload Only (without publishing)

```yaml
steps:
  - uses: FireTail-io/firetail-deploy-edge-extension@v2
    with:
      product-id: your-addon-product-id
      zip-path: your-addon.zip
      api-key: ${{ secrets.EDGE_API_KEY }}
      client-id: ${{ secrets.EDGE_CLIENT_ID }}
      upload-only: "true"
```

## References

- [Using the Microsoft Edge Add-ons API](https://learn.microsoft.com/en-us/microsoft-edge/extensions-chromium/publish/api/using-addons-api)
- [Microsoft Edge Add-ons API Reference](https://learn.microsoft.com/en-us/microsoft-edge/extensions-chromium/publish/api/addons-api-reference)
