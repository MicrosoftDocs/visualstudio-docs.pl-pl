---
title: Wytyczne dotyczące importowania wielokrotnych przepływów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 329d38e8c258148830347a506ceef5845c1cf268
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874279"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>Wytyczne dotyczące importowania wielokrotnych przepływów danych
  Aby zaimportować przepływów danych wielokrotnego użytku, utworzone w programie SharePoint Designer, należy użyć szablonu projektu Importowanie programu SharePoint 2010 przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ten szablon importuje *deklaratywne* *przepływu pracy* ([!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]— tylko) i konwertuje ją na *kodu przepływu pracy*, czyli przepływu pracy, które mogą poprawić z oboma [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] kodu. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Wskazówki: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
 Jednak szablonu Importowanie programu SharePoint 2010 przepływu pracy wielokrotnego użytku można importować tylko w rozwiązaniach farmy. Jeśli chcesz wdrożyć przepływ pracy jako rozwiązanie w trybie piaskownicy, należy go zaimportować za pomocą szablonu Importowanie pakietu rozwiązania programu SharePoint 2010. Jednak w ten sposób nie można przekonwertować go do kodu przepływu pracy i nie będzie można go modyfikować w związku z tym.  
  
## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>Importowanie przepływów danych wielokrotnego użytku, za pomocą szablonu przepływu pracy wielokrotnego użytku importu
 Jeśli importujesz wielokrotny przepływ przy użyciu szablonu importowanie wielokrotnego użytku programu SharePoint 2010 przepływu pracy, można uruchomić lub zmienić rozwiązania, tak jak każdy inny [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint, ale może być konieczne ręcznie rozwiązać niektóre elementy.  
  
### <a name="import-task-forms"></a>Formularze zadań importu
 Szablon projektu przepływu pracy programu importowanie wielokrotnego użytku programu SharePoint 2010 importuje wszystkie formularze inicjacji i skojarzenia, ale importuje tylko jedno zadanie formularza, ponieważ schemat przepływów pracy kodu zezwala tylko na jeden formularz zadania. Wszystkie formularze dodatkowego zadania z oryginalnym rozwiązaniu przepływu pracy są umieszczane w **inne zaimportowane pliki** folderu w **Eksploratora rozwiązań**.  
  
## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>Importowanie przepływów danych wielokrotnego użytku, za pomocą szablonu Importowanie pakietu rozwiązań programu SharePoint 2010
 Jeśli importujesz wielokrotny przepływ przy użyciu szablonu Importowanie pakietu rozwiązania programu SharePoint 2010, należy wziąć pod uwagę następujące kwestie:  
  
-   Po zaimportowaniu przepływu pracy, można natychmiast wdrożyć i uruchomić go w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierając **F5** klucza. Jednak jeśli zmienisz niczego w przepływie pracy w rozwiązaniu importowanych, może być konieczne ręcznie rozwiązać elementy w projekcie, zanim można wdrożyć i uruchomić przepływ pracy.  
  
-   Ponieważ przepływ pracy jest deklaratywnym, kod nie można dodać do niego. Aby przekonwertować przepływu pracy do przepływu pracy kodu, należy zaimportować go do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu szablonu importowania programu SharePoint 2010 przepływu pracy wielokrotnego użytku.  
  
-   Chociaż można edytować plik projektanta (xoml) przepływu pracy w widoku Projekt, zaleca się edytować ją w widoku źródła ponieważ projektanta przepływów pracy wyświetla fałszywe błędy.  
  
-   Debugowanie w przepływie pracy nie działa w przypadku deklaratywne zawartości. Punkty przerwania ustawione w [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] nie są osiągane.  
  
## <a name="import-globally-reusable-workflow-solutions"></a>Importowanie rozwiązania globalnie wielokrotny przepływ danych
 Nie można zaimportować globalnie wielokrotnych przepływów danych przy użyciu szablonu przepływu pracy importowania wielokrotnego użytku programu SharePoint 2010. Aby zaimportować globalny wielokrotny przepływ danych programu, należy je przekształcić w skali globalnej wielokrotny przepływ danych programu, lub należy użyć szablonu Importowanie pakietu rozwiązania programu SharePoint 2010.  
  
 Aby przekonwertować przepływu pracy, należy utworzyć kopię globalnie wielokrotny przepływ danych w programie SharePoint Designer (, otwierając menu skrótów dla przepływu pracy, a następnie wybierając **Zapisz jako kopię**). Następnie zaimportuj nowy przepływ pracy wielokrotnego użytku z szablonem Importowanie programu SharePoint 2010 przepływu pracy wielokrotnego użytku w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Aby zaimportować globalny wielokrotny przepływ danych bez modyfikowania go, należy użyć szablonu Importowanie pakietu rozwiązania programu SharePoint 2010. Jeśli ta metoda przepływu pracy nie jest konwertowana na przepływie pracy kodu i pozostaje deklaracyjnego przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także
 [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)  
