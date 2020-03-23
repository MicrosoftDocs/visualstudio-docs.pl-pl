---
title: Kolejność budowania celu docelowego | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585460"
---
# <a name="target-build-order"></a>Docelowa kolejność kompilacji

Obiekty docelowe muszą być uporządkowane, jeśli dane wejściowe do jednego obiektu docelowego zależy od danych wyjściowych innego obiektu docelowego. Za pomocą tych atrybutów można określić kolejność uruchamiania obiektów docelowych:

- `InitialTargets`. Ten `Project` atrybut określa obiekty docelowe, które będą uruchamiane jako pierwsze, `DefaultTargets` nawet jeśli obiekty docelowe są określone w wierszu polecenia lub w atrybucie.

- `DefaultTargets`. Ten `Project` atrybut określa, które obiekty docelowe są uruchamiane, jeśli obiekt docelowy nie jest wyraźnie określony w wierszu polecenia.

- `DependsOnTargets`. Ten `Target` atrybut określa obiekty docelowe, które muszą zostać uruchomione przed uruchomieniem tego obiektu docelowego.

- `BeforeTargets`i `AfterTargets`. Te `Target` atrybuty określają, że ten obiekt docelowy powinien być uruchamiany przed lub po określonych obiektach docelowych (MSBuild 4.0).

Cel nigdy nie jest uruchamiany dwa razy podczas kompilacji, nawet jeśli kolejny cel w kompilacji zależy od niego. Po uruchomieniu obiektu docelowego jego wkład w kompilację jest zakończony.

Obiekty docelowe `Condition` mogą mieć atrybut. Jeśli określony warunek ocenia `false`, cel nie jest wykonywany i nie ma wpływu na kompilacji. Aby uzyskać więcej informacji na temat warunków, zobacz [Warunki](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>Początkowe cele

Atrybut `InitialTargets` [Project](../msbuild/project-element-msbuild.md) element określa cele, które będą uruchamiane jako pierwsze, nawet jeśli `DefaultTargets` obiekty docelowe są określone w wierszu polecenia lub w atrybucie. Początkowe obiekty docelowe są zwykle używane do sprawdzania błędów.

Wartość atrybutu `InitialTargets` może być rozdzielona średnikami, uporządkowana lista obiektów docelowych. Poniższy przykład określa, `Warm` że obiekt docelowy jest uruchamiany, a następnie uruchamia obiekt docelowy. `Eject`

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Importowane projekty mogą `InitialTargets` mieć własne atrybuty. Wszystkie początkowe cele są agregowane razem i uruchamiane w kolejności.

Aby uzyskać więcej informacji, zobacz [Jak: Określanie celu docelowego, który ma być najpierw skompilowy](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Domyślne obiekty docelowe

Atrybut `DefaultTargets` [Project](../msbuild/project-element-msbuild.md) element określa, które obiekty docelowe lub obiekty docelowe są budowane, jeśli obiekt docelowy nie jest wyraźnie określony w wierszu polecenia.

Wartość atrybutu `DefaultTargets` może być rozdzielona średnikami, uporządkowana lista domyślnych obiektów docelowych. Poniższy przykład określa, `Clean` że obiekt docelowy jest uruchamiany, a następnie uruchamia obiekt docelowy. `Build`

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Domyślne obiekty docelowe można zastąpić za pomocą przełącznika **-target** w wierszu polecenia. Poniższy przykład określa, `Build` że obiekt docelowy jest uruchamiany, a następnie uruchamia obiekt docelowy. `Report` Po określeniu obiektów docelowych w ten sposób wszystkie domyślne obiekty docelowe są ignorowane.

 `msbuild -target:Build;Report`

Jeśli określono zarówno początkowe obiekty docelowe, jak i domyślne obiekty docelowe, a jeśli nie określono żadnych celów wiersza polecenia, msBuild najpierw uruchamia początkowe obiekty docelowe, a następnie uruchamia domyślne obiekty docelowe.

Importowane projekty mogą `DefaultTargets` mieć własne atrybuty. Pierwszy `DefaultTargets` napotkany atrybut określa, które domyślne obiekty docelowe zostaną uruchomione.

Aby uzyskać więcej informacji, zobacz [Jak: Określanie celu docelowego, który ma być najpierw skompilowy](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>Pierwszy cel

Jeśli nie ma żadnych początkowych obiektów docelowych, domyślnych obiektów docelowych lub celów wiersza polecenia, program MSBuild uruchamia pierwszy obiekt docelowy, który napotka w pliku projektu lub wszystkie importowane pliki projektu.

## <a name="target-dependencies"></a>Zależności docelowe

Obiekty docelowe można opisać relacje zależności ze sobą. Atrybut `DependsOnTargets` wskazuje, że obiekt docelowy zależy od innych obiektów docelowych. Na przykład:

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

informuje MSBuild, `Serve` że obiekt `Chop` docelowy `Cook` zależy od obiektu docelowego i obiektu docelowego. MSBuild uruchamia `Chop` obiekt docelowy, `Cook` a następnie `Serve` uruchamia obiekt docelowy przed uruchomieniu obiektu docelowego.

## <a name="beforetargets-and-aftertargets"></a>Przedtargety i AfterTargets

W MSBuild 4.0 można określić kolejność `BeforeTargets` `AfterTargets` docelową przy użyciu atrybutów i.

Należy wziąć pod uwagę następujący skrypt.

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

Aby utworzyć pośredni `Optimize` obiekt docelowy, który działa po miejsce docelowe, `Compile` ale przed obiektem docelowym, `Link` dodaj następujący obiekt docelowy w dowolnym miejscu `Project` elementu.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Określanie docelowej kolejności kompilacji

MSBuild określa docelową kolejność kompilacji w następujący sposób:

1. `InitialTargets`cele są uruchamiane.

2. Obiekty docelowe określone w wierszu polecenia przez przełącznik **-target** są uruchamiane. Jeśli nie określisz żadnych obiektów docelowych w wierszu `DefaultTargets` polecenia, obiekty docelowe zostaną uruchomione. Jeśli żadna z nich nie jest obecny, a następnie pierwszy obiekt docelowy napotkane jest uruchamiany.

3. Atrybut `Condition` obiektu docelowego jest oceniany. Jeśli `Condition` atrybut jest obecny i `false`ocenia do , cel nie jest wykonywany i nie ma dalszego wpływu na kompilacji.

   Inne obiekty docelowe, które `BeforeTargets` `AfterTargets` wymieniają cel warunkowy w lub nadal wykonywane w określonej kolejności.

4. Przed wykonaniem lub pominięciem `DependsOnTargets` obiektu docelowego jego `Condition` obiekty docelowe są uruchamiane, `false`chyba że atrybut zostanie zastosowany do obiektu docelowego i oceni .

   > [!NOTE]
   > Obiekt docelowy jest uważany za pominięty, jeśli nie jest wykonywany, ponieważ jego elementy wyjściowe są aktualne (zobacz [kompilacja przyrostowa).](../msbuild/incremental-builds.md) Ta kontrola jest wykonywana tuż przed wykonaniem zadań wewnątrz obiektu docelowego i nie wpływa na kolejność wykonywania obiektów docelowych.

5. Zanim obiekt docelowy zostanie wykonany lub pominięty, zostanie `BeforeTargets` uruchomiony inny obiekt docelowy, który wyświetla listę docelowych w atrybucie.

6. Przed wykonaniem obiektu `Inputs` docelowego `Outputs` jest porównywany jego atrybut i atrybut. Jeśli MSBuild stwierdzi, że wszystkie pliki wyjściowe są nieaktualne w odniesieniu do odpowiedniego pliku wejściowego lub plików, następnie MSBuild wykonuje obiekt docelowy. W przeciwnym razie MSBuild pomija obiekt docelowy.

7. Po wykonaniu lub pominięciu obiektu docelowego zostanie uruchomiony `AfterTargets` każdy inny obiekt docelowy, który wyświetla go w atrybucie.

## <a name="see-also"></a>Zobacz też

- [Cele](../msbuild/msbuild-targets.md)
