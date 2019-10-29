---
title: Przegląd okienka Akcje
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
ms.openlocfilehash: 82bf3ac9515effaa1053a011085849f0afea67f5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986310"
---
# <a name="actions-pane-overview"></a>Przegląd okienka Akcje
  Okienko akcji to dostosowywalne okienko zadań **Akcje dokumentu** , które jest dołączone do określonego Microsoft Office dokumentu programu Word Microsoft Office lub skoroszytu programu Excel. Okienko akcje jest hostowane wewnątrz okienka zadań pakietu Office wraz z innymi wbudowanymi okienkami zadań, takimi jak okienko zadań **Źródło XML** w programie Excel lub w okienku zadania **Style i formatowanie** w programie Word. Aby zaprojektować interfejs użytkownika okienka akcji, można użyć formantów Windows Forms lub formantów WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Okienko akcji można utworzyć tylko w przypadku dostosowania na poziomie dokumentu dla programu Word lub Excel. Nie można utworzyć okienka akcji w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dostępność funkcji według aplikacji pakietu Office i typów projektów](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Okienko akcje różni się od niestandardowych okienek zadań. Niestandardowe okienka zadań są skojarzone z aplikacją, a nie określonym dokumentem. W dodatkach narzędzi VSTO można tworzyć niestandardowe okienka zadań dla niektórych Microsoft Office aplikacji. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Wyświetlanie okienka Akcje
 Okienko akcje jest reprezentowane przez klasę <xref:Microsoft.Office.Tools.ActionsPane>. Podczas tworzenia projektu na poziomie dokumentu wystąpienie tej klasy jest dostępne dla kodu przy użyciu pola `ActionsPane` w `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) w projekcie. Aby wyświetlić okienko akcje, Dodaj kontrolkę Windows Forms do właściwości <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> pola `ActionsPane`. Poniższy przykład kodu dodaje kontrolkę o nazwie `actions` do okienka Akcje.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Okienko akcje będzie widoczne w czasie wykonywania, gdy tylko jawnie dodasz do niego kontrolkę. Po wyświetleniu okienka Akcje można dynamicznie dodawać lub usuwać kontrolki w odpowiedzi na akcje użytkownika. Zazwyczaj należy dodać kod, aby wyświetlić okienko akcje w `Startup` procedury obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` tak, aby okienko akcje było widoczne, gdy użytkownik otwiera dokument po raz pierwszy. Może jednak być konieczne wyświetlenie okienka Akcje tylko w odpowiedzi na akcję użytkownika w dokumencie. Można na przykład dodać kod do zdarzenia `Click` formantu w dokumencie.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Dodawanie wielu formantów do okienka Akcje
 Po dodaniu wielu formantów do okienka Akcje należy zgrupować kontrolki w kontrolce użytkownika, a następnie dodać kontrolkę użytkownika do właściwości <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>. Ten proces obejmuje następujące kroki:

1. Utwórz interfejs użytkownika w okienku Akcje, dodając **kontrolkę okienko akcji** lub element **kontrolki użytkownika** do projektu. Oba te elementy zawierają niestandardową klasę <xref:System.Windows.Forms.UserControl> Windows Forms. Elementy **kontrolne okienka Akcje** i **kontrolki użytkownika** są równoważne; Jedyną różnicą jest ich nazwa.

2. Dodaj Windows Forms kontrolki do <xref:System.Windows.Forms.UserControl> za pomocą projektanta lub pisząc kod.

   > [!NOTE]
   > Możesz również dodać formanty WPF do okienka Akcje, dodając <xref:System.Windows.Controls.UserControl> WPF do Windows Forms <xref:System.Windows.Forms.UserControl>. Aby uzyskać więcej informacji, zobacz [Korzystanie z formantów WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Dodaj wystąpienie niestandardowej kontrolki użytkownika do formantów, które są zawarte w `ActionsPane` polu klasy `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) w projekcie.

   Przykłady, które pokazują ten proces bardziej szczegółowo, można znaleźć w temacie [How to: Add a Actions to Document Words or skoroszyts Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Ukryj okienko akcje
 Chociaż Klasa <xref:Microsoft.Office.Tools.ActionsPane> ma metodę <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> i Właściwość <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, nie można usunąć okienka Akcje z interfejsu użytkownika przy użyciu żadnych elementów członkowskich samej klasy <xref:Microsoft.Office.Tools.ActionsPane>. Wywołanie metody <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> lub ustawienie dla właściwości <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> **wartości false** powoduje ukrycie tylko kontrolek w okienku Akcje. nie powoduje ukrycia okienka zadań.

 Aby ukryć okienko zadań w rozwiązaniu, masz kilka opcji:

- Dla programu Word ustaw właściwość <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> obiektu <xref:Microsoft.Office.Interop.Word.TaskPane>, który reprezentuje okienko zadań akcje dokumentu na **wartość FAŁSZ**. Poniższy przykład kodu jest przeznaczony do uruchomienia z klasy `ThisDocument` w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Dla programu Excel ustaw właściwość <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> obiektu <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> na **wartość false**. Poniższy przykład kodu jest przeznaczony do uruchomienia z klasy `ThisWorkbook` w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Dla programu Word lub Excel można alternatywnie ustawić właściwość <xref:Microsoft.Office.Core.CommandBar.Visible%2A> paska poleceń, który reprezentuje okienko zadań, na **wartość FAŁSZ**. Poniższy przykład kodu jest przeznaczony do uruchomienia z klasy `ThisDocument` lub `ThisWorkbook` w projekcie.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Wyczyść okienko akcje, gdy dokument zostanie otwarty
 Gdy użytkownik zapisuje dokument, gdy okienko akcje jest widoczne, okienko akcje jest widoczne za każdym razem, gdy dokument zostanie otwarty, niezależnie od tego, czy okienko akcje zawiera formanty. Jeśli chcesz kontrolować gdy pojawia się, wywołaj metodę <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> pola `ActionsPane` w procedurze obsługi zdarzeń `Startup` `ThisDocument` lub `ThisWorkbook`, aby upewnić się, że okienko akcje nie jest widoczne po otwarciu dokumentu.

### <a name="determine-when-the-actions-pane-is-closed"></a>Ustalanie, kiedy okienko akcji jest zamknięte
 W przypadku zamknięcia okienka Akcje nie ma zdarzenia, które jest zgłaszane. Chociaż Klasa <xref:Microsoft.Office.Tools.ActionsPane> ma zdarzenie <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, to zdarzenie nie jest wywoływane, gdy użytkownik końcowy zamknie okienko akcje. Zamiast tego to zdarzenie jest zgłaszane, gdy kontrolki okienka Akcje są ukrywane przez wywołanie metody <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> lub przez ustawienie właściwości <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> na **false**.

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
 Jeśli zostanie wyświetlone okno komunikatu w obsłudze zdarzeń <xref:System.Windows.Forms.Control.Validating> formantu w okienku Akcje, zdarzenie może zostać wywołane po drugim przeniesieniu fokusu z kontrolki do okna komunikatu. Aby zapobiec temu problemowi, użyj kontrolki <xref:System.Windows.Forms.ErrorProvider>, aby wyświetlić wszystkie komunikaty o błędach walidacji.

## <a name="user-control-stacking-order"></a>Kolejność układania formantów użytkownika
 Jeśli używasz wielu kontrolek użytkownika, możesz napisać kod w celu prawidłowego stosu kontrolek użytkownika w okienku Akcje, niezależnie od tego, czy jest zadokowany pionowo czy poziomo. Kolejność układania formantów użytkownika w okienku Akcje można ustawić przy użyciu <xref:Microsoft.Office.Tools.StackStyle> Wyliczenie właściwości <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Aby uzyskać więcej informacji, zobacz [jak: zarządzanie układem kontroli w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Właściwość <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> może przyjmować następujące <xref:Microsoft.Office.Tools.StackStyle> wartości wyliczenia.

|Styl stosu|Definicja|
|--------------------|----------------|
|FromBottom|Stos u dołu okienka Akcje.|
|FromLeft|Stos z lewej strony okienka Akcje.|
|FromRight|Stos z prawej strony okienka Akcje.|
|FromTop|Stos w górnej części okienka Akcje.|
|Brak|Nie zdefiniowano kolejności układania; zamówienie jest kontrolowane przez dewelopera.|

 Poniższy kod ustawia właściwość <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> na stos formantów użytkownika w górnej części okienka Akcje.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Kontrolki kotwic
 Jeśli użytkownik zmieni rozmiar okienka Akcje w czasie wykonywania, kontrolki mogą zmieniać rozmiar w okienku Akcje. Właściwości <xref:System.Windows.Forms.Control.Anchor%2A> kontrolki Windows Forms można użyć do zakotwiczenia kontrolek w okienku Akcje. Możesz również zakotwiczyć kontrolki Windows Forms w kontrolce użytkownika w taki sam sposób. Aby uzyskać więcej informacji, zobacz [jak: kontrolki kotwicowe na Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Zmień rozmiar okienka Akcje
 Nie można bezpośrednio zmienić rozmiaru <xref:Microsoft.Office.Tools.ActionsPane>, ponieważ <xref:Microsoft.Office.Tools.ActionsPane> jest osadzony w okienku zadań. Można jednak programowo zmienić szerokość okienka zadań, ustawiając właściwość <xref:Microsoft.Office.Core.CommandBar.Width%2A> <xref:Microsoft.Office.Core.CommandBar>, która reprezentuje okienko zadań. Możesz zmienić wysokość okienka zadań, jeśli jest zadokowana w poziomie lub w pionie.

 Programowe zmienianie rozmiaru okienka zadań nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wybrania rozmiaru okienka zadań, który najlepiej odpowiada potrzebom. Jednak w przypadku konieczności zmiany szerokości okienka zadań można użyć poniższego kodu do osiągnięcia tego zadania.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Zmień położenie okienka Akcje
 Nie można bezpośrednio zmienić położenia <xref:Microsoft.Office.Tools.ActionsPane>, ponieważ jest on osadzony w okienku zadań. Można jednak programowo przenieść okienko zadań przez ustawienie właściwości <xref:Microsoft.Office.Core.CommandBar.Position%2A> <xref:Microsoft.Office.Core.CommandBar>, która reprezentuje okienko zadań.

 Programowo zmiana położenia okienka zadań nie jest zalecana, ponieważ użytkownik powinien mieć możliwość wybrania pozycji okienka zadań na ekranie, który najlepiej odpowiada jego potrzebom. Jeśli jednak musisz przenieść okienko zadań do określonego położenia, możesz użyć poniższego kodu, aby wykonać to zadanie.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Użytkownicy końcowi mogą ręcznie zmieniać położenie okienka zadań w dowolnym momencie. Nie ma żadnego sposobu, aby upewnić się, że okienko zadań pozostanie zadokowane w miejscu, które będzie używane programowo. Można jednak sprawdzić zmiany orientacji i upewnić się, że kontrolki w okienku Akcje są ułożone w odpowiednim kierunku. Aby uzyskać więcej informacji, zobacz [jak: zarządzanie układem kontroli w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Ustawienie właściwości <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> i <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> <xref:Microsoft.Office.Tools.ActionsPane> nie zmienia jej położenia, ponieważ obiekt <xref:Microsoft.Office.Tools.ActionsPane> jest osadzony w okienku zadań.

 Jeśli okienko zadań nie jest zadokowane, można ustawić właściwości <xref:Microsoft.Office.Core.CommandBar.Top%2A> i <xref:Microsoft.Office.Core.CommandBar.Left%2A> <xref:Microsoft.Office.Core.CommandBar>, które reprezentują okienko zadań. Poniższy kod przenosi niezadokowane okienko zadań do lewego górnego rogu dokumentu.

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
