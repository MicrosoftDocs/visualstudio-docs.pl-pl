---
title: Copy — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba0e7e85f4367c775c8b9185c6c2684b728cc4d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943905"
---
# <a name="copy-task"></a>Copy — Zadanie
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
|`SkipUnchangedFiles`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli ma wartość `true`, następuje pomijanie kopiowania plików, które są niezmienione między lokalizacjami źródłowymi i docelowymi. Zadanie `Copy` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji. <br /><br /> **Uwaga:**  Jeśli w parametrze zostanie ustawiona wartość `true`, nie należy stosować analizy zależności do miejsca docelowego, ponieważ zadanie zostałoby wykonane tylko wtedy, gdy czasy ostatniej modyfikacji plików źródłowych są nowsze niż czasy ostatniej modyfikacji plików docelowych.|  
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
 Poniższy przykładowy kod kopiuje elementy w `MySourceFiles` elementu kolekcji do folderu *c:\MyProject\Destination*.  
  
```xml  
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
 Poniższy przykład ilustruje, jak wykonać kopiowanie cykliczne. Ten projekt kopiuje wszystkie rekursywnie pliki z *c:\MySourceTree* do *c:\MyDestinationTree*, przy zachowaniu struktury katalogów.  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)