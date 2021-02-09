---
title: Obsługa formularzy w przepływach pracy | Microsoft Docs
description: 'Przeczytaj informacje o obsłudze formularzy w przepływach pracy programu SharePoint. W przepływie pracy można używać czterech typów formularzy: skojarzenia, inicjacji, zadania i modyfikacji.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adf5de014c7921130bd6f3ecd3cf8c5bb5daa92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876683"
---
# <a name="form-support-in-workflows"></a>Obsługa formularzy w przepływach pracy
  W przepływie pracy można używać czterech typów formularzy: skojarzenia, inicjacji, zadania i modyfikacji. Te typy formularzy mogą opierać się na formularzu ASPX lub formularzu programu InfoPath. Poziom obsługi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapewniany dla określonego formularza zależy od kilku czynników, które są opisane w poniższych tabelach. Aby uzyskać więcej informacji na temat typów formularzy przepływu pracy, zobacz [Omówienie formularzy przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14)).

## <a name="xml-refactoring"></a>Refaktoryzacja kodu XML
 Po dodaniu skojarzenia ASPX lub formularza inicjowania do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementu projektu przepływu pracy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatycznie REFAKTORYZACJA kodu XML w pliku *Elements.xml* przepływu pracy, aby zachować atrybut odwołujący się do skojarzenia lub formularza inicjowania w synchronizacji za każdym razem, gdy nazwa formularza lub ścieżka wdrożenia zostanie zaktualizowana lub formularz zostanie usunięty. Jednak w przypadku korzystania z innych typów formularzy w przepływie pracy, takich jak zadanie lub formularz modyfikacji, plik *Elements.xml* nie jest używany do refaktoryzacji.

## <a name="form-support-in-new-visual-studio-workflows"></a>Obsługa formularzy w nowych przepływach pracy programu Visual Studio
 W poniższej tabeli przedstawiono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługę różnych typów formularzy dla formularzy aspx lub programu InfoPath w przepływach pracy, które zostały utworzone w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Typ formularza|Przepływ pracy utworzony w programie Visual Studio z formularzem ASPX|Przepływ pracy utworzony w programie Visual Studio przy użyciu formularza programu InfoPath|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|Skojarzenie|-Formularz skojarzenia ASPX można dodać do przepływu pracy przy użyciu szablonu elementu **formularza skojarzenia przepływu pracy** .<br />- *Elements.xml* plik przepływu pracy jest refaktoryzacją, gdy formularz zostanie dodany, zmieniono jego nazwę lub usunięty lub gdy jego ścieżka wdrożenia ulegnie zmianie.<br />-Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie przepływu pracy przy użyciu formularzy skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programem a projektantem programu InfoPath.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|
|Rozpoczęcie|-Formularz inicjacji ASPX można dodać do przepływu pracy przy użyciu szablonu elementu **formularza inicjowania przepływu pracy** .<br />- *Elements.xml* plik przepływu pracy jest refaktoryzacją, gdy formularz zostanie dodany, zmieniono jego nazwę lub usunięty lub gdy jego ścieżka wdrożenia ulegnie zmianie.<br />-Aby uzyskać więcej informacji, zobacz [Przewodnik: tworzenie przepływu pracy przy użyciu formularzy skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-Brak szablonu formularza skojarzenia programu InfoPath w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programem a projektantem programu InfoPath.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|
|Zadanie|— Szablon formularza zadania ASPX nie jest dostępny w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Należy utworzyć stronę aplikacji i dodać do niej kod.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.<br />-Aby uzyskać więcej informacji, zobacz [formularze zadań przepływu pracy (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14))|-Nie ma szablonu formularza zadania programu InfoPath w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programem a projektantem programu InfoPath.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|
|Modyfikowanie|— Szablon formularza modyfikacji ASPX nie jest dostępny w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby dodać formularz modyfikacji, należy utworzyć stronę aplikacji i dodać do niej kod.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją. Należy ręcznie edytować go zgodnie z potrzebami.<br />-Aby uzyskać więcej informacji, zobacz [formularze modyfikacji przepływu pracy (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14))|— W programie nie ma szablonu formularza modyfikacji programu InfoPath [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />— Nie ma integracji między [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programem a projektantem programu InfoPath.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>Obsługa formularzy w zaimportowanych przepływach pracy wielokrotnego użytku programu SharePoint
 W poniższej tabeli przedstawiono [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsługę różnych typów formularzy dla formularzy aspx lub programu InfoPath w ramach przepływów pracy wielokrotnego użytku programu SharePoint, które są importowane do usługi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|Typ formularza|Przepływ pracy wielokrotnego użytku z formularzem ASPX zaimportowanym z programu SharePoint Designer|Przepływ pracy wielokrotnego użytku z formularzem programu InfoPath zaimportowany z programu SharePoint Designer|
|---------------|-------------------------------------------------------------------------------| - |
|Skojarzenie|— Odwołanie do formularza znajduje się w pliku *Elements.xml* przepływu pracy.<br />- *Elements.xml* plik przepływu pracy jest zastępowany po zmianie nazwy lub usunięciu formularza lub po zmianie jego ścieżki wdrożenia.|— Formularz zostanie zaimportowany, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|
|Rozpoczęcie|-Do formularza odwołuje się przepływ pracy w pliku *Elements.xml* przepływu pracy.<br />- *Elements.xml* plik przepływu pracy jest zastępowany po zmianie nazwy lub usunięciu formularza lub po zmianie jego ścieżki wdrożenia.|— Formularz zostanie zaimportowany, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją. **Uwaga:**  Aby ten scenariusz działał, należy dodać i zmienić reguły i właściwości.|
|Zadanie|— Odwołanie do formularza znajduje się w pliku *Elements.xml* przepływu pracy.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją.|— Formularz zostanie zaimportowany, ale nie jest przywoływany w *Elements.xml* przepływu pracy.<br />-Plik *Elements.xml* przepływu pracy nie jest refaktoryzacją. **Uwaga:**  Aby ten scenariusz działał, należy dodać i zmienić reguły i właściwości.|
|Modyfikowanie|Nie dotyczy. Formularzy modyfikacji ASPX nie można tworzyć w programie SharePoint Designer.|Nie dotyczy. Formularzy modyfikacji programu InfoPath nie można tworzyć w programie SharePoint Designer, z wyjątkiem wbudowanego przepływu pracy programu SharePoint Server, który nie jest zawarty w pliku wsp podczas eksportowania przepływu pracy.|

## <a name="see-also"></a>Zobacz też
- [Przewodnik: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Importuj elementy z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
