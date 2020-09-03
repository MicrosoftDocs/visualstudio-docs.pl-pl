---
title: rozwiązania programu Word
ms.date: 08/14/2019
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
ms.openlocfilehash: c2d3b9ea3257db11eed766079b169a7bc81fe28a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985376"
---
# <a name="word-solutions"></a>rozwiązania programu Word
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dostosowań na poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Word. Można używać tych rozwiązań do automatyzowania programu Word, rozszerzeń funkcji programu Word i dostosowywania interfejsu użytkownika programu Word. Aby uzyskać więcej informacji o różnicach między dostosowaniami dostosowań na poziomie dokumentu a dodatkami programu VSTO, zobacz temat [programowanie rozwiązań pakietu Office — omówienie &#40;narzędzi vsto&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Ten temat zawiera następujące informacje:

- [Automatyzowanie programu Word](#automating).

- [Opracowywanie dostosowań na poziomie dokumentu dla programu Word](#doclevel).

- [Opracowywanie dodatków narzędzi VSTO dla programu Word](#applevel).

- [Dostosowywanie interfejsu użytkownika programu Word](#UI).

## <a name="automate-word"></a><a name="automating"></a> Automatyzowanie programu Word
 Model obiektów programu Word uwidacznia wiele typów, których można użyć do zautomatyzowania programu Word. Na przykład można programowo tworzyć tabele, formatować dokumenty i ustawiać tekst w zakresach i akapitach. Aby uzyskać więcej informacji, zobacz temat [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md).

 Podczas opracowywania rozwiązań programu Word w programie Visual Studio można także używać *elementów hosta* i *kontrolek hosta* w swoich rozwiązaniach. Są to obiekty, które poszerzają niektóre często używane obiekty w modelu obiektów programu Word, takie <xref:Microsoft.Office.Interop.Word.Document> jak <xref:Microsoft.Office.Interop.Word.ContentControl> obiekty i. Obiekty rozszerzone zachowują się jak obiekty programu Word, na których się opierają, ale dodają do obiektów dodatkowe zdarzenia i możliwości powiązania danych. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-word"></a><a name="doclevel"></a> Opracowywanie dostosowań na poziomie dokumentu dla programu Word
 Dostosowanie na poziomie dokumentu dla Microsoft Office Word składa się z zestawu, który jest skojarzony z określonym dokumentem. Zestaw zwykle rozszerza dokument przez dostosowanie interfejsu użytkownika i automatyzację programu Word. W przeciwieństwie do dodatku VSTO, który jest skojarzony z samym programem Word, funkcjonalność zaimplementowana w dostosowaniu jest dostępna tylko wtedy, gdy skojarzony dokument jest otwarty w programie Word.

 Aby utworzyć projekt dostosowania na poziomie dokumentu dla programu Word, użyj szablonów projektu dokumentu programu Word lub Word w oknie dialogowym **Nowy projekt** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać więcej informacji na temat sposobu działania dostosowań na poziomie dokumentu, [architektury dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Model programowania dostosowywania wyrazów
 Po utworzeniu projektu na poziomie dokumentu dla programu Word, program Visual Studio generuje klasę o nazwie, `ThisDocument` która jest podstawą rozwiązania. Ta klasa reprezentuje dokument, który jest skojarzony z rozwiązaniem i udostępnia punkt wyjścia do pisania kodu.

 Więcej informacji o `ThisDocument` klasie i innych funkcjach, których można użyć w projekcie na poziomie dokumentu, znajduje się w temacie [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-word"></a><a name="applevel"></a> Opracowywanie dodatków narzędzi VSTO dla programu Word
 Dodatek narzędzi VSTO dla Microsoft Office Word składa się z zestawu, który jest ładowany przez program Word. Zestaw zwykle rozszerza program Word, dostosowując interfejs użytkownika i automatyzując program Word. W przeciwieństwie do dostosowania na poziomie dokumentu, które jest skojarzone z określonym dokumentem, funkcjonalność zaimplementowana w dodatku VSTO nie jest ograniczona do żadnego pojedynczego dokumentu.

 Aby utworzyć projekt dodatku narzędzi VSTO dla programu Word, użyj szablonów projektu dodatku programu Word w oknie dialogowym **Nowy projekt** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Aby uzyskać ogólne informacje o działaniu dodatków VSTO, zobacz [architektury dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Model programowania dodatku programu Word
 Podczas tworzenia projektu dodatku VSTO dla programu Word, program Visual Studio generuje klasę o nazwie, `ThisAddIn` która jest podstawą rozwiązania. Ta klasa udostępnia punkt wyjścia do pisania kodu, a także udostępnia model obiektów programu Word do dodatku VSTO.

 Aby uzyskać więcej informacji o `ThisAddIn` klasie i innych funkcjach, których można użyć w dodatku narzędzi VSTO, zobacz [dodatek narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-word"></a><a name="UI"></a> Dostosowywanie interfejsu użytkownika programu Word
 Istnieje kilka różnych sposobów dostosowywania interfejsu użytkownika programu Word. Niektóre opcje są dostępne dla wszystkich typów projektów, a inne opcje są dostępne tylko dla dodatków VSTO lub dostosowań na poziomie dokumentu.

### <a name="options-for-all-project-types"></a>Opcje dla wszystkich typów projektów
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne zarówno dla dostosowań na poziomie dokumentu, jak i dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dostosuj Wstążkę.|[Omówienie wstążki](../vsto/ribbon-overview.md)|
|Dodaj kontrolki Windows Forms lub rozszerzone formanty programu Word do niestandardowego dokumentu (dla dostosowania na poziomie dokumentu) lub dowolnego otwartego dokumentu (dla dodatku VSTO).|[Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Opcje dostosowywania na poziomie dokumentu
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dostosowań na poziomie dokumentu.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodaj okienko akcje do dokumentu.|[Przegląd okienka Akcje](../vsto/actions-pane-overview.md)<br /><br /> [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Dodaj rozszerzone kontrolki XMLNode i XmlNode do powierzchni dokumentu.|[Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Opcje dodatków narzędzi VSTO
 W poniższej tabeli wymieniono opcje dostosowywania, które są dostępne tylko dla dodatków narzędzi VSTO.

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Utwórz niestandardowe okienko zadań.|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)|Zawiera przegląd typów głównych dostarczonych przez model obiektów programu Word.|
|[Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)|Zawiera informacje o rozszerzonych obiektach (dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] program), których można używać w rozwiązaniach programu Word.|
|[Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)|Opisuje sposób dodawania formantów Windows Forms do dokumentów programu Word.|
|[Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Pokazuje, jak utworzyć podstawowe dostosowanie na poziomie dokumentu dla programu Word.|
|[Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Pokazuje, jak utworzyć podstawowy dodatek narzędzi VSTO dla programu Word.|
|[Przewodnik: Dodawanie kontrolek do dokumentu w czasie wykonywania w dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Pokazuje, jak dodać przycisk Windows Forms i <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu w czasie wykonywania przy użyciu dodatku VSTO.|
|[Word 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff601860(v=office.14))|Zawiera łącza do artykułów i dokumentacji referencyjnej dotyczącej opracowywania rozwiązań programu Word (niespecyficznych dla programowania Office przy użyciu programu Visual Studio).|
