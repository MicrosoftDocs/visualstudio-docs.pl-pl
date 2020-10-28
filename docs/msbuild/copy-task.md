---
title: Kopiuj zadanie | Microsoft Docs
description: Dowiedz się, jak skopiować pliki do nowego pliku lub lokalizacji folderu w systemie plików przy użyciu zadania Copy programu MSBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 00544b6d1e797a1fd8a7a197197480cae5620f10
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796230"
---
# <a name="copy-task"></a>Copy — Zadanie

Kopiowanie plików do nowej lokalizacji w systemie plików.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Copy` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`CopiedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera elementy, które zostały pomyślnie skopiowane, w *tym* te, które nie zostały faktycznie skopiowane, ale zostały pominięte, ponieważ były już aktualne i `SkipUnchangedFiles` były `true` .|
|`DestinationFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa listę plików, do których należy skopiować pliki źródłowe. Ta lista powinna być zmapowana jeden-do-jednego na listę określoną w parametrze `SourceFiles`. Oznacza to, że pierwszy plik określony w parametrze `SourceFiles` będzie kopiowany do pierwszej lokalizacji określonej w parametrze `DestinationFiles` itd.|
|`DestinationFolder`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa katalog, do którego pliki mają zostać skopiowane. Musi to być katalog, a nie plik. Jeśli katalog nie istnieje, zostanie utworzony automatycznie.|
|`OverwriteReadOnlyFiles`|Opcjonalny `Boolean` parametr.<br /><br /> Zastępowanie plików następuje nawet wtedy, gdy są oznaczone jako tylko do odczytu.|
|`Retries`|Opcjonalny `Int32` parametr.<br /><br /> Określa, ile razy należy podjąć próbę kopiowania, jeśli wszystkie poprzednie próby się nie powiodły. Domyślnie przyjmuje wartość zero.<br /><br /> **Przestroga:** Użycie ponownych prób może maskować problem z synchronizacją w procesie kompilacji.<br /><br /> **Uwaga:** Gdy domyślne *zadanie* to zero ponownych prób, użycie zadania często przebiega, `$(CopyRetryCount)` co jest domyślnie niezerowe.|
|`RetryDelayMilliseconds`|Opcjonalny `Int32` parametr.<br /><br /> Określa opóźnienie między kolejnymi niezbędnymi ponownymi próbami. Wartością domyślną jest wartość argumentu RetryDelayMillisecondsDefault, który jest przekazywany do konstruktora CopyTask.|
|`SkipUnchangedFiles`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ma wartość `true`, następuje pomijanie kopiowania plików, które są niezmienione między lokalizacjami źródłowymi i docelowymi. Zadanie `Copy` uznaje pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam czas ostatniej modyfikacji. <br /><br /> **Uwaga:**  Jeśli ustawisz ten parametr na `true` , nie należy używać analizy zależności na elemencie docelowym zawierającym, ponieważ to zadanie działa tylko wtedy, gdy czas ostatniej modyfikacji plików źródłowych jest nowszy niż czas ostatniej modyfikacji plików docelowych.|
|`SourceFiles`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki do skopiowania.|
|`UseHardlinksIfPossible`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli ma wartość `true`, będą tworzone twarde łącza do kopiowanych plików zamiast kopiowania plików.|

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

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example-1"></a>Przykład 1

Poniższy przykład kopiuje elementy z `MySourceFiles` kolekcji Item do folderu *c:\MyProject\Destination* .

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

## <a name="example-2"></a>Przykład 2

Poniższy przykład ilustruje, jak wykonać kopiowanie cykliczne. Ten projekt kopiuje wszystkie pliki cyklicznie z *c:\MySourceTree* do *c:\MyDestinationTree* przy zachowaniu struktury katalogów.

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
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
