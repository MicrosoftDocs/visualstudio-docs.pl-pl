---
title: Przegląd okienka Akcje
description: Dowiedz się, jak okienko akcje to okienko zadań akcje dostosowywalne, które jest dołączone do określonego Microsoft Office dokumentu programu Word lub skoroszytu programu Excel.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d03ba8968b08fb07eb2cc9c17839af57cf06eca
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844832"
---
# <a name="actions-pane-overview"></a>Przegląd okienka Akcje
  Okienko akcji to dostosowywalne okienko zadań **Akcje dokumentu** , które jest dołączone do określonego Microsoft Office dokumentu programu Word Microsoft Office lub skoroszytu programu Excel. Okienko akcje jest hostowane wewnątrz okienka zadań pakietu Office wraz z innymi wbudowanymi okienkami zadań, takimi jak okienko zadań **Źródło XML** w programie Excel lub w okienku zadania **Style i formatowanie** w programie Word. Aby zaprojektować interfejs użytkownika okienka akcji, można użyć formantów Windows Forms lub formantów WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Okienko akcji można utworzyć tylko w przypadku dostosowania na poziomie dokumentu dla programu Word lub Excel. Nie można utworzyć okienka akcji w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Okienko akcje różni się od niestandardowych okienek zadań. Niestandardowe okienka zadań są skojarzone z aplikacją, a nie określonym dokumentem. W dodatkach narzędzi VSTO można tworzyć niestandardowe okienka zadań dla niektórych Microsoft Office aplikacji. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Wyświetlanie okienka Akcje
 Okienko akcje jest reprezentowane przez <xref:Microsoft.Office.Tools.ActionsPane> klasę. Podczas tworzenia projektu na poziomie dokumentu wystąpienie tej klasy jest dostępne dla kodu przy użyciu `ActionsPane` pola `ThisWorkbook` klasy (dla programu Excel) lub `ThisDocument` (dla programu Word) w projekcie. Aby wyświetlić okienko akcje, Dodaj kontrolkę Windows Forms do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości `ActionsPane` pola. Poniższy przykład kodu dodaje kontrolkę o nazwie `actions` do okienka Akcje.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Okienko akcje będzie widoczne w czasie wykonywania, gdy tylko jawnie dodasz do niego kontrolkę. Po wyświetleniu okienka Akcje można dynamicznie dodawać lub usuwać kontrolki w odpowiedzi na akcje użytkownika. Zazwyczaj należy dodać kod, aby wyświetlić okienko akcje w programie `Startup` obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` tak, aby okienko akcje było widoczne, gdy użytkownik po raz pierwszy otworzy dokument. Może jednak być konieczne wyświetlenie okienka Akcje tylko w odpowiedzi na akcję użytkownika w dokumencie. Na przykład, można dodać kod do `Click` zdarzenia kontrolki dokumentu.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Dodawanie wielu formantów do okienka Akcje
 Po dodaniu wielu formantów do okienka Akcje należy zgrupować kontrolki w kontrolce użytkownika, a następnie dodać kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości. Ten proces obejmuje następujące kroki:

1. Utwórz interfejs użytkownika w okienku Akcje, dodając **kontrolkę okienko akcji** lub element **kontrolki użytkownika** do projektu. Oba te elementy zawierają niestandardową <xref:System.Windows.Forms.UserControl> klasę Windows Forms. Elementy **kontrolne okienka Akcje** i **kontrolki użytkownika** są równoważne; Jedyną różnicą jest ich nazwa.

2. Dodaj kontrolki Windows Forms do programu przy <xref:System.Windows.Forms.UserControl> użyciu projektanta lub pisząc kod.

   > [!NOTE]
   > Możesz również dodać formanty WPF do okienka Akcje przez dodanie WPF <xref:System.Windows.Controls.UserControl> do Windows Forms <xref:System.Windows.Forms.UserControl> . Aby uzyskać więcej informacji, zobacz [Korzystanie z formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Dodaj wystąpienie niestandardowej kontrolki użytkownika do formantów, które są zawarte w `ActionsPane` polu `ThisWorkbook` klasy (dla programu Excel) lub `ThisDocument` (dla programu Word) w projekcie.

   Przykłady, które pokazują ten proces bardziej szczegółowo, można znaleźć w temacie [How to: Add a Actions to Document Words or skoroszyts Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Ukryj okienko akcje
 Chociaż <xref:Microsoft.Office.Tools.ActionsPane> Klasa ma <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metodę i <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> Właściwość, nie można usunąć okienka Akcje z interfejsu użytkownika przy użyciu żadnych elementów członkowskich <xref:Microsoft.Office.Tools.ActionsPane> samej klasy. Wywołanie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> **wartości false** powoduje ukrycie tylko kontrolek w okienku Akcje; nie powoduje ukrycia okienka zadań.

 Aby ukryć okienko zadań w rozwiązaniu, masz kilka opcji:

- Dla programu Word Ustaw <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> Właściwość <xref:Microsoft.Office.Interop.Word.TaskPane> obiektu, który reprezentuje okienko zadań akcje dokumentu na **wartość FAŁSZ**. Poniższy przykład kodu jest przeznaczony do uruchomienia z `ThisDocument` klasy w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Dla programu Excel Ustaw <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> Właściwość <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> obiektu na **false**. Poniższy przykład kodu jest przeznaczony do uruchomienia z `ThisWorkbook` klasy w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Dla programu Word lub Excel można alternatywnie ustawić <xref:Microsoft.Office.Core.CommandBar.Visible%2A> Właściwość paska poleceń, który reprezentuje okienko zadania, na **wartość FAŁSZ**. Poniższy przykład kodu jest przeznaczony do uruchamiania z `ThisDocument` lub `ThisWorkbook` klasy w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Wyczyść okienko akcje, gdy dokument zostanie otwarty
 Gdy użytkownik zapisuje dokument, gdy okienko akcje jest widoczne, okienko akcje jest widoczne za każdym razem, gdy dokument zostanie otwarty, niezależnie od tego, czy okienko akcje zawiera formanty. Jeśli chcesz kontrolować gdy pojawia się, wywołaj <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> metodę `ActionsPane` pola w programie `Startup` obsługi zdarzeń `ThisDocument` lub, `ThisWorkbook` Aby upewnić się, że okienko akcje nie jest widoczne po otwarciu dokumentu.

### <a name="determine-when-the-actions-pane-is-closed"></a>Ustalanie, kiedy okienko akcji jest zamknięte
 W przypadku zamknięcia okienka Akcje nie ma zdarzenia, które jest zgłaszane. Chociaż <xref:Microsoft.Office.Tools.ActionsPane> Klasa ma <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> zdarzenie, to zdarzenie nie jest wywoływane, gdy użytkownik końcowy zamknie okienko akcje. Zamiast tego to zdarzenie jest zgłaszane, gdy kontrolki okienka Akcje są ukrywane przez wywołanie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub przez ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości na **false**.

 Gdy użytkownik zamknie okienko akcje, użytkownik może go wyświetlić ponownie, wykonując jedną z następujących procedur w interfejsie użytkownika aplikacji.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Aby wyświetlić okienko akcje przy użyciu interfejsu użytkownika programu Word lub Excel

1. Na wstążce kliknij kartę **Widok** .

2. W grupie **Pokaż/Ukryj** kliknij przycisk Przełącz **Akcje dokumentu** .

## <a name="program-actions-pane-events"></a>Zdarzenia okienka Akcje programu
 Do okienka Akcje można dodać wiele kontrolek użytkownika, a następnie napisać kod w celu reagowania na zdarzenia w dokumencie, pokazując i ukrywając kontrolki użytkownika. Jeśli mapujesz elementy schematu XML do dokumentu, możesz pokazać niektóre kontrolki użytkownika w okienku Akcje, gdy punkt wstawiania znajduje się w jednym z elementów XML. Aby uzyskać więcej informacji, zobacz [How to: map schematów do dokumentów programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) i [instrukcje: mapowanie schematów do arkuszy w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Możesz również napisać kod, aby odpowiedzieć na zdarzenia dowolnego obiektu, w tym zdarzenia kontroli hosta, aplikacji lub dokumentu. Aby uzyskać więcej informacji, zobacz [Przewodnik: program dla zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Powiązywanie danych z kontrolkami w okienku Akcje
 Kontrolki w okienku Akcje mają takie same możliwości powiązania danych jak kontrolki na Windows Forms. Można powiązać kontrolki ze źródłami danych, takimi jak zestawy danych, zestawy danych w określonym formacie i XML. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Można powiązać kontrolki w okienku Akcje i kontrolki na dokumencie z tym samym zestawem danych. Na przykład można utworzyć relację wzorzec/szczegóły między kontrolkami w okienku Akcje i kontrolkami w arkuszu. Aby uzyskać więcej informacji, zobacz [Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Sprawdzanie poprawności danych w kontrolkach okienka akcji
 Jeśli zostanie wyświetlone okno komunikatu w <xref:System.Windows.Forms.Control.Validating> procedurze obsługi zdarzeń kontrolki w okienku Akcje, zdarzenie może zostać wywołane po przeniesieniu fokusu z formantu do okna komunikatu. Aby uniknąć tego problemu, użyj <xref:System.Windows.Forms.ErrorProvider> kontrolki, aby wyświetlić wszystkie komunikaty o błędach walidacji.

## <a name="user-control-stacking-order"></a>Kolejność układania formantów użytkownika
 Jeśli używasz wielu kontrolek użytkownika, możesz napisać kod w celu prawidłowego stosu kontrolek użytkownika w okienku Akcje, niezależnie od tego, czy jest zadokowany pionowo czy poziomo. Kolejność układania formantów użytkownika w okienku Akcje można ustawić przy użyciu <xref:Microsoft.Office.Tools.StackStyle> wyliczenia <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> właściwości. Aby uzyskać więcej informacji, zobacz [jak: zarządzanie układem kontroli w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>Właściwość może przyjmować następujące <xref:Microsoft.Office.Tools.StackStyle> wartości wyliczania.

|Styl stosu|Definicja|
|--------------------|----------------|
|FromBottom|Stos u dołu okienka Akcje.|
|FromLeft|Stos z lewej strony okienka Akcje.|
|FromRight|Stos z prawej strony okienka Akcje.|
|FromTop|Stos w górnej części okienka Akcje.|
|Brak|Nie zdefiniowano kolejności układania; zamówienie jest kontrolowane przez dewelopera.|

 Poniższy kod ustawia <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Właściwość w celu stosu kontrolek użytkownika w górnej części okienka Akcje.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Kontrolki kotwic
 Jeśli użytkownik zmieni rozmiar okienka Akcje w czasie wykonywania, kontrolki mogą zmieniać rozmiar w okienku Akcje. Za pomocą <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki Windows Forms można zakotwiczyć kontrolki w okienku Akcje. Możesz również zakotwiczyć kontrolki Windows Forms w kontrolce użytkownika w taki sam sposób. Aby uzyskać więcej informacji, zobacz [jak: kontrolki kotwicowe na Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Zmień rozmiar okienka Akcje
 Nie można bezpośrednio zmienić rozmiaru, <xref:Microsoft.Office.Tools.ActionsPane> ponieważ <xref:Microsoft.Office.Tools.ActionsPane> jest osadzony w okienku zadań. Można jednak programowo zmienić szerokość okienka zadań, ustawiając <xref:Microsoft.Office.Core.CommandBar.Width%2A> Właściwość <xref:Microsoft.Office.Core.CommandBar> , która reprezentuje okienko zadań. Możesz zmienić wysokość okienka zadań, jeśli jest zadokowana w poziomie lub w pionie.

 Programowe zmienianie rozmiaru okienka zadań nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wybrania rozmiaru okienka zadań, który najlepiej odpowiada potrzebom. Jednak w przypadku konieczności zmiany szerokości okienka zadań można użyć poniższego kodu do osiągnięcia tego zadania.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Zmień położenie okienka Akcje
 Nie można bezpośrednio zmienić położenia, <xref:Microsoft.Office.Tools.ActionsPane> ponieważ jest on osadzony w okienku zadań. Można jednak programowo przenieść okienko zadań przez ustawienie <xref:Microsoft.Office.Core.CommandBar.Position%2A> właściwości <xref:Microsoft.Office.Core.CommandBar> , która reprezentuje okienko zadań.

 Programowo zmiana położenia okienka zadań nie jest zalecana, ponieważ użytkownik powinien mieć możliwość wybrania pozycji okienka zadań na ekranie, który najlepiej odpowiada jego potrzebom. Jeśli jednak musisz przenieść okienko zadań do określonego położenia, możesz użyć poniższego kodu, aby wykonać to zadanie.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Użytkownicy końcowi mogą ręcznie zmieniać położenie okienka zadań w dowolnym momencie. Nie ma żadnego sposobu, aby upewnić się, że okienko zadań pozostanie zadokowane w miejscu, które będzie używane programowo. Można jednak sprawdzić zmiany orientacji i upewnić się, że kontrolki w okienku Akcje są ułożone w odpowiednim kierunku. Aby uzyskać więcej informacji, zobacz [jak: zarządzanie układem kontroli w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> właściwości i <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> <xref:Microsoft.Office.Tools.ActionsPane> nie powoduje zmiany położenia, ponieważ <xref:Microsoft.Office.Tools.ActionsPane> obiekt jest osadzony w okienku zadań.

 Jeśli okienko zadań nie jest zadokowane, można ustawić <xref:Microsoft.Office.Core.CommandBar.Top%2A> właściwości i, <xref:Microsoft.Office.Core.CommandBar.Left%2A> <xref:Microsoft.Office.Core.CommandBar> które reprezentują okienko zadań. Poniższy kod przenosi niezadokowane okienko zadań do lewego górnego rogu dokumentu.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Zobacz także
- [Korzystanie z formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Przewodnik: powiązywanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Instrukcje: zarządzanie układem sterowania w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
