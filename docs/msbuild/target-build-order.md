---
title: Docelowy porządek kompilacji | Microsoft Docs
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607584b4b41bdfde224bdb35d30eec1c6c8a4197
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585460"
---
# <a name="target-build-order"></a>Docelowy porządek kompilacji

Elementy docelowe muszą być uporządkowane, jeśli dane wejściowe do jednego obiektu docelowego są zależne od danych wyjściowych innego obiektu docelowego. Można użyć tych atrybutów do określenia kolejności, w której są uruchamiane obiekty docelowe:

- `InitialTargets`. Ten `Project` atrybutu określa elementy docelowe, które będą uruchamiane jako pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w atrybucie `DefaultTargets`.

- `DefaultTargets`. Ten atrybut `Project` określa, które obiekty docelowe są uruchamiane, jeśli element docelowy nie zostanie określony jawnie w wierszu polecenia.

- `DependsOnTargets`. Ten atrybut `Target` określa elementy docelowe, które muszą zostać uruchomione, aby można było uruchomić ten element docelowy.

- `BeforeTargets` i `AfterTargets`. Te atrybuty `Target` określają, że ten element docelowy powinien zostać uruchomiony przed lub po określonych obiektach docelowych (MSBuild 4,0).

Element docelowy nigdy nie jest uruchamiany dwukrotnie podczas kompilacji, nawet jeśli kolejny element docelowy w kompilacji zależy od niej. Po uruchomieniu elementu docelowego jego udział w kompilacji jest zakończony.

Elementy docelowe mogą mieć atrybut `Condition`. Jeśli określony warunek oblicza `false`, element docelowy nie zostanie wykonany i nie ma wpływu na kompilację. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Początkowe elementy docelowe

Atrybut `InitialTargets` elementu [projektu](../msbuild/project-element-msbuild.md) określa elementy docelowe, które będą uruchamiane jako pierwsze, nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w atrybucie `DefaultTargets`. Początkowe cele są zwykle używane do sprawdzania błędów.

Wartością atrybutu `InitialTargets` może być rozdzielana średnikami lista elementów docelowych. W poniższym przykładzie określono, że element docelowy `Warm` jest uruchomiony, a następnie zostanie uruchomiony `Eject` docelowy.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importowane projekty mogą mieć własne atrybuty `InitialTargets`. Wszystkie początkowe elementy docelowe są agregowane i uruchamiane w kolejności.

Aby uzyskać więcej informacji, zobacz [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Domyślne elementy docelowe

Atrybut `DefaultTargets` elementu [projektu](../msbuild/project-element-msbuild.md) określa, które elementy docelowe lub docelowe są kompilowane, jeśli element docelowy nie został jawnie określony w wierszu polecenia.

Wartość atrybutu `DefaultTargets` może być rozdzielana średnikami, uporządkowaną listą domyślnych elementów docelowych. W poniższym przykładzie określono, że element docelowy `Clean` jest uruchomiony, a następnie zostanie uruchomiony `Build` docelowy.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Można zastąpić domyślne obiekty docelowe przy użyciu przełącznika **-Target** w wierszu polecenia. W poniższym przykładzie określono, że element docelowy `Build` jest uruchomiony, a następnie zostanie uruchomiony `Report` docelowy. Gdy określisz elementy docelowe w ten sposób, wszystkie domyślne elementy docelowe zostaną zignorowane.

 `msbuild -target:Build;Report`

Jeśli określono zarówno początkowe elementy docelowe, jak i domyślne elementy docelowe, a jeśli nie określono elementów docelowych wiersza polecenia, program MSBuild najpierw uruchamia początkowe elementy docelowe, a następnie uruchamia domyślne elementy docelowe.

Importowane projekty mogą mieć własne atrybuty `DefaultTargets`. Napotkano pierwszy `DefaultTargets` atrybutu określający, które domyślne elementy docelowe zostaną uruchomione.

Aby uzyskać więcej informacji, zobacz [How to: Określ, który element docelowy należy skompilować jako pierwszy](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>Pierwszy element docelowy

Jeśli nie ma początkowych elementów docelowych, domyślnych obiektów docelowych lub obiektów docelowych wiersza polecenia, program MSBuild uruchamia pierwszy element docelowy napotkany w pliku projektu lub zaimportowanych plikach projektu.

## <a name="target-dependencies"></a>Zależności docelowe

Obiekty docelowe mogą opisywać relacje zależności ze sobą. Atrybut `DependsOnTargets` wskazuje, że element docelowy zależy od innych elementów docelowych. Na przykład

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

informuje program MSBuild, że element docelowy `Serve` zależy od elementu docelowego `Chop` i elementu docelowego `Cook`. Program MSBuild uruchamia `Chop` miejsce docelowe, a następnie uruchamia `Cook` docelowy przed uruchomieniem `Serve` celu.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets i AfterTargets

W programie MSBuild 4,0 można określić kolejność obiektów docelowych przy użyciu atrybutów `BeforeTargets` i `AfterTargets`.

Rozważmy następujący skrypt.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

Aby utworzyć pośredni `Optimize` docelowy, który jest uruchamiany po elemencie docelowym `Compile`, ale przed obiektem docelowym `Link`, Dodaj następujący element docelowy gdziekolwiek w elemencie `Project`.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Określ kolejność kompilacji docelowej

Program MSBuild określa docelowy porządek kompilacji w następujący sposób:

1. są uruchamiane `InitialTargets` obiektów docelowych.

2. Elementy docelowe określone w wierszu polecenia przez przełącznik **-Target** są uruchamiane. Jeśli w wierszu polecenia nie określono żadnych elementów docelowych, zostaną uruchomione `DefaultTargets` obiekty docelowe. Jeśli żaden z nich nie jest obecny, zostanie uruchomiony pierwszy element docelowy.

3. Atrybut `Condition` elementu docelowego jest oceniany. Jeśli atrybut `Condition` jest obecny i szacuje `false`, element docelowy nie zostanie wykonany i nie ma żadnego wpływu na kompilację.

   Inne elementy docelowe, które wystawiają warunkowe miejsce docelowe w `BeforeTargets` lub `AfterTargets` nadal wykonywane w określonej kolejności.

4. Przed wykonaniem lub pominięciem elementu docelowego `DependsOnTargets` są uruchamiane, chyba że atrybut `Condition` zostanie zastosowany do obiektu docelowego i zostanie oszacowany `false`.

   > [!NOTE]
   > Element docelowy jest uznawany za pominięty, jeśli nie zostanie wykonany, ponieważ jego elementy wyjściowe są aktualne (zobacz [kompilacja przyrostowa](../msbuild/incremental-builds.md)). To sprawdzenie jest wykonywane tuż przed wykonaniem zadań wewnątrz elementu docelowego i nie ma wpływu na kolejność wykonywania elementów docelowych.

5. Przed wykonaniem lub pominięciem elementu docelowego, należy uruchomić wszystkie inne elementy docelowe, które wyświetlają element docelowy w atrybucie `BeforeTargets`.

6. Przed wykonaniem elementu docelowego jego atrybut `Inputs` i atrybut `Outputs` są porównywane. Jeśli program MSBuild ustali, że wszystkie pliki wyjściowe są nieaktualne w odniesieniu do odpowiedniego pliku lub plików wejściowych, MSBuild wykonuje miejsce docelowe. W przeciwnym razie program MSBuild pomija element docelowy.

7. Po wykonaniu lub pominięciu elementu docelowego można uruchomić wszystkie inne elementy docelowe, które wyświetlają ją w atrybucie `AfterTargets`.

## <a name="see-also"></a>Zobacz także

- [Docelowe elementy](../msbuild/msbuild-targets.md)
