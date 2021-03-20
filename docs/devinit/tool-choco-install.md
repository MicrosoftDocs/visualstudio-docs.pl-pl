---
title: choco-install
description: devinit Tool Choco — Instaluj, aby zainstalować pakiety czekoladowe.
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
ms.openlocfilehash: c1f5b1c587ea8d1d6335e19b2e7303cc12ad9783
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671659"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

Za `choco-install` pomocą tego narzędzia można instalować i aktualizować pakiety [czekoladowe](https://chocolatey.org/) .

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie nie będzie niczego robić.

| Nazwa                                             | Typ   | Wymagane  | Wartość                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie        | Opcjonalna Właściwość komentarzy. Nie używany.                                                                          |
| [**klawiatur**](#input)                              | ciąg | Tak       | Pakiet do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | ciąg | Nie        | Dodatkowe opcje do przekazania do narzędzia. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.       |

### <a name="input"></a>Dane wejściowe

`input`Właściwość służy do określenia nazwy pakietu do zainstalowania (na przykład "MongoDB") lub ścieżki do pliku konfiguracji następujących formatów _packages.config_, _. nuspec_ i _. nupkg_. Wartość `input` zostanie dołączona do `choco install` polecenia (na przykład `choco install mongodb` ) wraz z dowolnymi argumentami określonymi w [`additionalOptions`](#additional-options) i wbudowane `choco` Opcje (zdefiniowane [poniżej](#built-in-options)). Pakiety znajdują się w [Galerii pakietów czekolady](https://chocolatey.org/packages). Przy użyciu pliku konfiguracji można przekazać ścieżkę do tego pliku we `input` właściwości, na przykład `"input":"packages.config"` .

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość `additionalOptions` . Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez [`choco install`](https://chocolatey.org/docs/commands-install) i są zdefiniowane w dokumentacji czekoladowej.

#### <a name="adding-new-feeds-to-chocolatey"></a>Dodawanie nowych źródeł danych do czekolady
Jeśli chcesz dodać nowe źródło danych do czekolady, podobnie jak `choco source add` polecenie, możesz przekazać `additionalOptions` do tego celu. Przykładem dodania nowego źródła danych jest [użycie przykładu](#example-usage). Jeśli chcesz dodać prywatne źródło danych, zalecamy uruchomienie tego narzędzia w wierszu polecenia, ponieważ wymaga ono poświadczeń. Na przykład,, `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` gdzie `{package}` , `{feed link}` , `{user}` i `{password}` zapoznaj się z określonym pakietem, linkiem kanału informacyjnego, nazwą użytkownika i hasłem. Więcej informacji znajduje się w dokumentacji dotyczącej czekolady, do której odwołuje się powyżej. 

### <a name="built-in-options"></a>Wbudowane opcje

`choco-install`Narzędzie ustawia wiele `choco` argumentów wiersza polecenia, aby zapewnić `choco` możliwość uruchamiania bezobsługowego. Te argumenty są wymienione poniżej i dokumentacja na nich znajduje się w [dokumentacji czekoladowej](https://chocolatey.org/docs/).

| Nazwa                  | Opis                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--tak**             | Potwierdź wszystkie monity — wybierają odpowiedź twierdzącą zamiast monitowania. Oznacza `--accept-license.` |
| **--No-Progress**     | Nie pokazuj postępów — procent postępu nie będzie pokazywany.                                         |
| **--Skip-PowerShell** | Pomijanie programu PowerShell — chocolateyInstall.ps1 nie zostanie uruchomiony.                                              |

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `choco-install` narzędzia jest błędem, ponieważ `input` Właściwość jest wymagana.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `choco-install` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.js, na którym zostaną zainstalowane pakiety wymienione w packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.js, na którym zostanie zainstalowany program MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.js, na którym zostanie zainstalowana określona wersja programu MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.js, który dodaje nowe źródło danych do czekolady:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```