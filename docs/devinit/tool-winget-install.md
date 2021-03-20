---
title: Winget — Zainstaluj
description: Narzędzie devinit dla Winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4a2ad1ef30692d7d23f2d450f0ba32d6f38f8262
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672625"
---
# <a name="winget-install"></a>Winget — Zainstaluj

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

`winget-install`Narzędzie służy do instalowania [pakietów Winget](https://docs.microsoft.com/windows/package-manager/winget/).

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie wyświetli błąd.

| Nazwa                                         | Typ   | Wymagane | Wartość                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **komentarz**                                 | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                             |
| [**klawiatur**](#input)                          | ciąg | Nie       | Pakiet do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                    |
| [**additionalOptions**](#additional-options) | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                  |

### <a name="input"></a>Dane wejściowe

Właściwość Input służy do określania `Id` lub `Name` pakietu do zainstalowania (na przykład "MongoDB. Server"). Wartość danych wejściowych zostanie dołączona do `winget install` polecenia (na przykład `winget install MongoDB.Server` ). Jeśli nazwa pakietu nie jest unikatowa i jest zgodna z innymi pakietami, możesz określić `Id` pakiet i dodać do `--exact` niego flagę, `additionalOptions` Aby upewnić się, że tożsamość pakietu pasuje dokładnie. `Id`Pakiet można znaleźć, wykonując `winget search` polecenie i korzystając z `Id` parametru pakietu.  

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość additionalOptions. Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez `winget install` i są zdefiniowane w `winget install` [dokumentacji](https://docs.microsoft.com/windows/package-manager/winget/install).

#### <a name="manifests"></a>Manifesty

Dodatkową opcjonalną `winget` obsługą jest możliwość udostępnienia [pliku manifestu](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) w celu podania szczegółów pakietu do zainstalowania. Aby użyć tej funkcji z devinit, `input` parametr powinien być pusty, a `additionalOptions` Właściwość powinna zawierać `--manifest` opcję, po której następuje ścieżka do manifestu (na przykład `--manifest path.to.manifest.yml` ).

### <a name="built-in-options"></a>Wbudowane opcje

Narzędzie Winget-Install ustawia wiele argumentów wiersza polecenia Winget, aby zapewnić, że Winget może uruchamiać bezobsługowe. Te argumenty są wymienione poniżej i dokumentacja na nich znajduje się w `winget install` [dokumentacji](https://docs.microsoft.com/windows/package-manager/winget/install).

| Nazwa     | Opis                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| — dyskretny | Uruchamia Instalatora w trybie dyskretnym. Spowoduje to pominięcie wszystkich interfejsów użytkownika. Domyślne środowisko pokazuje postęp Instalatora.                       | 

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
