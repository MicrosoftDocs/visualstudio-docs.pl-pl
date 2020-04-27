---
title: Exec — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 634916d9ab4ef0ce3119fcb5695301598992f38c
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167306"
---
# <a name="exec-task"></a>Exec — Zadanie

Uruchamia określony program lub polecenie przy użyciu określonych argumentów.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Exec` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Command`|Wymagany parametr interfejsu `String`.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak attrib lub wykonywalny, takie jak *program exe*, *runprogram. bat*lub *Setup. msi*.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wiele poleceń w pliku wsadowym i uruchomić je za pomocą tego parametru.|
|`ConsoleOutput`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Każdy element wyjściowy jest wierszem ze standardowego wyjścia lub standardowego strumienia błędów emitowanego przez narzędzie. Jest to przechwytywane tylko `ConsoleToMsBuild` wtedy, gdy `true`jest ustawiona na.|
|`ConsoleToMsBuild`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie przechwytuje standardowy błąd i standardowe wyjście narzędzia i udostępni je w parametrze `ConsoleOutput` Output.<br /><br />Wartość domyślna: `false`.|
|`CustomErrorRegularExpression`|Opcjonalny `String` parametr.<br /><br /> Określa wyrażenie regularne, które jest używane do określania wierszy błędów w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.<br /><br />Wartość domyślna `null` : (bez przetwarzania niestandardowego).|
|`CustomWarningRegularExpression`|Opcjonalny `String` parametr.<br /><br /> Określa wyrażenie regularne, które jest używane do wyświetlania wierszy ostrzeżeń w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.<br /><br />Wartość domyślna `null` : (bez przetwarzania niestandardowego).|
|`EchoOff`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`zadanie nie będzie emitować rozwiniętej postaci `Command` do dziennika MSBuild.<br /><br />Wartość domyślna: `false`.|
|`ExitCode`|Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie.|
|`IgnoreExitCode`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true`, zadanie zignoruje kod zakończenia, który jest dostarczany przez wykonane polecenie. W przeciwnym razie zadanie zwraca `false` wartość, jeśli wykonane polecenie zwróci niezerowy kod zakończenia.<br /><br />Wartość domyślna: `false`.|
|`IgnoreStandardErrorWarningFormat`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `false`program wybierze wiersze w danych wyjściowych, które pasują do standardowego formatu błędu/ostrzeżenia, i rejestruje je jako błędy/ostrzeżenia. Jeśli `true`to zachowanie jest wyłączone.<br /><br />Wartość domyślna: `false`.|
|`Outputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy wyjściowe zadania. `Exec` Zadanie nie ustawia tych samych wartości. Zamiast tego można je określić tak, jakby je ustawił, tak aby mogły być używane później w projekcie.|
|`StdErrEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie strumienia błędów standardowego przechwyconego zadania. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|
|`StdOutEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie przechwyconego strumienia wyjściowego zadania standardowego. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|
|`WorkingDirectory`|Opcjonalny `String` parametr.<br /><br /> Określa katalog, w którym zostanie uruchomione polecenie.<br /><br />Domyślnie: bieżący katalog roboczy projektu.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="remarks"></a>Uwagi

To zadanie jest przydatne, gdy określone zadanie programu MSBuild dla zadania, które chcesz wykonać, jest niedostępne. Jednak `Exec` zadanie, w przeciwieństwie do bardziej konkretnego zadania, nie może wykonać dodatkowych operacji przetwarzania ani wykonywania warunkowego na podstawie wyniku uruchomionego narzędzia lub polecenia.

`Exec` Zadanie wywołuje *cmd. exe* , zamiast bezpośrednio wywołujący proces.

## <a name="example"></a>Przykład

Poniższy przykład używa `Exec` zadania do uruchomienia polecenia.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Binaries Include="*.dll;*.exe"/>
    </ItemGroup>

    <Target Name="SetACL">
        <!-- set security on binaries-->
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz także

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
