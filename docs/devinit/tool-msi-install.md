---
title: MSI-instalacja
description: Narzędzie devinit dla narzędzia Msiexec.
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98667c602272f22e7803647a688ee75d6c6cbd70
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402313"
---
# <a name="msi-install"></a>MSI-instalacja

`msi-install`Narzędzie służy do instalowania `.msi` formatów plików pakietu przy użyciu polecenia [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Użycie

Jeśli `input` parametr zostanie pominięty lub pusty, narzędzie wyświetli błąd.

| Nazwa                                         | Typ   | Wymagane | Wartość                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **komentarz**                                 | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                             |
| [**klawiatur**](#input)                          | ciąg | Tak      | `msi`Do zainstalowania. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .                      |
| [**additionalOptions**](#additional-options) | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.                  |

### <a name="input"></a>Dane wejściowe

Właściwość Input służy do określania ścieżki lub adresu URL do `.msi` pliku, który zostanie zainstalowany. Jeśli ścieżka do `.msi` jest niepoprawna lub adres URL nie wskazuje `.msi` bezpośrednio, oznacza to, `msi-install` że nie można otworzyć pakietu instalacyjnego.

### <a name="additional-options"></a>Opcje dodatkowe

Dodatkowe opcje konfiguracji mogą być przesyłane jako wartość additionalOptions. Te argumenty są bezpośrednim przekazywaniem do argumentów używanych przez `msiexec` i są zdefiniowane w `msiexec` [dokumentacji](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

### <a name="built-in-options"></a>Wbudowane opcje

Narzędzie MSI-Install ustawia liczbę `msiexec` argumentów wiersza polecenia, aby upewnić się, że plik msi może działać jako bezobsługowy. Te argumenty są wymienione poniżej i dokumentacja na nich znajduje się w `msiexec` [dokumentacji](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

| Nazwa          | Opis                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Uruchamia normalną instalację                                                                                                                                                                    | 
| /quiet        | Określa tryb cichy bez interakcji użytkownika                                                                                                                                        | 
| /Qn           | Określa, że podczas procesu instalacji nie ma interfejsu użytkownika                                                                                                                                           | 
| /Passive      | Określa tryb instalacji nienadzorowanej, w którym tylko pokazuje pasek postępu                                                                                                                    | 
| /l * V          | Włącza rejestrowanie i rejestruje wszystkie informacje, łącznie z pełnymi informacjami, do `devinit.log` pliku w lokalnym folderze tymczasowym maszyny. Jeśli narzędzie się nie powiedzie, zostanie wyświetlona ścieżka pliku dziennika.      | 
| /norestart    | Powoduje zatrzymanie ponownego uruchomienia komputera po zakończeniu instalacji, ale zwróci kod zakończenia 3010, jeśli jest wymagany ponowny rozruch                                                                  | 

## <a name="example-usage"></a>Przykład użycia

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "comments": "Installs the 7-Zip MSI",
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
