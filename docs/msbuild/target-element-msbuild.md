---
title: Target — element (MSBuild) | Microsoft Docs
description: Dowiedz się więcej o elemencie docelowym programu MSBuild, który zawiera zestaw zadań wykonywanych sekwencyjnie dla programu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 231ffd185eaf06fb91a709631082c2b68db372ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966126"
---
# <a name="target-element-msbuild"></a>Target — element (MSBuild)

Zawiera zestaw zadań wykonywanych sekwencyjnie dla programu MSBuild.

 \<Project> \<Target>

## <a name="syntax"></a>Składnia

```xml
<Target Name="Target Name"
        Inputs="Inputs"
        Outputs="Outputs"
        Returns="Returns"
        KeepDuplicateOutputs="true/false"
        BeforeTargets="Targets"
        AfterTargets="Targets"
        DependsOnTargets="DependentTarget"
        Condition="'String A' == 'String B'"
        Label="Label">
    <Task>... </Task>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <OnError... />
</Target>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Atrybut wymagany.<br /><br /> Nazwa elementu docelowego. Nazwa docelowa może zawierać dowolny znak z wyjątkiem `$@()%*?.` .|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczony. Jeśli warunek ma wartość `false` , obiekt docelowy nie wykona treści elementu docelowego ani żadnych elementów docelowych ustawionych w `DependsOnTargets` atrybucie. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Inputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wejściowe w tym miejscu docelowym. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików będą porównywane z sygnaturami czasowymi plików w programie `Outputs` , aby określić, czy `Target` jest ona aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)i [transformacje](../msbuild/msbuild-transforms.md).|
|`Outputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wyjściowe w tym miejscu docelowym. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików będą porównywane z sygnaturami czasowymi plików w programie `Inputs` , aby określić, czy `Target` jest ona aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)i [transformacje](../msbuild/msbuild-transforms.md).|
|`Returns`|Atrybut opcjonalny.<br /><br /> Zestaw elementów, które zostaną udostępnione dla zadań, które wywołują ten element docelowy, na przykład zadania programu MSBuild. Wiele obiektów docelowych jest oddzielonych średnikami. Jeśli obiekty docelowe w pliku nie mają żadnych `Returns` atrybutów, zamiast tego są używane atrybuty danych wyjściowych.|
|`KeepDuplicateOutputs`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli zostanie `true` zarejestrowane wiele odwołań do tego samego elementu w zwracanych wartościach docelowych.  Domyślnie ten atrybut jest `false` .|
|`BeforeTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych.  Gdy ta wartość jest określona, wskazuje, że ten element docelowy powinien zostać uruchomiony przed określonym elementem docelowym lub celem. Pozwala to autorowi projektu na rozszerać istniejący zestaw elementów docelowych bez konieczności ich bezpośredniego modyfikowania. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md).|
|`AfterTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych. Jeśli ta wartość jest określona, wskazuje, że ten element docelowy powinien zostać uruchomiony po określonym elemencie docelowym lub Target. Pozwala to autorowi projektu na rozszerać istniejący zestaw elementów docelowych bez konieczności ich bezpośredniego modyfikowania. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Atrybut opcjonalny.<br /><br /> Elementy docelowe, które muszą zostać wykonane, zanim będzie można wykonać tę wartość docelową lub mogą wystąpić analizy zależności najwyższego poziomu. Wiele obiektów docelowych jest oddzielonych średnikami.|
|`Label`|Atrybut opcjonalny.<br /><br /> Identyfikator, który może identyfikować lub zamówić elementy systemu i użytkownika.|

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Zadanie](../msbuild/task-element-msbuild.md) | Tworzy i wykonuje wystąpienie zadania programu MSBuild. W elemencie docelowym mogą istnieć co najmniej zero zadań. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Zawiera zestaw elementów zdefiniowanych przez użytkownika `Property` . Począwszy od .NET Framework 3,5, `Target` element może zawierać `PropertyGroup` elementy. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Zawiera zestaw elementów zdefiniowanych przez użytkownika `Item` . Począwszy od .NET Framework 3,5, `Target` element może zawierać `ItemGroup` elementy. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Powoduje, że co najmniej jeden obiekt docelowy jest wykonywany, jeśli `ContinueOnError` atrybut jest ErrorAndStop (lub `false` ) dla zadania zakończonego niepowodzeniem. Element docelowy może zawierać zero lub więcej `OnError` elementów. Jeśli `OnError` są obecne elementy, muszą one być ostatnimi elementami w `Target` elemencie.<br /><br /> Aby uzyskać informacje na temat `ContinueOnError` atrybutu, zobacz [element Task (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 Pierwszy cel do wykonania jest określony w czasie wykonywania. Elementy docelowe mogą mieć zależności od innych elementów docelowych. Na przykład element docelowy wdrożenia zależy od elementu docelowego kompilacji. Aparat MSBuild wykonuje zależności w kolejności, w jakiej występują w `DependsOnTargets` atrybucie, od lewej do prawej. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md).

 MSBuild jest zależna od kolejności importu, a ostatnią definicją obiektu docelowego z określonym `Name` atrybutem jest definicja użyta.

 Element docelowy jest wykonywany tylko raz podczas kompilacji, nawet jeśli więcej niż jeden element docelowy ma zależność.

 Jeśli element docelowy został pominięty, ponieważ jego `Condition` atrybut jest obliczany do `false` , nadal może być wykonywany, jeśli zostanie wywołana w dalszej części kompilacji, a jego `Condition` atrybut `true` w tym czasie ma wartość.

 Przed MSBuild 4 `Target` zwróci wszystkie elementy, które zostały określone w `Outputs` atrybucie.  W tym celu program MSBuild musiał zarejestrować te elementy w późniejszej części zadania kompilacji. Ze względu na to, że nie można wskazać, które elementy docelowe mają dane wyjściowe wymagane przez wywołujących, program MSBuild zgromadził wszystkie elementy ze wszystkich elementów `Outputs` we wszystkich wywołaniach `Target` . To prowadzi do skalowania problemów dotyczących kompilacji, które mają dużą liczbę elementów wyjściowych.

 Jeśli użytkownik określi `Returns` dowolny `Target` element w projekcie, wówczas tylko te `Target` , które mają `Returns` atrybut zapisują te elementy.

 `Target`Może zawierać zarówno `Outputs` atrybut, jak i `Returns` atrybut.  `Outputs` służy `Inputs` do określenia, czy element docelowy jest aktualny. `Returns`, jeśli jest obecny, zastępuje wartość, `Outputs` Aby określić, które elementy są zwracane do wywoływania.  Jeśli `Returns` nie jest obecny, `Outputs` zostanie udostępniona dla wywoływania, z wyjątkiem przypadków opisanych wcześniej.

 Przed MSBuild 4, za każdym razem, gdy `Target` w jego przypadku uwzględniono wiele odwołań do tego samego elementu `Outputs` , te zduplikowane elementy zostałyby zarejestrowane. W bardzo dużych kompilacjach, które mają dużą liczbę danych wyjściowych i wiele współzależności między projektami, może to spowodować marnowanie dużej ilości pamięci, ponieważ duplikaty elementów nie były używane. Gdy `KeepDuplicateOutputs` atrybut jest ustawiony na `true` , te duplikaty są rejestrowane.

## <a name="example"></a>Przykład

 Poniższy przykład kodu przedstawia `Target` element, który wykonuje `Csc` zadanie.

```xml
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Zobacz też

- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
