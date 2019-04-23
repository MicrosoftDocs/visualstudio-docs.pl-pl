---
title: Programowanie za pomocą interfejsu API UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e85fc0add84f6f6097355d1fc7a58cc954c8e538
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111756"
---
# <a name="programming-with-the-uml-api"></a>Programowanie za pomocą API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML interfejsu API programu Visual Studio pozwala napisać kod, aby utworzyć, odczytać i aktualizować modele UML i diagramy. Aby dowiedzieć się, które wersje programu Visual Studio obsługują modeli UML, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Oprócz stron referencyjnych interfejsu API w poniższych tematach opisano interfejs API.  
  
|Temat|Przykład typów i metod opisanych|Opisane funkcje|  
|-----------|-----------------------------------------|------------------------|  
|[Nawigowanie po relacjach za pomocą interfejsu API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Elementy UML i ich właściwości i skojarzenia. Na przykład IElement i jego elementy potomne, w tym: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|W programie Visual Studio, modele UML odpowiadają specyfikacji UML wersji 2.1.2, którą można uzyskać w [stronie zasobów UML](http://go.microsoft.com/fwlink/?LinkId=160796). Każdy typ jest interfejsem, który ma taką samą nazwę jak typ UML, poprzedzoną przedrostkiem "I".|  
|[Tworzenie elementów i relacji w modelach UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Każdy typ elementu posiada metody tworzenia jego obiektów podrzędnych.|  
|[Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Każdy element w modelu może być reprezentowany jako kształt na diagramie. W niektórych przypadkach można utworzyć nowe kształty dla każdego obiektu. Można przenieść, zmienić rozmiar, kolor i zwinąć lub rozwinąć te kształty.|  
|[Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Store modeli przechowuje model.<br /><br /> Kontekst Diagram daje dostęp do bieżącego diagramu i sklepu.|  
|[Łączenie aktualizacji modelu UML za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Można połączyć szereg zmian do jednej transakcji.|  
|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Możesz rozszerzyć funkcjonalność diagramu przez definiowanie polecenia wywoływanego przez dwukrotne kliknięcie i przeciągnięcie go na diagramie.|  
|[Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Można zdefiniować reguły, które ułatwiają upewnij się, że wzór spełnia określone ograniczenia sprawdzania.|  
|[Pobieranie elementów modelu UML z elementu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Gdy element zostanie przeciągnięty z Eksploratora modelu UML lub diagramu UML do innego diagramu lub aplikacji, jest serializowany jako IDataObject.|  
|[Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IMessage IInteraction, ILifeline,|Tworzenie i aktualizowanie diagramu interakcji jest nieco różne od pracy z innymi typami diagramów.|  
|[Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Można napisać kod, aby tworzyć i edytować warstwę diagramu i zweryfikować kod programu przed nimi.|  
  
## <a name="about-the-implementation"></a>Informacje na temat implementacji  
 Narzędzia modelowania UML są oparte na [!INCLUDE[dsl](../includes/dsl-md.md)]. Każdy pakiet i każdy diagram jest reprezentowany przez [!INCLUDE[dsl](../includes/dsl-md.md)] modelu, a kolekcja reguł i innych metod zachowujących spójność między nimi.  
  
 Typy z tej platformy są widoczne w niektórych zestawów, które odwołują się w celu napisania rozszerzenia UML. Chociaż można wykonać rozszerzenia do narzędzi UML po zalogowaniu się do [!INCLUDE[dsl](../includes/dsl-md.md)] interfejsu API, następujące kwestie należy mieć na uwadze:  
  
- Może się okazać, że niektóre pozornie proste zmiany wprowadzają niespójności i niespodziewane skutki.  
  
- Implementacja mogą ulec zmianie w przyszłości, tak aby dostosowania wprowadzone przez Ciebie za pomocą [!INCLUDE[dsl](../includes/dsl-md.md)] interfejsu API nie mogły już działać.  
  
## <a name="the-api-assemblies"></a>Zestawy API  
 Ta tabela zawiera zestawienie zestawy, które przewiduje rozszerzalności narzędzi UML i obszary nazw, które są zalecane do użycia.  
  
|Zestaw|Namespaces|Zapewnia dostęp do:|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Wszystkie)|Typy UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Metody tworzenia](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Diagramy i kształty](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Projekt modelowania](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Rozszerzenie menu polecenia](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Połączone cofnięcie transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Walidacja](../modeling/define-validation-constraints-for-uml-models.md)|  
||(inne przestrzenie nazw)|Zalecane tylko dla zaawansowanych.|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Program obsługi gestów](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(inne przestrzenie nazw)|Zalecane tylko dla zaawansowanych.|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[Łącza do elementów roboczych](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[Elementy robocze i ich pól](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[Elementy robocze i ich pól](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Eksportuj i Importuj składniki MEF](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Łatwe manipulowanie kolekcjami, szczególnie w przypadku, gdy chodzi o relacje](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
