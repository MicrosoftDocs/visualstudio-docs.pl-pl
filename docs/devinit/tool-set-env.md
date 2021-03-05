---
title: set-env
description: Narzędzie devinit wymaga-set-env.
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
ms.openlocfilehash: 82f0def521a7a5a6bf4bd4595d32775324a0a39c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171023"
---
# <a name="set-env"></a>set-env

`set-env`Narzędzie może służyć do ustawiania zmiennych środowiskowych do użycia w bieżącym procesie. Zmienne środowiskowe są ustawiane tylko w bieżącym procesie i będą używane przez inne `devinit` Narzędzia, jeśli są uruchamiane w ramach tego procesu.

To narzędzie korzysta z interfejsu API programu .NET Core `Environment.SetEnvironment` i ma takie same ograniczenia, jak ten interfejs API. Aby uzyskać więcej informacji, zapoznaj się z [dokumentacją](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) `Environment.SetEnvironment` .

## <a name="usage"></a>Użycie

| Nazwa                                         | Typ   | Wymagane | Wartość                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **komentarz**                                 | ciąg | Nie       | Opcjonalna Właściwość komentarzy. Nie używany.                                       |
| [**klawiatur**](#input)                          | ciąg | Nie       | Dane wejściowe narzędzia. Aby uzyskać szczegółowe informacje, zobacz poniższe [dane wejściowe](#input) .               |
| [**additionalOptions**](#additional-options) | ciąg | Nie       | Aby uzyskać szczegółowe informacje, zobacz [dodatkowe opcje](#additional-options) poniżej.            |

### <a name="input"></a>Dane wejściowe

`set-env`Narzędzie pobiera jeden ciąg jako dane wejściowe `input` właściwości. Ciąg powinien być sformatowany jako ciąg średnika (;) rozdzielane pary kluczowe wartości (nazwa = wartość) i cztery możliwe akcje na podstawie wartości `input` właściwości.

| Akcja       | Dane wejściowe            | Opis                                                                                                                                                              | Przykład             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Wyświetl wszystko** | puste lub pominięte | Wyświetl listę wszystkich bieżących zmiennych środowiskowych.                                                                                                                           | `"input":""`        |
| **Lista jeden** | ciąg           | Wyświetl wartość konkretnej zmiennej środowiskowej według nazwy.                                                                                                               | `"input":"foo"`     |
| **add**      | ciąg           | Ustawia wartość zmiennej środowiskowej jako parę klucz-wartość. Dodaje nową zmienną środowiskową, jeśli jeszcze nie istnieje lub nie ustawił wartości istniejącej zmiennej środowiskowej | `"input":"foo=bar"` |
| **delete**   | ciąg           | Usuwa istniejącą zmienną środowiskową, przekazując ciąg pustej wartości.                                                                                            | `"input":"foo="`    |

`input`Ciąg może zawierać na przykład rozszerzenie zmiennej środowiskowej `%userprofile%` , które jest rozwinięte, gdy wartość jest odczytywana.

### <a name="additional-options"></a>Opcje dodatkowe

 `--user`, `--process` lub `--machine` mogą być dołączone do określenia miejsca, w którym należy ustawić zmienne środowiskowe. Domyślnie jest on przeznaczony dla użytkownika. Aby uzyskać więcej informacji o możliwych celach dla zmiennych środowiskowych, zobacz [EnvironmentVariableTarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget).

### <a name="default-behavior"></a>Zachowanie domyślne

Domyślnym zachowaniem tego `set-env` narzędzia jest wyświetlenie listy bieżących zmiennych środowiskowych.

## <a name="usage-in-a-codespace"></a>Użycie w codespace

Jeśli używasz codespace, możesz ustawić zmienne środowiskowe używane w codespace przez dostosowanie `remoteEnv` właściwości w [`.devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) pliku.

## <a name="example-usage"></a>Przykład użycia
Poniżej znajdują się przykłady sposobu uruchamiania programu `set-env` przy użyciu programu `.devinit.json` .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.js, w którym zostanie ustawiona zmienna środowiskowa, `foo` do wartości `bar` :
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.jsna to ustawienie zmiennej środowiskowej, `foo` do wartości, `bar` przechowywanej w bloku środowiska skojarzonego z bieżącym procesem:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "additionalOptions": "--process",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.js, na którym zostanie wyświetlona wartość zmiennej środowiskowej:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>.devinit.js, w którym zostaną wystawione wszystkie zmienne środowiskowe:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.js, w którym zostanie usunięta zmienna środowiskowa:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.js, który będzie używać rozwinięcia zmiennej środowiskowej:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.js, który ustawi wartość zmiennej środowiskowej przy użyciu manipulowania ścieżką:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.js, na którym zostanie przywrócona ścieżka z zapisanej kopii:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
