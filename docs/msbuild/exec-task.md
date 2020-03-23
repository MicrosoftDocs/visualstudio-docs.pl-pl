---
title: Zadanie Exec | Dokumenty firmy Microsoft
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
ms.openlocfilehash: f588ae1b32b8b8d47d6323ee32d02c9053a3de32
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634217"
---
# <a name="exec-task"></a>Exec — Zadanie

Uruchamia określony program lub polecenie przy użyciu określonych argumentów.

## <a name="parameters"></a>Parametry

W poniższej tabeli `Exec` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Command`|Wymagany parametr interfejsu `String`.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak attrib lub plik wykonywalny, taki jak *program.exe*, *runprogram.bat*lub *setup.msi*.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wiele poleceń w pliku wsadowym i uruchomić go przy użyciu tego parametru.|
|`ConsoleOutput`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Każde wyjście elementu jest wierszem ze standardowego wyjścia lub standardowego strumienia błędów emitowanego przez narzędzie. Jest to przechwytywane tylko wtedy, gdy `ConsoleToMsBuild` jest ustawiona na `true`.|
|`ConsoleToMsBuild`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie przechwyci błąd standardowy i standardowe wyjście narzędzia `ConsoleOutput` i udostępni je w parametrze wyjściowym.<br /><br />Wartość domyślna: `false`.|
|`CustomErrorRegularExpression`|Parametr `String` opcjonalny.<br /><br /> Określa wyrażenie regularne używane do wykrywania linii błędów w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi, które generują niezwykle sformatowane dane wyjściowe.<br /><br />Domyślnie: `null` (brak przetwarzania niestandardowego).|
|`CustomWarningRegularExpression`|Parametr `String` opcjonalny.<br /><br /> Określa wyrażenie regularne używane do wykrywania linii ostrzegawczych w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi, które generują niezwykle sformatowane dane wyjściowe.<br /><br />Domyślnie: `null` (brak przetwarzania niestandardowego).|
|`EchoOff`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie nie będzie emitować `Command` rozwiniętą formę do dziennika MSBuild.<br /><br />Wartość domyślna: `false`.|
|`ExitCode`|Opcjonalny `Int32` parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie.|
|`IgnoreExitCode`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`zadanie ignoruje kod zakończenia, który jest dostarczany przez wykonane polecenie. W przeciwnym razie `false` zadanie zwraca, jeśli wykonane polecenie zwraca kod zakończenia niezerowego.<br /><br />Wartość domyślna: `false`.|
|`IgnoreStandardErrorWarningFormat`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `false`, wybierze wiersze w danych wyjściowych, które pasują do standardowego formatu błędu/ostrzeżenia i rejestruje je jako błędy/ostrzeżenia. Jeśli `true`, wyłącz to zachowanie.<br /><br />Wartość domyślna: `false`.|
|`Outputs`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera elementy wyjściowe z zadania. Zadanie `Exec` nie ustawia się same. Zamiast tego można podać je tak, jakby je ustawić, tak aby mogły być używane w dalszej części projektu.|
|`StdErrEncoding`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa kodowanie przechwyconego standardowego strumienia błędów zadań. Wartością domyślną jest bieżące kodowanie danych wyjściowych konsoli.|
|`StdOutEncoding`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Określa kodowanie przechwyconego strumienia wyjściowego standardowego zadania. Wartością domyślną jest bieżące kodowanie danych wyjściowych konsoli.|
|`WorkingDirectory`|Parametr `String` opcjonalny.<br /><br /> Określa katalog, w którym zostanie uruchomione polecenie.<br /><br />Domyślnie: bieżący katalog roboczy projektu.|

## <a name="remarks"></a>Uwagi

To zadanie jest przydatne, gdy określone zadanie MSBuild dla zadania, które chcesz wykonać, nie jest dostępne. Jednak zadanie, w `Exec` przeciwieństwie do bardziej szczegółowego zadania, nie może wykonać dodatkowych operacji przetwarzania lub warunkowych na podstawie wyniku uruchomionego narzędzia lub polecenia.

Zadanie `Exec` wywołuje *cmd.exe* zamiast bezpośrednio wywoływać proces.

Oprócz parametrów wymienionych w tym dokumencie to zadanie <xref:Microsoft.Build.Tasks.ToolTaskExtension> dziedziczy parametry z <xref:Microsoft.Build.Utilities.ToolTask> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension klasy podstawowej](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `Exec` użyto zadania do uruchomienia polecenia.

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

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
