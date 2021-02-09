---
title: Model obiektów programu Word — omówienie
description: Model obiektów programu Word składa się z klas i interfejsów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu Word i są zdefiniowane w przestrzeni nazw programu Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3d593185412db23fa985f7effea6e91f9b3faa6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847651"
---
# <a name="word-object-model-overview"></a>Model obiektów programu Word — omówienie
  Podczas opracowywania rozwiązań programu Word w programie Visual Studio można korzystać z modelu obiektów programu Word. Ten model obiektów składa się z klas i interfejsów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu Word i są zdefiniowane w <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ten temat zawiera krótkie omówienie modelu obiektów programu Word. Aby uzyskać więcej informacji na temat całego modelu obiektów programu Word, zobacz [Korzystanie z dokumentacji modelu obiektów programu Word](#WordOMDocumentation).

 Aby uzyskać informacje o używaniu modelu obiektów programu Word do wykonywania określonych zadań, zobacz następujące tematy:

- [Pracuj z dokumentami](../vsto/working-with-documents.md)

- [Pracuj z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)

- [Praca z tabelami](../vsto/working-with-tables.md)

## <a name="understand-the-word-object-model"></a><a name="understanding"></a> Zrozumienie modelu obiektów programu Word
 Program Word zawiera setki obiektów, z którymi można korzystać. Te obiekty są zorganizowane w hierarchii, która blisko interfejsu użytkownika. W górnej części hierarchii jest <xref:Microsoft.Office.Interop.Word.Application> obiekt. Ten obiekt reprezentuje bieżące wystąpienie programu Word. <xref:Microsoft.Office.Interop.Word.Application>Obiekt zawiera <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> obiekty,, <xref:Microsoft.Office.Interop.Word.Bookmark> , i <xref:Microsoft.Office.Interop.Word.Range> . Każdy z tych obiektów ma wiele metod i właściwości, które są dostępne do manipulowania i współdziałania z obiektem.

 Na poniższej ilustracji przedstawiono jeden widok tych obiektów w hierarchii modelu obiektów programu Word.

 ![Grafika modelu obiektów programu Word](../vsto/media/wrwordobjectmodel.gif "Grafika modelu obiektów programu Word")

 Na pierwszy rzut oka obiekty pojawiają się na siebie. Na przykład <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> obiekty i są obu elementów członkowskich <xref:Microsoft.Office.Interop.Word.Application> obiektu, ale <xref:Microsoft.Office.Interop.Word.Document> obiekt jest również elementem członkowskim <xref:Microsoft.Office.Interop.Word.Selection> obiektu. <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> Obiekty i zawierają <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Range> obiekty i. Nakładanie się istnieje, ponieważ istnieje wiele sposobów uzyskania dostępu do tego samego typu obiektu. Na przykład stosujesz formatowanie do <xref:Microsoft.Office.Interop.Word.Range> obiektu, ale możesz chcieć uzyskać dostęp do zakresu bieżącego zaznaczenia, określonego akapitu, sekcji lub całego dokumentu.

 W poniższych sekcjach krótko opisano obiekty najwyższego poziomu i sposób współdziałania ze sobą. Te obiekty obejmują następujące pięć:

- Obiekt aplikacji

- Obiekt dokumentu

- Zaznacz obiekt

- obiekt zakresu

- Zakładka — obiekt

  Poza modelem obiektów programu Word, projekty pakietu Office w programie Visual Studio udostępniają *elementy hosta* i *formanty hosta* , które poszerzają niektóre obiekty w modelu obiektów programu Word. Elementy hosta i formanty hosta zachowują się jak obiekty programu Word, które rozszerzają się, ale również mają dodatkowe funkcje, takie jak możliwości powiązań danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Word przy użyciu rozszerzonych obiektów](../vsto/automating-word-by-using-extended-objects.md) i [elementów hosta oraz kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Obiekt aplikacji
 <xref:Microsoft.Office.Interop.Word.Application>Obiekt reprezentuje aplikację Word i jest elementem nadrzędnym wszystkich innych obiektów. Jego członkowie zazwyczaj mają zastosowanie do programu Word jako całości. Aby kontrolować środowisko programu Word, można użyć jego właściwości i metod.

 W projektach dodatku VSTO można uzyskać dostęp do <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą `Application` pola `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 W projektach na poziomie dokumentu można uzyskać dostęp do <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą <xref:Microsoft.Office.Tools.Word.Document.Application%2A> właściwości `ThisDocument` klasy.

### <a name="document-object"></a>Obiekt dokumentu
 <xref:Microsoft.Office.Interop.Word.Document>Obiekt jest centralnym programowaniem programu Word. Reprezentuje dokument i całą jego zawartość. Po otwarciu dokumentu lub utworzeniu nowego dokumentu należy utworzyć nowy <xref:Microsoft.Office.Interop.Word.Document> obiekt, który jest dodawany do <xref:Microsoft.Office.Interop.Word.Documents> kolekcji <xref:Microsoft.Office.Interop.Word.Application> obiektu. Dokument, który ma fokus, jest nazywany aktywnym dokumentem. Jest reprezentowana przez <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> Właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu.

 Narzędzia programistyczne pakietu Office w programie Visual Studio zwiększają <xref:Microsoft.Office.Interop.Word.Document> obiekt, dostarczając <xref:Microsoft.Office.Tools.Word.Document> Typ. Ten typ jest *elementem hosta* , który zapewnia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Word.Document> obiektu i dodaje dodatkowe zdarzenia i możliwość dodawania formantów zarządzanych.

 Podczas tworzenia projektu na poziomie dokumentu można uzyskiwać dostęp do <xref:Microsoft.Office.Tools.Word.Document> elementów członkowskich przy użyciu wygenerowanej `ThisDocument` klasy w projekcie. Możesz uzyskać dostęp do elementów członkowskich <xref:Microsoft.Office.Tools.Word.Document> elementu hosta za pomocą **mnie** lub **tych** słów kluczowych z kodu w `ThisDocument` klasie lub korzystając `Globals.ThisDocument` z kodu poza `ThisDocument` klasą. Aby uzyskać więcej informacji, zobacz temat [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md). Na przykład, aby zaznaczyć pierwszy akapit w dokumencie, użyj poniższego kodu.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 W projektach dodatku VSTO można generować <xref:Microsoft.Office.Tools.Word.Document> elementy hosta w czasie wykonywania. Możesz użyć wygenerowanego elementu hosta, aby dodać kontrolki do skojarzonego dokumentu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Zaznacz obiekt
 <xref:Microsoft.Office.Interop.Word.Selection>Obiekt reprezentuje aktualnie wybrany obszar. Podczas wykonywania operacji w interfejsie użytkownika programu Word, takiej jak tekst pogrubiony, należy wybrać lub podświetlić tekst, a następnie zastosować formatowanie. <xref:Microsoft.Office.Interop.Word.Selection>Obiekt jest zawsze obecny w dokumencie. Jeśli nic nie jest zaznaczone, oznacza punkt wstawiania. Ponadto zaznaczenie może obejmować wiele bloków tekstu, które nie są ciągłe.

### <a name="range-object"></a>obiekt zakresu
 <xref:Microsoft.Office.Interop.Word.Range>Obiekt reprezentuje ciągły obszar w dokumencie i jest zdefiniowany przez początkową pozycję znaku i końcową pozycję znaku. Nie jest ograniczony do pojedynczego <xref:Microsoft.Office.Interop.Word.Range> obiektu. Można zdefiniować wiele <xref:Microsoft.Office.Interop.Word.Range> obiektów w tym samym dokumencie. <xref:Microsoft.Office.Interop.Word.Range>Obiekt ma następującą charakterystykę:

- Może składać się wyłącznie z punktu wstawiania, zakresu tekstu lub całego dokumentu.

- Zawiera znaki niedrukowalne, takie jak spacje, znaki tabulacji i znaczniki akapitu.

- Może to być obszar reprezentowany przez bieżące zaznaczenie lub może reprezentować obszar różny od bieżącego zaznaczenia.

- Nie jest on widoczny w dokumencie, w przeciwieństwie do zaznaczenia, które jest zawsze widoczne.

- Nie jest on zapisywany w dokumencie i istnieje tylko w czasie, gdy kod jest uruchomiony.

  Po wstawieniu tekstu na końcu zakresu program Word automatycznie rozszerza zakres, aby uwzględnić wstawiony tekst.

### <a name="content-control-objects"></a>Obiekty kontroli zawartości
 A <xref:Microsoft.Office.Interop.Word.ContentControl> umożliwia kontrolowanie danych wejściowych i prezentacji tekstu oraz innych typów zawartości w dokumentach programu Word. <xref:Microsoft.Office.Interop.Word.ContentControl>Może wyświetlać kilka różnych typów interfejsu użytkownika, które są zoptymalizowane do użycia w dokumentach programu Word, takich jak kontrolka tekstu sformatowanego, selektor daty lub pole kombi. Możesz również użyć, <xref:Microsoft.Office.Interop.Word.ContentControl> Aby uniemożliwić użytkownikom edytowanie sekcji dokumentu lub szablonu.

 Program Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.ContentControl> obiekt do kilku różnych kontrolek hosta. Podczas gdy <xref:Microsoft.Office.Interop.Word.ContentControl> obiekt może wyświetlić dowolny z różnych typów interfejsu użytkownika, które są dostępne dla formantów zawartości, program Visual Studio udostępnia inny typ dla każdej kontrolki zawartości. Na przykład można użyć <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do utworzenia kontrolki tekstu sformatowanego lub można użyć <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do utworzenia selektora dat. Te kontrolki hosta zachowują się jak natywny <xref:Microsoft.Office.Interop.Word.ContentControl> , ale mają dodatkowe zdarzenia i możliwości powiązania danych. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Zakładka — obiekt
 <xref:Microsoft.Office.Interop.Word.Bookmark>Obiekt reprezentuje ciągły obszar w dokumencie, zarówno na pozycji początkowej, jak i końcowej. Zakładki umożliwiają oznaczenie lokalizacji w dokumencie lub jako kontener dla tekstu w dokumencie. <xref:Microsoft.Office.Interop.Word.Bookmark>Obiekt może składać się z punktu wstawiania lub być tak duży jak cały dokument. <xref:Microsoft.Office.Interop.Word.Bookmark>Ma następujące cechy, które ustawiają je niezależnie od <xref:Microsoft.Office.Interop.Word.Range> obiektu:

- Zakładkę można nazwać w czasie projektowania.

- <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty są zapisywane wraz z dokumentem, więc nie są usuwane, gdy kod przestanie działać lub dokument jest zamknięty.

- Zakładki mogą być ukrywane lub widoczne, ustawiając <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> Właściwość <xref:Microsoft.Office.Interop.Word.View> obiektu na **false** lub **true**.

  Program Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.Bookmark> obiekt, dostarczając <xref:Microsoft.Office.Tools.Word.Bookmark> formant hosta. <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka hosta zachowuje się jak natywny <xref:Microsoft.Office.Interop.Word.Bookmark> , ale ma dodatkowe zdarzenia i możliwości powiązania danych. Dane można powiązać z kontrolką zakładki w dokumencie w taki sam sposób, w jaki dane są powiązane z kontrolką pola tekstowego w formularzu systemu Windows. Aby uzyskać więcej informacji, zobacz [kontrolka zakładka](../vsto/bookmark-control.md).

## <a name="use-the-word-object-model-documentation"></a><a name="WordOMDocumentation"></a> Korzystanie z dokumentacji modelu obiektów programu Word
 Aby uzyskać pełne informacje na temat modelu obiektów programu Word, można odwołać się do odwołania do podstawowego zestawu międzyoperacyjnego (PIA) programu Word i odwołania do modelu obiektu Visual Basic for Applications (VBA).

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego
 Dokumentacja zestawu PIA wyrazów zawiera opis typów w podstawowym zestawie międzyoperacyjnym dla programu Word. Ta dokumentacja jest dostępna w następującej lokalizacji: [Word 2010 podstawowe odwołanie do zestawu międzyoperacyjnego](../vsto/office-primary-interop-assemblies.md).

 Aby uzyskać więcej informacji o projektowaniu PIA wyrazów, takich jak różnice między klasami i interfejsami w PIAu i sposobie implementacji zdarzeń w PIA, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu Word, ponieważ jest on uwidoczniony w kodzie VBA. Aby uzyskać więcej informacji, zobacz temat [Dokumentacja modelu obiektów programu Word 2010](/office/vba/api/overview/Word/object-model).

 Wszystkie obiekty i elementy członkowskie w odniesieniu do modelu obiektów VBA odpowiadają typom i elementom członkowskim kodu PIA wyrazów. Na przykład obiekt dokumentu w odniesieniu do modelu obiektów VBA odnosi się do <xref:Microsoft.Office.Interop.Word.Document> obiektu w pliku PIA programu Word. Chociaż dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub Visual C#, jeśli chcesz użyć ich w projekcie programu Word, który tworzysz przy użyciu programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Pracuj z dokumentami](../vsto/working-with-documents.md)
- [Pracuj z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)
- [Praca z tabelami](../vsto/working-with-tables.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
