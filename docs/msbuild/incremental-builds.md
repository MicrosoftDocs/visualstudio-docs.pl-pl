---
title: Kompilacje przyrostowe | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7283d67710a3b5b319b2d25a1c5d6535fed83b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633723"
---
# <a name="incremental-builds"></a>Kompilacje przyrostowe

Kompilacje przyrostowe to kompilacje zoptymalizowane w taki sposób, że elementy docelowe, których pliki wyjściowe mają tak samo aktualną zawartość jak pliki wejściowe, nie są wykonywane. Element docelowy może mieć zarówno atrybut `Inputs`, który wskazuje elementy oczekiwane przez element docelowy na wejściu, oraz atrybut `Outputs`, który wskazuje elementy generowane przez element docelowy na wyjściu. Program MSBuild próbuje znaleźć mapowania 1-do-1 między wartościami tych atrybutów. Jeśli istnieje mapowanie 1-do-1, MSBuild porównuje znacznik czasu każdego elementu wejściowego ze znacznikiem czasu odpowiadającego mu elementu wyjściowego. Pliki wyjściowe pozbawione mapowań 1-do-1 są porównywane ze wszystkimi plikami wejściowymi. Element uważa się za aktualny, jeśli plik wyjściowy jest nie starszy niż plik lub pliki wejściowe.

> [!NOTE]
> Gdy MSBuild ocenia pliki wejściowe, uwzględniana jest tylko zawartość listy w bieżącym wykonaniu. Zmiany na liście z ostatniej kompilacji nie automatycznie sprawiają, że obiekt docelowy jest nieaktualny.

Jeśli wszystkie elementy wyjściowe są aktualne, program MSBuild pomija element docelowy. Ta *przyrostowa kompilacja* obiektu docelowego może znacznie poprawić szybkość kompilacji. Jeśli tylko niektóre pliki są aktualne, program MSBuild wykonuje element docelowy, ale pomija elementy aktualne. W efekcie wszystkie elementy stają się aktualne. Proces ten jest nazywany *częściową kompilacją przyrostową*.

Mapowania 1-do-1 są z reguły tworzone wskutek przekształceń elementów. Aby uzyskać więcej informacji, zobacz [Przekształcenia](../msbuild/msbuild-transforms.md).

 Rozważmy następujący element docelowy.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

Zestaw plików reprezentowanych przez `Compile` typ elementu jest kopiowany do katalogu kopii zapasowej. Pliki kopii zapasowej mają rozszerzenie nazwy pliku *.bak.* Jeśli pliki reprezentowane przez typ elementu `Compile` lub odpowiadające im pliki kopii zapasowej nie zostaną usunięte lub zmodyfikowane po uruchomieniu elementu docelowego będącego kopią zapasową, wtedy ten element jest pomijany w kolejnych kompilacjach.

## <a name="output-inference"></a>Wnioskowanie o wyjściu

Program MSBuild porównuje atrybuty `Inputs` i `Outputs` elementu docelowego w celu ustalenia, czy element docelowy ma zostać wykonany. Najlepiej, aby zestaw plików istniejących po ukończeniu kompilacji przyrostowej pozostawał bez zmian niezależnie od tego, czy skojarzone z nimi elementy docelowe zostały wykonane. Ponieważ właściwości i elementy tworzone lub zmieniane przez zadania mogą wpływać na kompilację, program MSBuild musi wywnioskować ich wartość, nawet gdy dotyczący ich element docelowy jest pomijany. Proces ten jest znany jako *wnioskowanie o wyjściu*.

Istnieją trzy przypadki:

- Element docelowy ma atrybut `Condition`, którego wynikiem jest wartość `false`. W tym przypadku element docelowy nie jest wykonywany i nie ma wpływu na kompilację.

- Obiekt docelowy ma nieaktualne dane wyjściowe i jest uruchamiany w celu ich aktualności.

- Element docelowy nie ma żadnych nieaktualnych danych wyjściowych, dlatego jest pomijany. Program MSBuild oblicza element docelowy, po czym wprowadza zmiany w elementach i właściwościach tak, jakby element został wykonany.

Aby umożliwić kompilację przyrostową, zadania muszą dopilnować, aby wartość atrybutu `TaskParameter` każdego elementu `Output` była równa parametrowi wejściowemu zadania. Oto kilka przykładów:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Ten kod tworzy właściwość Easy, która ma wartość "123", niezależnie od tego, czy obiekt docelowy jest wykonywany, czy pomijany.

Począwszy od programu MSBuild 3.5 wnioskowanie danych wyjściowych jest wykonywane automatycznie wobec grup elementów i właściwości w elemencie docelowym. `CreateItem`zadania nie są wymagane w celu i należy ich unikać. Ponadto zadań `CreateProperty` należy używać w elemencie docelowym tylko w celu określenia, czy został on wykonany.

Przed MSBuild 3.5 można użyć [createitem](../msbuild/createitem-task.md) zadania.

## <a name="determine-whether-a-target-has-been-run"></a>Określanie, czy obiekt docelowy został uruchomiony

Z powodu wnioskowania danych wyjściowych należy do elementu docelowego dodać zadanie `CreateProperty`, które będzie badało właściwości i elementy w celu określenia, czy element docelowy został wykonany. Należy do elementu docelowego dodać zadanie `CreateProperty`, a do niego element `Output`, którego parametr `TaskParameter` ma wartość „ValueSetByTask”.

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Ten kod tworzy właściwość CompileRan `true`i nadaje jej wartość , ale tylko wtedy, gdy cel jest wykonywany. Jeśli element docelowy jest pomijany, właściwość CompileRan nie powstaje.

## <a name="see-also"></a>Zobacz też

- [Cele](../msbuild/msbuild-targets.md)
