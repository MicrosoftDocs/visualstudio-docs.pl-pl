---
title: Elementy hosta i formanty hosta — Omówienie
description: Dowiedz się, że elementy hosta i formanty hosta są typami, które ułatwiają zapewnienie modelu programowania dla rozwiązań pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c58ad4dee128f7b2d0dcd91edb7b19c7f8f5a474
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933625"
---
# <a name="host-items-and-host-controls-overview"></a>Elementy hosta i formanty hosta — Omówienie
  Elementy hosta i formanty hosta są typami, które ułatwiają zapewnienie modelu programowania dla rozwiązań pakietu Office utworzonych przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio. Elementy hosta i kontrolki hosta współpracują z modelami obiektów Microsoft Office Word i Microsoft Office Excel, które są oparte na modelu COM, podobnie jak w przypadku współpracy z obiektami zarządzanymi, takimi jak formanty Windows Forms.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="host-items"></a>Elementy hosta
 Elementy hosta to typy, które znajdują się w górnej części hierarchii modelu obiektów w projektach pakietu Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Definiuje następujące elementy hosta dla rozwiązań programów Word i Excel:

- <xref:Microsoft.Office.Tools.Word.Document>

- <xref:Microsoft.Office.Tools.Excel.Workbook>

- <xref:Microsoft.Office.Tools.Excel.Worksheet>

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Każdy z tych typów rozszerza obiekt, który istnieje natywnie w modelu obiektów programu Word lub Excel, nazywany *natywnym obiektem pakietu Office*. Na przykład <xref:Microsoft.Office.Tools.Word.Document> element hosta rozszerza <xref:Microsoft.Office.Interop.Word.Document> obiekt, który jest zdefiniowany w podstawowym zestawie międzyoperacyjnym dla programu Word.

  Elementy hosta mają zwykle te same funkcje podstawowe, co odpowiednie obiekty pakietu Office, ale zostały ulepszone przy użyciu następujących funkcji:

- Możliwość hostowania formantów zarządzanych, w tym formantów hosta i formantów Windows Forms.

- Bogatsze modele zdarzeń. Niektóre zdarzenia dokumentów, skoroszytów i arkuszy w natywnych modelach programów Word i Excel są wywoływane tylko na poziomie aplikacji. Elementy hosta zapewniają te zdarzenia na poziomie dokumentu, dzięki czemu można łatwiej obsłużyć zdarzenia dla określonego dokumentu.

### <a name="understand-host-items-in-document-level-projects"></a>Zrozumienie elementów hosta w projektach na poziomie dokumentu
 W projektach na poziomie dokumentu elementy hosta udostępniają punkt wejścia dla kodu i mają projektanci, którzy pomagają opracowywać rozwiązanie.

 <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Excel.Worksheet> Elementy hosta i są skojarzone z projektantami, które są wizualną reprezentacją dokumentu lub arkusza, takiego jak Projektant Windows Forms. Za pomocą tego projektanta można modyfikować zawartość dokumentu lub arkusza bezpośrednio w programie Word lub Excel i przeciągać formanty na powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [dokument](../vsto/document-host-item.md) elementy hosta i [arkusz elementów hosta](../vsto/worksheet-host-item.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook>Element hosta nie działa jako kontener dla formantów, które mają interfejs użytkownika. Zamiast tego, Projektant dla tego elementu hosta działa jako zasobnik składnika, który umożliwia przeciąganie składnika, takiego jak <xref:System.Data.DataSet> , na powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [skoroszyt element hosta](../vsto/workbook-host-item.md).

 Elementy hosta nie mogą być tworzone programowo w projektach na poziomie dokumentu. Zamiast tego należy użyć `ThisDocument` `ThisWorkbook` klas, lub `Sheet` *n* , które program Visual Studio automatycznie generuje w projekcie w czasie projektowania. Te wygenerowane klasy pochodzą od elementów hosta i udostępniają punkt wejścia dla kodu. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="understand-host-items-in-vsto-add-in-projects"></a>Omówienie elementów hosta w projektach dodatku narzędzi VSTO
 Po utworzeniu dodatku narzędzi VSTO nie masz domyślnego dostępu do żadnych elementów hosta. Można jednak generować <xref:Microsoft.Office.Tools.Word.Document> , <xref:Microsoft.Office.Tools.Excel.Workbook> i <xref:Microsoft.Office.Tools.Excel.Worksheet> hostować elementy w dodatkach narzędzi VSTO programu Word i Excel w czasie wykonywania.

 Po wygenerowaniu elementu hosta można wykonać zadania, takie jak dodawanie kontrolek do dokumentów. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="host-controls"></a>Kontrolki hosta
 Formanty hosta poszerzają różne obiekty interfejsu użytkownika w modelach programów Word i Excel, takich jak `Microsoft.Office.Interop.Word.ContentControl` <xref:Microsoft.Office.Interop.Excel.Range> obiekty i.

 Następujące kontrolki hosta są dostępne dla projektów programu Excel:

- [Kontrolka wykresu](../vsto/chart-control.md)

- [ListObject — formant](../vsto/listobject-control.md)

- [NamedRange — formant](../vsto/namedrange-control.md)

- [XmlMappedRange — formant](../vsto/xmlmappedrange-control.md)

  Następujące kontrolki hosta są dostępne dla projektów programu Word:

- [Kontrolka zakładki](../vsto/bookmark-control.md)

- [Kontrolki zawartości](../vsto/content-controls.md)

- [XMLNode — formant](../vsto/xmlnode-control.md)

- [Formant XMLNodes](../vsto/xmlnodes-control.md)

  Formanty hosta, które są dodawane do dokumentów pakietu Office, zachowują się jak natywne obiekty pakietu Office; jednak formanty hosta mają dodatkowe funkcje, w tym zdarzenia i możliwości powiązania danych. Na przykład jeśli chcesz przechwytywać zdarzenia obiektu natywnego <xref:Microsoft.Office.Interop.Excel.Range> w programie Excel, musisz najpierw obsłużyć zdarzenie zmiany w arkuszu. Następnie należy określić, czy zmiana została wprowadzona w ramach programu <xref:Microsoft.Office.Interop.Excel.Range> . Z kolei <xref:Microsoft.Office.Tools.Excel.NamedRange> formant hosta ma <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie, które można obsłużyć bezpośrednio.

  Relacja między elementem hosta i kontrolkami hosta jest podobna do relacji między kontrolkami formularza systemu Windows i Windows Forms. Tak samo jak umieszczasz kontrolkę pole tekstowe w formularzu systemu Windows, umieścisz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę na <xref:Microsoft.Office.Tools.Excel.Worksheet> elemencie hosta. Poniższa ilustracja przedstawia relację między elementami hosta i kontrolkami hosta.

  ![Relacja między elementami hosta i kontrolkami hosta](../vsto/media/hostitemscontrols.png "Relacja między elementami hosta i kontrolkami hosta")

  Możesz również użyć formantów Windows Forms w rozwiązaniach pakietu Office, dodając je bezpośrednio do powierzchni dokumentu Word i Excel. Aby uzyskać więcej informacji, zobacz [Windows Forms kontrolki w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md).

> [!NOTE]
> Dodawanie formantów hosta lub formantów Windows Forms do dokumentu podrzędnego programu Word nie jest obsługiwane.

### <a name="add-host-controls-to-your-documents"></a>Dodawanie formantów hosta do dokumentów
 W projektach na poziomie dokumentu można dodać kontrolki hosta do dokumentów programu Word lub arkuszy programu Excel w czasie projektowania w następujący sposób:

- Dodaj formanty hosta do dokumentu w czasie projektowania w taki sam sposób, jak dodać obiekt macierzysty.

- Przeciągnij formanty hosta z **przybornika** do dokumentów i arkuszy. Formanty hosta programu Excel są dostępne na karcie **formanty programu Excel** w obszarze projekty programu Excel, a formanty hosta programu Word są dostępne na karcie **formanty programu** Word w projektach programu Word.

- Przeciągnij kontrolki hosta z okna **źródła danych** na dokumenty i arkusze. Pozwala to na dodawanie formantów, które są już powiązane z danymi. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

  W projektach dodatku na poziomie dokumentu i narzędzi VSTO można także dodać niektóre formanty hosta do dokumentów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Więcej informacji o sposobach dodawania formantów hosta do dokumentów znajduje się w następujących tematach:

- [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Instrukcje: Dodawanie kontrolek XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)

### <a name="name-host-controls"></a>Nazwy formantów hosta
 Gdy przeciągasz kontrolkę hosta z **przybornika** do dokumentu, formant jest automatycznie nazwany przy użyciu typu kontrolki z liczbą przyrostową na końcu. Na przykład zakładki mają nazwę **Bookmark1**, **bookmark2** i tak dalej. Jeśli używasz natywnej funkcji programu Word lub Excel do dodawania formantu, możesz nadać mu określoną nazwę w momencie utworzenia. Możesz również zmienić nazwy kontrolek, zmieniając wartość właściwości **Nazwa** w oknie **Właściwości** .

> [!NOTE]
> Nie można używać słów zarezerwowanych do nazwy kontrolek hosta. Na przykład jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do arkusza i zmienisz nazwę na **system**, wystąpią błędy podczas kompilowania projektu.

### <a name="delete-host-controls"></a>Usuwanie formantów hosta
 W projektach na poziomie dokumentu można usunąć kontrolki hosta w czasie projektowania, zaznaczając kontrolkę w arkuszu programu Excel lub dokumencie programu Word i naciskając klawisz **delete** . Należy jednak użyć okna dialogowego **Definiowanie nazwy** w programie Excel do usuwania <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek.

 Jeśli dodasz kontrolkę hosta do dokumentu w czasie projektowania, nie należy jej usuwać programowo w czasie wykonywania, ponieważ przy następnym próbie użycia formantu w kodzie zostanie zgłoszony wyjątek. `Delete`Metoda kontrolki hosta usuwa tylko kontrolki hosta, które są dodawane do dokumentu w czasie wykonywania. W przypadku wywołania `Delete` metody kontrolki hosta, która została utworzona w czasie projektowania, zgłaszany jest wyjątek.

 Na przykład metoda programu <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> pomyślnie usuwa, <xref:Microsoft.Office.Tools.Excel.NamedRange> Jeśli została ona programowo dodana do arkusza, co jest znane jako dynamiczne tworzenie kontrolek hosta. Dynamicznie utworzone formanty hosta można także usunąć, przekazując nazwę kontrolki do `Remove` metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> lub <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Jeśli użytkownicy końcowi usuną kontrolę hosta z dokumentu w czasie wykonywania, rozwiązanie może się nie powieść w nieoczekiwany sposób. Możesz użyć funkcji ochrony dokumentów w programach Word i Excel, aby chronić formanty hosta przed ich usunięciem. Aby uzyskać więcej informacji, zobacz [przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).

> [!NOTE]
> Nie należy programistycznie usuwać formantów podczas `Shutdown` obsługi zdarzeń dokumentu lub arkusza. Elementy interfejsu użytkownika nie są już dostępne w przypadku `Shutdown` wystąpienia zdarzenia. Jeśli chcesz usunąć formanty przed zamknięciem aplikacji, Dodaj kod do innego programu obsługi zdarzeń, takiego jak `BeforeClose` lub `BeforeSave` .

### <a name="program-against-host-control-events"></a>Program względem zdarzeń kontroli hosta
 Jednym ze sposobów, aby formanty hosta rozszerzający obiekty pakietu Office, jest dodawanie zdarzeń. Na przykład <xref:Microsoft.Office.Interop.Excel.Range> obiekt w programie Excel i <xref:Microsoft.Office.Interop.Word.Bookmark> obiekt w programie Word nie ma zdarzeń, ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozszerza te obiekty przez dodanie zdarzeń programowalnych. Możesz uzyskać dostęp do tych zdarzeń i ich kodu w taki sam sposób, jak w przypadku dostępu do zdarzeń formantów na Windows Forms: za pomocą listy rozwijanej zdarzeń w Visual Basic i stronie właściwości zdarzenia w języku C#. Aby uzyskać więcej informacji, zobacz [Przewodnik: program dla zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

> [!NOTE]
> Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel na **wartość false**. Ustawienie dla tej właściwości **wartości false** uniemożliwia programowi Excel podnoszenie jakichkolwiek zdarzeń, w tym zdarzeń kontrolek hosta.

## <a name="see-also"></a>Zobacz też
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
