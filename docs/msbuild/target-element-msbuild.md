---
title: Element docelowy (MSBuild) | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79686132adce043b4864d545f0912564709cfe2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631981"
---
# <a name="target-element-msbuild"></a>Element docelowy (MSBuild)

Zawiera zestaw zadań dla MSBuild do wykonania sekwencyjnie.

 \<> \<docelowe> projektu

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
|`Name`|Atrybut wymagany.<br /><br /> Nazwa elementu docelowego.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać oceniony. Jeśli warunek ocenia `false`, cel nie wykona treści obiektu docelowego lub żadnych `DependsOnTargets` obiektów docelowych, które są ustawione w atrybucie. Aby uzyskać więcej informacji na temat warunków, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`Inputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wejściowe do tego obiektu docelowego. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików zostaną porównane z sygnaturami czasowymi plików w `Outputs` celu ustalenia, `Target` czy jest aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [Jak: Tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md)i [Przekształca](../msbuild/msbuild-transforms.md).|
|`Outputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wyjściowe do tego obiektu docelowego. Wiele plików jest oddzielonych średnikami. Sygnatury czasowe plików zostaną porównane z sygnaturami czasowymi plików w `Inputs` celu ustalenia, `Target` czy jest aktualna. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](../msbuild/incremental-builds.md), [Jak: Tworzenie przyrostowo](../msbuild/how-to-build-incrementally.md)i [Przekształca](../msbuild/msbuild-transforms.md).|
|`Returns`|Atrybut opcjonalny.<br /><br /> Zestaw elementów, które zostaną udostępnione do zadań, które wywołują ten obiekt docelowy, na przykład zadania MSBuild. Wiele obiektów docelowych jest oddzielonych średnikami. Jeśli obiekty docelowe w `Returns` pliku nie mają żadnych atrybutów, atrybuty Outputs są używane zamiast tego celu.|
|`KeepDuplicateOutputs`|Opcjonalny atrybut logiczny.<br /><br /> Jeśli `true`, wiele odwołań do tego samego towaru w docelowym Returns są rejestrowane.  Domyślnie ten atrybut `false`to .|
|`BeforeTargets`|Atrybut opcjonalny.<br /><br /> Oddzielona średnikami lista nazw docelowych.  Po określeniu wskazuje, że ten obiekt docelowy powinien być uruchamiany przed określonym celem lub obiektem docelowym. Dzięki temu autor projektu rozszerza istniejący zestaw obiektów docelowych bez modyfikowania ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [Docelowa kolejność kompilacji](../msbuild/target-build-order.md).|
|`AfterTargets`|Atrybut opcjonalny.<br /><br /> Oddzielona średnikami lista nazw docelowych. Po określeniu wskazuje, że ten cel powinien być uruchamiany po określonym celu lub obiektach docelowych. Dzięki temu autor projektu rozszerza istniejący zestaw obiektów docelowych bez modyfikowania ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [Docelowa kolejność kompilacji](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Atrybut opcjonalny.<br /><br /> Obiekty docelowe, które muszą zostać wykonane przed wykonaniem tego obiektu docelowego lub może wystąpić analiza zależności najwyższego poziomu. Wiele obiektów docelowych jest oddzielonych średnikami.|
|`Label`|Atrybut opcjonalny.<br /><br /> Identyfikator, który może identyfikować lub uporządkować elementy systemu i użytkownika.|

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Zadanie](../msbuild/task-element-msbuild.md) | Tworzy i wykonuje wystąpienie zadania MSBuild. W target może być zero lub więcej zadań. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | Zawiera zestaw elementów `Property` zdefiniowanych przez użytkownika. Począwszy od .NET Framework 3.5 `Target` `PropertyGroup` element może zawierać elementy. |
| [Itemgroup](../msbuild/itemgroup-element-msbuild.md) | Zawiera zestaw elementów `Item` zdefiniowanych przez użytkownika. Począwszy od .NET Framework 3.5 `Target` `ItemGroup` element może zawierać elementy. Aby uzyskać więcej informacji, zobacz [Elementy](../msbuild/msbuild-items.md). |
| [Onerror](../msbuild/onerror-element-msbuild.md) | Powoduje, że jeden lub `ContinueOnError` więcej obiektów docelowych do `false`wykonania, jeśli atrybut jest ErrorAndStop (lub) dla zadania nie powiodło się. Może istnieć zero `OnError` lub więcej elementów w docelowych. Jeśli `OnError` elementy są obecne, muszą być `Target` ostatnimi elementami w elemencie.<br /><br /> Aby uzyskać `ContinueOnError` informacje o tym atrybucie, zobacz [Task element (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |

## <a name="remarks"></a>Uwagi

 Pierwszy obiekt docelowy do wykonania jest określony w czasie wykonywania. Obiekty docelowe mogą mieć zależności od innych obiektów docelowych. Na przykład miejsce docelowe dla wdrożenia zależy od obiektu docelowego kompilacji. Aparat MSBuild wykonuje zależności w kolejności, w jakiej `DependsOnTargets` pojawiają się w atrybucie, od lewej do prawej. Aby uzyskać więcej informacji, zobacz [Cele](../msbuild/msbuild-targets.md).

 MSBuild jest zależny od zamówienia importu, a `Name` ostatnią definicją obiektu docelowego z określonym atrybutem jest używana definicja.

 Obiekt docelowy jest wykonywany tylko raz podczas kompilacji, nawet jeśli więcej niż jeden obiekt docelowy ma zależność od niego.

 Jeśli obiekt docelowy jest `Condition` pomijany, `false`ponieważ jego atrybut jest oceniany do , nadal `Condition` może być wykonywany, jeśli jest wywoływany później w kompilacji i jego atrybut ocenia `true` w tym czasie.

 Przed MSBuild 4, zwrócił wszystkie elementy, `Target` które zostały określone w `Outputs` atrybucie.  Aby to zrobić, MSBuild musiał zarejestrować te elementy w przypadku, gdy zadania później w kompilacji zażądał ich. Ponieważ nie było sposobu, aby wskazać, które obiekty docelowe miały dane wyjściowe, `Outputs` które wymagają `Target`wywołań, MSBuild zgromadził wszystkie elementy ze wszystkich na wszystkie wywoływane s. Prowadzi to do skalowania problemów dla kompilacji, które miały dużą liczbę elementów wyjściowych.

 Jeśli użytkownik określa `Returns` na `Target` dowolny element w projekcie, `Target`a następnie `Returns` tylko te s, które mają atrybut rekord tych elementów.

 A `Target` może zawierać `Outputs` zarówno atrybut, jak i `Returns` atrybut.  `Outputs`służy `Inputs` do określenia, czy obiekt docelowy jest aktualny. `Returns`, jeśli jest obecny, zastępuje `Outputs` wartość, aby określić, które towary są zwracane do wywołujących.  Jeśli `Returns` nie ma `Outputs` go, zostanie on udostępniony dzwoniącym, z wyjątkiem opisanego wcześniej przypadku.

 Przed MSBuild 4, w `Target` dowolnym momencie, że zawarte `Outputs`wiele odwołań do tego samego elementu w jego , te zduplikowane elementy będą rejestrowane. W bardzo dużych kompilacjach, które miały dużą liczbę wyjść i wiele współzależności projektu, spowodowałoby to dużą ilość pamięci do zmarnowania, ponieważ zduplikowane elementy nie były żadnego użycia. Gdy `KeepDuplicateOutputs` atrybut jest ustawiony `true`na , te duplikaty są rejestrowane.

## <a name="example"></a>Przykład

 Poniższy przykład kodu `Target` przedstawia element, `Csc` który wykonuje zadanie.

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

- [Cele](../msbuild/msbuild-targets.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
