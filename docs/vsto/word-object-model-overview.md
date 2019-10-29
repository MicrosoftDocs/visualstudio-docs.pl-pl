---
title: Model obiektów programu Word — omówienie
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e66d6cda802b2b1243911e1927af751e2cdbe9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985388"
---
# <a name="word-object-model-overview"></a>Model obiektów programu Word — omówienie
  Podczas opracowywania rozwiązań programu Word w programie Visual Studio można korzystać z modelu obiektów programu Word. Ten model obiektów składa się z klas i interfejsów, które są dostępne w podstawowym zestawie międzyoperacyjnym dla programu Word i są zdefiniowane w przestrzeni nazw <xref:Microsoft.Office.Interop.Word>.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ten temat zawiera krótkie omówienie modelu obiektów programu Word. Aby uzyskać więcej informacji na temat całego modelu obiektów programu Word, zobacz [Korzystanie z dokumentacji modelu obiektów programu Word](#WordOMDocumentation).

 Aby uzyskać informacje o używaniu modelu obiektów programu Word do wykonywania określonych zadań, zobacz następujące tematy:

- [Pracuj z dokumentami](../vsto/working-with-documents.md)

- [Pracuj z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)

- [Pracuj z tabelami](../vsto/working-with-tables.md)

## <a name="understanding"></a>Zrozumienie modelu obiektów programu Word
 Program Word zawiera setki obiektów, z którymi można korzystać. Te obiekty są zorganizowane w hierarchii, która blisko interfejsu użytkownika. W górnej części hierarchii jest obiektem <xref:Microsoft.Office.Interop.Word.Application>. Ten obiekt reprezentuje bieżące wystąpienie programu Word. Obiekt <xref:Microsoft.Office.Interop.Word.Application> zawiera obiekty <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>i <xref:Microsoft.Office.Interop.Word.Range>. Każdy z tych obiektów ma wiele metod i właściwości, które są dostępne do manipulowania i współdziałania z obiektem.

 Na poniższej ilustracji przedstawiono jeden widok tych obiektów w hierarchii modelu obiektów programu Word.

 ![Grafika modelu obiektów programu Word](../vsto/media/wrwordobjectmodel.gif "Grafika modelu obiektów programu Word")

 Na pierwszy rzut oka obiekty pojawiają się na siebie. Na przykład obiekty <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> są elementami członkowskimi obiektu <xref:Microsoft.Office.Interop.Word.Application>, ale obiekt <xref:Microsoft.Office.Interop.Word.Document> jest również elementem członkowskim obiektu <xref:Microsoft.Office.Interop.Word.Selection>. Obiekty <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> zawierają obiekty <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Interop.Word.Range>. Nakładanie się istnieje, ponieważ istnieje wiele sposobów uzyskania dostępu do tego samego typu obiektu. Na przykład można zastosować formatowanie do obiektu <xref:Microsoft.Office.Interop.Word.Range>; ale możesz chcieć uzyskać dostęp do zakresu bieżącego zaznaczenia, określonego akapitu lub całego dokumentu.

 W poniższych sekcjach krótko opisano obiekty najwyższego poziomu i sposób współdziałania ze sobą. Te obiekty obejmują następujące pięć:

- Obiekt aplikacji

- Obiekt dokumentu

- Zaznacz obiekt

- obiekt zakresu

- Zakładka — obiekt

  Poza modelem obiektów programu Word, projekty pakietu Office w programie Visual Studio udostępniają *elementy hosta* i *formanty hosta* , które poszerzają niektóre obiekty w modelu obiektów programu Word. Elementy hosta i formanty hosta zachowują się jak obiekty programu Word, które rozszerzają się, ale również mają dodatkowe funkcje, takie jak możliwości powiązań danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Word przy użyciu rozszerzonych obiektów](../vsto/automating-word-by-using-extended-objects.md) i [elementów hosta oraz kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt <xref:Microsoft.Office.Interop.Word.Application> reprezentuje aplikację Word i jest elementem nadrzędnym wszystkich innych obiektów. Jego członkowie zazwyczaj mają zastosowanie do programu Word jako całości. Aby kontrolować środowisko programu Word, można użyć jego właściwości i metod.

 W projektach dodatku VSTO można uzyskać dostęp do obiektu <xref:Microsoft.Office.Interop.Word.Application> przy użyciu pola `Application` klasy `ThisAddIn`. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 W projektach na poziomie dokumentu dostęp do obiektu <xref:Microsoft.Office.Interop.Word.Application> można uzyskać przy użyciu właściwości <xref:Microsoft.Office.Tools.Word.Document.Application%2A> klasy `ThisDocument`.

### <a name="document-object"></a>Obiekt dokumentu
 Obiekt <xref:Microsoft.Office.Interop.Word.Document> to centralne Programowanie programu Word. Reprezentuje dokument i całą jego zawartość. Podczas otwierania dokumentu lub tworzenia nowego dokumentu tworzony jest nowy obiekt <xref:Microsoft.Office.Interop.Word.Document>, który jest dodawany do <xref:Microsoft.Office.Interop.Word.Documents> kolekcji obiektu <xref:Microsoft.Office.Interop.Word.Application>. Dokument, który ma fokus, jest nazywany aktywnym dokumentem. Jest reprezentowana przez właściwość <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> obiektu <xref:Microsoft.Office.Interop.Word.Application>.

 Narzędzia programistyczne pakietu Office w programie Visual Studio zwiększają <xref:Microsoft.Office.Interop.Word.Document> obiektu, dostarczając typ <xref:Microsoft.Office.Tools.Word.Document>. Ten typ jest *elementem hosta* , który zapewnia dostęp do wszystkich funkcji obiektu <xref:Microsoft.Office.Interop.Word.Document> i dodaje dodatkowe zdarzenia i możliwość dodawania formantów zarządzanych.

 Podczas tworzenia projektu na poziomie dokumentu można uzyskiwać dostęp do <xref:Microsoft.Office.Tools.Word.Document> elementów członkowskich przy użyciu wygenerowanej klasy `ThisDocument` w projekcie. Możesz uzyskać dostęp do członków elementu hosta <xref:Microsoft.Office.Tools.Word.Document> przy użyciu **mnie** lub **tych** słów kluczowych z kodu w klasie `ThisDocument` lub używając `Globals.ThisDocument` z kodu poza klasą `ThisDocument`. Aby uzyskać więcej informacji, zobacz temat [programowe dostosowanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md). Na przykład, aby zaznaczyć pierwszy akapit w dokumencie, użyj poniższego kodu.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 W projektach dodatku VSTO można generować <xref:Microsoft.Office.Tools.Word.Document> elementy hosta w czasie wykonywania. Możesz użyć wygenerowanego elementu hosta, aby dodać kontrolki do skojarzonego dokumentu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Zaznacz obiekt
 Obiekt <xref:Microsoft.Office.Interop.Word.Selection> reprezentuje aktualnie wybrany obszar. Podczas wykonywania operacji w interfejsie użytkownika programu Word, takiej jak tekst pogrubiony, należy wybrać lub podświetlić tekst, a następnie zastosować formatowanie. Obiekt <xref:Microsoft.Office.Interop.Word.Selection> jest zawsze obecny w dokumencie. Jeśli nic nie jest zaznaczone, oznacza punkt wstawiania. Ponadto zaznaczenie może obejmować wiele bloków tekstu, które nie są ciągłe.

### <a name="range-object"></a>obiekt zakresu
 Obiekt <xref:Microsoft.Office.Interop.Word.Range> reprezentuje ciągły obszar w dokumencie i jest zdefiniowany przez początkową pozycję znaku i końcową pozycję znaku. Nie jest ograniczony do pojedynczego obiektu <xref:Microsoft.Office.Interop.Word.Range>. Można zdefiniować wiele obiektów <xref:Microsoft.Office.Interop.Word.Range> w tym samym dokumencie. Obiekt <xref:Microsoft.Office.Interop.Word.Range> ma następującą charakterystykę:

- Może składać się wyłącznie z punktu wstawiania, zakresu tekstu lub całego dokumentu.

- Zawiera znaki niedrukowalne, takie jak spacje, znaki tabulacji i znaczniki akapitu.

- Może to być obszar reprezentowany przez bieżące zaznaczenie lub może reprezentować obszar różny od bieżącego zaznaczenia.

- Nie jest on widoczny w dokumencie, w przeciwieństwie do zaznaczenia, które jest zawsze widoczne.

- Nie jest on zapisywany w dokumencie i istnieje tylko w czasie, gdy kod jest uruchomiony.

  Po wstawieniu tekstu na końcu zakresu program Word automatycznie rozszerza zakres, aby uwzględnić wstawiony tekst.

### <a name="content-control-objects"></a>Obiekty kontroli zawartości
 <xref:Microsoft.Office.Interop.Word.ContentControl> zapewnia sposób sterowania danymi wejściowymi i prezentacjami tekstu i innych typów zawartości w dokumentach programu Word. <xref:Microsoft.Office.Interop.Word.ContentControl> może wyświetlać kilka różnych typów interfejsu użytkownika, które są zoptymalizowane do użycia w dokumentach programu Word, takich jak kontrolka tekstu sformatowanego, selektor daty lub pole kombi. Możesz również użyć <xref:Microsoft.Office.Interop.Word.ContentControl>, aby uniemożliwić użytkownikom edytowanie sekcji dokumentu lub szablonu.

 Program Visual Studio rozszerza obiekt <xref:Microsoft.Office.Interop.Word.ContentControl> na kilka różnych kontrolek hosta. Podczas gdy obiekt <xref:Microsoft.Office.Interop.Word.ContentControl> może wyświetlić dowolny z różnych typów interfejsu użytkownika, które są dostępne dla formantów zawartości, program Visual Studio udostępnia inny typ dla każdej kontrolki zawartości. Na przykład można użyć <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do utworzenia kontrolki tekstu sformatowanego lub można użyć <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do utworzenia selektora dat. Te kontrolki hosta zachowują się jak natywne <xref:Microsoft.Office.Interop.Word.ContentControl>, ale mają dodatkowe zdarzenia i możliwości powiązania danych. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Zakładka — obiekt
 Obiekt <xref:Microsoft.Office.Interop.Word.Bookmark> reprezentuje ciągły obszar w dokumencie, zarówno na pozycji początkowej, jak i końcowej. Zakładki umożliwiają oznaczenie lokalizacji w dokumencie lub jako kontener dla tekstu w dokumencie. Obiekt <xref:Microsoft.Office.Interop.Word.Bookmark> może składać się z punktu wstawiania lub być tak duży jak cały dokument. <xref:Microsoft.Office.Interop.Word.Bookmark> ma następujące cechy, które ustawiają je niezależnie od obiektu <xref:Microsoft.Office.Interop.Word.Range>:

- Zakładkę można nazwać w czasie projektowania.

- obiekty <xref:Microsoft.Office.Interop.Word.Bookmark> są zapisywane wraz z dokumentem, więc nie są usuwane, gdy kod przestanie działać lub dokument jest zamknięty.

- Zakładki mogą być ukrywane lub widoczne, ustawiając właściwość <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> obiektu <xref:Microsoft.Office.Interop.Word.View> na **wartość false** lub **true**.

  Program Visual Studio rozszerza obiekt <xref:Microsoft.Office.Interop.Word.Bookmark>, dostarczając formant hosta <xref:Microsoft.Office.Tools.Word.Bookmark>. Kontrolka hosta <xref:Microsoft.Office.Tools.Word.Bookmark> zachowuje się jak natywny <xref:Microsoft.Office.Interop.Word.Bookmark>, ale ma dodatkowe zdarzenia i możliwości powiązania danych. Dane można powiązać z kontrolką zakładki w dokumencie w taki sam sposób, w jaki dane są powiązane z kontrolką pola tekstowego w formularzu systemu Windows. Aby uzyskać więcej informacji, zobacz [kontrolka zakładka](../vsto/bookmark-control.md).

## <a name="WordOMDocumentation"></a>Korzystanie z dokumentacji modelu obiektów programu Word
 Aby uzyskać pełne informacje na temat modelu obiektów programu Word, można odwołać się do odwołania do podstawowego zestawu międzyoperacyjnego (PIA) programu Word i odwołania do modelu obiektu Visual Basic for Applications (VBA).

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego
 Dokumentacja zestawu PIA wyrazów zawiera opis typów w podstawowym zestawie międzyoperacyjnym dla programu Word. Ta dokumentacja jest dostępna w następującej lokalizacji: [Word 2010 podstawowe odwołanie do zestawu międzyoperacyjnego](../vsto/office-primary-interop-assemblies.md).

 Aby uzyskać więcej informacji o projektowaniu PIA wyrazów, takich jak różnice między klasami i interfejsami w PIAu i sposobie implementacji zdarzeń w PIA, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu Word, ponieważ jest on uwidoczniony w kodzie VBA. Aby uzyskać więcej informacji, zobacz temat [Dokumentacja modelu obiektów programu Word 2010](/office/vba/api/overview/Word/object-model).

 Wszystkie obiekty i elementy członkowskie w odniesieniu do modelu obiektów VBA odpowiadają typom i elementom członkowskim kodu PIA wyrazów. Na przykład obiekt dokumentu w odniesieniu do modelu obiektów VBA odpowiada obiektowi <xref:Microsoft.Office.Interop.Word.Document> w pliku PIA programu Word. Chociaż dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub wizualizacji C# , jeśli chcesz użyć ich w projekcie programu Word, który tworzysz przy użyciu programu Visual Studio .

## <a name="see-also"></a>Zobacz także
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Pracuj z dokumentami](../vsto/working-with-documents.md)
- [Pracuj z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)
- [Pracuj z tabelami](../vsto/working-with-tables.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
