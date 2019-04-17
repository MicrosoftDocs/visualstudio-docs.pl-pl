---
title: Copy — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 805a8d6616b4f6c198173ad2a9c9d733ad50de32
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648710"
---
# <a name="copy-task"></a>Copy — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kopiowanie plików do nowej lokalizacji w systemie plików.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Copy` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CopiedFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały pomyślnie skopiowane.|  
|`DestinationFiles`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa listę plików, do których należy skopiować pliki źródłowe. Ta lista powinna być zmapowana jeden-do-jednego na listę określoną w parametrze `SourceFiles`. Oznacza to, że pierwszy plik określony w parametrze `SourceFiles` będzie kopiowany do pierwszej lokalizacji określonej w parametrze `DestinationFiles` itd.|  
|`DestinationFolder`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa katalog, do którego pliki mają zostać skopiowane. Musi to być katalog, a nie plik. Jeśli katalog nie istnieje, zostanie utworzony automatycznie.|  
|`OverwriteReadOnlyFiles`|Opcjonalnie `Boolean` parametru.<br /><br /> Zastępowanie plików następuje nawet wtedy, gdy są oznaczone jako tylko do odczytu.|  
|`Retries`|Opcjonalnie `Int32` parametru.<br /><br /> Określa, ile razy należy podjąć próbę kopiowania, jeśli wszystkie poprzednie próby się nie powiodły. Domyślnie przyjmuje wartość zero.<br /><br /> **Uwaga:** Stosowanie ponownych prób może maskować problem z synchronizacją w procesie kompilacji.|  
|`RetryDelayMilliseconds`|Opcjonalnie `Int32` parametru.<br /><br /> Określa opóźnienie między kolejnymi niezbędnymi ponownymi próbami. Wartością domyślną jest wartość argumentu RetryDelayMillisecondsDefault, który jest przekazywany do konstruktora CopyTask.|  
|`SkipUnchangedFiles`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ma wartość `true`, następuje pomijanie kopiowania plików, które są niezmienione między lokalizacjami źródłowymi i docelowymi. Zadanie `Copy` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji. **Uwaga:**  Jeśli w parametrze zostanie ustawiona wartość `true`, nie należy stosować analizy zależności do miejsca docelowego, ponieważ zadanie zostałoby wykonane tylko wtedy, gdy czasy ostatniej modyfikacji plików źródłowych są nowsze niż czasy ostatniej modyfikacji plików docelowych.|  
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do skopiowania.|  
|`UseHardlinksIfPossible`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ma wartość `true`, będą tworzone twarde łącza do kopiowanych plików zamiast kopiowania plików.|  
  
## <a name="warnings"></a>Ostrzeżenia  
 Ostrzeżenia są rejestrowane, w tym:  
  
-   `Copy.DestinationIsDirectory`  
  
-   `Copy.SourceIsDirectory`  
  
-   `Copy.SourceFileNotFound`  
  
-   `Copy.CreatesDirectory`  
  
-   `Copy.HardLinkComment`  
  
-   `Copy.RetryingAsFileCopy`  
  
-   `Copy.FileComment`  
  
-   `Copy.RemovingReadOnlyAttribute`  
  
## <a name="remarks"></a>Uwagi  
 Musi być określony parametr `DestinationFolder` lub `DestinationFiles`, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie następuje skopiowanie elementów z kolekcji elementów `MySourceFiles` do folderu c:\MyProject\Destination.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFolder="c:\MyProject\Destination"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje, jak wykonać kopiowanie cykliczne. Wszystkie pliki zostaną skopiowane cyklicznie z folderu c:\MySourceTree do folderu c:\MyDestinationTree przy zachowaniu struktury katalogów.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"  
        />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
