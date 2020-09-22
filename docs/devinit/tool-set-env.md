---
title: set-env
description: Narzędzie devinit wymaga-set-env.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2f4ec5489f22e94ad8f57f22ddc7742dc0ae3ade
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005996"
---
# <a name="set-env"></a>set-env

`set-env`Narzędzie może służyć do ustawiania zmiennych środowiskowych do użycia w bieżącym procesie. Zmienne środowiskowe są ustawiane tylko w bieżącym procesie i będą używane przez inne `devinit` Narzędzia, jeśli są uruchamiane w ramach tego procesu.

To narzędzie korzysta z interfejsu API programu .NET Core `Environment.SetEnvironment` i ma takie same ograniczenia, jak ten interfejs API. Aby uzyskać więcej informacji, zapoznaj się z [dokumentacją](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) `Environment.SetEnvironment` .

## <a name="usage"></a>Użycie

| Nazwa                                         | Typ   | Wymagane | Wartość                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **komentarz**                                 | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                       |
| [**klawiatur**](#input)                          | ciąg | Nie       | Dane wejściowe narzędzia. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .               |
| [**additionalOptions**](#additional-options) | ciąg | Nie       | Nie używany. Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.  |

### <a name="input"></a>Dane wejściowe

`set-env`Narzędzie pobiera jeden ciąg jako dane wejściowe `input` właściwości. Ciąg powinien być sformatowany jako ciąg średnika (;) rozdzielane pary kluczowe wartości (nazwa = wartość) i cztery możliwe akcje na podstawie wartości `input` właściwości.

| Akcja       | Dane wejściowe            | Opis                                                                                                                                                              | Przykład             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Wyświetl wszystko** | puste lub pominięte | Wyświetl listę wszystkich bieżących zmiennych środowiskowych.                                                                                                                              | `"input":""`        |
| **Lista jeden** | ciąg           | Wyświetl wartość konkretnej zmiennej środowiskowej według nazwy.                                                                                                               | `"input":"foo"`     |
| **add**      | ciąg           | Ustawia wartość zmiennej środowiskowej jako parę klucz-wartość. Dodaje nową zmienną środowiskową, jeśli jeszcze nie istnieje lub nie ustawił wartości istniejącej zmiennej środowiskowej | `"input":"foo=bar"` |
| **delete**   | ciąg           | Usuwa istniejącą zmienną środowiskową, przekazując ciąg pustej wartości.                                                                                            | `"input":"foo="`    |

`input`Ciąg może zawierać na przykład rozszerzenie zmiennej środowiskowej `%userprofile%` , które jest rozwinięte, gdy wartość jest odczytywana.

### <a name="additional-options"></a>Opcje dodatkowe

Nie używany.

## <a name="usage-in-a-codespace"></a>Użycie w codespace

Jeśli używasz codespace, możesz ustawić zmienne środowiskowe używane w codespace przez customizating `remoteEnv` Właściwość w [`.devcontainer.json`](https://docs.microsoft.com/visualstudio/codespaces/reference/configuring) pliku.

## <a name="example-usage"></a>Przykład użycia

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```
