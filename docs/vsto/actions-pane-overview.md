---
title: Omówienie okienka Akcje
description: Dowiedz się, jak okienko akcji jest dostosowywalnym okienkiem zadań Akcje dokumentu dołączonym do określonego Microsoft Office programu Word lub skoroszytu programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 61e7ab9f00db6036d3bc8e41b9a2f19cf51f5511
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828153"
---
# <a name="actions-pane-overview"></a>Omówienie okienka Akcje
  Okienko akcji to dostosowywalne okienko zadań Akcje dokumentu dołączone do określonego Microsoft Office programu Word lub Microsoft Office programu Excel.  Okienko akcji jest hostowane wewnątrz okienka zadań pakietu Office wraz z innymi wbudowanymi okienkami  zadań, takimi jak okienko zadań Źródło **XML** w programie Excel lub okienko zadań Style i formatowanie w programie Word. Aby zaprojektować interfejs użytkownika okienka akcji, możesz użyć Windows Forms lub kontrolek WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Okienko akcji można tworzyć tylko w dostosowywaniu na poziomie dokumentu dla programu Word lub Excel. Nie można utworzyć okienka akcji w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Funkcje dostępne według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Okienko akcji różni się od niestandardowych okienek zadań. Niestandardowe okienka zadań są skojarzone z aplikacją, a nie określonym dokumentem. W niektórych aplikacjach można tworzyć niestandardowe okienka zadań w dodatekach Microsoft Office narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

## <a name="display-the-actions-pane"></a>Wyświetlanie okienka akcji
 Okienko akcji jest reprezentowane przez <xref:Microsoft.Office.Tools.ActionsPane> klasę . Podczas tworzenia projektu na poziomie dokumentu wystąpienie tej klasy jest dostępne dla kodu przy użyciu pola klasy (dla programu Excel) lub (dla programu `ActionsPane` `ThisWorkbook` `ThisDocument` Word) w projekcie. Aby wyświetlić okienko akcji, Windows Forms kontrolkę do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości `ActionsPane` pola. Poniższy przykład kodu dodaje kontrolkę o nazwie `actions` do okienka akcji.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

 Okienko akcji staje się widoczne w czasie działania natychmiast po jawnie dodaniu do niego kontrolki. Po wyświetlaniu okienka akcji można dynamicznie dodawać lub usuwać kontrolki w odpowiedzi na akcje użytkownika. Zazwyczaj dodaje się kod w celu wyświetlenia okienka akcji w programie obsługi zdarzeń lub w taki sposób, aby okienko akcji było widoczne, gdy użytkownik po raz pierwszy `Startup` `ThisDocument` otworzy `ThisWorkbook` dokument. Jednak okienko akcji może być wyświetlane tylko w odpowiedzi na akcję użytkownika w dokumencie. Możesz na przykład dodać kod do zdarzenia `Click` kontrolki w dokumencie.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Dodawanie wielu kontrolek do okienka akcji
 Po dodaniu wielu kontrolek do okienka akcji należy zgrupować kontrolki w kontrolce użytkownika, a następnie dodać kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości . Ten proces obejmuje następujące kroki:

1. Utwórz interfejs użytkownika okienka akcji, dodając element Kontrolka okienka akcji **lub** **Kontrolka** użytkownika do projektu. Oba te elementy zawierają niestandardową Windows Forms <xref:System.Windows.Forms.UserControl> klasy. Elementy **Kontrolka okienka akcje** i **Kontrolka** użytkownika są równoważne. Jedyną różnicą jest ich nazwa.

2. Dodaj Windows Forms do <xref:System.Windows.Forms.UserControl> kontrolki przy użyciu projektanta lub przez napisanie kodu.

   > [!NOTE]
   > Kontrolki WPF można również dodać do okienka akcji, dodając do okienka <xref:System.Windows.Controls.UserControl> Windows Forms <xref:System.Windows.Forms.UserControl> . Aby uzyskać więcej informacji, zobacz [Używanie kontrolek WPF w rozwiązaniach pakietu Office.](../vsto/using-wpf-controls-in-office-solutions.md)

3. Dodaj wystąpienie niestandardowej kontrolki użytkownika do kontrolek, które znajdują się w polu klasy (dla programu Excel) lub `ActionsPane` `ThisWorkbook` `ThisDocument` (dla programu Word) w projekcie.

   Przykłady, które pokazują ten proces bardziej szczegółowo, można znaleźć w temacie How [to: Add an actions pane to Word documents or Excel workbooks](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)(Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel).

## <a name="hide-the-actions-pane"></a>Ukrywanie okienka akcji
 Mimo że klasa ma metodę i właściwość, nie można usunąć okienka akcji z interfejsu użytkownika przy użyciu żadnych <xref:Microsoft.Office.Tools.ActionsPane> <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> składowych <xref:Microsoft.Office.Tools.ActionsPane> samej klasy. Wywołanie metody lub ustawienie dla właściwości wartości false powoduje ukrycie tylko kontrolek w okienku akcji. Okienko zadań nie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> jest ukrywane. 

 Aby ukryć okienko zadań w rozwiązaniu, masz kilka opcji:

- W przypadku programu Word ustaw właściwość obiektu reprezentującego okienko zadań <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> Akcje dokumentu na wartość <xref:Microsoft.Office.Interop.Word.TaskPane> **false**. Poniższy przykład kodu jest przeznaczony do uruchamiania z `ThisDocument` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet34":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet34":::

- W przypadku programu Excel <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> ustaw właściwość obiektu na wartość <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> **false**. Poniższy przykład kodu jest przeznaczony do uruchamiania z `ThisWorkbook` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet11":::

- W przypadku programu Word lub Excel można też ustawić właściwość paska poleceń reprezentującą okienko <xref:Microsoft.Office.Core.CommandBar.Visible%2A> zadań na wartość **false**. Poniższy przykład kodu jest przeznaczony do uruchamiania z klasy `ThisDocument` lub `ThisWorkbook` w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet9":::

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Wyczyść okienko akcji po otwarciu dokumentu
 Gdy użytkownik zapisuje dokument, gdy okienko akcji jest widoczne, okienko akcji jest widoczne za każdym razem, gdy dokument jest otwierany, bez względu na to, czy okienko akcji zawiera jakiekolwiek kontrolki. Jeśli chcesz kontrolować, kiedy zostanie wyświetlony, wywołaj metodę pola w programie obsługi zdarzeń lub , aby upewnić się, że okienko akcji nie jest widoczne po <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> `ActionsPane` `Startup` `ThisDocument` `ThisWorkbook` otwarciu dokumentu.

### <a name="determine-when-the-actions-pane-is-closed"></a>Określanie, kiedy okienko akcji jest zamknięte
 Po zamknięciu okienka akcji nie jest wywoływane żadne zdarzenie. Mimo że klasa ma zdarzenie, to zdarzenie nie jest wywoływane, gdy użytkownik <xref:Microsoft.Office.Tools.ActionsPane> <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> końcowy zamknie okienko akcji. Zamiast tego to zdarzenie jest wywoływane, gdy kontrolki w okienku akcji są ukryte przez wywołanie metody lub ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> właściwości na wartość <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> **false**.

 Gdy użytkownik zamknie okienko akcji, może wyświetlić je ponownie, wykonując jedną z poniższych procedur w interfejsie użytkownika aplikacji.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Aby wyświetlić okienko akcji przy użyciu interfejsu użytkownika programu Word lub Excel

1. Na wstążce kliknij **kartę** Widok.

2. W grupie **Pokaż/Ukryj** kliknij przycisk przełączania **Akcje** dokumentu.

## <a name="program-actions-pane-events"></a>Zdarzenia okienka Akcje programu
 Do okienka akcji można dodać wiele kontrolek użytkownika, a następnie napisać kod reagujący na zdarzenia w dokumencie, wyświetlając i ukrywając kontrolki użytkownika. W przypadku mapowania elementów schematu XML do dokumentu niektóre kontrolki użytkownika można wyświetlić w okienku akcji zawsze, gdy punkt wstawiania znajduje się wewnątrz jednego z elementów XML. Aby uzyskać więcej informacji, zobacz How [to: Map schemas to Word documents inside Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) (Jak mapować schematy na arkusze w dokumentach programu Word) i How [to: Map schemas to worksheets inside Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Można również napisać kod, aby reagować na zdarzenia dowolnego obiektu, w tym zdarzenia kontrolek hosta, aplikacji lub dokumentów. Aby uzyskać więcej informacji, [zobacz Walkthrough: Program against events of a NamedRange control (Przewodnik: programowanie względem zdarzeń kontrolki NamedRange).](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Wiązanie danych z kontrolkami w okienku akcji
 Kontrolki w okienku akcji mają takie same możliwości powiązania danych jak kontrolki na Windows Forms. Kontrolki można powiązać ze źródłami danych, takimi jak zestawy danych, typowane zestawy danych i kod XML. Aby uzyskać więcej informacji, zobacz [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Kontrolki w okienku akcji i kontrolki w dokumencie można powiązać z tym samym zestawem danych. Na przykład można utworzyć relację wzorzec/szczegół między kontrolkami w okienku akcji i kontrolkami w arkuszu. Aby uzyskać więcej informacji, zobacz [Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Excel.](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)

## <a name="validate-data-in-actions-pane-controls"></a>Weryfikowanie danych w kontrolkach okienka akcji
 Jeśli w programie obsługi zdarzeń kontrolki w okienku akcji zostanie wyświetlane okno komunikatu, zdarzenie może zostać podniesione po raz drugi, gdy fokus zostanie przeniesiony z kontrolki do <xref:System.Windows.Forms.Control.Validating> okna komunikatu. Aby uniknąć tego problemu, użyj <xref:System.Windows.Forms.ErrorProvider> kontrolki, aby wyświetlić wszystkie komunikaty o błędach weryfikacji.

## <a name="user-control-stacking-order"></a>Kolejność stosu kontrolek użytkownika
 Jeśli używasz wielu kontrolek użytkownika, możesz napisać kod, aby poprawnie ustawić stos kontrolek użytkownika w okienku akcji, niezależnie od tego, czy jest on zadokowany w pionie, czy w poziomie. Możesz ustawić kolejność stosu kontrolek użytkownika w okienku akcji przy użyciu <xref:Microsoft.Office.Tools.StackStyle> wyliczenia <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> właściwości . Aby uzyskać więcej informacji, [zobacz Temat Jak zarządzać układem kontrolek w okienkach akcji.](../vsto/how-to-manage-control-layout-on-actions-panes.md)

 Właściwość <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> może przyjmować następujące wartości <xref:Microsoft.Office.Tools.StackStyle> wyliczenia.

|Styl stosu|Definicja|
|--------------------|----------------|
|FromBottom|Stosuj stos w dolnej części okienka akcji.|
|FromLeft|Stosuj stos z lewej strony okienka akcji.|
|FromRight|Stosuj stos z prawej strony okienka akcji.|
|FromTop|Stosuj stos w górnej części okienka akcji.|
|Brak|Nie zdefiniowano kolejności stosu; zamówienie jest kontrolowane przez dewelopera.|

 Poniższy kod ustawia właściwość <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> tak, aby stosować kontrolki użytkownika w górnej części okienka akcji.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet10":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet10":::

## <a name="anchor-controls"></a>Kontrolki zakotwiczenia
 Jeśli użytkownik zmienia rozmiar okienka akcji w czasie uruchamiania, kontrolki mogą zmieniać rozmiar za pomocą okienka akcji. Możesz użyć właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki Windows Forms, aby zakotwiczyć kontrolki w okienku akcji. Możesz również zakotwiczyć kontrolki Windows Forms w kontrolce użytkownika w ten sam sposób. Aby uzyskać więcej informacji, zobacz How to: Anchor controls on Windows Forms ( Jak [zakotwiczyć kontrolki na Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)).

## <a name="resize-the-actions-pane"></a>Zmienianie rozmiaru okienka akcji
 Nie można bezpośrednio zmienić rozmiaru obiektu <xref:Microsoft.Office.Tools.ActionsPane> , ponieważ element jest osadzony w <xref:Microsoft.Office.Tools.ActionsPane> okienku zadań. Można jednak programowo zmienić szerokość okienka zadań, ustawiając właściwość obiektu <xref:Microsoft.Office.Core.CommandBar.Width%2A> <xref:Microsoft.Office.Core.CommandBar> reprezentującą okienko zadań. Wysokość okienka zadań można zmienić, jeśli jest ono zadokowane w poziomie lub jest przestawne.

 Programowe zmienianie rozmiaru okienka zadań nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wybrania rozmiaru okienka zadań, który najlepiej odpowiada jego potrzebom. Jeśli jednak musisz zmienić szerokość okienka zadań, możesz użyć następującego kodu, aby wykonać to zadanie.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet102":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet102":::

## <a name="reposition-the-actions-pane"></a>Zmiana położenia okienka akcji
 Nie można bezpośrednio zmienić położenia obiektu <xref:Microsoft.Office.Tools.ActionsPane> , ponieważ jest on osadzony w okienku zadań. Można jednak programowo przenieść okienko zadań, ustawiając właściwość obiektu <xref:Microsoft.Office.Core.CommandBar.Position%2A> <xref:Microsoft.Office.Core.CommandBar> reprezentującą okienko zadań.

 Programowe zmiany położenia okienka zadań nie są zalecane, ponieważ użytkownik powinien mieć możliwość wybrania pozycji okienka zadań na ekranie, która najlepiej odpowiada jego potrzebom. Jeśli jednak musisz przenieść okienko zadań do określonej pozycji, możesz użyć następującego kodu, aby wykonać to zadanie.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet100":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet100":::

> [!NOTE]
> Użytkownicy końcowi mogą ręcznie zmienić położenie okienka zadań w dowolnym momencie. Nie ma możliwości zapewnienia, że okienko zadań pozostanie zadokowane w miejscu wskazywanym programowo. Można jednak sprawdzić zmiany orientacji i upewnić się, że kontrolki w okienku akcji są ułożone w prawidłowym kierunku. Aby uzyskać więcej informacji, [zobacz Temat Jak zarządzać układem kontrolek w okienkach akcji.](../vsto/how-to-manage-control-layout-on-actions-panes.md)

 Ustawienie właściwości i obiektu nie zmienia jego położenia, <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> ponieważ obiekt jest osadzony w <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> <xref:Microsoft.Office.Tools.ActionsPane> <xref:Microsoft.Office.Tools.ActionsPane> okienku zadań.

 Jeśli okienko zadań nie jest zadokowane, można ustawić właściwości i , które <xref:Microsoft.Office.Core.CommandBar.Top%2A> <xref:Microsoft.Office.Core.CommandBar.Left%2A> reprezentują okienko <xref:Microsoft.Office.Core.CommandBar> zadań. Poniższy kod przenosi oddokowane okienko zadań do lewego górnego rogu dokumentu.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet101":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet101":::

## <a name="see-also"></a>Zobacz też
- [Używanie kontrolek WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [How to: Add an actions pane to Word documents or Excel workbooks (Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel)](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Samodzielnie: zarządzanie układem kontrolek w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
