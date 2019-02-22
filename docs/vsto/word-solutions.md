---
title: rozwiązania programu Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 484998916619a7dc72693d1854d29849bb62d833
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612650"
---
# <a name="word-solutions"></a>rozwiązania programu Word
  Program Visual Studio udostępnia szablony projektów, których można użyć do utworzenia dostosowań poziomu dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Word. Rozwiązania te można użyć do zautomatyzowania programu Word, Rozszerz funkcje programu Word i dostosowania interfejsu użytkownika (UI) programu Word. Aby uzyskać więcej informacji na temat różnic między dostosowań na poziomie dokumentu i dodatków narzędzi VSTO dla programów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

> [!NOTE]
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.

 Ten temat zawiera następujące informacje:

-   [Automatyzowanie programu Word](#automating).

-   [Opracowywanie dostosowań poziomu dokumentu dla programu Word](#doclevel).

-   [Tworzenie dodatków narzędzi VSTO dla programu Word](#applevel).

-   [Dostosowywanie interfejsu użytkownika programu Word](#UI).

##  <a name="automating"></a> Automatyzowanie programu Word
 Model obiektów programu Word uwidacznia wiele typów, których można użyć do zautomatyzowania programu Word. Na przykład możesz można programowo tworzyć tabele, formatować dokumenty i ustawiać tekst w zakresach i akapitach. Aby uzyskać więcej informacji, zobacz [model obiektu Word — omówienie](../vsto/word-object-model-overview.md).

 Podczas opracowywania rozwiązań programu Word w programie Visual Studio, możesz również użyć *hostować elementy* i *hostowania kontrolek* w posiadanych rozwiązaniach. Są to obiekty, które rozszerzają niektóre powszechnie używane obiekty w modelu obiektów programu Word, takie jak <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.ContentControl> obiektów. Obiekty rozszerzone zachowują się jak obiekty programu Word, w których są one oparte na, ale dodają dodatkowe zdarzenia i możliwości wiązania danych do obiektów. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).

##  <a name="doclevel"></a> Opracowywanie dostosowań poziomu dokumentu dla programu Word
 Dostosowania poziomu dokumentu dla programu Microsoft Office Word składa się z zestawu, który jest skojarzony z określonym dokumentem. Zestaw zazwyczaj rozszerza dokument przez dostosowanie interfejsu użytkownika i automatyzowanie programu Word. W przeciwieństwie do dodatku narzędzi VSTO, który jest skojarzony z samym programem Word, funkcja implementowana w dostosowaniu jest dostępna tylko wtedy, gdy skojarzony dokument jest otwarty w programie Word.

 Aby utworzyć projekt dostosowania poziomu dokumentu dla programu Word, korzystanie z szablonów projektów dokumentów programu Word lub szablon programu Word w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać więcej informacji na temat działania dostosowań na poziomie dokumentów [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Model programowania dostosowywania programu Word
 Po utworzeniu projektu na poziomie dokumentu dla programu Word, program Visual Studio generuje klasę o nazwie `ThisDocument`, która jest podstawą rozwiązania. Ta klasa reprezentuje dokument, który jest skojarzony z rozwiązaniem, a jego stanowi punkt wyjścia do pisania kodu.

 Aby uzyskać więcej informacji na temat `ThisDocument` klasy i inne funkcje, można użyć w projekcie na poziomie dokumentu, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

##  <a name="applevel"></a> Tworzenie dodatków narzędzi VSTO dla programu Word
 Dodatek narzędzi VSTO dla programu Microsoft Office Word składa się z zestawu, który jest ładowany przez program Word. Zestaw zazwyczaj rozszerza program Word przez dostosowanie interfejsu użytkownika i automatyzowanie programu Word. W przeciwieństwie do dostosowywania poziomie dokumentu, który jest skojarzony z określonym dokumentem, funkcje implementowane w dodatku narzędzi VSTO dla programów nie jest ograniczone do pojedynczego dokumentu.

 Aby utworzyć projekt dodatku narzędzi VSTO dla programu Word, korzystanie z dodatku programu Word szablonów projektów w **nowy projekt** okno dialogowe programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać ogólne informacje o współdziałaniu dodatków narzędzi VSTO dla programów, zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Word dodatku model programowania
 Podczas tworzenia projektu dodatku narzędzi VSTO programu Word, program Visual Studio generuje klasę o nazwie `ThisAddIn`, która jest podstawą rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także udostępnia model obiektów programu Word do dodatku narzędzi VSTO dla programów.

 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i inne funkcje, które można używać w dodatku narzędzi VSTO dla programów, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

##  <a name="UI"></a> Dostosowywanie interfejsu użytkownika programu Word
 Istnieje kilka różnych sposobów dostosowania interfejsu użytkownika programu Word. Niektóre opcje są dostępne dla wszystkich typów projektów, a inne opcje są dostępne tylko dla dodatków narzędzi VSTO dla programów lub dostosowań na poziomie dokumentu.

### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne dla dostosowywania poziomie dokumentu i dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|
|Dodaj formanty Windows Forms lub rozszerzone formanty programu Word do dokumentu niestandardowego (dla dostosowania poziomu dokumentu) lub dowolnego otwartego dokumentu (w przypadku dodatku narzędzi VSTO).|[Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Opcje dla dostosowywania poziomie dokumentu
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dostosowywania poziomie dokumentu.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodawanie okienek akcji do dokumentu.|[Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)<br /><br /> [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Dodaj rozszerzoną XMLNode i formanty XMLNodes do powierzchni dokumentu.|[Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Opcje dotyczące dodatków narzędzi VSTO
 Poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Tworzenie niestandardowego okienka zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)|Zawiera omówienie podstawowych typów dostarczonych przez model obiektów programu Word.|
|[Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)|Zawiera informacje o rozszerzonych obiektach (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) używanego w rozwiązaniach programu Word.|
|[Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|W tym artykule opisano, jak dodać kontrolek formularzy Windows Forms do dokumentów programu Word.|
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Pokazuje, jak utworzyć podstawowe dostosowanie poziomu dokumentu dla programu Word.|
|[Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Pokazuje, jak utworzyć podstawowy dodatku narzędzi VSTO dla programu Word.|
|[Przewodnik: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Pokazuje, jak dodać Windows Forms przycisk, a co <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu w czasie wykonywania za pomocą dodatku narzędzi VSTO.|
|[Word 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Zawiera łącza do artykułów i dokumentacji o tworzeniu rozwiązań programu Word (nie odnoszą się do rozwoju pakietu Office przy użyciu programu Visual Studio).|
