---
title: Automatyzowanie instalacji przy użyciu pliku odpowiedzi
description: Dowiedz się, jak utworzyć plik odpowiedzi JSON, który umożliwia zautomatyzowanie instalacji programu Visual Studio
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 43a4212a9faf0b7fef3395a847e8c614507e56df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588537"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Jak definiować ustawienia w pliku odpowiedzi

Administratorzy, którzy wdrażają programu Visual Studio można określić plik odpowiedzi, przy użyciu `--in` parametru, jak w poniższym przykładzie:

```cmd
vs_enterprise.exe --in customInstall.json
```

Pliki odpowiedzi są [JSON](http://json-schema.org/) pliki, których zawartość duplikatów argumenty wiersza polecenia.  Ogólnie rzecz biorąc, jeśli parametr wiersza polecenia nie przyjmuje żadnych argumentów (na przykład `--quiet`, `--passive`, itp.), wartość w pliku odpowiedzi powinna być PRAWDA/FAŁSZ.  Jeśli zajmuje argumentu (na przykład `--installPath <dir>`), wartość w pliku odpowiedzi musi być ciągiem.  Jeśli przyjmuje argument, a może wystąpić więcej niż raz w wierszu polecenia (na przykład `--add <id>`), należy go tablicę ciągów.

Parametry, które są określone w ustawieniach przesłonięcia wiersza polecenia z pliku odpowiedzi, z wyjątkiem czasie, gdy parametry przenieść wielu danych wejściowych (na przykład `--add`). Jeśli masz wielu danych wejściowych, dane wejściowe podane w wierszu polecenia są scalane z ustawień z pliku odpowiedzi.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Ustawienie konfiguracji domyślnej dla programu Visual Studio

Jeśli utworzono pamięci podręcznej układu sieci za pomocą `--layout`, po początkowym `response.json` plik jest tworzony w układzie. Jeśli tworzysz częściowe układu, ten plik odpowiedzi zawiera obciążeń i języki, które zostały uwzględnione w układzie.  Uruchamiania Instalatora z tego układu automatycznie używa tego pliku response.json, który wybiera obciążeń i składników zawartych w układzie.  Użytkownicy mogą nadal zaznacz lub odznacz wszystkie obciążenia w konfiguracji interfejsu użytkownika przed zainstalowaniem programu Visual Studio.

Administratorzy, którzy tworzenie układu można zmodyfikować `response.json` w układzie, aby kontrolować ustawienia domyślne, aby ich użytkownicy widzą podczas instalacji programu Visual Studio z układu.  Na przykład, jeśli administrator chce konkretnych obciążeń i składników, instalowane domyślnie, można skonfigurować `response.json` plik, aby je dodać.

Po uruchomieniu Instalatora programu Visual Studio z folderem układu go _automatycznie_ używa pliku odpowiedzi w folderze układu.  Nie trzeba stosować `--in` opcji.

Możesz zaktualizować `response.json` pliku, który jest tworzony w folderze układu w trybie offline, aby zdefiniować domyślne ustawienie dla użytkowników, którzy instalują z tego układu.

> [!WARNING]
> Koniecznie pozostanie istniejące właściwości, które zostały określone podczas tworzenia układu.

Podstawa `response.json` pliku w układzie powinien wyglądać podobnie do poniższego przykładu, z tą różnicą, że będzie ona zawierać wartość dla produktu i kanału, który chcesz zainstalować:

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

Podczas tworzenia lub aktualizacji układu jest też tworzony plik response.template.json.  Ten plik zawiera wszystkie obciążenia, składników i identyfikatorów, których można użyć języka.  Ten plik jest dostarczany jako szablon dla wszystkich, jakie mogłyby zostać włączone w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punktu wyjścia dla pliku odpowiedzi niestandardowej.  Po prostu usuń identyfikatory dla elementów, których nie chcesz zainstalować i zapisz go w pliku odpowiedzi.  Nie należy modyfikować pliku response.template.json lub wprowadzone zmiany zostaną utracone przy każdej aktualizacji układu.

## <a name="example-layout-response-file-content"></a>Przykładowy układ odpowiedzi pliku zawartości

W poniższym przykładzie instalację programu Visual Studio Enterprise z sześciu typowych obciążeń i składników, a w językach angielskim i francuskim interfejsu użytkownika. W tym przykładzie można użyć jako szablonu; można zmienić w przypadku obciążeń i składników do tych, które chcesz zainstalować:

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

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego](troubleshooting-network-related-errors-in-visual-studio.md)
