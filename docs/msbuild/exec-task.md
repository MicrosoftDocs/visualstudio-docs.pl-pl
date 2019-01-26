---
title: Exec — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 481f752bdefcc35af594029e90162173df66d90c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969931"
---
# <a name="exec-task"></a>Exec — Zadanie
Uruchamia określony program lub polecenie przy użyciu określonych argumentów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Exec` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Command`|Wymagane `String` parametru.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak atrybuty lub plik wykonywalny, taki jak *program.exe*, *runprogram.bat*, lub *setup.msi*.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wiele poleceń w pliku wsadowym i uruchom go przy użyciu tego parametru.|  
|`ConsoleOutput`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Każdy element danych wyjściowych jest wiersz ze standardowego strumienia wyjściowego lub błędzie standardowym wyemitowany przez narzędzie. Jest to przechwytywana tylko wtedy, gdy `ConsoleToMsBuild` ustawiono `true`.|
|`ConsoleToMsBuild`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie zostanie przechwycony błąd standardowy i standardowe dane wyjściowe narzędzia i udostępnij je w `ConsoleOutput` parametr wyjściowy.<br /><br />Wartość domyślna: `false`.|  
|`CustomErrorRegularExpression`|Opcjonalnie `String` parametru.<br /><br /> Określa wyrażenie regularne, który jest używany wierszom dodatkowy błąd w danych wyjściowych narzędzia. Jest to przydatne dla narzędzi, które generują niezwykle sformatowane wyniki.<br /><br />Wartość domyślna: `null` (nie niestandardowe przetwarzanie).|  
|`CustomWarningRegularExpression`|Opcjonalnie `String` parametru.<br /><br /> Określa wyrażenie regularne, który służy do dodatkowych wierszy ostrzeżenie w danych wyjściowych narzędzia. Jest to przydatne dla narzędzi, które generują niezwykle sformatowane wyniki.<br /><br />Wartość domyślna: `null` (nie niestandardowe przetwarzanie).|  
|`EchoOff`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie nie zostanie wyemitowany przez rozszerzonej postaci `Command` dziennik programu MSBuild.<br /><br />Wartość domyślna: `false`.|
|`ExitCode`|Opcjonalnie `Int32` parametr tylko do odczytu danych wyjściowych.<br /><br /> Określa kod zakończenia, dostarczone przez wykonanego polecenia.|  
|`IgnoreExitCode`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie ignoruje kod zakończenia, dostarczone przez wykonanego polecenia. W przeciwnym razie zwraca zadanie `false` Jeśli wykonanego polecenia zwróci kod zakończenia różny od zera.<br /><br />Wartość domyślna: `false`.|  
|`IgnoreStandardErrorWarningFormat`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `false`, wybiera wiersze w danych wyjściowych, który jest zgodny z formatem standardowy błąd/ostrzeżenie i rejestruje je jako błędy i ostrzeżenia. Jeśli `true`, wyłączyć to zachowanie.<br /><br />Wartość domyślna: `false`.|  
|`Outputs`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy danych wyjściowych z zadania. `Exec` Zadanie nie powoduje ustawienia te sam. Zamiast tego możesz podać je tak, jakby ona ustawiona, dzięki czemu mogą być używane w dalszej części projektu.|  
|`StdErrEncoding`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa kodowanie przechwyconych zadań Standardowy strumień błędów. Ustawieniem domyślnym jest bieżący konsoli danych wyjściowych kodowania.|  
|`StdOutEncoding`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa kodowanie przechwyconych zadań standardowego strumienia wyjściowego. Ustawieniem domyślnym jest bieżący konsoli danych wyjściowych kodowania.|  
|`WorkingDirectory`|Opcjonalnie `String` parametru.<br /><br /> Określa katalog, w którym będą uruchamiane polecenie.<br /><br />Wartość domyślna: Bieżący katalog roboczy projektu|  
  
## <a name="remarks"></a>Uwagi  
 To zadanie jest przydatne, gdy określony [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zadań dla zadania, które mają być wykonywane jest niedostępny. Jednak `Exec` zadania, w przeciwieństwie do bardziej szczegółowe zadania, nie można wykonać dodatkowego przetwarzania i operacje warunkowe na podstawie wyniku narzędzia lub polecenia, w którym działa.
  
 `Exec` Zadań wywołania *cmd.exe* zamiast bezpośrednie wywołanie procesu.  
  
 Oprócz parametrów wymienionych w niniejszym dokumencie, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Exec` zadania do uruchomienia polecenia.  
  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
