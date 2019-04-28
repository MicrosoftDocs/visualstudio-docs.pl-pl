---
title: Model obiektu Word — omówienie
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
ms.openlocfilehash: 92a0b432e75cb8df6318be0961cc587257869b27
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009364"
---
# <a name="word-object-model-overview"></a>Model obiektu Word — omówienie
  Podczas opracowywania rozwiązań programu Word w programie Visual Studio możesz korzystać z modelu obiektów programu Word. Ten model obiektów składa się z klasy i interfejsy, które znajdują się w podstawowy zestaw międzyoperacyjny dla programu Word i są definiowane w <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ten temat zawiera krótkie omówienie modelu obiektów programu Word. Dla zasobów można znaleźć więcej informacji na temat całego modelu obiektów programu Word, zobacz [zapoznaj się z dokumentacją model obiektu Word](#WordOMDocumentation).

 Aby dowiedzieć się, jak za pomocą modelu obiektów programu Word do wykonywania określonych zadań zobacz następujące tematy:

- [Praca z dokumentami](../vsto/working-with-documents.md)

- [Praca z dokumentami tekstowymi](../vsto/working-with-text-in-documents.md)

- [Praca z tabelami](../vsto/working-with-tables.md)

## <a name="understanding"></a> Omówienie modelu obiektów programu Word
 Word istnieją setki obiektów, z którymi możesz wchodzić w interakcje. Te obiekty są zorganizowane w hierarchii, który jest ściśle zgodna interfejsu użytkownika. W górnej części hierarchii jest <xref:Microsoft.Office.Interop.Word.Application> obiektu. Ten obiekt reprezentuje bieżące wystąpienie programu Word. <xref:Microsoft.Office.Interop.Word.Application> Obiekt zawiera <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>, i <xref:Microsoft.Office.Interop.Word.Range> obiektów. Każdy z tych obiektów ma wiele metod i właściwości, do których masz dostęp do manipulowania i interakcji z obiektem.

 Poniższa ilustracja przedstawia jeden widok tych obiektów w hierarchii modelu obiektów programu Word.

 ![Grafika przedstawiająca Model obiektów programu Word](../vsto/media/wrwordobjectmodel.gif "grafiki modelu obiektów programu Word")

 Na pierwszy rzut oka obiekty wydają się się nakładają się na siebie. Na przykład <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> obiekty należą do obu <xref:Microsoft.Office.Interop.Word.Application> obiektu, ale <xref:Microsoft.Office.Interop.Word.Document> obiektu jest również członkiem <xref:Microsoft.Office.Interop.Word.Selection> obiektu. Zarówno <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> obiekty zawierają <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Interop.Word.Range> obiektów. Nachodzące na siebie istnieje, ponieważ istnieje wiele sposobów, które są dostępne z tego samego typu obiektu. Na przykład zastosować formatowanie do <xref:Microsoft.Office.Interop.Word.Range> obiektu; ale może być dostępu do zakresu bieżącego zaznaczenia, określonego akapitu, sekcji lub całego dokumentu.

 W poniższych sekcjach opisano skrótowo obiektów najwyższego poziomu i jak współdziałają ze sobą. Te obiekty obejmują pięć następujących:

- Obiekt aplikacji

- Obiekt dokumentu

- Obiekt wyboru

- obiekt zakresu

- Obiekt zakładki

  Oprócz modelu obiektów programu Word projektów pakietu Office w Visual Studio zapewniają *hostować elementy* i *hostowania kontrolek* które rozszerzają niektóre obiekty w modelu obiektów programu Word. Obiekty hosta i kontrolek hosta zachowują się jak obiekty programu Word, które rozszerzają, ale mają także dodatkowe funkcje, takie jak możliwości wiązania danych i dodatkowych zdarzeń. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md) i [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Obiekt aplikacji
 <xref:Microsoft.Office.Interop.Word.Application> Obiekt reprezentuje aplikacji Word, a jest nadrzędne względem wszystkich innych obiektów. Jej członków zwykle mają zastosowanie do programu Word jako całości. Jej właściwości i metod można użyć do kontrolowania środowiska programu Word.

 W projektach dodatku narzędzi VSTO uzyskujesz dostęp do <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą `Application` pole `ThisAddIn` klasy. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

 W projektach na poziomie dokumentu można uzyskać dostęp <xref:Microsoft.Office.Interop.Word.Application> obiektu za pomocą <xref:Microsoft.Office.Tools.Word.Document.Application%2A> właściwość `ThisDocument` klasy.

### <a name="document-object"></a>Obiekt dokumentu
 <xref:Microsoft.Office.Interop.Word.Document> Obiekt ma decydujące znaczenie dla programowania programu Word. Reprezentuje dokument i całą jego zawartość. Po otwarciu dokumentu lub utworzyć nowy dokument, Utwórz nową <xref:Microsoft.Office.Interop.Word.Document> obiektu, który jest dodawany do <xref:Microsoft.Office.Interop.Word.Documents> zbiór <xref:Microsoft.Office.Interop.Word.Application> obiektu. Dokument, który ma fokus nosi nazwę aktywnego dokumentu. Jest reprezentowany przez <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu.

 Rozszerzanie narzędzi programistycznych pakietu Office w programie Visual Studio <xref:Microsoft.Office.Interop.Word.Document> obiektu, zapewniając <xref:Microsoft.Office.Tools.Word.Document> typu. Ten typ jest *element hosta* daje Ci dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Word.Document> obiektu i dodaje dodatkowe zdarzenia i możliwość dodawania formantów zarządzanego.

 Podczas tworzenia projektów dokumentów, możesz uzyskać dostęp <xref:Microsoft.Office.Tools.Word.Document> elementów członkowskich przy użyciu wygenerowany `ThisDocument` klasy w projekcie. Możesz uzyskać dostęp członkowie <xref:Microsoft.Office.Tools.Word.Document> element hosta za pomocą **mnie** lub **to** słowa kluczowe z kodu w `ThisDocument` klasy lub przy użyciu `Globals.ThisDocument` kodu spoza `ThisDocument` Klasa. Aby uzyskać więcej informacji, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md). Na przykład wybierz pierwszy akapit w dokumencie, należy użyć następującego kodu.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 W projektach dodatku narzędzi VSTO dla programów, można wygenerować <xref:Microsoft.Office.Tools.Word.Document> hosta elementy w czasie wykonywania. Element hosta wygenerowanego umożliwia dodawanie formantów do skojarzonego dokumentu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Obiekt wyboru
 <xref:Microsoft.Office.Interop.Word.Selection> Obiekt reprezentuje obszar, który jest aktualnie wybrany. Podczas wykonywania operacji w interfejsie użytkownika programu Word, np. tekstu pogrubienie, wybierz lub zaznacz tekst, a następnie Zastosuj formatowanie. <xref:Microsoft.Office.Interop.Word.Selection> Obiekt zawsze jest obecny w dokumencie. Jeśli nic nie jest zaznaczone, następnie reprezentuje punkt wstawiania. Ponadto wyboru może obejmować wiele bloków tekstu, które nie są ciągłe.

### <a name="range-object"></a>obiekt zakresu
 <xref:Microsoft.Office.Interop.Word.Range> Obiekt reprezentuje obszar ciągły w dokumencie i jest definiowany przez znak początkową i końcową pozycji znaku. Nie są ograniczone do pojedynczego <xref:Microsoft.Office.Interop.Word.Range> obiektu. Można zdefiniować wiele <xref:Microsoft.Office.Interop.Word.Range> obiektów w tym samym dokumencie. A <xref:Microsoft.Office.Interop.Word.Range> obiekt ma następującą charakterystykę:

- Może składać się wyłącznie punkt wstawiania, zakres tekstu lub całego dokumentu.

- Obejmuje ona niedrukowalne znaki, takie jak spacje, znaki tabulacji i znaczników akapitu.

- Może być obszaru, reprezentowane przez bieżącego zaznaczenia lub może ona reprezentować obszar różni się od bieżącego zaznaczenia.

- Nie jest widoczne w dokumencie, w przeciwieństwie do wyboru, który jest zawsze widoczny.

- Go nie jest zapisywane wraz z dokumentem i istnieje tylko w przypadku, gdy kod jest uruchomiony.

  Po wstawieniu tekstu na końcu zakresu programu Word automatycznie rozszerza zakres obejmujący wstawionego tekstu.

### <a name="content-control-objects"></a>Obiekty kontrolek zawartości
 A <xref:Microsoft.Office.Interop.Word.ContentControl> umożliwia kontrolowanie danych wejściowych i prezentacji tekst i inne typy zawartości w dokumentach programu Word. Element <xref:Microsoft.Office.Interop.Word.ContentControl> można wyświetlić na kilka różnych typów interfejsu użytkownika, które są zoptymalizowane do użycia w dokumentach programu Word, takich jak kontrolki tekstu sformatowanego, selektor daty lub pola kombi. Można również użyć <xref:Microsoft.Office.Interop.Word.ContentControl> aby uniemożliwić użytkownikom edytowanie części dokumentu lub szablonu.

 Program Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.ContentControl> obiektu do kilku formantów do innego hosta. Natomiast <xref:Microsoft.Office.Interop.Word.ContentControl> obiektu można wyświetlić żadnego z różnego rodzaju interfejsu użytkownika, które są dostępne dla formantów zawartości, program Visual Studio oferuje innego typu dla każdego formantu zawartości. Na przykład, można użyć <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do tworzenia kontrolki tekstu sformatowanego, lub można użyć <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> można utworzyć selektora daty. Te kontrolki hosta zachowują się jak natywnych <xref:Microsoft.Office.Interop.Word.ContentControl>, ale mają dodatkowe zdarzenia i możliwości wiązania danych. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Obiekt zakładki
 <xref:Microsoft.Office.Interop.Word.Bookmark> Obiekt reprezentuje obszar ciągły w dokumencie za pomocą pozycji początkowej i końcowej pozycji. Zakładki służy do oznaczania miejsc w dokumencie lub jako kontener dla tekstu w dokumencie. Element <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu składają się z punktu wstawiania, lub można tak duże jak całego dokumentu. A <xref:Microsoft.Office.Interop.Word.Bookmark> ma następujące cechy, które ustaw ją z wyjątkiem <xref:Microsoft.Office.Interop.Word.Range> obiektu:

- Możesz nazwać zakładki w czasie projektowania.

- <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty są zapisane w dokumencie i związku z tym nie są usuwane, gdy kod przestanie działać lub dokumentu jest zamknięty.

- Zakładki, które mogą być ukryte lub przez ustawienie <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> właściwość <xref:Microsoft.Office.Interop.Word.View> obiekt **false** lub **true**.

  Program Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu, zapewniając <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta. <xref:Microsoft.Office.Tools.Word.Bookmark> Kontrolki hosta, który zachowuje się jak macierzystej <xref:Microsoft.Office.Interop.Word.Bookmark>, ale ma dodatkowe zdarzenia i możliwości wiązania danych. Można powiązać danych kontrolka zakładki w dokumencie, w taki sam sposób, jak powiązać dane z formantu pola tekstowego w formularzu Windows. Aby uzyskać więcej informacji, zobacz [Bookmark, formant](../vsto/bookmark-control.md).

## <a name="WordOMDocumentation"></a> Zapoznaj się z dokumentacją modelu obiektów programu Word
 Aby uzyskać pełne informacje na temat modelu obiektów programu Word mogą odwoływać się do programu Word odwołanie do zestawu podstawowej usługi międzyoperacyjnej (PIA) i Visual Basic for Applications (VBA) odwołania do modelu obiektu.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do zestawu podstawowej usługi międzyoperacyjnej
 Dokumentacja referencyjna programu Word PIA opisano typy w podstawowy zestaw międzyoperacyjny dla programu Word. Ta dokumentacja jest dostępna z następującej lokalizacji: [Odwołanie do zestawu podstawowej usługi międzyoperacyjnej Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Aby uzyskać więcej informacji na temat projektowania PIA słowa, takie jak różnice między klasami i interfejsy, które PIA i sposobu implementacji zdarzenia w PIA, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592).

### <a name="vba-object-model-reference"></a>Dokumentacja modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumenty modelu obiektów programu Word, ponieważ jest ona udostępniana dla kodu VBA. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu Word 2010](http://go.microsoft.com/fwlink/?LinkId=199772).

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w PIA programu Word. Na przykład, obiekt dokumentu w dokumentacja modelu obiektów VBA odpowiada <xref:Microsoft.Office.Interop.Word.Document> obiektu w PIA programu Word. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metody i zdarzenia, należy translacji kodu VBA w ramach tego odwołania do Visual Basic lub Visual C# Jeśli chcesz użyć ich w projekcie programu Word, które tworzysz przy użyciu programu Visual Studio .

## <a name="see-also"></a>Zobacz także
- [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Praca z dokumentami](../vsto/working-with-documents.md)
- [Praca z dokumentami tekstowymi](../vsto/working-with-text-in-documents.md)
- [Praca z tabelami](../vsto/working-with-tables.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
