---
title: rozwiązania programu Excel
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cb370be32929436fb6d37ff70837470ee8196689
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863802"
---
# <a name="excel-solutions"></a>rozwiązania programu Excel
  Program Visual Studio udostępnia szablony projektów, których można użyć do utworzenia dostosowań poziomu dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Excel. Automatyzowanie programu Excel, rozszerzania funkcji programu Excel i dostosowywanie interfejsu użytkownika (UI) programu Excel, można użyć tych rozwiązań. Aby uzyskać więcej informacji na temat różnic między dostosowań na poziomie dokumentu i dodatków narzędzi VSTO dla programów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  

> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  

 Ten temat zawiera następujące informacje:  

-   [Automatyzowanie programu Excel](#automating).  

-   [Opracowywanie dostosowań poziomu dokumentu dla programu Excel](#doclevel).  

-   [Tworzenie dodatków narzędzi VSTO dla programu Excel](#applevel).  

-   [Dostosowywanie interfejsu użytkownika programu Excel](#UI).  

##  <a name="automating"></a> Automatyzowanie programu Excel  
 Model obiektów programu Excel uwidacznia wiele typów, których można użyć do zautomatyzowania programu Excel. Na przykład możesz można programowo tworzyć wykresy, sformatuj arkuszy i ustaw wartości zakresów i komórek. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).  

 Podczas opracowywania rozwiązania programu Excel w programie Visual Studio, możesz również użyć *hostować elementy* i *hostowania kontrolek* w posiadanych rozwiązaniach. Są to obiekty, które rozszerzają niektóre powszechnie używane obiekty w modelu obiektów programu Excel, takich jak <xref:Microsoft.Office.Interop.Excel.Worksheet> i <xref:Microsoft.Office.Interop.Excel.Range> obiektów. Obiekty rozszerzone zachowują się jak obiekty programu Excel, które są one oparte na, ale dodają dodatkowe zdarzenia i możliwości wiązania danych do obiektów. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md).  

##  <a name="doclevel"></a> Opracowywanie dostosowań poziomu dokumentu dla programu Excel  
 Dostosowania poziomu dokumentu dla programu Microsoft Office Excel składa się z zestawu, który jest skojarzony z określonym skoroszycie. Zestaw zazwyczaj rozszerza skoroszyt przez dostosowanie interfejsu użytkownika i automatyzowanie programu Excel. W przeciwieństwie do dodatku narzędzi VSTO, który jest skojarzony z programem Excel, samego, funkcja implementowana w dostosowaniu jest dostępna tylko wtedy, gdy skojarzony skoroszyt jest otwarty w programie Excel.  

 Aby utworzyć projekt dostosowania poziomu dokumentu dla programu Excel, należy użyć skoroszyt programu Excel lub szablonów projektu szablon programu Excel w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 Aby uzyskać więcej informacji na temat działania dostosowań na poziomie dokumentów, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  

### <a name="excel-customization-programming-model"></a>Model programowania dostosowywania programu Excel  
 Po utworzeniu projektu na poziomie dokumentu dla programu Excel, programu Visual Studio generuje kilka klas, które są podstawą rozwiązania: `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3`. Te klasy reprezentują skoroszytu i arkuszy, które są skojarzone z rozwiązaniem i zapewniają punkt wyjścia do pisania kodu.  

 Aby uzyskać więcej informacji na temat tych wygenerowanych klas i innych funkcji, można użyć w projekcie na poziomie dokumentu, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).  

##  <a name="applevel"></a> Tworzenie dodatków narzędzi VSTO dla programu Excel  
 Dodatek narzędzi VSTO dla programu Microsoft Office Excel składa się z zestawu, który jest ładowany przez program Excel. Zestaw zazwyczaj rozszerza program Excel przez dostosowanie interfejsu użytkownika i automatyzowanie programu Excel. W przeciwieństwie do dostosowywania poziomie dokumentu, który jest skojarzony z określonym skoroszycie, funkcje implementowane w dodatku narzędzi VSTO dla programów nie jest ograniczona do dowolnego pojedynczego skoroszytu.  

 Aby utworzyć projekt dodatku narzędzi VSTO dla programu Excel, należy użyć skoroszyt programu Excel lub szablonów projektu szablon programu Excel w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

 Aby uzyskać ogólne informacje o współdziałaniu dodatków narzędzi VSTO dla programów, zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Dodaj model programowania w programie Excel  
 Podczas tworzenia projektu dodatku narzędzi VSTO programu Excel, programu Visual Studio generuje klasę o nazwie `ThisAddIn`, która jest podstawą rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także udostępnia model obiektów programu Excel do dodatku narzędzi VSTO dla programów.  

 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i inne funkcje programu Visual Studio można używać w dodatku narzędzi VSTO dla programów, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).  

##  <a name="UI"></a> Dostosowywanie interfejsu użytkownika programu Excel  
 Istnieje kilka różnych sposobów dostosowania interfejsu użytkownika programu Excel. Niektóre opcje są dostępne dla wszystkich typów projektów, a inne opcje są dostępne tylko dla dodatków narzędzi VSTO dla programów lub dostosowań na poziomie dokumentu.  

### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów  
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne dla dostosowywania poziomie dokumentu i dodatków narzędzi VSTO.  

|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dostosuj Wstążkę.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
|Dodawanie kontrolek formularzy Windows Forms lub rozszerzone formanty programu Excel do arkusza w skoroszycie dostosowane do dostosowywania poziomie dokumentu lub w dowolnej otwarty skoroszyt dodatku narzędzi VSTO dla programów.|[Instrukcje: Dodawanie kontrolek formularzy Windows forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  

### <a name="options-for-document-level-customizations"></a>Opcje dla dostosowywania poziomie dokumentu  
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dostosowywania poziomie dokumentu.  

|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodawanie okienek akcji do skoroszytu.|[Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)<br /><br /> [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Dodawania formantów rozszerzonego zakresu, które są mapowane do węzłów XML do arkusza.|[Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  

### <a name="options-for-vsto-add-ins"></a>Opcje dotyczące dodatków narzędzi VSTO  
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dodatków narzędzi VSTO.  

|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  

### <a name="related-topics"></a>Tematy pokrewne  

| Tytuł | Opis |
| - | - |
| [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md) | Zawiera omówienie podstawowych typów dostarczonych przez model obiektów programu Excel. |
| [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md) | Zawiera informacje o rozszerzonych obiektach (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) używanego w rozwiązaniach programu Excel. |
| [Globalizacja i lokalizacja rozwiązania programu Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Zawiera informacje o specjalne uwagi dotyczące rozwiązania programu Excel, które będą uruchamiane na komputerach, które mają ustawienia innej niż angielska dla Windows. |
| [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | W tym artykule opisano sposób dodawania kontrolek formularzy Windows Forms w arkuszach programu Excel. |
| [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Pokazuje, jak utworzyć podstawowe dostosowanie poziomu dokumentu dla programu Excel. |
| [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Przedstawia sposób tworzenia podstawowego dodatku narzędzi VSTO dla programu Excel. |
| [Przewodnik: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Pokazuje, jak dodać przycisk Windows Forms <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza w czasie wykonywania za pomocą dodatku narzędzi VSTO. |
| [Opis współtworzenia i dodatków](./understanding-coauthoring-and-addins.md) | W tym artykule opisano zmiany konieczne może być do rozwiązania w celu uwzględnienia współtworzenia. |
| [Excel 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199011) | Zawiera łącza do artykułów i dokumentacji o tworzeniu rozwiązań programu Excel. Nie są specyficzne dla programowania pakietu Office przy użyciu programu Visual Studio. |
