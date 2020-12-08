---
title: Funkcje dostępne według aplikacji pakietu Office i typu projektu
description: Dowiedz się, w jaki sposób program Visual Studio zawiera kilka typów szablonów projektów, które obsługują różne scenariusze biznesowe dla Microsoft Office aplikacji.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24db499602642f6ec980628d290ec8b5dd07fed3
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847809"
---
# <a name="features-available-by-office-application-and-project-type"></a>Funkcje dostępne według aplikacji pakietu Office i typu projektu
  Program Visual Studio zawiera kilka typów szablonów projektów, które obsługują różne scenariusze biznesowe dla Microsoft Office aplikacji, w tym następujące typy:

- Dostosowania na poziomie dokumentu.

- Dodatki narzędzi VSTO.

  Nie wszystkie aplikacje mogą używać każdego typu projektu. Na przykład projekty na poziomie dokumentu są dostępne tylko dla programów Microsoft Office Word i Microsoft Office Excel. Podobnie niektóre funkcje są dostępne tylko dla niektórych typów projektów lub aplikacji. Na przykład okienko akcje jest dostępne tylko w projektach na poziomie dokumentu, a rozszerzenia wstążki są dostępne tylko dla niektórych aplikacji. Aby uzyskać więcej informacji na temat różnych typów projektów, zobacz [Omówienie tworzenia rozwiązań pakietu Office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Szablony projektów pakietu Office są dostępne tylko w niektórych wersjach programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Typy projektów dostępne dla różnych aplikacji Microsoft Office
 W poniższej tabeli przedstawiono aplikacje, których można użyć w przypadku każdego typu projektu.

|Typy projektów|Aplikacja Microsoft Office|
|-------------------|----------------------------------|
|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|
|Dodatki narzędzi VSTO|Excel<br /><br /> InfoPath (tylko InfoPath 2013 i InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Funkcje dostępne w różnych typach projektów
 W poniższej tabeli pokazano, które typy projektów zapewniają każdą funkcję.

|Cechy|Typy projektów, które udostępniają funkcję|Dalsze informacje|
|-------------|--------------------------------------------|---------------------|
|Okienko akcji.|Projekty na poziomie dokumentu.|[Przegląd okienka Akcje](../vsto/actions-pane-overview.md)|
|Wdrożenie ClickOnce.|Projekty a i na poziomie dokumentu.|[Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)|
|Niestandardowe okienka zadań.|Projekty dodatków VSTO dla następujących aplikacji:<br /><br /> — Excel<br />— InfoPath (tylko InfoPath 2013 i InfoPath 2010)<br />-Outlook<br />— PowerPoint<br />-Word|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|
|Niestandardowe części XML.|Projekty na poziomie dokumentu.<br /><br /> Projekty na poziomie aplikacji dla następujących aplikacji:<br /><br /> — Excel<br />— PowerPoint<br />-Word|[Niestandardowe części XML — Omówienie](../vsto/custom-xml-parts-overview.md)|
|Pamięć podręczna danych.|Projekty na poziomie dokumentu.|[Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)|
|Uwidacznianie obiektu w dodatku VSTO do innych rozwiązań Microsoft Office.|Projekty dodatku VSTO.|[Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Następujące kontrolki hosta:<br /><br /> -Wykres<br />-ListObject<br />-NamedRange<br />— Kontrolki zawartości<br />— Zakładka|Projekty na poziomie dokumentu.<br /><br /> Projekty dodatków VSTO dla programów Word i Excel.|[Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)|
|Następujące kontrolki hosta:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Projekty na poziomie dokumentu.|[Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)|
|Wdrożenie wiele projektów.|Projekty na poziomie dokumentu.<br /><br /> Projekty dodatku VSTO.|[Przewodnik: wdrażanie wielu rozwiązań pakietu Office w jednym instalatorze ClickOnce](/previous-versions/dd465290(v=vs.110))|
|Regiony formularzy programu Outlook.|Projekty dodatków VSTO dla programu Outlook.|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|
|Akcje po wdrożeniu.|Projekty na poziomie dokumentu.<br /><br /> Projekty dodatku VSTO.|[Przewodnik: kopiowanie dokumentu na komputer użytkownika końcowego po instalacji ClickOnce](/previous-versions/dd465291(v=vs.110))|
|Dostosowania wstążki.|Projekty na poziomie dokumentu.<br /><br /> Projekty dodatków VSTO dla następujących aplikacji:<br /><br /> — Excel<br />— InfoPath (tylko InfoPath 2013 i InfoPath 2010)<br />-Outlook<br />— PowerPoint<br />— Projekt<br />— Visio<br />-Word|[Omówienie wstążki](../vsto/ribbon-overview.md)|
|Visual Document Designer.|Projekty na poziomie dokumentu.|[Projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)