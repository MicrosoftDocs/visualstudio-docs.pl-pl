---
title: wsl-install
description: devinit narzędzie WSL — Zainstaluj.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: cd48cbe0eac8438bb761029bbca4cd27e13f2319
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442092"
---
# <a name="wsl-install"></a>wsl-install

`wsl-install`Narzędzie to służy do instalowania dystrybucje systemu Linux dla [podsystemu Windows w systemie Linux](/windows/wsl/) (WSL).

> [!IMPORTANT]
> `wsl-install`Narzędzie wymaga, aby WSL 2 było już włączone w systemie Windows. Jeśli z jakiegoś powodu WSL 2 nie jest włączona, możesz wykonać czynności opisane w [dokumentacji programu WSL Install](https://docs.microsoft.com/windows/wsl/install-win10). Można również użyć narzędzia [WindowsFeature-Enable](tool-windowsfeature-enable.md) , aby włączyć wszystkie potrzebne funkcje systemu Windows.

## <a name="usage"></a>Użycie

Jeśli obie `input` właściwości i `additionalOptions` zostaną pominięte lub puste, narzędzie będzie przestrzegać [domyślnego](#default-behavior) zachowania podanego poniżej.

| Nazwa                                             | Typ   | Wymagane | Wartość                                                             |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------|
| **komentarz**                                     | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                             |
| [**klawiatur**](#input)                              | ciąg | Tak      | Dystrybucji do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .     |
| [**additionalOptions**](#additional-options)     | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.  |

### <a name="input"></a>Dane wejściowe

Identyfikator URI pakietu dystrybucji aplikacji AppX ( `.appx` ) zawierającego dystrybucji do wdrożenia. Identyfikator URI musi wskazywać na `.appx` archiwum, które zawiera jeden z nich `install.tar.gz` w katalogu głównym archiwum lub wewnątrz Archiwum wewnętrznym `.appx` . Przykłady obsługiwanych dystrybucje obejmują:

| Dystrybucji                          | Adresu                                                           |
|---------------------------------|---------------------------------------------------------------|
| Ubuntu 20.04                    | https://aka.ms/wslubuntu2004                                  |
| Ubuntu 18.04                    | https://aka.ms/wsl-ubuntu-1804                                |
| Ubuntu 16.04                    | https://aka.ms/wsl-ubuntu-1604                                |
| Debian GNU/Linux                | https://aka.ms/wsl-debian-gnulinux                            |
| Kali Linux                      | https://aka.ms/wsl-kali-linux-new                             |
| OpenSUSE przestępnie 42                | https://aka.ms/wsl-opensuse-42                                |
| SUSE Linux Enterprise Server 12 | https://aka.ms/wsl-sles-12                                    |

> [!NOTE]
> System ARM Linux dystrybucje nie jest obecnie obsługiwany w usłudze GitHub Codespaces.

### <a name="additional-options"></a>Opcje dodatkowe

Obsługiwane są wiele dodatkowych opcji:

| Nazwa                      | Typ      | Wymagane | Wartość                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --WSL-Version             | ciąg    | Nie       | WSL wersja do użycia. Wartość domyślna to 2.                                                                                                                                  |
| --Po utworzeniu polecenia     | ciąg    | Nie       | Polecenie do wykonania w dystrybucji systemu Linux po zakończeniu instalacji. Polecenie powinno być sformatowane jako pojedyncze słowo lub opakowane w cudzysłów. Wartość domyślna to No.  |

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślne zachowanie `wsl-install` narzędzia to błąd, który jest `input` wymagany do zainstalowania dystrybucji.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `wsl-install` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-install-ubuntu-2004"></a>.devinit.js, na którym zostanie zainstalowany program Ubuntu 20,04:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command"></a>.devinit.js, na którym zostanie zainstalowany program Ubuntu 20,04 i zostanie wykonane polecenie post create:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'echo Hello from Ubuntu!'"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-ubuntu-2004-and-perform-a-post-create-command-that-configures-the-packages-listed"></a>.devinit.js, na którym zostanie zainstalowany program Ubuntu 20,04 i zostanie wykonane polecenie post create, które konfiguruje wymienione pakiety:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```
