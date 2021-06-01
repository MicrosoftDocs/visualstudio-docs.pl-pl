---
title: Automatyzowanie instalacji za pomocą pliku odpowiedzi
description: Dowiedz się, jak utworzyć plik odpowiedzi JSON, który ułatwia automatyzowanie instalacji Visual Studio plików
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7554ac46d7c4171cfb71166c51689ff4ae95c0d5
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724554"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>Automatyzowanie instalacji przy użyciu ustawień w pliku odpowiedzi

Administratorzy wdraża Visual Studio mogą określić plik odpowiedzi przy użyciu `--in` parametru , jak w poniższym przykładzie:

```cmd
vs_enterprise.exe --in customInstall.json
```

Pliki odpowiedzi to [pliki JSON,](http://json-schema.org/) których zawartość odzwierciedla argumenty wiersza polecenia.  Ogólnie rzecz biorąc, jeśli parametr wiersza polecenia nie przyjmuje żadnych argumentów (na przykład , itp.), wartość w pliku odpowiedzi powinna `--quiet` `--passive` być true/false.  Jeśli przyjmuje argument (na przykład ), wartość w pliku `--installPath <dir>` odpowiedzi powinna być ciągiem.  Jeśli przyjmuje argument i może pojawić się w wierszu polecenia więcej niż raz (na przykład ), powinien `--add <id>` być tablicą ciągów.

Parametry określone w ustawieniach zastąpienia wiersza polecenia z pliku odpowiedzi, z wyjątkiem sytuacji, gdy parametry mają wiele danych wejściowych (na przykład `--add` ). Jeśli masz wiele danych wejściowych, dane wejściowe podane w wierszu polecenia są scalane z ustawieniami z pliku odpowiedzi.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Ustawianie domyślnej konfiguracji dla Visual Studio

Jeśli utworzono pamięć podręczną układu sieciowego za pomocą pliku , w `--layout` `response.json` układzie zostanie utworzony plik początkowy. Jeśli utworzysz układ częściowy, ten plik odpowiedzi zawiera obciążenia i języki, które zostały uwzględnione w układzie.  Uruchomienie instalatora z tego układu automatycznie używa response.jsw pliku, który wybiera obciążenia i składniki zawarte w układzie.  Użytkownicy mogą nadal wybierać lub usuwać zaznaczenie dowolnych obciążeń w interfejsie użytkownika konfiguracji przed zainstalowaniem Visual Studio.

Administratorzy, którzy tworzą układ, mogą modyfikować plik w układzie, aby kontrolować ustawienia domyślne, które użytkownicy widzą podczas instalowania Visual Studio `response.json` z układu.  Jeśli na przykład administrator chce domyślnie zainstalować określone obciążenia i składniki, może skonfigurować `response.json` plik, aby je dodać.

Gdy Visual Studio jest uruchamiana z folderu układu, automatycznie używa pliku odpowiedzi w folderze układu.   Nie musisz używać opcji `--in` .

Możesz zaktualizować plik utworzony w folderze układu offline, aby zdefiniować domyślne ustawienie dla użytkowników, którzy `response.json` instalują z tego układu.

> [!WARNING]
> Bardzo ważne jest pozostawienie istniejących właściwości, które zostały zdefiniowane podczas tworzenia układu.

Plik podstawowy w układzie powinien wyglądać podobnie do poniższego przykładu, z tą różnicą, że zawierałby wartość produktu i kanału, `response.json` który chcesz zainstalować:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Podczas tworzenia lub aktualizowania układu jest również tworzona response.template.jspliku.  Ten plik zawiera wszystkie identyfikatory obciążenia, składnika i języka, których można użyć.  Ten plik jest dostarczany jako szablon dla tego, co można doinstalować w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punktu wyjścia dla niestandardowego pliku odpowiedzi.  Po prostu usuń identyfikatory dla rzeczy, których nie chcesz instalować, i zapisz je we własnym pliku odpowiedzi.  Nie dostosuj response.template.jsw pliku lub zmiany zostaną utracone przy każdej aktualizacji układu.

## <a name="example-layout-response-file-content"></a>Przykładowa zawartość pliku odpowiedzi układu

W poniższym przykładzie jest instalowana Visual Studio Enterprise z sześcioma wspólnymi obciążeniami i składnikami oraz przy użyciu języka angielskiego i francuskiego interfejsu użytkownika. Możesz użyć tego przykładu jako szablonu; Wystarczy zmienić obciążenia i składniki na te, które chcesz zainstalować:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Rozwiązywanie problemów związanych z siecią podczas instalowania lub używania Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
