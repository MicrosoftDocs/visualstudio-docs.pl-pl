---
title: Formularz pomocy technicznej w przepływach pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27e8ab6651c6838de92b8a3d83311ebd47fabcbb
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296193"
---
# <a name="form-support-in-workflows"></a>Obsługa formularzy w przepływach pracy
  Cztery rodzaje formularzy może służyć w przepływie pracy: skojarzenie, inicjowania, zadania i modyfikacji. Tych typów formularza może opierać się na formularzu ASPX lub formularza programu InfoPath. Poziom pomocy technicznej, który [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] udostępnia dla danego formularza zależy od wielu czynników, które są opisane w poniższych tabelach. Aby uzyskać więcej informacji na temat typów formularza przepływu pracy, zobacz [Przegląd formularzy przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=185228).  
  
## <a name="xml-refactoring"></a>Refaktoryzacja XML
 Po dodaniu ASPX skojarzenia i inicjacji formularz, aby [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementu projektu przepływu pracy, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatycznie refactors XML w przepływie pracy *Elements.xml* plik, aby zachować atrybut, który odwołuje się do skojarzenia lub formularza inicjowania zsynchronizowany przy każdej aktualizacji formularza nazwę lub wdrożenia ścieżkę lub został usunięty. Jednak kiedy używasz innych typów formularza w przepływie pracy, takich jak formularz zadania lub modyfikacji *Elements.xml* pliku nie jest zaprojektowane od nowa.  
  
## <a name="form-support-in-new-visual-studio-workflows"></a>Obsługa formularzy w nowych przepływów pracy programu Visual Studio
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocy technicznej dla różnych typów ASPX lub InfoPath formularzy w przepływach pracy, które są tworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formularza|Przepływ pracy utworzony w programie Visual Studio z formularzem ASPX|Przepływ pracy utworzony w programie Visual Studio za pomocą formularza programu InfoPath|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Skojarzenie|-Można dodać ASPX formularza skojarzenia do przepływu pracy przy użyciu **formularza skojarzenia przepływu pracy** szablon elementu.<br />*Elements.xml* plik przepływu pracy jest zaprojektowane od nowa po dodaniu, zmieniono jego nazwę lub usunięto formularza lub zmianie jego ścieżka wdrożenia.<br />-Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia nie programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Jest Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu InfoPath Designer.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|  
|Inicjowania|-Można dodać ASPX formularza inicjowania do przepływu pracy przy użyciu **formularza inicjowania przepływu pracy** szablon elementu.<br />*Elements.xml* plik przepływu pracy jest zaprojektowane od nowa po dodaniu, zmieniono jego nazwę lub usunięto formularza lub zmianie jego ścieżka wdrożenia.<br />-Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia nie programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Jest Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu InfoPath Designer.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|  
|Zadanie|-Brak szablonu formularza zadania ASPX jest dostępna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Należy utworzyć stronę aplikacji i dodać do niego kod.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.<br />-Aby uzyskać więcej informacji, zobacz [formularze zadania przepływu pracy (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-Jest nie szablonu formularza programu InfoPath zadań w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Jest Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu InfoPath Designer.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|  
|Modyfikacja|-Brak modyfikacji ASPX szablonem jest dostępna w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby dodać formularza modyfikacji, możesz utworzyć stronę aplikacji i dodać do niego kod.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa. Należy ręcznie zmodyfikować zgodnie z potrzebami.<br />-Aby uzyskać więcej informacji, zobacz [formularze modyfikacji przepływu pracy (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-Jest nie szablonu formularza programu InfoPath modyfikacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Jest Brak integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu InfoPath Designer.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|  
  
## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Obsługa formularzy w zaimportowanych przepływach pracy wielokrotnego użytku programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pomocy technicznej dla różnych typów ASPX lub InfoPath formularzy w przepływach pracy wielokrotnego użytku programu SharePoint, które są importowane do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Typ formularza|Przepływ pracy wielokrotnego użytku, który ma postać ASPX importowane z programu SharePoint Designer|Przepływ pracy wielokrotnego użytku, który ma formularza programu InfoPath, zaimportowane z programu SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------| - |  
|Skojarzenie|-Formularza mowa w punkcie *Elements.xml* plik przepływu pracy.<br />*Elements.xml* plik przepływu pracy jest zaprojektowane od nowa, gdy zmieniono jego nazwę lub usunięto formularza lub po zmianie jego ścieżki wdrażania.|-Formularza jest zaimportowane, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|  
|Inicjowania|-Formularza odwołuje się do przepływu pracy w *Elements.xml* plik przepływu pracy.<br />*Elements.xml* plik przepływu pracy jest zaprojektowane od nowa, gdy zmieniono jego nazwę lub usunięto formularza lub po zmianie jego ścieżki wdrażania.|-Formularza jest zaimportowane, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa. **Uwaga:** zasady i właściwości musi być dodany i zmienić dla tego scenariusza.|  
|Zadanie|-Formularza mowa w punkcie *Elements.xml* plik przepływu pracy.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa.|-Formularza jest zaimportowane, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />*Elements.xml* plik przepływu pracy nie zaprojektowane od nowa. **Uwaga:** zasady i właściwości musi być dodany i zmienić dla tego scenariusza.|  
|Modyfikacja|Nie dotyczy. Formularze modyfikacji ASPX, nie można utworzyć w programie SharePoint Designer.|Nie dotyczy. Formularze programu InfoPath modyfikacji nie można utworzyć w programie SharePoint Designer, z wyjątkiem wbudowanego serwera SharePoint przepływu pracy, która nie znajduje się w pliku wsp podczas eksportowania przepływu pracy.|  
  
## <a name="see-also"></a>Zobacz także
 [Wskazówki: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Tworzenie rozwiązań przepływu pracy SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  
