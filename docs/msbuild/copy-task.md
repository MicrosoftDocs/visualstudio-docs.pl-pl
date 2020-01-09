---
title: Kopiuj zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bed57982fb177a49ed89bbe601d753fe155aba22
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596089"
---
# <a name="copy-task"></a>Copy — Zadanie
Kopiowanie plików do nowej lokalizacji w systemie plików.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `Copy`.

|Parametr|Opis|
|---------------|-----------------|
|`CopiedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały pomyślnie skopiowane.|
|`DestinationFiles`|Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa listę plików, do których należy skopiować pliki źródłowe. Ta lista powinna być zmapowana jeden-do-jednego na listę określoną w parametrze `SourceFiles`. Oznacza to, że pierwszy plik określony w parametrze `SourceFiles` będzie kopiowany do pierwszej lokalizacji określonej w parametrze `DestinationFiles` itd.|
|`DestinationFolder`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa katalog, do którego pliki mają zostać skopiowane. Musi to być katalog, a nie plik. Jeśli katalog nie istnieje, zostanie utworzony automatycznie.|
|`OverwriteReadOnlyFiles`|Opcjonalny parametr `Boolean`.<br /><br /> Zastępowanie plików następuje nawet wtedy, gdy są oznaczone jako tylko do odczytu.|
|`Retries`|Opcjonalny parametr `Int32`.<br /><br /> Określa, ile razy należy podjąć próbę kopiowania, jeśli wszystkie poprzednie próby się nie powiodły. Domyślnie przyjmuje wartość zero.<br /><br /> **Uwaga:** Użycie ponownych prób może maskować problem z synchronizacją w procesie kompilacji.|
|`RetryDelayMilliseconds`|Opcjonalny parametr `Int32`.<br /><br /> Określa opóźnienie między kolejnymi niezbędnymi ponownymi próbami. Wartością domyślną jest wartość argumentu RetryDelayMillisecondsDefault, który jest przekazywany do konstruktora CopyTask.|
|`SkipUnchangedFiles`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ma wartość `true`, następuje pomijanie kopiowania plików, które są niezmienione między lokalizacjami źródłowymi i docelowymi. Zadanie `Copy` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji. <br /><br /> **Uwaga:**  Jeśli ustawisz ten parametr na `true`, nie należy używać analizy zależności na elemencie docelowym zawierającym, ponieważ to zadanie działa tylko wtedy, gdy czas ostatniej modyfikacji plików źródłowych jest nowszy niż czas ostatniej modyfikacji plików docelowych.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do skopiowania.|
|`UseHardlinksIfPossible`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli ma wartość `true`, będą tworzone twarde łącza do kopiowanych plików zamiast kopiowania plików.|

## <a name="warnings"></a>Ostrzeżenia
Ostrzeżenia są rejestrowane, w tym:

- `Copy.DestinationIsDirectory`

- `Copy.SourceIsDirectory`

- `Copy.SourceFileNotFound`

- `Copy.CreatesDirectory`

- `Copy.HardLinkComment`

- `Copy.RetryingAsFileCopy`

- `Copy.FileComment`

- `Copy.RemovingReadOnlyAttribute`

## <a name="remarks"></a>Uwagi
Musi być określony parametr `DestinationFolder` lub `DestinationFiles`, ale nie oba. W razie podania obu parametrów zadanie nie powiedzie się i zostanie zarejestrowany błąd.

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład kopiuje elementy w kolekcji elementów `MySourceFiles` do folderu *c:\MyProject\Destination*.

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
Poniższy przykład ilustruje, jak wykonać kopiowanie cykliczne. Ten projekt kopiuje wszystkie pliki cyklicznie z *c:\MySourceTree* do *c:\MyDestinationTree*przy zachowaniu struktury katalogów.

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
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
