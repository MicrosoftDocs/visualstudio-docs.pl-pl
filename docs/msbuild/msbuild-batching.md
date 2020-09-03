---
title: Tworzenie wsadowe MSBuild | Microsoft Docs
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d7c72d1da270220144cd5e6167ebecb66462ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85289277"
---
# <a name="msbuild-batching"></a>Przetwarzanie wsadowe w programie MSBuild

Program MSBuild dzieli listy elementów na różne kategorie lub partie na podstawie metadanych elementów, a następnie uruchamia obiekt docelowy lub zadanie jednokrotnie przy każdej partii.

## <a name="task-batching"></a>Tworzenie partii zadań

Tworzenie wsadowe zadań pozwala uprościć pliki projektu, zapewniając sposób dzielenia list elementów na różne partie i przekazywanie poszczególnych partii do zadania oddzielnie. Oznacza to, że plik projektu musi mieć tylko jedno zadanie i jego atrybuty, nawet jeśli można wykonać kilka razy.

Należy określić, że program MSBuild ma wykonywać przetwarzanie wsadowe za pomocą zadania przy użyciu `%(ItemMetaDataName)` notacji w jednym z atrybutów zadania. Poniższy przykład dzieli `Example` listę elementów na partie na podstawie `Color` wartości metadanych elementu i przekazuje poszczególne partie do `MyTask` zadania oddzielnie.

> [!NOTE]
> Jeśli nie odwołujesz się do listy elementów w innym miejscu atrybutów zadania lub nazwa metadanych może być niejednoznaczna, można użyć notacji%(<obiekt ItemCollection. ItemMetaDataName>), aby w pełni zakwalifikować wartość metadanych elementu do użycia na potrzeby przetwarzania wsadowego.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Aby zapoznać się z bardziej szczegółowymi przykładami wsadowymi, zobacz [metadane elementu w partii zadań](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Przetwarzanie wsadowe docelowe

Program MSBuild sprawdza, czy dane wejściowe i wyjściowe elementu docelowego są aktualne przed uruchomieniem obiektu docelowego. Jeśli oba dane wejściowe i wyjściowe są aktualne, element docelowy jest pomijany. Jeśli zadanie wewnątrz elementu docelowego używa operacji wsadowych, program MSBuild musi określić, czy dane wejściowe i wyjściowe dla każdej partii elementów są aktualne. W przeciwnym razie obiekt docelowy jest wykonywany za każdym razem, gdy zostanie trafiony.

Poniższy przykład pokazuje `Target` element, który zawiera `Outputs` atrybut z `%(ItemMetadataName)` notacją. Program MSBuild będzie dzielić `Example` listę elementów na partie na podstawie `Color` metadanych elementów i analizować sygnatury czasowe plików wyjściowych dla każdej partii. Jeśli dane wyjściowe z partii nie są aktualne, obiekt docelowy jest uruchamiany. W przeciwnym razie element docelowy zostanie pominięty.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Aby uzyskać inny przykład tworzenia wsadowych obiektów docelowych, zobacz [metadane elementu w przetwarzaniu wsadowym](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Mutacje elementów i właściwości

W tej sekcji opisano, jak zrozumieć skutki zmiany właściwości i/lub metadanych elementu przy użyciu docelowego wsadowego tworzenia lub przetwarzania wsadowego zadań.

Ponieważ tworzenie wsadowe obiektów docelowych i wsadowe zadania są dwiema różnymi operacjami MSBuild, ważne jest, aby dokładnie zrozumieć, która z nich korzysta w przypadku tworzenia wsadowych pakietów MSBuild. Gdy składnia wsadowa `%(ItemMetadataName)` pojawia się w zadaniu w obiekcie docelowym, ale nie w atrybucie obiektu docelowego, MSBuild używa zadania wsadowego. Jedynym sposobem określenia docelowej partii jest użycie składni wsadowej na atrybucie docelowym, zazwyczaj `Outputs` atrybutu.

W przypadku tworzenia wsadowych grup docelowych i wsadowych zadań partie mogą być traktowane jako uruchamiane niezależnie. Wszystkie partie zaczynają się od kopii tego samego stanu początkowego wartości metadanych właściwości i elementu. Wszelkie mutacje wartości właściwości podczas wykonywania wsadowego nie są widoczne dla innych partii. Rozpatrzmy następujący przykład:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

Dane wyjściowe są następujące:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

`ItemGroup`Obiekt w obiekcie docelowym jest niejawnie zadaniem i z `%(Color)` w `Condition` atrybucie, wykonywane jest wykonywanie zadań wsadowych. Istnieją dwie partie: jeden dla czerwieni i drugi dla niebieski. Właściwość `%(NeededColorChange)` jest ustawiana tylko wtedy `%(Color)` , gdy metadane są niebieskie i ustawienie ma wpływ tylko na poszczególne elementy, które pasują do warunku, gdy została uruchomiona niebieska Partia zadań. `Message`Atrybut zadania nie `Text` wyzwala tworzenia wsadowego, pomimo `%(ItemMetadataName)` składni, ponieważ jest używany wewnątrz przekształcenia elementu.

Partie działają niezależnie, ale nie równolegle. Powoduje to różnicę podczas uzyskiwania dostępu do wartości metadanych, które zmieniają się w wykonaniu wsadowym. W przypadku ustawienia właściwości na podstawie niektórych metadanych w wykonaniu wsadowym, właściwość przyjmuje *ostatnią* wartość zestawu:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Po wykonaniu wsadowym Właściwość zachowuje końcową wartość `%(MetadataValue)` .

Mimo że partie są uruchamiane niezależnie, ważne jest, aby uwzględnić różnicę między docelowym przetwarzaniem wsadowym a przetwarzaniem wsadowym zadań i wiedzieć, który typ ma zastosowanie do danej sytuacji. Rozważmy następujący przykład, aby zrozumieć lepsze znaczenie tego rozróżnienia.

Zadania mogą być niejawne, a nie jawne, co może być mylące w przypadku wystąpienia zadań wsadowych z niejawnymi zadaniami. Gdy `PropertyGroup` element or `ItemGroup` występuje w `Target` , każda Deklaracja właściwości w grupie jest niejawnie traktowana jak oddzielne zadanie [Właściwości](createproperty-task.md) lub [elementu](createitem-task.md) . Oznacza to, że zachowanie jest inne, gdy element docelowy jest przetwarzany wsadowo, a w przypadku, gdy obiekt docelowy nie jest wsadowy (to znaczy, gdy nie ma `%(ItemMetadataName)` składni w `Outputs` atrybucie). Gdy element docelowy jest przetwarzany wsadowo, jest `ItemGroup` wykonywany raz na miejsce docelowe, ale jeśli obiekt docelowy nie zostanie wsadem wsadowym, niejawne odpowiedniki `CreateItem` lub `CreateProperty` zadania są wsadowe przy użyciu wsadowych zadań, więc element docelowy jest wykonywany tylko raz, a każdy element lub Każda właściwość w grupie jest przetwarzana osobno przy użyciu wsadowego wykonywania zadań.

Poniższy przykład ilustruje docelowe przetwarzanie wsadowe i tworzenie wsadowe zadań w przypadku, gdy metadane są mutacjowo. Rozważ sytuację, w której masz foldery A i B z niektórymi plikami:

```
A\1.stub
B\2.stub
B\3.stub
```

Teraz spójrzmy na dane wyjściowe tych dwóch podobnych projektów.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Dane wyjściowe są następujące:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Teraz Usuń `Outputs` atrybut, który określa docelowe przetwarzanie wsadowe.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

Dane wyjściowe są następujące:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Należy zauważyć, że nagłówek `Test1` jest drukowany tylko raz, ale w poprzednim przykładzie został wydrukowany dwa razy. Oznacza to, że element docelowy nie jest wsadowy.  W związku z tym dane wyjściowe są inaczej różne.

Przyczyną jest to, że w przypadku korzystania z wsadowego określania wartości docelowej każda partia docelowa wykonuje wszystko w obiekcie docelowym z własną niezależną kopią wszystkich właściwości i elementów, ale po pominięciu tego `Outputs` atrybutu poszczególne wiersze w grupie właściwości są traktowane jako osobne, potencjalnie przetwarzane zadania wsadowe. W tym przypadku `ComponentDir` zadanie jest wsadowe (używa `%(ItemMetadataName)` składni), więc przez czas wykonywania `ComponentName` wiersza, obie partie `ComponentDir` wiersza zostały zakończone, a drugi, który uruchomił, określa wartość, jak pokazano w drugim wierszu.

## <a name="property-functions-using-metadata"></a>Funkcje właściwości korzystające z metadanych

Przetwarzanie wsadowe może być kontrolowane przez funkcje właściwości, które obejmują metadane. Przykład:

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

używa <xref:System.IO.Path.Combine%2A> do łączenia ścieżki folderu głównego z ścieżką elementu kompilacji.

Funkcje właściwości mogą nie występować w obrębie wartości metadanych. Przykład:

`%(Compile.FullPath.Substring(0,3))`

nie jest dozwolone.

Aby uzyskać więcej informacji na temat funkcji właściwości, zobacz [funkcje właściwości](../msbuild/property-functions.md).

## <a name="see-also"></a>Zobacz też

- [ItemMetadata —, element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
