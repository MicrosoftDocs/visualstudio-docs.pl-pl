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
ms.openlocfilehash: 78aef20a322ad3743ed1cb89955654456dff670e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591453"
---
# <a name="exec-task"></a>Exec — Zadanie
Uruchamia określony program lub polecenie przy użyciu określonych argumentów.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `Exec`.

|Parametr|Opis|
|---------------|-----------------|
|`Command`|Wymagany `String` parametr.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak attrib lub wykonywalny, takie jak *program exe*, *runprogram. bat*lub *Setup. msi*.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wiele poleceń w pliku wsadowym i uruchomić je za pomocą tego parametru.|
|`ConsoleOutput`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Każdy element wyjściowy jest wierszem ze standardowego wyjścia lub standardowego strumienia błędów emitowanego przez narzędzie. Ta wartość jest przechwytywana tylko wtedy, gdy `ConsoleToMsBuild` jest ustawiona na `true`.|
|`ConsoleToMsBuild`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie spowoduje przechwycenie standardowego błędu i standardowego wyjścia narzędzia i udostępnienie ich w parametrze danych wyjściowych `ConsoleOutput`.<br /><br />Wartość domyślna: `false`.|
|`CustomErrorRegularExpression`|Opcjonalny parametr `String`.<br /><br /> Określa wyrażenie regularne, które jest używane do określania wierszy błędów w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.<br /><br />Wartość domyślna: `null` (bez przetwarzania niestandardowego).|
|`CustomWarningRegularExpression`|Opcjonalny parametr `String`.<br /><br /> Określa wyrażenie regularne, które jest używane do wyświetlania wierszy ostrzeżeń w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.<br /><br />Wartość domyślna: `null` (bez przetwarzania niestandardowego).|
|`EchoOff`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie nie będzie emitować rozwiniętej formy `Command` do dziennika MSBuild.<br /><br />Wartość domyślna: `false`.|
|`ExitCode`|Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie.|
|`IgnoreExitCode`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, zadanie zignoruje kod zakończenia, który jest dostarczany przez wykonane polecenie. W przeciwnym razie zadanie zwraca `false`, jeśli wykonane polecenie zwróci niezerowy kod zakończenia.<br /><br />Wartość domyślna: `false`.|
|`IgnoreStandardErrorWarningFormat`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `false`, program wybierze wiersze w danych wyjściowych, które pasują do standardowego formatu błędu/ostrzeżenia, i rejestruje je jako błędy/ostrzeżenia. Jeśli `true`, należy wyłączyć to zachowanie.<br /><br />Wartość domyślna: `false`.|
|`Outputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera elementy wyjściowe zadania. Zadanie `Exec` nie ustawia tych samych wartości. Zamiast tego można je określić tak, jakby je ustawił, tak aby mogły być używane później w projekcie.|
|`StdErrEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie strumienia błędów standardowego przechwyconego zadania. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|
|`StdOutEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie przechwyconego strumienia wyjściowego zadania standardowego. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|
|`WorkingDirectory`|Opcjonalny parametr `String`.<br /><br /> Określa katalog, w którym zostanie uruchomione polecenie.<br /><br />Domyślnie: bieżący katalog roboczy projektu.|

## <a name="remarks"></a>Uwagi
To zadanie jest przydatne, gdy określone zadanie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dla zadania, które chcesz wykonać, jest niedostępne. Jednak zadanie `Exec`, w przeciwieństwie do bardziej określonego zadania, nie może wykonać dodatkowych operacji przetwarzania ani wykonywania warunkowego na podstawie wyniku uruchomionego narzędzia lub polecenia.

Zadanie `Exec` wywołuje *cmd. exe* , zamiast bezpośrednio wywołujący proces.

Oprócz parametrów wymienionych w tym dokumencie, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.ToolTask>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład używa zadania `Exec`, aby uruchomić polecenie.

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
