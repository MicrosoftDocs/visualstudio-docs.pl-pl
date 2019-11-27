---
title: Target — element (MSBuild) | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1748064482e13eba95e9aa83e9cb04c93b8066f
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491617"
---
# <a name="target-element-msbuild"></a>Target — element (MSBuild)
Zawiera zestaw zadań, które mają być wykonywane sekwencyjnie przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

 \<projekt > \<docelowy >

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

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Atrybut wymagany.<br /><br /> Nazwa elementu docelowego.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczony. Jeśli warunek szacuje się `false`, obiekt docelowy nie będzie wykonywać treści elementu docelowego ani żadnych elementów docelowych ustawionych w atrybucie `DependsOnTargets`. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Inputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wejściowe w tym miejscu docelowym. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików będą porównywane z sygnaturami czasowymi plików w `Outputs`, aby określić, czy `Target` jest aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)i [transformacje](../msbuild/msbuild-transforms.md).|
|`Outputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wyjściowe w tym miejscu docelowym. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików będą porównywane z sygnaturami czasowymi plików w `Inputs`, aby określić, czy `Target` jest aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [instrukcje: kompilowanie przyrostowe](../msbuild/how-to-build-incrementally.md)i [transformacje](../msbuild/msbuild-transforms.md).|
|`Returns`|Atrybut opcjonalny.<br /><br /> Zestaw elementów, które zostaną udostępnione dla zadań, które wywołują ten element docelowy, na przykład zadania programu MSBuild. Wiele obiektów docelowych jest oddzielonych średnikami. Jeśli obiekty docelowe w pliku nie mają atrybutów `Returns`, zamiast tego są używane atrybuty danych wyjściowych.|
|`KeepDuplicateOutputs`|Opcjonalny atrybut Boolean.<br /><br /> Jeśli `true`, rejestrowane są wiele odwołań do tego samego elementu w zwracanych wartościach docelowych.  Domyślnie ten atrybut jest `false`.|
|`BeforeTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych.  Gdy ta wartość jest określona, wskazuje, że ten element docelowy powinien zostać uruchomiony przed określonym elementem docelowym lub celem. Pozwala to autorowi projektu na rozszerać istniejący zestaw elementów docelowych bez konieczności ich bezpośredniego modyfikowania. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md).|
|`AfterTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych. Jeśli ta wartość jest określona, wskazuje, że ten element docelowy powinien zostać uruchomiony po określonym elemencie docelowym lub Target. Pozwala to autorowi projektu na rozszerać istniejący zestaw elementów docelowych bez konieczności ich bezpośredniego modyfikowania. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Atrybut opcjonalny.<br /><br /> Elementy docelowe, które muszą zostać wykonane, zanim będzie można wykonać tę wartość docelową lub mogą wystąpić analizy zależności najwyższego poziomu. Wiele obiektów docelowych jest oddzielonych średnikami.|
|`Label`|Atrybut opcjonalny.<br /><br /> Identyfikator, który może identyfikować lub zamówić elementy systemu i użytkownika.|

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Zadaniem](../msbuild/task-element-msbuild.md) | Tworzy i wykonuje wystąpienie zadania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. W elemencie docelowym mogą istnieć co najmniej zero zadań. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Zawiera zestaw elementów `Property` zdefiniowanych przez użytkownika. Począwszy od .NET Framework 3,5, element `Target` może zawierać `PropertyGroup` elementów. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Zawiera zestaw elementów `Item` zdefiniowanych przez użytkownika. Począwszy od .NET Framework 3,5, element `Target` może zawierać `ItemGroup` elementów. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Powoduje, że co najmniej jeden obiekt docelowy jest wykonywany, jeśli atrybut `ContinueOnError` jest ErrorAndStop (lub `false`) dla zadania zakończonego niepowodzeniem. Element docelowy może mieć co najmniej zero elementów `OnError`. Jeśli elementy `OnError` są obecne, muszą one być ostatnimi elementami elementu `Target`.<br /><br /> Aby uzyskać informacje o atrybucie `ContinueOnError`, zobacz [element Task (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Projektu](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Uwagi
 Pierwszy cel do wykonania jest określony w czasie wykonywania. Elementy docelowe mogą mieć zależności od innych elementów docelowych. Na przykład element docelowy wdrożenia zależy od elementu docelowego kompilacji. Aparat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wykonuje zależności w kolejności, w jakiej występują w atrybucie `DependsOnTargets`, od lewej do prawej. Aby uzyskać więcej informacji, zobacz [targets](../msbuild/msbuild-targets.md).

 MSBuild jest zależna od kolejności importu, a ostatnią definicją obiektu docelowego z określonym atrybutem `Name` jest definicja użyta.

 Element docelowy jest wykonywany tylko raz podczas kompilacji, nawet jeśli więcej niż jeden element docelowy ma zależność.

 Jeśli element docelowy został pominięty, ponieważ jego atrybut `Condition` jest obliczany na `false`, nadal może być wykonywany, jeśli zostanie wywołana później w kompilacji, a jego atrybut `Condition` w tym czasie ma wartość `true`.

 Przed MSBuild 4 `Target` zwróciła wszystkie elementy, które zostały określone w atrybucie `Outputs`.  W tym celu program MSBuild musiał zarejestrować te elementy w późniejszej części zadania kompilacji. Ze względu na to, że nie można wskazać, które elementy docelowe mają dane wyjściowe wymagane przez wywołujących, program MSBuild zgromadził wszystkie elementy ze wszystkich `Outputs` wszystkich wywołanych `Target`s. To prowadzi do skalowania problemów dotyczących kompilacji, które mają dużą liczbę elementów wyjściowych.

 Jeśli użytkownik określi `Returns` dla dowolnego elementu `Target` w projekcie, wówczas tylko te `Target`s, które mają atrybut `Returns`, zapisują te elementy.

 `Target` może zawierać zarówno atrybut `Outputs`, jak i atrybut `Returns`.  `Outputs` jest używany z `Inputs`, aby określić, czy element docelowy jest aktualny. `Returns`, jeśli istnieje, zastępuje wartość `Outputs`, aby określić, które elementy są zwracane do wywoływania.  Jeśli `Returns` nie istnieje, `Outputs` zostanie udostępniona dla wywoływania, z wyjątkiem przypadków opisanych wcześniej.

 Przed MSBuild 4, za każdym razem, gdy `Target` zawiera wiele odwołań do tego samego elementu w jego `Outputs`, te zduplikowane elementy zostałyby zarejestrowane. W bardzo dużych kompilacjach, które mają dużą liczbę danych wyjściowych i wiele współzależności między projektami, może to spowodować marnowanie dużej ilości pamięci, ponieważ duplikaty elementów nie były używane. Gdy atrybut `KeepDuplicateOutputs` jest ustawiony na `true`, te duplikaty są rejestrowane.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje `Target` element, który wykonuje `Csc` zadanie.

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

## <a name="see-also"></a>Zobacz także
- [Docelowe elementy](../msbuild/msbuild-targets.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
