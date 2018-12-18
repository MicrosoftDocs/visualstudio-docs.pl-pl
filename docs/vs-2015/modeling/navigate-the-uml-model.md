---
title: Nawigowanie po modelu UML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: 6d789b6d-2aa9-4ceb-92c4-84a300065a76
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f77e72c55c0984f66a6884b0582716e5529abd0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727772"
---
# <a name="navigate-the-uml-model"></a>Nawigowanie po modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat wprowadza główne typy modelu UML.  
  
## <a name="the-model-elements-model-and-model-store"></a>Elementy modelu, Model i Store modelu  
 Typy zdefiniowane w zestawie **Microsoft.VisualStudio.Uml.Interfaces.dll** odnoszą się do typów zdefiniowanych w [specyfikacji UML wersji 2.1.2](http://www.omg.org/spec/UML/2.1.2/Superstructure/PDF/).  
  
 Typy w specyfikacji UML są realizowane jako interfejsy w programie Visual Studio. Litera "I" jest dołączona do nazwy każdego typu. Na przykład: <xref:Microsoft.VisualStudio.Uml.Classes.IElement>, <xref:Microsoft.VisualStudio.Uml.Classes.IClass>, <xref:Microsoft.VisualStudio.Uml.Interactions.IInteraction>, <xref:Microsoft.VisualStudio.Uml.Classes.IOperation>.  
  
 Wszystkie typy z wyjątkiem IElement dziedziczą właściwości z jednego lub kilku nadtypów.  
  
-   Aby uzyskać podsumowanie typów modeli, zobacz [typy elementów modelu UML](../modeling/uml-model-element-types.md).  
  
-   Aby uzyskać szczegółowe informacje o interfejsie API, zobacz [wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  
  
### <a name="relationships"></a>Relacje  
 Właściwości i relacje, które są zdefiniowane w specyfikacji UML są implementowane jako właściwości .NET.  
  
 Większość relacje są można nawigować w obu kierunkach. Relacja odpowiada parze właściwości, z jedną właściwością w typie na każdym końcu. Na przykład właściwości `IElement.Owner` i `IElement.OwnedElements` stanowią dwa końce relacji. W związku z tym to wyrażenie będzie zawsze przyjmowało wartość true:  
  
 `IElement c; ...  c.OwnedElements.All(x => x.Owner == c)`  
  
 Wiele związków, takich jak IAssociation, również jest reprezentowanych przez obiekt, który może mieć własne właściwości.  
  
 Jeśli usuniesz element z modelu, każda relacja, w której bierze jest automatycznie usuwana, a właściwość na drugim końcu jest aktualizowana.  
  
 Jeśli specyfikacja UML przypisuje liczebność 0.. 1 do właściwości, może mieć wartość `null`. Liczebność z wartością maksymalną większą niż 1 oznacza, że właściwość .NET jest typu: `IEnumerable<` *typu*`>`.  
  
 Aby uzyskać więcej informacji dotyczących nakierowanych relacji, zobacz [nawigowanie po relacjach z UML API](../modeling/navigate-relationships-with-the-uml-api.md).  
  
### <a name="the-ownership-tree"></a>Drzewo własności  
 Model zawiera drzewo <xref:Microsoft.VisualStudio.Uml.Classes.IElement> obiektów. Każdy element ma właściwości `OwnedElements` i `Owner`.  
  
 W większości przypadków obiekty docelowe `Owner` i `OwnedElements` właściwości odnoszą się również do innych właściwości, które mają bardziej szczegółowe nazwy. Na przykład każda operacja UML jest własnością klasy UML. W związku z tym <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> ma właściwość o nazwie <xref:Microsoft.VisualStudio.Uml.Classes.IOperation.Class%2A>, a następnie w każdej <xref:Microsoft.VisualStudio.Uml.Classes.IOperation> obiektu `Class == Owner`.  
  
 Jest elementem najwyższego drzewa, która nie ma właściciela, <xref:Microsoft.VisualStudio.Uml.AuxiliaryConstructs.IModel>. IModel jest zawarty w <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, w której jest <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore.Root%2A>.  
  
 Każdy element modelu jest tworzony z właścicielem. Aby uzyskać więcej informacji, zobacz [tworzenie elementów i relacji w modelach UML](../modeling/create-elements-and-relationships-in-uml-models.md).  
  
 ![Diagram klas: Model, Diagram, kształt i Element](../modeling/media/uml-mm1.png "UML_MM1")  
  
## <a name="shapes-and-diagrams"></a>Kształty i diagramy  
 Elementy modelu UML mogą być wyświetlane na diagramach. Różne rodzaje diagramów mogą wyświetlić różne podtypy IElement.  
  
 W niektórych przypadkach element może znajdować się na więcej niż jednym diagramie. Na przykład IUseCase element może mieć kilka elementów IShapes, które mogą być wyświetlane na jednym diagramie lub różnych diagramach.  
  
 Kształty są rozmieszczone w drzewie. Krawędzie drzewa są reprezentowane przez właściwości ParentShape i ChildShapes. Diagramy są jedynymi kształtami, które nie mają elementów nadrzędnych. Kształty znajdujące się na powierzchni diagramu składają się z mniejszych części. Na przykład kształt klasy posiada przedziały dla atrybutów i operacji.  
  
 Aby uzyskać więcej informacji na temat zdarzeń, zobacz [wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="access-to-the-model-in-extensions"></a>Dostęp do modelu w rozszerzeniach  
 W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeń zdefiniowanych jako składniki MEF, można zadeklarować właściwości, które importują informacje z kontekstu, w którym jest uruchamiane rozszerzenie.  
  
|Typ atrybutu|Czego to zapewnia dostęp do|Więcej informacji|  
|--------------------|----------------------------------|----------------------|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation<br /><br /> . IDiagramContext<br /><br /> (w Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll)|Bieżący diagram fokusowy.|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|  
|Microsoft.VisualStudio.Modeling.ExtensionEnablement<br /><br /> . ILinkedUndoContext<br /><br /> (w Microsoft.VisualStudio.Modeling.Sdk. [wersja] .dll)|Pozwala na pogrupowanie zmian w transakcje.|[Łączenie aktualizacji modelu UML za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md)|  
|Microsoft.VisualStudio.Shell. SVsServiceProvider<br /><br /> (w Microsoft.VisualStudio.Shell.Immutable. [wersja] .dll)|Host [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Z tego miejsca można uzyskać dostęp, plików, projektów i innych aspektów.|[Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)|  
  
### <a name="to-get-the-context"></a>Aby uzyskać kontekst  
 Zadeklaruj jeden lub oba z następujących interfejsów wewnątrz klasy rozszerzenia:  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
  
```  
  
 Managed Extensibility Framework (MEF), będą wiązać te definicje, w których można uzyskać bieżący diagram, Magazyn modeli, obiekt główny i tak dalej:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
IClassDiagram classDiagram = diagram as IClassDiagram;  
       // or diagrams of other types  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
### <a name="to-get-the-current-selection"></a>Aby uzyskać bieżące zaznaczenie  
  
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
  
-   Użyj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelu autobusu do tworzenia łączy między elementami w różnych modelach. Aby uzyskać więcej informacji, zobacz [modeli UML, integracja z innymi modelami i narzędziami](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Załaduj projekt modelowania i diagramy w trybie tylko do odczytu bez uwidaczniania tego w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Otwórz projekt modelowania i jego diagramów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], a następnie uzyskać dostęp do zawartości. Aby uzyskać więcej informacji, zobacz [Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)



