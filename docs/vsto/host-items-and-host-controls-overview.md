---
title: Host formantów Przegląd obiektów hosta i
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ef2d97b0e3b15accdeb267513b38ef6d5bd729d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607112"
---
# <a name="host-items-and-host-controls-overview"></a>Host formantów Przegląd obiektów hosta i
  Obiekty hosta i kontrolek hosta są typy, które pomagają modelu programowania rozwiązań pakietu Office, które są tworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio. Obiekty hosta i kontrolek hosta upewnij się, interakcji z modeli obiektów programu Microsoft Office Word i Microsoft Office Excel, które są oparte na modelu COM, bardziej jak interakcji z obiektami zarządzanymi, takie jak kontrolek formularzy Windows.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="host-items"></a>Obiekty hosta
 Obiekty hosta są typy, które znajdowały się u góry hierarchii modelu obiektów w projektach pakietu Office. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Definiuje następujące elementy hosta dla programów Word i Excel rozwiązań:

- <xref:Microsoft.Office.Tools.Word.Document>

- <xref:Microsoft.Office.Tools.Excel.Workbook>

- <xref:Microsoft.Office.Tools.Excel.Worksheet>

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Każdy z tych typów rozszerza obiekt, który natywnie istnieje w modelu obiektów programu Word lub Excel, o nazwie *obiekt natywny Office*. Na przykład <xref:Microsoft.Office.Tools.Word.Document> rozszerza element hosta <xref:Microsoft.Office.Interop.Word.Document> obiektu, który jest zdefiniowany w podstawowy zestaw międzyoperacyjny dla programu Word.

  Obiekty hosta zazwyczaj mają taką samą funkcjonalność podstawowego, jak odnośnych obiektach pakietu Office, ale są ulepszone dzięki następującym funkcjom:

- Możliwość hostowania zarządzane formanty, łącznie z kontrolki hosta i kontrolek formularzy Windows Forms.

- Bardziej zaawansowane modele zdarzeń. Niektóre zdarzenia dokumentu, skoroszytu i arkuszy w macierzystym modele obiektów programu Word i Excel są wywoływane tylko na poziomie aplikacji. Obiekty hosta oferuje te zdarzenia na poziomie dokumentu, dlatego jest łatwiejsze do obsługi zdarzeń dla określonego dokumentu.

### <a name="understand-host-items-in-document-level-projects"></a>Omówienie elementów hosta w projektach na poziomie dokumentu
 W projektach na poziomie dokumentu elementów hosta zapewnia punkt wejścia dla kodu i mają projektantów ułatwiające opracowania swojego rozwiązania.

 <xref:Microsoft.Office.Tools.Word.Document> i <xref:Microsoft.Office.Tools.Excel.Worksheet> elementów hosta skojarzony projektantach, które są wizualnej reprezentacji w dokumencie lub arkuszu, takich jak Windows Forms designer. Można użyć tego projektanta, zmodyfikuj zawartość dokumentu lub arkuszu bezpośrednio w programie Word lub Excel i przeciągnij formanty na powierzchni projektowej. Aby uzyskać więcej informacji, zobacz [element hosta dokumentu](../vsto/document-host-item.md) i [element hosta arkusza](../vsto/worksheet-host-item.md).

 <xref:Microsoft.Office.Tools.Excel.Workbook> Element hosta nie działa jako kontener dla formantów, które mają interfejs użytkownika. Zamiast tego projektanta dla tego elementu hosta działa jako zasobnika składnika, co pozwala na przeciągnij składnik, taki jak <xref:System.Data.DataSet>, na jego powierzchnię projektu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).

 Obiekty hosta nie można utworzyć programowo w projektach na poziomie dokumentu. Zamiast tego należy użyć `ThisDocument`, `ThisWorkbook`, lub `Sheet` *n* klas, które program Visual Studio automatycznie generuje w projekcie w czasie projektowania. Te wygenerowane klasy pochodzić od elementów hosta i zapewniają punkt wejścia dla kodu. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="understand-host-items-in-vsto-add-in-projects"></a>Omówienie elementów hosta w projektach dodatku narzędzi VSTO
 Podczas tworzenia dodatku narzędzi VSTO domyślnie nie mają dostępu do wszystkich elementów hosta. Jednakże, można wygenerować <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, i <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta elementów w programach Word i dodatków narzędzi VSTO dla programu Excel w czasie wykonywania.

 Po wygenerowaniu elementu hosta można wykonywać zadania, takie jak dodawanie formantów do dokumentów. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="host-controls"></a>Kontrolki hosta
 Formanty hosta rozszerzyć różnych obiektów interfejsu użytkownika w modelach obiektów programu Word i Excel, takich jak `Microsoft.Office.Interop.Word.ContentControl` i <xref:Microsoft.Office.Interop.Excel.Range> obiektów.

 Dostępne dla projektów programu Excel są następujące formanty hosta:

- [Kontrolka wykresu](../vsto/chart-control.md)

- [ListObject — formant](../vsto/listobject-control.md)

- [Namedrange — formant](../vsto/namedrange-control.md)

- [Xmlmappedrange — formant](../vsto/xmlmappedrange-control.md)

  Następujące kontrolki hosta są dostępne dla projektów programu Word:

- [BOOKMARK, kontrolka](../vsto/bookmark-control.md)

- [Formanty zawartości](../vsto/content-controls.md)

- [Formant XMLNode](../vsto/xmlnode-control.md)

- [Formant XMLNodes](../vsto/xmlnodes-control.md)

  Formanty hosta, które są dodawane do dokumentów pakietu Office zachowują się jak natywnych obiektów pakietu Office; jednak formanty hosta mają dodatkowe funkcje, w tym zdarzenia i możliwości wiązania danych. Na przykład, kiedy mają być przechwytywane zdarzenia macierzystej <xref:Microsoft.Office.Interop.Excel.Range> obiektu w programie Excel, najpierw musi obsługiwać zdarzenia zmiany arkusza. Następnie należy określić, czy zmiana została wprowadzona w ramach <xref:Microsoft.Office.Interop.Excel.Range>. Z kolei <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki hosta ma <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> zdarzenie, dla którego można obsługiwać bezpośrednio.

  Relacja między elementem hosta i kontrolek hosta jest podobna do relacji między kontrolkami formularz Windows i Windows Forms. Tak samo, jak umieszczenie kontrolkę pola tekstowego w formularzu Windows, umieść <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować na <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Poniższa ilustracja przedstawia relację między elementów hosta i kontrolek hosta.

  ![Relacja między elementami hosta i kontrolek hosta](../vsto/media/hostitemscontrols.png "relacji między elementami hosta i kontrolek hosta")

  Umożliwia także kontrolek formularzy Windows Forms w rozwiązaniach pakietu Office, dodając je bezpośrednio do powierzchni dokument programu Word i Excel. Aby uzyskać więcej informacji, zobacz [kontrolek formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

> [!NOTE]
>  Dodawanie kontrolki hosta lub kontrolek formularzy Windows Forms do dokumentu programu Word nie jest obsługiwana.

### <a name="add-host-controls-to-your-documents"></a>Dodawanie hosta formantów do dokumentów
 W projektach na poziomie dokumentu można dodać kontrolki hosta do dokumentów programu Word lub arkuszy programu Excel w czasie projektowania w następujący sposób:

- Dodaj formanty hosta do dokumentu w czasie projektowania w taki sam sposób należy dodać obiekt za pomocą natywnego.

- Przeciągnij formanty hosta z **przybornika** na swoje dokumenty i arkusze. Kontrolki hosta programu Excel są dostępne w **kontrolki programu Excel** kartę w projektach programu Excel i host programu Word, które są dostępne w **formanty programu Word** kartę w projektach programu Word.

- Przeciągnij formanty hosta z **źródeł danych** okna na swoje dokumenty i arkusze. Pozwala na dodawanie formantów, które już są powiązane z danymi. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

  W poziomie dokumentu i projektów dodatku VSTO możesz dodać niektóre formanty hosta do dokumentów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Aby uzyskać więcej informacji o sposobie dodawania formantów hosta do dokumentów zobacz następujące tematy:

- [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)

- [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

- [Instrukcje: Dodaj zawartość formantów do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Instrukcje: Dodawanie formantów XMLNode do dokumentów programu Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Instrukcje: Dodawanie formantów XMLNodes do dokumentów programu Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)

### <a name="name-host-controls"></a>Nazwa kontrolki hosta
 Przeciągnięcie formantu hosta z **przybornika** do dokumentu, kontrolka ma automatycznie nadawaną nazwę z liczbą przyrostową na koniec za pomocą typu formantu. Na przykład zakładki są nazywane **bookmark1**, **bookmark2**i tak dalej. Jeśli używasz macierzystą funkcjonalność programu Word lub Excel, aby dodać kontrolkę, można mu nazwę w czasie jego tworzenia. Można również zmienić nazwę kontrolki, zmieniając wartość **nazwa** właściwość **właściwości** okna.

> [!NOTE]
>  Nie można użyć słowa zastrzeżone do nazwy hosta formantów. Na przykład jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli do arkusza i Zmień nazwę na **systemu**, wystąpi błąd podczas tworzenia projektu.

### <a name="delete-host-controls"></a>Usuń kontrolki hosta
 W projektach na poziomie dokumentu, można usunąć kontrolki hosta w czasie projektowania, zaznaczenie kontrolki w arkuszu programu Excel lub dokumentu programu Word, a następnie naciskając klawisz **Usuń** klucza. Jednakże, należy użyć **Definiowanie nazwy** okno dialogowe w programie Excel, aby usunąć <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki.

 Jeśli dodasz kontrolki hosta do dokumentu w czasie projektowania, nie należy usuwać je programowo w czasie wykonywania ponieważ następnym razem użytkownik próbuje użyć kontrolki w kodzie, zgłaszany jest wyjątek. `Delete` Metoda kontrolki hosta powoduje usunięcie tylko formanty hosta, które są dodawane do dokumentu w czasie wykonywania. Jeśli wywołasz `Delete` metody kontrolki hosta, który został utworzony w czasie projektowania, zgłaszany jest wyjątek.

 Na przykład <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> tylko pomyślnie usuwa <xref:Microsoft.Office.Tools.Excel.NamedRange> jeśli programowo została dodana do arkusza, który jest znany jako dynamicznie Tworzenie formantów hosta. Formanty hosta dynamicznie utworzoną może zostać także usunięty przez przekazanie nazwy kontrolki do `Remove` metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> lub <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Jeśli użytkownicy końcowi usunęli kontrolki hosta z dokumentu w czasie wykonywania, rozwiązanie może zakończyć się niepowodzeniem w nieoczekiwany sposób. Funkcje ochrony dokumentu w programach Word i Excel można użyć do ochrony kontrolki hosta przed usunięciem. Aby uzyskać więcej informacji, zobacz [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

> [!NOTE]
>  Nie usuwaj programowo kontrole podczas `Shutdown` programu obsługi zdarzeń w dokumencie lub arkuszu. Elementy interfejsu użytkownika nie są już dostępne podczas `Shutdown` wystąpi zdarzenie. Jeśli chcesz usunąć kontrolki przed zamknięciem aplikacji, Dodaj kod do innego programu obsługi zdarzeń takich jak `BeforeClose` lub `BeforeSave`.

### <a name="program-against-host-control-events"></a>Program w odniesieniu do zdarzeń kontrolki hosta
 Jednym ze sposobów, że formanty hosta rozszerzyć obiektów pakietu Office jest dodanie zdarzenia. Na przykład <xref:Microsoft.Office.Interop.Excel.Range> obiektu w programie Excel i <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu w programie Word braku zdarzenia, ale [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozszerza te obiekty, dodając programowalny zdarzenia. Masz dostęp i kod dla tych zdarzeń, taki sam sposób dostępu zdarzeń formantów na formularzach Windows Forms: za pomocą listy rozwijanej zdarzeń w języku Visual Basic i na stronie właściwości zdarzenia w języku C#. Aby uzyskać więcej informacji, zobacz [instruktażu: Program w odniesieniu do zdarzeń kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

> [!NOTE]
>  Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel, aby **false**. Ustawienie tej właściwości na **false** zapobiega podnoszenie żadnych wydarzeń, takich jak zdarzenia kontrolki hosta programu Excel.

## <a name="see-also"></a>Zobacz także
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
