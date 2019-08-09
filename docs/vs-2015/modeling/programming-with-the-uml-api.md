---
title: Programowanie za pomocą interfejsu API UML | Microsoft Docs
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
ms.openlocfilehash: d0cd086221b1c0ee6a4e2111cda543a3f8f4ec0e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871763"
---
# <a name="programming-with-the-uml-api"></a>Programowanie za pomocą API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Interfejs API UML programu Visual Studio umożliwia pisanie kodu umożliwiającego tworzenie, odczytywanie i aktualizowanie modeli i diagramów UML. Aby sprawdzić, które wersje programu Visual Studio obsługują modele UML, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Oprócz stron referencyjnych interfejsu API w poniższych tematach opisano interfejs API.

|Temat|Przykładowe typy i metody opisane|Opisane funkcje|
|-----------|-----------------------------------------|------------------------|
|[Nawigowanie po relacjach za pomocą interfejsu API UML](../modeling/navigate-relationships-with-the-uml-api.md)|Elementy UML i ich właściwości i skojarzenia. Na przykład IElement i jego elementy podrzędne, w tym: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|W programie Visual Studio modele UML są zgodne ze specyfikacją języka UML w wersji 2.1.2, którą można uzyskać na [stronie zasobów UML](http://go.microsoft.com/fwlink/?LinkId=160796). Każdy typ jest interfejsem, który ma taką samą nazwę jak typ UML, poprzedzony prefiksem "I".|
|[Tworzenie elementów i relacji w modelach UML](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Każdy typ elementu ma metody do tworzenia elementów podrzędnych.|
|[Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Każdy element w modelu może być reprezentowany jako kształt na diagramie. W niektórych przypadkach można utworzyć nowe kształty dla każdego obiektu. Można przenosić, zmieniać rozmiar, kolorować i zwijać lub rozwijać te kształty.|
|[Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Magazyn modeli przechowuje model.<br /><br /> Kontekst diagramu zapewnia dostęp do bieżącego diagramu i magazynu.|
|[Łączenie aktualizacji modelu UML za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Możesz połączyć serię zmian w jedną transakcję.|
|[Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Można zwiększyć funkcjonalność diagramu przez definiowanie poleceń wywoływanych przez dwukrotne kliknięcie i przeciągnięcie na diagram.|
|[Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Można zdefiniować reguły walidacji, które pomagają upewnić się, że model jest zgodny z określonymi ograniczeniami.|
|[Pobieranie elementów modelu UML z elementu IDataObject](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Gdy element zostanie przeciągnięty z Eksploratora modelu UML lub diagramu UML do innego diagramu lub aplikacji, jest on serializowany jako IDataObject.|
|[Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Tworzenie i aktualizowanie diagramu interakcji różni się nieco od pracy z innymi typami diagramów.|
|[Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Można napisać kod, aby tworzyć i edytować Diagramy warstw, a także sprawdzać poprawność kodu programu.|

## <a name="about-the-implementation"></a>Informacje o implementacji
 Narzędzia modelowania UML są wbudowane [!INCLUDE[dsl](../includes/dsl-md.md)]. Każdy pakiet i każdy diagram są reprezentowane przez [!INCLUDE[dsl](../includes/dsl-md.md)] model, a zbiór reguł i innych metod zachowuje spójność między nimi.

 Typy z tej platformy są widoczne w niektórych zestawach, do których odwołuje się w celu zapisania rozszerzeń UML. Chociaż można wprowadzać rozszerzenia narzędzi UML, uzyskując dostęp [!INCLUDE[dsl](../includes/dsl-md.md)] do interfejsu API, należy zwrócić uwagę na następujące kwestie:

- Może się okazać, że niektóre pozornie proste zmiany wprowadzają niespójności i nieoczekiwane efekty.

- Implementacja może ulec zmianie w przyszłości, dzięki czemu adaptacje wprowadzone przy użyciu [!INCLUDE[dsl](../includes/dsl-md.md)] interfejsu API mogą przestać działać.

## <a name="the-api-assemblies"></a>Zestawy interfejsów API
 Ta tabela zawiera podsumowanie zestawów, które zapewniają rozszerzalność narzędzi UML i przestrzenie nazw, których należy użyć.

|Zestaw|Namespaces|Zapewnia dostęp do:|
|--------------|----------------|-------------------------|
|Microsoft.VisualStudio.Uml.Interfaces|Całą|Typy UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Microsoft. VisualStudio. ArchitectureTools. rozszerzalność. UML|[Metody tworzenia](../modeling/create-elements-and-relationships-in-uml-models.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation|[Diagramy i kształty](../modeling/display-a-uml-model-on-diagrams.md)|
||Microsoft.VisualStudio.ArchitectureTools.Extensibility|[Projekt modelowania](../modeling/read-a-uml-model-in-program-code.md)|
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Rozszerzenie polecenia menu](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Połączone transakcje cofania](../modeling/link-uml-model-updates-by-using-transactions.md).|
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Walidacja](../modeling/define-validation-constraints-for-uml-models.md)|
||(inne przestrzenie nazw)|Zalecane tylko do użycia zaawansowanego.|
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Programy obsługi gestów](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|
||(inne przestrzenie nazw)|Zalecane tylko do użycia zaawansowanego.|
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|[Linki do elementów roboczych](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.WorkItemTracking.Client|Microsoft.TeamFoundation.WorkItemTracking.Client|[Elementy robocze i ich pola](../modeling/define-a-work-item-link-handler.md).|
|Microsoft.TeamFoundation.Client|Microsoft.TeamFoundation.Client|[Elementy robocze i ich pola](../modeling/define-a-work-item-link-handler.md).|
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Eksportowanie i importowanie dla składników MEF](../modeling/define-and-install-a-modeling-extension.md)|
|System.Linq|<xref:System.Linq>|[Łatwe manipulowanie kolekcjami, szczególnie w przypadku pracy z relacjami](../modeling/navigate-relationships-with-the-uml-api.md).|

## <a name="see-also"></a>Zobacz też
 [Rozszerzając modele i diagramy UML](../modeling/extend-uml-models-and-diagrams.md) [Dokumentacja interfejsu API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
