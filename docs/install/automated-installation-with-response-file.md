---
title: Automatyzowanie instalacji przy użyciu pliku odpowiedzi
description: Dowiedz się, jak utworzyć plik odpowiedzi JSON, który pomoże zautomatyzować instalację programu Visual Studio
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d3fa063d82a9d0ba9f26e326961b1345b47151b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868737"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Jak zdefiniować ustawienia w pliku odpowiedzi

Administratorzy, którzy wdrażają program Visual Studio, mogą określić plik odpowiedzi przy użyciu `--in` parametru, jak w poniższym przykładzie:

```cmd
vs_enterprise.exe --in customInstall.json
```

Pliki odpowiedzi to pliki [JSON](http://json-schema.org/) , których zawartość jest duplikatem argumentów wiersza polecenia.  Ogólnie rzecz biorąc, jeśli parametr wiersza polecenia nie przyjmuje argumentów (na przykład, `--quiet` `--passive` itp.), wartość w pliku odpowiedzi powinna być równa true/false.  Jeśli przyjmuje argument (na przykład `--installPath <dir>` ), wartość w pliku odpowiedzi powinna być ciągiem.  Jeśli przyjmuje argument i może być wyświetlany w wierszu polecenia więcej niż raz (na przykład `--add <id>` ), powinien być tablicą ciągów.

Parametry, które są określone w ustawieniach przesłonięcia wiersza polecenia z pliku odpowiedzi, z wyjątkiem przypadków, gdy parametry pobierają wiele danych wejściowych (na przykład `--add` ). Jeśli masz wiele danych wejściowych, dane wejściowe podane w wierszu polecenia są scalane z ustawieniami z pliku odpowiedzi.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Ustawianie konfiguracji domyślnej dla programu Visual Studio

W przypadku utworzenia pamięci podręcznej układu sieciowego przy użyciu programu `--layout` `response.json` tworzony jest początkowy plik w układzie. W przypadku utworzenia układu częściowego ten plik odpowiedzi obejmuje obciążenia i Języki, które zostały uwzględnione w układzie.  Uruchomienie Instalatora z tego układu automatycznie używa tego response.jsw pliku, który wybiera obciążenia i składniki zawarte w układzie.  Przed zainstalowaniem programu Visual Studio użytkownicy mogą nadal wybierać lub wyznaczać dowolne obciążenia w interfejsie użytkownika Instalatora.

Administratorzy, którzy tworzą układ, mogą modyfikować `response.json` plik w układzie w celu kontrolowania ustawień domyślnych, które użytkownicy widzą po zainstalowaniu programu Visual Studio z układu.  Na przykład, jeśli administrator chce, aby określone obciążenia i składniki były domyślnie instalowane, można skonfigurować `response.json` plik do dodania.

Gdy Instalator programu Visual Studio jest uruchamiany z folderu układowego, _automatycznie_ używa pliku odpowiedzi w folderze układu.  Nie trzeba używać tej `--in` opcji.

Można zaktualizować `response.json` plik, który jest tworzony w folderze układu offline w celu zdefiniowania ustawienia domyślnego dla użytkowników, którzy instalują się z tego układu.

> [!WARNING]
> Ważne jest pozostawienie istniejących właściwości, które zostały zdefiniowane podczas tworzenia układu.

Plik podstawowy `response.json` w układzie powinien wyglądać podobnie do poniższego przykładu, z tą różnicą, że będzie zawierać wartość dla produktu i kanału, który ma zostać zainstalowany:

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

Podczas tworzenia lub aktualizowania układu jest również tworzony response.template.jsna pliku.  Ten plik zawiera wszystkie identyfikatory obciążeń, składników i języka, których można użyć.  Ten plik jest dostarczany jako szablon dla wszystkich elementów, które można uwzględnić w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punktu wyjścia dla niestandardowego pliku odpowiedzi.  Po prostu usuń identyfikatory elementów, których nie chcesz instalować, i Zapisz je w pliku odpowiedzi.  Nie dostosowuj response.template.jsw pliku lub zmiany zostaną utracone za każdym razem, gdy układ zostanie zaktualizowany.

## <a name="example-layout-response-file-content"></a>Przykładowa zawartość pliku odpowiedzi układu

Poniższy przykład służy do instalowania Visual Studio Enterprise z sześcioma typowymi obciążeniami i składnikami oraz z językiem interfejsu użytkownika w języku angielskim i francuskim. Możesz użyć tego przykładu jako szablonu. wystarczy zmienić obciążenia i składniki na te, które mają zostać zainstalowane:

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
* [Rozwiązywanie problemów związanych z siecią podczas instalowania programu Visual Studio lub korzystania z niego](troubleshooting-network-related-errors-in-visual-studio.md)
