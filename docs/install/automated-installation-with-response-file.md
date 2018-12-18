---
title: Automatyzowanie instalacji przy użyciu pliku odpowiedzi
description: Dowiedz się, jak utworzyć plik odpowiedzi JSON, który umożliwia zautomatyzowanie instalacji programu Visual Studio
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30e7af50259a2087a0a380b1fe2d0c96c0d83f9a
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158778"
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

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

Podczas tworzenia lub aktualizacji układu jest też tworzony plik response.template.json.  Ten plik zawiera wszystkie obciążenia, składników i identyfikatorów, których można użyć języka.  Ten plik jest dostarczany jako szablon dla wszystkich, jakie mogłyby zostać włączone w instalacji niestandardowej.  Administratorzy mogą używać tego pliku jako punktu wyjścia dla pliku odpowiedzi niestandardowej.  Po prostu usuń identyfikatory dla elementów, których nie chcesz zainstalować i zapisz go w pliku odpowiedzi.  Nie należy modyfikować pliku response.template.json lub wprowadzone zmiany zostaną utracone przy każdej aktualizacji układu.

## <a name="example-layout-response-file-content"></a>Przykładowy układ odpowiedzi pliku zawartości

W poniższym przykładzie instalację programu Visual Studio Enterprise z sześciu typowych obciążeń i składników, a w językach angielskim i francuskim interfejsu użytkownika. W tym przykładzie można użyć jako szablonu; można zmienić w przypadku obciążeń i składników do tych, które chcesz zainstalować:

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Visual Studio 2017 obciążeń i składników identyfikatorów](workload-and-component-ids.md)
