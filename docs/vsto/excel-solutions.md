---
title: rozwiązania programu Excel
description: Dowiedz się, w jaki sposób można używać szablonów projektów do automatyzowania programu Excel, rozszerzeń funkcji programu Excel i dostosowywania interfejsu użytkownika programu Excel
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3833ff549b2cceb3f783afc43a4f71dacc00ecb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931282"
---
# <a name="excel-solutions"></a>rozwiązania programu Excel
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dostosowań na poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Excel. Można używać tych rozwiązań do automatyzowania programu Excel, rozszerzeń funkcji programu Excel i dostosowywania interfejsu użytkownika programu Excel. Aby uzyskać więcej informacji o różnicach między dostosowaniami dostosowań na poziomie dokumentu a dodatkami programu VSTO, zobacz temat [programowanie rozwiązań pakietu Office — omówienie &#40;narzędzi vsto&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Ten temat zawiera następujące informacje:

- [Automatyzowanie programu Excel](#automating).

- [Opracowywanie dostosowań na poziomie dokumentu dla programu Excel](#doclevel).

- [Opracowywanie dodatków narzędzi VSTO dla programu Excel](#applevel).

- [Dostosuj interfejs użytkownika programu Excel](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Automatyzowanie programu Excel
 Model obiektów programu Excel udostępnia wiele typów, których można użyć do automatyzowania programu Excel. Na przykład można programowo tworzyć wykresy, formatować arkusze i ustawiać wartości zakresów i komórek. Aby uzyskać więcej informacji, zobacz [model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md).

 Podczas opracowywania rozwiązań programu Excel w programie Visual Studio można także używać *elementów hosta* i *kontrolek hosta* w swoich rozwiązaniach. Są to obiekty, które poszerzają niektóre często używane obiekty w modelu obiektów programu Excel, takie <xref:Microsoft.Office.Interop.Excel.Worksheet> jak <xref:Microsoft.Office.Interop.Excel.Range> obiekty i. Obiekty rozszerzone zachowują się jak obiekty programu Excel, na których się opierają, ale dodają do obiektów dodatkowe zdarzenia i możliwości powiązania danych. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Opracowywanie dostosowań na poziomie dokumentu dla programu Excel
 Dostosowanie na poziomie dokumentu dla Microsoft Office Excel składa się z zestawu, który jest skojarzony z określonym skoroszytem. Zestaw zwykle rozszerza skoroszyt przez dostosowanie interfejsu użytkownika i Automatyzowanie programu Excel. W przeciwieństwie do dodatku VSTO, który jest skojarzony z samym programem Excel, funkcjonalność zaimplementowana w dostosowaniu jest dostępna tylko wtedy, gdy skojarzony skoroszyt jest otwarty w programie Excel.

 Aby utworzyć projekt dostosowania na poziomie dokumentu dla programu Excel, użyj szablonów skoroszytu programu Excel lub projektu programu Excel w oknie dialogowym **Nowy projekt** programu Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać więcej informacji na temat sposobu działania dostosowań na poziomie dokumentu, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Model programowania dostosowywania programu Excel
 Po utworzeniu projektu na poziomie dokumentu dla programu Excel program Visual Studio generuje kilka klas, które są podstawą rozwiązania:,, `ThisWorkbook` `Sheet1` `Sheet2` , i `Sheet3` . Klasy te reprezentują skoroszyt i arkusze, które są skojarzone z Twoim roztworem i zapewniają punkt wyjścia do pisania kodu.

 Aby uzyskać więcej informacji na temat tych wygenerowanych klas i innych funkcji, których można użyć w projekcie na poziomie dokumentu, zobacz [dostosowania na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Opracowywanie dodatków narzędzi VSTO dla programu Excel
 Dodatek narzędzi VSTO dla programu Microsoft Office Excel składa się z zestawu, który jest ładowany przez program Excel. Zestaw zwykle rozszerza program Excel przez dostosowanie interfejsu użytkownika i Automatyzowanie programu Excel. W przeciwieństwie do dostosowania na poziomie dokumentu, który jest skojarzony z określonym skoroszytem, funkcje zaimplementowane w dodatku VSTO nie są ograniczone do żadnego pojedynczego skoroszytu.

 Aby utworzyć projekt dodatku VSTO dla programu Excel, użyj szablonów skoroszytu programu Excel lub projektu programu Excel w oknie dialogowym **Nowy projekt** programu Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać ogólne informacje o działaniu dodatków VSTO, zobacz [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Model programowania dodatku dla programu Excel
 Podczas tworzenia projektu dodatku VSTO dla programu Excel program Visual Studio generuje klasę o nazwie, `ThisAddIn` która jest podstawą rozwiązania. Ta klasa udostępnia punkt początkowy do pisania kodu, a także udostępnia model obiektów programu Excel do dodatku VSTO.

 Aby uzyskać więcej informacji o `ThisAddIn` klasie i innych funkcjach programu Visual Studio, których można użyć w dodatku narzędzi VSTO, zobacz [dodatek narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Dostosowywanie interfejsu użytkownika programu Excel
 Istnieje kilka różnych sposobów dostosowywania interfejsu użytkownika programu Excel. Niektóre opcje są dostępne dla wszystkich typów projektów, a inne opcje są dostępne tylko dla dodatków VSTO lub dostosowań na poziomie dokumentu.

### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne zarówno dla dostosowań na poziomie dokumentu, jak i dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Omówienie wstążki](../vsto/ribbon-overview.md)|
|Dodaj kontrolki Windows Forms lub rozszerzone kontrolki programu Excel do arkusza w dostosowanym skoroszycie dla dostosowania na poziomie dokumentu lub w dowolnym otwartym skoroszycie dla dodatku VSTO.|[Instrukcje: Dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Opcje dostosowywania na poziomie dokumentu
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dostosowań na poziomie dokumentu.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodaj okienko akcje do skoroszytu.|[Przegląd okienka Akcje](../vsto/actions-pane-overview.md)<br /><br /> [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Dodawanie formantów zakresu rozszerzonego, które są mapowane na węzły XML do arkusza.|[Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Opcje dodatków narzędzi VSTO
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Utwórz niestandardowe okienko zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Powiązane tematy

| Tytuł | Opis |
| - | - |
| [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md) | Zawiera przegląd typów głównych dostarczonych przez model obiektów programu Excel. |
| [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md) | Zawiera informacje o rozszerzonych obiektach (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program), których można użyć w rozwiązaniach programu Excel. |
| [Globalizacja i lokalizacja rozwiązań programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Zawiera informacje dotyczące specjalnych zagadnień dotyczących rozwiązań programu Excel, które będą uruchamiane na komputerach, które mają ustawienia inne niż angielskie dla systemu Windows. |
| [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md) | Opisuje, w jaki sposób można dodać kontrolki Windows Forms do arkuszy programu Excel. |
| [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Pokazuje, jak utworzyć podstawowe dostosowanie na poziomie dokumentu dla programu Excel. |
| [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Pokazuje, jak utworzyć podstawowy dodatek narzędzi VSTO dla programu Excel. |
| [Przewodnik: Dodawanie kontrolek do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Pokazuje, jak dodać przycisk Windows Forms, a <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza w czasie wykonywania przy użyciu dodatku VSTO. |
| [Omówienie współtworzenia i dodatków](./understanding-coauthoring-and-addins.md) | W tym artykule opisano zmiany, które mogą być konieczne w celu uwzględnienia współtworzenia rozwiązań. |
| [Excel 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Zawiera łącza do artykułów i dokumentacji referencyjnej dotyczącej tworzenia rozwiązań programu Excel. Nie są one specyficzne dla programowania pakietu Office przy użyciu programu Visual Studio. |
