---
title: Model obiektu Word — omówienie
description: Model obiektów programu Word składa się z klas i interfejsów, które są dostępne w podstawowym zestawie międzyoptykowym dla programu Word i są zdefiniowane w przestrzeni nazw programu Word.
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
ms.openlocfilehash: 3367c1ad557c647639b9fd2d2aacf7845e067660
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826632"
---
# <a name="word-object-model-overview"></a>Model obiektu Word — omówienie
  Podczas tworzenia rozwiązań programu Word w Visual Studio, wchodzisz w interakcję z modelem obiektów programu Word. Ten model obiektów składa się z klas i interfejsów, które są dostarczane w podstawowym zestawie międzyoptykowym dla programu Word i są zdefiniowane w przestrzeni <xref:Microsoft.Office.Interop.Word> nazw .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Ten temat zawiera krótkie omówienie modelu obiektów programu Word. Zasoby, w których można dowiedzieć się więcej na temat całego modelu obiektów programu Word, można znaleźć w dokumentacji dotyczącej używania [modelu obiektów programu Word.](#WordOMDocumentation)

 Aby uzyskać informacje na temat używania modelu obiektów programu Word do wykonywania określonych zadań, zobacz następujące tematy:

- [Praca z dokumentami](../vsto/working-with-documents.md)

- [Praca z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)

- [Praca z tabelami](../vsto/working-with-tables.md)

## <a name="understand-the-word-object-model"></a><a name="understanding"></a> Opis modelu obiektów programu Word
 Program Word udostępnia setki obiektów, z którymi można wchodzić w interakcje. Te obiekty są zorganizowane w hierarchii, która jest ściśle zgodna z interfejsem użytkownika. W górnej części hierarchii znajduje się <xref:Microsoft.Office.Interop.Word.Application> obiekt . Ten obiekt reprezentuje bieżące wystąpienie programu Word. Obiekt <xref:Microsoft.Office.Interop.Word.Application> zawiera obiekty , , i <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Range> . Każdy z tych obiektów ma wiele metod i właściwości, do których można uzyskać dostęp, aby manipulować obiektem i wchodzić z nim w interakcje.

 Na poniższej ilustracji przedstawiono jeden widok tych obiektów w hierarchii modelu obiektów programu Word.

 ![Grafika przedstawiająca model obiektu Word](../vsto/media/wrwordobjectmodel.gif "Grafika modelu obiektu Word")

 Na pierwszy rzut oka obiekty nakładają się na siebie. Na przykład obiekty i są członkami obiektu , ale obiekt jest <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Selection> również <xref:Microsoft.Office.Interop.Word.Application> <xref:Microsoft.Office.Interop.Word.Document> członkiem obiektu <xref:Microsoft.Office.Interop.Word.Selection> . Obiekty <xref:Microsoft.Office.Interop.Word.Document> i <xref:Microsoft.Office.Interop.Word.Selection> zawierają obiekty i <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Interop.Word.Range> . Nakładanie się istnieje, ponieważ istnieje wiele sposobów uzyskiwania dostępu do tego samego typu obiektu. Na przykład stosujesz formatowanie do obiektu, ale możesz chcieć uzyskać dostęp do zakresu bieżącego zaznaczenia, określonego akapitu, sekcji lub <xref:Microsoft.Office.Interop.Word.Range> całego dokumentu.

 W poniższych sekcjach krótko opisano obiekty najwyższego poziomu i sposób, w jaki współdziałają ze sobą. Te obiekty obejmują następujące pięć:

- Obiekt aplikacji

- Obiekt dokumentu

- Selection, obiekt

- obiekt zakresu

- Obiekt zakładki

  Oprócz modelu obiektów programu Word projekty pakietu Office  w  programie Visual Studio zapewniają elementy hosta i kontrolki hosta, które rozszerzają niektóre obiekty w modelu obiektów programu Word. Elementy hosta i kontrolki hosta zachowują się jak obiekty programu Word, które rozszerzają, ale mają również dodatkowe funkcje, takie jak możliwości powiązania danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md) oraz Omówienie elementów hosta i [kontrolek hosta.](../vsto/host-items-and-host-controls-overview.md)

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt <xref:Microsoft.Office.Interop.Word.Application> reprezentuje aplikację Word i jest elementem nadrzędnym wszystkich innych obiektów. Jego elementy członkowskie zwykle mają zastosowanie do programu Word jako całości. Za pomocą jego właściwości i metod można kontrolować środowisko programu Word.

 W projektach dodatków VSTO można uzyskać dostęp do obiektu przy <xref:Microsoft.Office.Interop.Word.Application> użyciu `Application` pola klasy `ThisAddIn` . Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md)

 W projektach na poziomie dokumentu można uzyskać dostęp do obiektu przy <xref:Microsoft.Office.Interop.Word.Application> użyciu <xref:Microsoft.Office.Tools.Word.Document.Application%2A> właściwości klasy `ThisDocument` .

### <a name="document-object"></a>Obiekt dokumentu
 Obiekt <xref:Microsoft.Office.Interop.Word.Document> jest centralnym elementem programowania programu Word. Reprezentuje dokument i całą jego zawartość. Po otwarciu dokumentu lub utworzeniu nowego dokumentu tworzysz nowy obiekt, który jest dodawany do <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Interop.Word.Documents> kolekcji <xref:Microsoft.Office.Interop.Word.Application> obiektu . Dokument, który ma fokus, jest nazywany aktywnym dokumentem. Jest on reprezentowany przez <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> właściwość <xref:Microsoft.Office.Interop.Word.Application> obiektu .

 Narzędzia programskie pakietu Office Visual Studio <xref:Microsoft.Office.Interop.Word.Document> rozszerzają obiekt, podając <xref:Microsoft.Office.Tools.Word.Document> typ . Ten typ jest *elementem hosta,* który zapewnia dostęp do wszystkich funkcji obiektu i dodaje dodatkowe zdarzenia oraz możliwość <xref:Microsoft.Office.Interop.Word.Document> dodawania kontrolek zarządzanych.

 Podczas tworzenia projektu na poziomie dokumentu można uzyskać dostęp do składowych przy użyciu <xref:Microsoft.Office.Tools.Word.Document> wygenerowanej `ThisDocument` klasy w projekcie. Dostęp do elementów członkowskich elementu hosta można uzyskać przy użyciu słowa kluczowego Me lub tego słowa kluczowego z kodu w klasie lub przy użyciu kodu <xref:Microsoft.Office.Tools.Word.Document>   `ThisDocument` `Globals.ThisDocument` spoza `ThisDocument` klasy . Aby uzyskać więcej informacji, zobacz [Program document-level customizations](../vsto/programming-document-level-customizations.md)(Program dostosowań na poziomie dokumentu). Aby na przykład wybrać pierwszy akapit w dokumencie, użyj następującego kodu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet120":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet120":::

 W projektach dodatków VSTO można generować <xref:Microsoft.Office.Tools.Word.Document> elementy hosta w czasie uruchamiania. Możesz użyć wygenerowanego elementu hosta, aby dodać kontrolki do skojarzonego dokumentu. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

### <a name="selection-object"></a>Obiekt wyboru
 Obiekt reprezentuje aktualnie wybrany <xref:Microsoft.Office.Interop.Word.Selection> obszar. Podczas wykonywania operacji w interfejsie użytkownika programu Word, takiej jak pogrubienie tekstu, zaznaczasz lub wyróżniasz tekst, a następnie stosujesz formatowanie. Obiekt <xref:Microsoft.Office.Interop.Word.Selection> jest zawsze obecny w dokumencie. Jeśli nic nie jest zaznaczone, reprezentuje on punkt wstawiania. Ponadto zaznaczenie może obejmować wiele bloków tekstu, które nie są ciągłe.

### <a name="range-object"></a>obiekt zakresu
 Obiekt reprezentuje ciągły obszar w dokumencie i jest definiowany przez początkową pozycję znaku i <xref:Microsoft.Office.Interop.Word.Range> końcową pozycję znaku. Nie trzeba ograniczać się do pojedynczego <xref:Microsoft.Office.Interop.Word.Range> obiektu. W tym samym dokumencie <xref:Microsoft.Office.Interop.Word.Range> można zdefiniować wiele obiektów. Obiekt <xref:Microsoft.Office.Interop.Word.Range> ma następujące cechy:

- Może składać się tylko z punktu wstawiania, zakresu tekstu lub całego dokumentu.

- Zawiera znaki bez drukowania, takie jak spacje, znaki tabułów i znaki akapitu.

- Może to być obszar reprezentowany przez bieżący wybór lub może reprezentować obszar inny niż bieżący wybór.

- W przeciwieństwie do zaznaczenia, który jest zawsze widoczny, nie jest widoczny w dokumencie.

- Nie jest on zapisywany wraz z dokumentem i istnieje tylko wtedy, gdy kod jest uruchomiony.

  Po wstawieniu tekstu na końcu zakresu program Word automatycznie rozszerza zakres, aby uwzględnić wstawiony tekst.

### <a name="content-control-objects"></a>Obiekty kontroli zawartości
 Umożliwia sterowanie wprowadzaniem i prezentacją tekstu oraz innych typów zawartości w <xref:Microsoft.Office.Interop.Word.ContentControl> dokumentach programu Word. Element może wyświetlać kilka różnych typów interfejsu użytkownika zoptymalizowanych pod kątem użycia w dokumentach programu Word, takich jak kontrolka tekstu sformatowanego, s wyboru daty <xref:Microsoft.Office.Interop.Word.ContentControl> lub pole kombi. Możesz również użyć funkcji , aby uniemożliwić użytkownikom edytowanie <xref:Microsoft.Office.Interop.Word.ContentControl> sekcji dokumentu lub szablonu.

 Visual Studio rozszerza obiekt <xref:Microsoft.Office.Interop.Word.ContentControl> na kilka różnych kontrolek hosta. Podczas gdy obiekt może wyświetlać dowolny z różnych typów interfejsu użytkownika dostępnych dla kontrolek zawartości, Visual Studio udostępnia inny typ dla <xref:Microsoft.Office.Interop.Word.ContentControl> każdej kontrolki zawartości. Możesz na przykład użyć kontrolki , aby utworzyć kontrolkę tekstu sformatowanego, lub użyć kontrolki , aby utworzyć s wyboru <xref:Microsoft.Office.Tools.Word.RichTextContentControl> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> daty. Te kontrolki hosta zachowują się jak natywne kontrolki , ale <xref:Microsoft.Office.Interop.Word.ContentControl> mają dodatkowe zdarzenia i możliwości powiązania danych. Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Obiekt zakładki
 Obiekt reprezentuje ciągły obszar w dokumencie, zarówno z pozycją początkową, jak <xref:Microsoft.Office.Interop.Word.Bookmark> i końcową. Za pomocą zakładek można oznaczać lokalizację w dokumencie lub jako kontener tekstu w dokumencie. Obiekt <xref:Microsoft.Office.Interop.Word.Bookmark> może składać się z punktu wstawiania lub być tak duży, jak cały dokument. Obiekt <xref:Microsoft.Office.Interop.Word.Bookmark> ma następujące cechy, które odróżniają go od <xref:Microsoft.Office.Interop.Word.Range> obiektu :

- Zakładkę można nazwać w czasie projektowania.

- <xref:Microsoft.Office.Interop.Word.Bookmark> Obiekty są zapisywane wraz z dokumentem i w związku z tym nie są usuwane po zatrzymaniu działania kodu lub zamknięciu dokumentu.

- Zakładki mogą być ukryte lub widoczne, ustawiając właściwość obiektu na wartość <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> <xref:Microsoft.Office.Interop.Word.View> **false** lub **true.**

  Visual Studio rozszerza <xref:Microsoft.Office.Interop.Word.Bookmark> obiekt, zapewniając kontrolę <xref:Microsoft.Office.Tools.Word.Bookmark> hosta. Kontrolka <xref:Microsoft.Office.Tools.Word.Bookmark> hosta zachowuje się jak natywny element , ale ma dodatkowe zdarzenia i możliwości powiązania <xref:Microsoft.Office.Interop.Word.Bookmark> danych. Dane można powiązać z kontrolką zakładki w dokumencie w taki sam sposób, jak powiązać dane z kontrolką pola tekstowego w formularzu systemu Windows. Aby uzyskać więcej informacji, zobacz [Kontrolka zakładki](../vsto/bookmark-control.md).

## <a name="use-the-word-object-model-documentation"></a><a name="WordOMDocumentation"></a> Korzystanie z dokumentacji modelu obiektów programu Word
 Aby uzyskać pełne informacje na temat modelu obiektów programu Word, można zapoznać się z odwołaniem do podstawowego zestawu międzyoptykowego (PIA) programu Word i odwołaniem do modelu obiektów Visual Basic for Applications (VBA).

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoptykowego
 W dokumentacji referencyjnej dotyczącej aplikacji Word PIA opisano typy w podstawowym zestawie międzyoptyku dla programu Word. Ta dokumentacja jest dostępna w następującej lokalizacji: Dokumentacja podstawowego zestawu [międzyoptykowego programu Word 2010.](../vsto/office-primary-interop-assemblies.md)

 Aby uzyskać więcej informacji na temat projektu aplikacji Word PIA, takich jak różnice między klasami i interfejsami w danych osobowych oraz sposób implementowania zdarzeń w usłudze PIA, zobacz Overview of classes and [interfaces in the Office primary interop assemblies](/previous-versions/office/office-12/ms247299(v=office.12))(Omówienie klas i interfejsów w podstawowych zestawach międzyoptykowych pakietu Office).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Odwołanie do modelu obiektów VBA dokumentuje model obiektów word, gdy jest on narażony na kod VBA. Aby uzyskać więcej informacji, zobacz Odwołanie do modelu obiektów programu [Word 2010](/office/vba/api/overview/Word/object-model).

 Wszystkie obiekty i elementy członkowskie w odwołaniach do modelu obiektów VBA odpowiadają typom i członkom w piacie programu Word. Na przykład obiekt Document w dokumentacji modelu obiektów VBA odpowiada obiektowi <xref:Microsoft.Office.Interop.Word.Document> w piacie programu Word. Mimo że odwołanie do modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu na język Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie programu Word, który tworzysz przy użyciu języka Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Podstawowe zestawy międzyzestawowe pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Praca z dokumentami](../vsto/working-with-documents.md)
- [Praca z tekstem w dokumentach](../vsto/working-with-text-in-documents.md)
- [Praca z tabelami](../vsto/working-with-tables.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
