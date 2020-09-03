---
title: Nawigowanie po modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23f87c81e43b2dfafb1c9c78c3135faff809bb9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74289858"
---
# <a name="navigate-the-uml-model"></a>Nawigowanie po modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie przedstawiono główne typy modelu UML.

## <a name="the-model-elements-model-and-model-store"></a>Elementy modelu, model i magazyn modelu
 Typy zdefiniowane w zestawie **Microsoft.VisualStudio.Uml.Interfaces.dll** odpowiadają typom zdefiniowanym w [specyfikacji UML w wersji 2.1.2](https://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).

 Typy w specyfikacji UML są realizowane jako interfejsy w programie Visual Studio. Litera "I" jest poprzedzona nazwą każdego typu. Na przykład: [IElement](/previous-versions/dd516035(v=vs.140)), [iClass](/previous-versions/dd523539%28v%3dvs.140%29), [IOperation](/previous-versions/dd481186(v=vs.140)).

 Wszystkie typy, z wyjątkiem IElement, dziedziczą właściwości z co najmniej jednego nadtypu.

- Aby uzyskać podsumowanie typów modelu, zobacz [typy elementów modelu UML](../modeling/uml-model-element-types.md).

- Aby uzyskać szczegółowe informacje o interfejsie API, zobacz [Dokumentacja interfejsu API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

### <a name="relationships"></a>Relacje
 Właściwości i relacje, które są zdefiniowane w specyfikacji UML, są implementowane jako właściwości platformy .NET.

 Większość relacji jest nawigować w obu kierunkach. Relacja odnosi się do pary właściwości, z jedną właściwością dla typu na każdym końcu. Na przykład właściwości `IElement.Owner` i `IElement.OwnedElements` reprezentują dwa zakończenia relacji. W związku z tym wyrażenie będzie zawsze oceniane jako prawdziwe:

 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`

 Wiele relacji, takich jak IAssociation, są również reprezentowane przez obiekt, który może mieć własne właściwości.

 W przypadku usunięcia elementu z modelu każda relacja, w której staje się częścią, zostanie automatycznie usunięta, a właściwość na drugim końcu zostanie zaktualizowana.

 Jeśli Specyfikacja UML przypisuje liczebność 0.. 1 do właściwości, może ona mieć wartość `null` . Liczebność z maksymalną liczbą większą niż 1 oznacza, że właściwość .NET ma typ: `IEnumerable<` *Type* `>` .

 Aby uzyskać więcej informacji na temat przechodzenia między relacjami, zobacz [nawigowanie po relacjach za pomocą interfejsu API UML](../modeling/navigate-relationships-with-the-uml-api.md).

### <a name="the-ownership-tree"></a>Drzewo własności
 Model zawiera drzewo obiektów [IElement](/previous-versions/dd516035(v=vs.140)) . Każdy element ma właściwości `OwnedElements` i `Owner` .

 W większości przypadków obiekty docelowe `Owner` i `OwnedElements` właściwości są również przywoływane przez inne właściwości, które mają bardziej szczegółowe nazwy. Na przykład każda operacja UML jest własnością klasy UML. W związku z tym [IOperation](/previous-versions/dd481186(v=vs.140)) ma właściwość o nazwie [IOperation. Class](/previous-versions/dd473473%28v%3dvs.140%29)i w każdym obiekcie [IOperation](/previous-versions/dd481186(v=vs.140)) , `Class == Owner` .

 Elementem najwyższego poziomu drzewa, który nie ma właściciela, jest `AuxiliaryConstructs.IModel` . IModel jest zawarty w `IModelStore` , w którym jest [IModelStore. root](/previous-versions/ee789368(v=vs.140)).

 Każdy element modelu jest tworzony z właścicielem. Aby uzyskać więcej informacji, zobacz [Tworzenie elementów i relacji w modelach UML](../modeling/create-elements-and-relationships-in-uml-models.md).

 ![Diagram klas: model, diagram, kształt i element](../modeling/media/uml-mm1.png)

## <a name="shapes-and-diagrams"></a>Kształty i diagramy
 Elementy w modelu UML mogą być wyświetlane na diagramach. Różne typy diagramów mogą wyświetlać różne podtypy IElement.

 W niektórych przypadkach element może znajdować się na więcej niż jednym diagramie. Na przykład element IUseCase może mieć kilka IShapes, które mogą być wyświetlane na jednym diagramie lub różnych diagramach.

 Kształty są ułożone w drzewie. Krawędzie drzewa są reprezentowane przez właściwości ParentShape i ChildShapes. Diagramy są jedynymi kształtami, które nie mają obiektów nadrzędnych. Kształty na powierzchni diagramu składają się z mniejszych części. Na przykład kształt klasy ma przedziały dla atrybutów i operacji.

 Aby uzyskać więcej informacji na temat kształtów, zobacz [Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="access-to-the-model-in-extensions"></a>Dostęp do modelu w rozszerzeniach
 W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeniach zdefiniowanych jako składniki MEF można zadeklarować właściwości, które zaimportują informacje z kontekstu, w którym jest uruchamiane rozszerzenie.

|Typ atrybutu|Do czego służy dostęp|Więcej informacji|
|--------------------|----------------------------------|----------------------|
|Microsoft. VisualStudio. ArchitectureTools. rozszerzalność. Prezentacja<br /><br /> . IDiagramContext<br /><br /> (w Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Bieżący diagram fokusu.|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|
|Microsoft. VisualStudio. Modeling. ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (w Microsoft. VisualStudio. Modeling. Sdk. [wersja]. dll)|Umożliwia grupowanie zmian w transakcjach.|[Łączenie aktualizacji modelu UML za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md)|
|Microsoft. VisualStudio. Shell. SVsServiceProvider<br /><br /> (w Microsoft. VisualStudio. Shell. unzmienna. [wersja]. dll)|Host [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Z tego miejsca możesz uzyskać dostęp do plików, projektów i innych aspektów.|[Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|

### <a name="to-get-the-context"></a>Aby uzyskać kontekst
 Zadeklaruj jeden lub oba z następujących interfejsów wewnątrz klasy rozszerzenia:

```
[Import] public IDiagramContext DiagramContext { get; set; }

```

 Managed Extensibility Framework (MEF) powiąże się z definicjami, z których można uzyskać bieżący diagram, Magazyn modeli, obiekt główny i tak dalej:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
IClassDiagram classDiagram = diagram as IClassDiagram;
       // or diagrams of other types
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

### <a name="to-get-the-current-selection"></a>Aby pobrać bieżące zaznaczenie

```
// All selected shapes and their elements
foreach (IShape shape in diagram.SelectedShapes)
{
   IDiagram selectedDiagram = shape as IDiagram;
   if (selectedDiagram != null)
   { // no shape selected - user right-clicked the diagram
     ... Context.CurrentDiagram ...
   }
   else
   {
     IElement selectedElement = shape.Element;
   ...}
// All selected shapes that display a specfic type of element
foreach (IShape<IInterface> in
   diagram.GetSelectedShapes<IInterface>())
{...}
```

## <a name="accessing-another-model-or-diagrams"></a>Uzyskiwanie dostępu do innego modelu lub diagramów
 Można:

- Użyj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelu Bus, aby utworzyć linki między elementami w różnych modelach. Aby uzyskać więcej informacji, zobacz [integrowanie modeli UML z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Załaduj projekt modelowania i diagramy w trybie tylko do odczytu bez uwidaczniania go w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsie użytkownika. Aby uzyskać więcej informacji, zobacz [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

- Otwórz projekt modelowania i jego diagramy w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , a następnie uzyskaj dostęp do zawartości. Aby uzyskać więcej informacji, zobacz [otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
- [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
