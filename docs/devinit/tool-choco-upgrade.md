---
title: choco-upgrade
description: devinit narzędzia Choco-Upgrade.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: fab2a3f2893ba79874b6909b3d19ccf939f8b14a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906318"
---
# <a name="choco-upgrade"></a>choco-upgrade

Za `choco-upgrade` pomocą tego narzędzia można instalować i aktualizować pakiety [czekoladowe](https://chocolatey.org/docs/commandsupgrade) .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie nie będzie niczego robić.

| Nazwa                                             | Typ   | Wymagane  | Wartość                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie        | Opcjonalna Właściwość komentarzy. Nie używany.                                                                          |
| [**klawiatur**](#input)                              | ciąg | Tak       | Pakiet do uaktualnienia. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | ciąg | Nie        | Dodatkowe opcje do przekazania do narzędzia. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.       |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia nazwy pakietu do uaktualnienia (na przykład "MongoDB") lub ścieżki do pliku konfiguracji następujących formatów _packages.config_, _. nuspec_ i _. nupkg_. Wartość `input` zostanie dołączona do `choco upgrade` polecenia (na przykład `choco upgrade mongodb` ) wraz z dowolnymi argumentami określonymi w [`additionalOptions`](#additional-options) i wbudowane `choco` Opcje (zdefiniowane [poniżej](#built-in-options)). Pakiety można znaleźć w [Galerii pakietów czekolady](https://chocolatey.org/packages). Przy użyciu pliku konfiguracji można przekazać ścieżkę do tego pliku we `input` właściwości na przykład: `"input":"packages.config"` .

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) i są zdefiniowane w dokumentacji czekoladowej.

### <a name="built-in-options"></a>Wbudowane opcje

`choco-upgrade`Narzędzie ustawia wiele `choco` argumentów wiersza polecenia, aby zapewnić `choco` możliwość uruchamiania bezobsługowego. Te argumenty są wymienione poniżej i dokumentacja na nich znajduje się w [dokumentacji czekoladowej](https://chocolatey.org/docs/).

| Nazwa                  | Opis                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--tak**             | Potwierdź wszystkie monity — wybierają odpowiedź twierdzącą zamiast monitowania. Oznacza `--accept-license` . |
| **--No-Progress**     | Nie pokazuj postępów — procent postępu nie będzie pokazywany.                                         |
| **--Skip-PowerShell** | Pomijanie programu PowerShell — chocolateyInstall.ps1 nie zostanie uruchomiony.                                              |

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `choco-upgrade` narzędzia jest błędem, ponieważ `input` Właściwość jest wymagana.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `choco-upgrade` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.js, na którym zostaną zaktualizowane pakiety wymienione w packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.js, na którym zostanie uaktualniony MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.jsw ramach uaktualnienia do określonej wersji programu MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```