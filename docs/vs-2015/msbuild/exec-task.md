---
title: Exec — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a69fc64c3371a2970c03ec0129d4c733f5ae9cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201754"
---
# <a name="exec-task"></a>Exec — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uruchamia określony program lub polecenie przy użyciu określonych argumentów.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Exec` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Command`|Wymagany parametr interfejsu `String`.<br /><br /> Polecenia do uruchomienia. Mogą to być polecenia systemowe, takie jak attrib lub wykonywalny, takie jak program.exe, runprogram.bat lub setup.msi.<br /><br /> Ten parametr może zawierać wiele wierszy poleceń. Alternatywnie można umieścić wiele poleceń w pliku wsadowym i uruchomić je za pomocą tego parametru.|  
|`CustomErrorRegularExpression`|Opcjonalny `String` parametr.<br /><br /> Określa wyrażenie regularne, które jest używane do określania wierszy błędów w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.|  
|`CustomWarningRegularExpression`|Opcjonalny `String` parametr.<br /><br /> Określa wyrażenie regularne, które jest używane do wyświetlania wierszy ostrzeżeń w danych wyjściowych narzędzia. Jest to przydatne w przypadku narzędzi generujących nietypowo sformatowane dane wyjściowe.|  
|`ExitCode`|Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia, który jest dostarczany przez wykonane polecenie.|  
|`IgnoreExitCode`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zadanie zignoruje kod zakończenia, który jest dostarczany przez wykonane polecenie. W przeciwnym razie zadanie zwraca wartość, `false` Jeśli wykonane polecenie zwróci niezerowy kod zakończenia.|  
|`IgnoreStandardErrorWarningFormat`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `false` program wybierze wiersze w danych wyjściowych, które pasują do standardowego formatu błędu/ostrzeżenia, i rejestruje je jako błędy/ostrzeżenia. Jeśli `true` to zachowanie jest wyłączone.|  
|`Outputs`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy wyjściowe zadania. `Exec`Zadanie nie ustawia tych samych wartości. Zamiast tego można je określić tak, jakby je ustawił, tak aby mogły być używane później w projekcie.|  
|`StdErrEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie strumienia błędów standardowego przechwyconego zadania. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|  
|`StdOutEncoding`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa kodowanie przechwyconego strumienia wyjściowego zadania standardowego. Wartość domyślna to bieżące kodowanie danych wyjściowych konsoli.|  
|`WorkingDirectory`|Opcjonalny `String` parametr.<br /><br /> Określa katalog, w którym zostanie uruchomione polecenie.|  
  
## <a name="remarks"></a>Uwagi  
 To zadanie jest przydatne, gdy określone [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadanie dla zadania, które chcesz wykonać, jest niedostępne. Jednak `Exec` zadanie, w przeciwieństwie do bardziej konkretnego zadania, nie umożliwia zebrania danych wyjściowych z narzędzia lub polecenia, które jest uruchamiane.  
  
 `Exec`Zadanie wywołuje cmd.exe, zamiast bezpośrednio wywołując proces.  
  
 Oprócz parametrów wymienionych w tym dokumencie, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Exec` zadania do uruchomienia polecenia.  
  
```  
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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
