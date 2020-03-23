---
title: Automatyzacja instalacji za pomocą pliku odpowiedzi
description: Dowiedz się, jak utworzyć plik odpowiedzi JSON ułatwiacy automatyzację instalacji programu Visual Studio
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecdda55bbe4e79af01f8fb9a9a2b77f775548b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115231"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Jak zdefiniować ustawienia w pliku odpowiedzi

Administratorzy, którzy wdrażają program Visual `--in` Studio, mogą określić plik odpowiedzi przy użyciu tego parametru, tak jak w poniższym przykładzie:

```cmd
vs_enterprise.exe --in customInstall.json
```

Pliki odpowiedzi są plikami [JSON,](http://json-schema.org/) których zawartość odzwierciedla argumenty wiersza polecenia.  Ogólnie rzecz biorąc, jeśli parametr wiersza polecenia `--quiet`nie `--passive`przyjmuje żadnych argumentów (na przykład , itp.), wartość w pliku odpowiedzi powinna być true/false.  Jeśli przyjmuje argument (na `--installPath <dir>`przykład), wartość w pliku odpowiedzi powinna być ciągiem.  Jeśli przyjmuje argument i może pojawić się w wierszu `--add <id>`polecenia więcej niż jeden raz (na przykład ), powinna to być tablica ciągów.

Parametry określone w wierszu polecenia zastępują ustawienia z pliku odpowiedzi, z wyjątkiem sytuacji, `--add`gdy parametry przyjmują wiele wejść (na przykład ). Jeśli masz wiele danych wejściowych, dane wejściowe podane w wierszu polecenia są scalane z ustawieniami z pliku odpowiedzi.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Ustawianie domyślnej konfiguracji programu Visual Studio

Jeśli utworzono pamięć podręczną układu sieciowego `--layout`z plikiem początkowym, `response.json` tworzony jest w układzie. Jeśli utworzysz układ częściowy, ten plik odpowiedzi zawiera obciążenia i języki, które zostały uwzględnione w układzie.  Uruchamianie konfiguracji z tego układu automatycznie używa tego pliku response.json, który wybiera obciążenia i składniki zawarte w układzie.  Użytkownicy mogą nadal zaznaczać lub odznaczać wszystkie obciążenia w interfejsie użytkownika konfiguracji przed zainstalowaniem programu Visual Studio.

Administratorzy, którzy tworzą układ `response.json` można zmodyfikować plik w układzie, aby kontrolować ustawienia domyślne, które ich użytkownicy widzą podczas instalowania programu Visual Studio z układu.  Na przykład jeśli administrator chce, aby określone obciążenia i składniki były `response.json` instalowane domyślnie, może skonfigurować plik, aby je dodać.

Gdy instalator programu Visual Studio jest uruchamiany z folderu układu, _automatycznie_ używa pliku odpowiedzi w folderze układu.  Nie musisz korzystać z `--in` tej opcji.

Można zaktualizować `response.json` plik utworzony w folderze układu trybu offline, aby zdefiniować ustawienie domyślne dla użytkowników instalujących z tego układu.

> [!WARNING]
> Bardzo ważne jest, aby pozostawić istniejące właściwości, które zostały zdefiniowane podczas tworzenia układu.

Plik `response.json` podstawowy w układzie powinien wyglądać podobnie do następującego przykładu, z tą różnicą, że zawiera wartość produktu i kanału, który chcesz zainstalować:

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

Podczas tworzenia lub aktualizowania układu tworzony jest również plik response.template.json.  Ten plik zawiera wszystkie identyfikatory obciążenia, składnika i języka, które mogą być używane.  Ten plik jest dostarczany jako szablon dla tego, co wszystko może być zawarte w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punktu wyjścia dla niestandardowego pliku odpowiedzi.  Wystarczy usunąć identyfikatory dla rzeczy, których nie chcesz zainstalować i zapisać je we własnym pliku odpowiedzi.  Nie należy dostosowywać pliku response.template.json lub zmiany zostaną utracone za każdym razem, gdy układ zostanie zaktualizowany.

## <a name="example-layout-response-file-content"></a>Przykładowa zawartość pliku odpowiedzi na układ

Poniższy przykład instaluje visual studio enterprise z sześciu typowych obciążeń i składników i w języku angielskim i francuskim interfejsu użytkownika. W tym przykładzie można użyć szablonu; wystarczy zmienić obciążenia i składniki na te, które chcesz zainstalować:

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
* [Rozwiązywanie problemów z błędami związanymi z siecią podczas instalowania lub używania programu Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
