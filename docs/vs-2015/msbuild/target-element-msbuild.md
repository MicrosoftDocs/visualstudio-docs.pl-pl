---
title: Docelowy Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f14815502a33fb7d49a10c2724c57a4a0d86e9f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144317"
---
# <a name="target-element-msbuild"></a>Target — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawiera zestaw zadań dla [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonania po kolei.  
  
 \<Project>  
 \<Docelowy >  
  
## <a name="syntax"></a>Składnia  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany.<br /><br /> Nazwa elementu docelowego.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek, który ma zostać obliczone. Jeśli warunek jest `false`, element docelowy nie zostanie wykonany treści obiektu docelowego lub obiektów docelowych, które są ustawiane w `DependsOnTargets` atrybutu. Aby uzyskać więcej informacji o warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Atrybut opcjonalny.<br /><br /> Pliki, które tworzą dane wejściowe do tego obiektu docelowego. Wiele plików są oddzielone średnikami. Pliki znacznikami czasu będą porównywane ze znacznikami czasu plików w `Outputs` ustalenie, czy `Target` jest aktualny. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md), [jak: Kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md), i [przekształca](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Atrybut opcjonalny.<br /><br /> Pliki wyjściowe do tego obiektu docelowego. Wiele plików są oddzielone średnikami. Pliki znacznikami czasu będą porównywane ze znacznikami czasu plików w `Inputs` ustalenie, czy `Target` jest aktualny. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md), [jak: Kompilacja przyrostowa](../msbuild/how-to-build-incrementally.md), i [przekształca](../msbuild/msbuild-transforms.md).|  
|`Returns`|Atrybut opcjonalny.<br /><br /> Zestaw elementów, które będą dostępne do zadań, które wywołują ten element docelowy, na przykład zadania programu MSBuild. Wiele elementów docelowych są oddzielone średnikami. Jeśli nie mają elementów docelowych w pliku `Returns` atrybuty danych wyjściowych atrybuty są używane zamiast tego w tym celu.|  
|`KeepDuplicateOutputs`|Opcjonalny logiczny atrybut.<br /><br /> Jeśli `true`, są rejestrowane przez wiele odwołań do tego samego elementu w element docelowy.  Domyślnie ten atrybut jest `false`.|  
|`BeforeTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych.  Jeśli zostanie określony, wskazuje, że ten element docelowy powinien być wykonywany przed określonego obiektu docelowego lub miejsc docelowych. Dzięki temu autora projektu rozszerzenia istniejącego zestawu obiektów docelowych bez modyfikowania ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [kolejności kompilacji docelowej](../msbuild/target-build-order.md).|  
|`AfterTargets`|Atrybut opcjonalny.<br /><br /> Rozdzielana średnikami lista nazw docelowych. Jeśli zostanie określony, wskazuje, że ten element docelowy powinien być wykonywany po określonego obiektu docelowego lub miejsc docelowych. Dzięki temu autora projektu rozszerzenia istniejącego zestawu obiektów docelowych bez modyfikowania ich bezpośrednio. Aby uzyskać więcej informacji, zobacz [kolejności kompilacji docelowej](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Atrybut opcjonalny.<br /><br /> Może wystąpić, obiektów docelowych, które muszą być wykonane przed ten element docelowy, mogą być wykonywane lub analizy zależności najwyższego poziomu. Wiele elementów docelowych są oddzielone średnikami.|  
|`Label`|Atrybut opcjonalny.<br /><br /> Identyfikator, który może identyfikacji lub porządkowania elementów systemu i użytkownika.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Zadanie](../msbuild/task-element-msbuild.md)|Tworzy i uruchamia wystąpienie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zadania. W elemencie docelowym może być zero lub więcej zadań.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Zawiera zestaw zdefiniowanych przez użytkownika `Property` elementów. Począwszy od programu .NET Framework 3.5 `Target` element może zawierać `PropertyGroup` elementów.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Zawiera zestaw zdefiniowanych przez użytkownika `Item` elementów. Począwszy od programu .NET Framework 3.5 `Target` element może zawierać `ItemGroup` elementów. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Powoduje, że jeden lub więcej obiektów docelowych do wykonania, jeśli `ContinueOnError` atrybut jest ErrorAndStop (lub `false`) dla zadania nie powiodło się. Może wynosić zero lub więcej `OnError` elementy w elemencie docelowym. Jeśli `OnError` elementy, muszą być ostatnie elementy w `Target` elementu.<br /><br /> Aby uzyskać informacje o `ContinueOnError` atrybutów, zobacz [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Element główny wymagany [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy element docelowy do wykonania jest określona w czasie wykonywania. Obiekty docelowe mogą mieć zależności na innych celów. Na przykład cel wdrożenia jest zależny od docelowej dla kompilacji. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Aparat wykonuje zależności w kolejności, w jakiej występują w `DependsOnTargets` atrybutu, od lewej do prawej. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).  
  
 Obiekt docelowy jest wykonywane tylko raz podczas kompilacji, nawet wtedy, gdy więcej niż jeden element docelowy ma zależność od jej.  
  
 Jeśli element docelowy jest pomijany, ponieważ jego `Condition` atrybutu daje w wyniku `false`, mogą być wykonywane nadal, jeśli jest wywoływany w dalszej części kompilacji i jej `Condition` atrybutu daje w wyniku `true` w tym czasie.  
  
 Przed MSBuild 4 `Target` zwrócone wszystkie elementy, które zostały określone w `Outputs` atrybutu.  Aby to zrobić, MSBuild musiał Rejestruj, w przypadku, gdy zadania w dalszej części kompilacji żądane je. Ponieważ nie było żadnych sposób, aby wskazać, które elementy docelowe miał danych wyjściowych, które wymagałyby obiektów wywołujących, program MSBuild zgromadzonych wszystkie elementy ze wszystkich `Outputs` na wszystkich wywoływane `Target`s. To doprowadzić do skalowania problemy dla kompilacji, które ma dużą liczbę elementów danych wyjściowych.  
  
 Jeśli użytkownik określi `Returns` na dowolnym `Target` elementu w projekcie, a następnie tylko te `Target`s, który ma `Returns` atrybut rejestrowanie tych elementów.  
  
 A `Target` może zawierać zarówno `Outputs` atrybutu i `Returns` atrybutu.  `Outputs` jest używana z `Inputs` do ustalenia, czy element docelowy jest aktualny. `Returns`, jeśli jest obecna, przesłania wartość `Outputs` Aby określić elementy, które są zwracane do obiektów wywołujących.  Jeśli `Returns` nie jest dostępny, wówczas `Outputs` będą dostępne dla kodu wywołującego, z wyjątkiem w przypadku opisanego wcześniej.  
  
 Przed 4 programu MSBuild, dowolny czas `Target` uwzględnione wiele odwołań do tego samego elementu w jego `Outputs`, są zapisywane te zduplikowane elementy. W bardzo dużych kompilacji, który ma dużą liczbę danych wyjściowych i wiele współzależności projektu, spowodowałoby to duża ilość pamięci do zostałby zmarnowany, ponieważ zduplikowane elementy nie zostały każde użycie. Gdy `KeepDuplicateOutputs` ma ustawioną wartość atrybutu `true`, są rejestrowane następujące duplikaty.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład `Target` element, który jest wykonywany `Csc` zadania.  
  
```  
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
 [Obiekty docelowe](../msbuild/msbuild-targets.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
