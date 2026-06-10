# Xsolla Mobile SDK for Windows

![License](https://img.shields.io/github/license/xsolla/xsolla-sdk-windows)
![Latest release](https://img.shields.io/github/v/release/xsolla/xsolla-sdk-windows)

## Overview

Xsolla Mobile SDK for Windows provides pre-built native C# and C++ libraries for integrating in-game payments into your Windows app via Xsolla Pay Station. Both SDKs share the same backend infrastructure and offer equivalent functionality: 1000+ payment methods across 200+ geographies, 130+ currencies, built-in anti-fraud, 25+ languages, player authentication, and product catalog support.

It is intended for Windows game developers who want native in-game purchases without building a payment backend.

## Requirements

- C# SDK: .NET 6.0 or later (or a .NET Standard 2.1 compatible runtime)
- C++ SDK: Windows x64 (MSVC) — *coming soon*
- An [Xsolla Publisher Account](https://publisher.xsolla.com) with a configured Pay Station project

## Install

Download the latest release ZIP from [GitHub Releases](https://github.com/xsolla/xsolla-sdk-windows/releases):

1. Download `com.xsolla.sdk-csharp-{version}.zip`.
2. Extract it — DLLs are organized by framework under `lib/`.
3. Reference `XsollaCSharpSDK.dll` matching your target framework.

## Usage

Configure the store client, initialize it, and purchase a product (C#):

```csharp
using Xsolla.SDK.Common;
using Xsolla.SDK.Store;

var settings = XsollaClientSettings.Builder.Create()
    .SetProjectId(YOUR_PROJECT_ID)
    .SetLoginId("YOUR_LOGIN_ID")
    .Build();

var configuration = XsollaClientConfiguration.Builder.Create()
    .SetSettings(settings)
    .SetSandbox(true)
    .Build();

var storeClient = XsollaStoreClient.Builder.Create()
    .SetConfiguration(configuration)
    .AddProducts(new[] { "booster_max_1", "key_1" })
    .Build();

storeClient.Initialize((products, error) => { /* list products */ });
storeClient.PurchaseProduct("key_1", (purchased, error) => { /* validate + consume */ });
```

## Documentation

- SDK Explorer (interactive demo): [developers.xsolla.com/sdk/demo](https://developers.xsolla.com/sdk/demo/)
- Full integration guide: [developers.xsolla.com/sdk](https://developers.xsolla.com/sdk/)

## Support

- **GitHub Issues:** [github.com/xsolla/xsolla-sdk-windows/issues](https://github.com/xsolla/xsolla-sdk-windows/issues)
- **Developer portal:** [developers.xsolla.com](https://developers.xsolla.com)

## License

Apache License 2.0. See [LICENSE](./LICENSE).
