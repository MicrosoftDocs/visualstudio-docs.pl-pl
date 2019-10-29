---
title: Obsługa formularzy w przepływach pracy | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986261"
---
# <a name="form-support-in-workflows"></a>Obsługa formularzy w przepływach pracy
  W przepływie pracy można używać czterech typów formularzy: skojarzenia, inicjacji, zadania i modyfikacji. Te typy formularzy mogą opierać się na formularzu ASPX lub formularzu programu InfoPath. Poziom pomocy technicznej, który [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapewnia dla konkretnego formularza, zależy od kilku czynników, które są opisane w poniższych tabelach. Aby uzyskać więcej informacji na temat typów formularzy przepływu pracy, zobacz [Omówienie formularzy przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refaktoryzacja kodu XML
 Gdy dodasz skojarzenie ASPX lub formularz inicjowania do elementu projektu przepływu pracy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatycznie refaktoryzację kodu XML w pliku *XML elementów* przepływu pracy, aby zachować atrybut odwołujący się do skojarzenia lub formularza inicjacji w synchronizacji za każdym razem, gdy nazwa formularza lub ścieżka wdrożenia zostanie zaktualizowana lub formularz zostanie usunięty. Jednak w przypadku używania innych typów formularzy w przepływie pracy, takich jak zadanie lub formularz modyfikacji, plik *elementy. XML* nie jest używany do refaktoryzacji.

## <a name="form-support-in-new-visual-studio-workflows"></a>Obsługa formularzy w nowych przepływach pracy programu Visual Studio
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługę różnych typów formularzy w formularzach ASPX lub InfoPath w przepływach pracy, które są tworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Typ formularza|Przepływ pracy utworzony w programie Visual Studio z formularzem ASPX|Przepływ pracy utworzony w programie Visual Studio przy użyciu formularza programu InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Skojarzenie|-Formularz skojarzenia ASPX można dodać do przepływu pracy przy użyciu szablonu elementu **formularza skojarzenia przepływu pracy** .<br />-Plik *Elements. XML* przepływu pracy jest ponownie dodawany po dodaniu formularza, zmianie nazwy lub usunięciu lub po zmianie jego ścieżki wdrożenia.<br />-Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie przepływu pracy przy użyciu formularzy skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektantem programu InfoPath.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|
|Rozpoczęcie|-Formularz inicjacji ASPX można dodać do przepływu pracy przy użyciu szablonu elementu **formularza inicjowania przepływu pracy** .<br />-Plik *Elements. XML* przepływu pracy jest ponownie dodawany po dodaniu formularza, zmianie nazwy lub usunięciu lub po zmianie jego ścieżki wdrożenia.<br />-Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie przepływu pracy przy użyciu formularzy skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektantem programu InfoPath.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|
|Zadanie|-Żaden szablon formularza zadania ASPX nie jest dostępny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Należy utworzyć stronę aplikacji i dodać do niej kod.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.<br />-Aby uzyskać więcej informacji, zobacz [formularze zadań przepływu pracy (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-Nie ma szablonu formularza zadania programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektantem programu InfoPath.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|
|Modyfikacji|-W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]nie jest dostępny żaden szablon formularza modyfikacji ASPX. Aby dodać formularz modyfikacji, należy utworzyć stronę aplikacji i dodać do niej kod.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją. Należy ręcznie edytować go zgodnie z potrzebami.<br />-Aby uzyskać więcej informacji, zobacz [formularze modyfikacji przepływu pracy (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|-Nie ma szablonu formularza modyfikacji programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i projektantem programu InfoPath.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Obsługa formularzy w zaimportowanych przepływach pracy wielokrotnego użytku programu SharePoint
 W poniższej tabeli wymieniono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługę różnych typów formularzy w formularzach ASPX lub programu InfoPath w ramach przepływów pracy wielokrotnego użytku programu SharePoint, które są importowane do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

|Typ formularza|Przepływ pracy wielokrotnego użytku z formularzem ASPX zaimportowanym z programu SharePoint Designer|Przepływ pracy wielokrotnego użytku z formularzem programu InfoPath zaimportowany z programu SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Skojarzenie|— Odwołanie do formularza znajduje się w pliku *elementy. XML* przepływu pracy.<br />-Plik *Elements. XML* przepływu pracy jest zastępowany po zmianie nazwy lub usunięciu formularza lub po zmianie jego ścieżki wdrożenia.|— Formularz jest importowany, ale nie jest przywoływany w *elementach. XML* przepływu pracy.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|
|Rozpoczęcie|-Formularz jest przywoływany przez przepływ pracy w pliku *elementy. XML* przepływu pracy.<br />-Plik *Elements. XML* przepływu pracy jest zastępowany po zmianie nazwy lub usunięciu formularza lub po zmianie jego ścieżki wdrożenia.|— Formularz jest importowany, ale nie jest przywoływany w *elementach. XML* przepływu pracy.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją. **Uwaga:**  Aby ten scenariusz działał, należy dodać i zmienić reguły i właściwości.|
|Zadanie|— Odwołanie do formularza znajduje się w pliku *elementy. XML* przepływu pracy.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją.|— Formularz jest importowany, ale nie jest przywoływany w *elementach. XML* przepływu pracy.<br />-Plik *elementów. XML* przepływu pracy nie jest refaktoryzacją. **Uwaga:**  Aby ten scenariusz działał, należy dodać i zmienić reguły i właściwości.|
|Modyfikacji|Nie dotyczy. Formularzy modyfikacji ASPX nie można tworzyć w programie SharePoint Designer.|Nie dotyczy. Formularzy modyfikacji programu InfoPath nie można tworzyć w programie SharePoint Designer, z wyjątkiem wbudowanego przepływu pracy programu SharePoint Server, który nie jest zawarty w pliku wsp podczas eksportowania przepływu pracy.|

## <a name="see-also"></a>Zobacz także
- [Przewodnik: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importuj elementy z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
