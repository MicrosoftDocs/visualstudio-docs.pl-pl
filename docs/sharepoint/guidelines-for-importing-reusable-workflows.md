---
title: Wytyczne dotyczące importowania przepływów pracy wielokrotnego użytku | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb386a2d80931ece415b0b3939f2947678808261
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557191"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Wytyczne dotyczące importowania przepływów pracy wielokrotnego użytku
  Aby zaimportować przepływy pracy wielokrotnego użytku utworzonych w programie SharePoint Designer, użyj szablonu projektu przepływu pracy programu SharePoint 2010 do ponownego wykorzystania [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Ten szablon polega na zaimportowaniu *deklaratywnego* *przepływu pracy* ( [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] tylko-) i przekonwertowaniu go do *przepływu pracy w kodzie*, który jest przepływem pracy, który można rozszerzyć za pomocą [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] kodu lub. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 Szablon przepływu pracy programu SharePoint 2010 można jednak zaimportować do wielokrotnego użytku. Jeśli chcesz wdrożyć przepływ pracy jako rozwiązanie w trybie piaskownicy, zaimportuj go za pomocą szablonu Importuj pakiet rozwiązania programu SharePoint 2010. Jednak dzięki temu nie można przekonwertować go na przepływ pracy kodu i nie będzie można go modyfikować.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importowanie przepływów pracy wielokrotnego użytku przy użyciu szablonu przepływu pracy do wielokrotnego użytku
 W przypadku zaimportowania przepływu pracy wielokrotnego użytku przy użyciu szablonu przepływu pracy do importowania programu SharePoint 2010 można uruchomić lub zmienić rozwiązanie tak samo jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązanie programu SharePoint, ale może być konieczne ręczne poprawienie niektórych elementów.

### <a name="import-task-forms"></a>Importuj formularze zadań
 Szablon projektu przepływu pracy programu SharePoint 2010 importu wielokrotnego użytku importuje wszystkie formularze inicjacji i skojarzenia, ale importuje tylko jeden formularz zadania, ponieważ schemat przepływu pracy kodu zezwala tylko na jeden formularz zadania. Wszystkie dodatkowe formularze zadań z oryginalnego rozwiązania przepływu pracy są umieszczane w folderze **inne zaimportowane pliki** w **Eksplorator rozwiązań**.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importuj przepływy pracy wielokrotnego użytku przy użyciu szablonu pakietu rozwiązań programu SharePoint 2010
 W przypadku importowania przepływu pracy wielokrotnego użytku przy użyciu szablonu pakietu rozwiązań programu SharePoint 2010 należy wziąć pod uwagę następujące problemy:

- Po zaimportowaniu przepływu pracy można go natychmiast wdrożyć i uruchomić w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierając klawisz **F5** . Jeśli jednak zmienisz wszystko w przepływie pracy w zaimportowanym rozwiązaniu, może być konieczne ręczne poprawienie elementów w projekcie przed wdrożeniem i uruchomieniem przepływu pracy.

- Ponieważ przepływ pracy jest deklaratywny, nie można dodać do niego kodu. Aby skonwertować przepływ pracy do przepływu pracy w kodzie, należy zaimportować go do programu przy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] użyciu szablonu przepływu pracy do importowania w programie SharePoint 2010.

- Chociaż można edytować plik projektanta przepływu pracy (xoml) w widok Projekt, zaleca się jego edytowanie w widoku źródła, ponieważ Projektant przepływu pracy wyświetla fałszywe błędy.

- Debugowanie w przepływie pracy nie działa w przypadku zawartości deklaracyjnej. Punkty przerwania ustawione w elemencie [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] nie są trafień.

## <a name="import-globally-reusable-workflow-solutions"></a>Importuj globalnie roztwory przepływu pracy wielokrotnego użytku
 Przepływy pracy wielokrotnego użytku nie można zaimportować za pomocą szablonu przepływu pracy programu SharePoint 2010 do ponownego użycia. W celu zaimportowania globalnego przepływu pracy wielokrotnego użytku należy go przekonwertować do przepływu pracy, który nie jest globalnie wielokrotnego użytku, lub należy użyć szablonu importowania pakietu rozwiązania programu SharePoint 2010.

 Aby przekonwertować przepływ pracy, Utwórz kopię przepływu pracy wielokrotnego użytku w programie SharePoint Designer (otwierając menu skrótów dla przepływu pracy, a następnie wybierając pozycję **Zapisz jako kopię**). Następnie zaimportuj nowy przepływ pracy wielokrotnego użytku z szablonem przepływu pracy programu SharePoint 2010 wielokrotnego użytku w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Aby zaimportować przepływ pracy wielokrotnego użytku, które nie są modyfikowane, użyj szablonu pakietu rozwiązań programu SharePoint 2010. W przypadku korzystania z tej metody przepływ pracy nie jest konwertowany do przepływu pracy kodu i pozostaje deklaratywnym przepływem pracy.

## <a name="see-also"></a>Zobacz też
- [Importuj elementy z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
