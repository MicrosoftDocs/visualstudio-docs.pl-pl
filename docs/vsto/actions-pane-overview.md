---
title: Okienko akcji ― omówienie
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: de9e6a7f148612716cee55b5a21a26f1bcf04d9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821130"
---
# <a name="actions-pane-overview"></a>Okienko akcji ― omówienie
  Okienka akcji jest dostosowywany **akcji dla dokumentów** okienka zadań, który jest dołączony do określonego dokumentu Microsoft Office Word lub skoroszytu programu Microsoft Office Excel. W okienku Akcje znajduje się wewnątrz okienka zadań pakietu Office oraz inne okienka wbudowanego zadania, takie jak **źródła XML** okienka zadań w programie Excel lub **style i formatowanie** okienka zadań w programie Word. Formanty Windows Forms lub kontrolek WPF umożliwia projektowanie interfejsu użytkownika w okienku Akcje.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Okienka akcji można utworzyć tylko w przypadku dostosowywania poziomie dokumentu dla programu Word lub Excel. Nie można utworzyć okienka akcji w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  W okienku Akcje różni się od niestandardowych okienek zadań. Niestandardowe okienka zadań są skojarzone z aplikacją, określony dokument. Możesz utworzyć niestandardowe okienka zadań w dodatkach VSTO niektórych aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Użyj kontrolek WPF w okienku akcji programu Excel? ](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Wyświetl okienko akcji  
 W okienku Akcje jest reprezentowany przez <xref:Microsoft.Office.Tools.ActionsPane> klasy. Podczas tworzenia projektów dokumentów wystąpienia tej klasy jest dostępna w kodzie, za pomocą `ActionsPane` pole `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) klasy w projekcie. Aby wyświetlić okienko akcji, należy dodać kontrolki Windows Forms z <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwość `ActionsPane` pola. Poniższy przykład kodu dodaje formant o nazwie `actions` w okienku Akcje.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 W okienku Akcje staje się widoczna w czasie wykonywania, gdy tylko dodasz formant do niego. Po wyświetleniu okienka działań może dynamicznie dodać lub usunąć kontrolki w odpowiedzi na działania użytkownika. Zwykle, możesz dodać kod, aby wyświetlić okienko akcji w `Startup` program obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` tak, aby widoczne jest okienko akcji po użytkownik najpierw otwiera dokument. Jednak można wyświetlić w okienku Akcje tylko w odpowiedzi na akcję użytkownika w dokumencie. Na przykład może dodać kod, aby `Click` zdarzeń kontrolki do dokumentu.  

### <a name="add-multiple-controls-to-the-actions-pane"></a>Dodawanie wielu formantów do okienka akcji  
 Gdy dodasz wiele kontrolek w okienku Akcje powinien grupowanie kontrolek w kontrolce użytkownika, a następnie dodać formant użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości. Ten proces obejmuje następujące kroki:  

1. Tworzenie interfejsu użytkownika (UI) w okienku Akcje, dodając **kontrolki okienka akcji** lub **kontrolki użytkownika** elementu do projektu. Oba te elementy obejmują niestandardowych formularzy Windows <xref:System.Windows.Forms.UserControl> klasy. **Kontrolki okienka akcji** i **kontrolki użytkownika** elementy są równoważne; jedyna różnica polega na ich nazwy.  

2. Dodaj formanty Windows Forms do <xref:System.Windows.Forms.UserControl> za pomocą projektanta lub napisanie kodu.  

   > [!NOTE]  
   >  Można również dodać kontrolki WPF w okienku Akcje, dodając WPF <xref:System.Windows.Controls.UserControl> do formularzy Windows Forms <xref:System.Windows.Forms.UserControl>. Aby uzyskać więcej informacji, zobacz [WPF Użyj kontrolki w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md).  

3. Dodaje wystąpienie kontrolki użytkownika niestandardowego do formantów, które są zawarte w `ActionsPane` pole `ThisWorkbook` (dla programu Excel) lub `ThisDocument` (dla programu Word) klasy w projekcie.  

   Aby uzyskać przykłady ilustrujące ten proces bardziej szczegółowo, zobacz [jak: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hide-the-actions-pane"></a>Ukrywanie okienka akcji  
 Mimo że <xref:Microsoft.Office.Tools.ActionsPane> klasa ma <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody i <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości nie można usunąć okienka akcji z poziomu interfejsu użytkownika przy użyciu wszystkich członków <xref:Microsoft.Office.Tools.ActionsPane> samej klasy. Wywoływanie <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości **false** powoduje ukrycie formantów w okienku akcji; nie ukrywa okienko zadań.  

 Aby ukryć okienka zadań w Twoim rozwiązaniu, masz kilka opcji:  

-   Dla programu Word, ustaw <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> właściwość <xref:Microsoft.Office.Interop.Word.TaskPane> obiekt, który reprezentuje Akcje dokumentu okienku zadań w celu **false**. Poniższy przykład kodu jest przeznaczona do uruchamiania z `ThisDocument` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Dla programu Excel, należy ustawić <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> właściwość <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> obiekt **false**. Poniższy przykład kodu jest przeznaczona do uruchamiania z `ThisWorkbook` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Dla programu Word lub Excel, można również ustawić <xref:Microsoft.Office.Core.CommandBar.Visible%2A> właściwości paska poleceń, reprezentujący w okienku zadań w celu **false**. Poniższy przykład kodu jest przeznaczona do uruchamiania z `ThisDocument` lub `ThisWorkbook` klasy w projekcie.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>W okienku Akcje należy wyczyścić, jeśli dokument jest otwarty  
 Podczas zapisywania przez użytkownika dokumentu, gdy jest widoczne okienko akcji, w okienku Akcje jest widoczny za każdym razem, gdy dokument jest otwarty, czy w okienku Akcje zawiera wszystkie kontrolki. Jeśli użytkownik chce kontrolować gdy się pojawi, wywołaj <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> metody `ActionsPane` pole `Startup` program obsługi zdarzeń `ThisDocument` lub `ThisWorkbook` aby upewnić się, że w okienku Akcje nie jest widoczny, gdy dokument jest otwarty.  

### <a name="determine-when-the-actions-pane-is-closed"></a>Określić po zamknięciu okienka akcji  
 Nie ma żadnego zdarzenia, które jest wywoływane, gdy zamknięto w okienku Akcje. Mimo że <xref:Microsoft.Office.Tools.ActionsPane> klasa ma <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> zdarzeń, to zdarzenie nie jest inicjowane, gdy użytkownik końcowy zostanie zamknięte w okienku Akcje. Zamiast tego należy to zdarzenie jest zgłaszane w przypadku kontrolek w okienku Akcje są ukryte przez wywołanie metody <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody lub przez ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> właściwości **false**.  

 Po zamknięciu przez użytkownika w okienku Akcje, użytkownik może wyświetlić ją ponownie, wykonując jedną z następujących procedur w interfejsie użytkownika (UI) aplikacji.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Aby wyświetlić okienko akcji przy użyciu interfejsu użytkownika programu Word lub Excel  

1.  Na wstążce kliknij **widoku** kartę.  

2.  W **Pokaż/Ukryj** grupy, kliknij przycisk **akcji dla dokumentów** przycisku przełączania.  

## <a name="program-actions-pane-events"></a>Zdarzenia w okienku akcji programu  
 Można dodać wiele kontrolek użytkownika w okienku Akcje, a następnie napisać kod, aby reagować na zdarzenia w dokumencie przez pokazywania i ukrywania kontrolek użytkownika. Jeśli mapujesz elementy schematu XML w dokumencie, zawsze wtedy, gdy punkt wstawiania znajduje się w jednym z elementów XML można wyświetlić niektórych kontrolek użytkownika w okienku Akcje. Aby uzyskać więcej informacji, zobacz [jak: Mapowanie schematów z dokumentami programu Word w programie Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) i [jak: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Można także napisać kod, aby reagować na zdarzenia dowolnego obiektu, w tym kontrolki hosta, aplikacji lub zdarzeń dokumentów. Aby uzyskać więcej informacji, zobacz [instruktażu: Program w odniesieniu do zdarzeń kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Wiązanie danych z kontrolkami w okienku Akcje  
 Formanty w okienku akcji mają te same możliwości wiązania danych jako kontrolek na formularzach Windows Forms. Kontrolki można powiązać ze źródłami danych, takich jak zestawy danych, typizowanych zestawów danych i XML. Aby uzyskać więcej informacji, zobacz [powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Możesz powiązać kontrolkami w okienku akcji i kontrolki do dokumentu do tego samego zestawu danych. Na przykład można utworzyć relacji wzorzec/szczegół między kontrolkami w okienku akcji i kontrolek w arkuszu. Aby uzyskać więcej informacji, zobacz [instruktażu: Wiązanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validate-data-in-actions-pane-controls"></a>Sprawdzanie poprawności danych w kontrolkach okienka akcji  
 Jeśli Wyświetla okno komunikatu w <xref:System.Windows.Forms.Control.Validating> programu obsługi zdarzeń formantu w okienku Akcje zdarzenia może zostać wywołane po raz drugi, gdy fokus z formantu do okna komunikatu. Aby uniknąć tego problemu, należy użyć <xref:System.Windows.Forms.ErrorProvider> formantu, aby wyświetlić komunikaty o błędach weryfikacji.  

## <a name="user-control-stacking-order"></a>Kontrolka użytkownika kolejność układania  
 Jeśli używasz wielu kontrolek użytkownika, można napisać kod, aby prawidłowo stosu kontrolki użytkownika w okienku akcji czy jest zadokowany w pionie lub poziomie. Możesz ustawić kolejność kontrolki użytkownika w okienku akcji, używając <xref:Microsoft.Office.Tools.StackStyle> wyliczenie <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> właściwości. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Właściwości można wziąć pod uwagę następujące <xref:Microsoft.Office.Tools.StackStyle> wartości wyliczenia.  

|Styl stosu|Definicja|  
|--------------------|----------------|  
|FromBottom|Stos w dolnej części okienka działań.|  
|FromLeft|Stack — z lewej strony, w okienku Akcje.|  
|FromRight|Stack — z prawej strony, w okienku Akcje.|  
|FromTop|Stosu, w górnej części okienka działań.|  
|Brak|Nie stosu zdefiniowane. kolejność jest kontrolowana przez dewelopera.|  

 Poniższy kod ustawia <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> właściwości stosu kontrolki użytkownika w górnej części okienka działań.  

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  

## <a name="anchor-controls"></a>Formanty zakotwiczenia  
 Jeśli użytkownik zmieni rozmiar okienka Akcje w czasie wykonywania, formanty można zmienić rozmiar przy użyciu okienka działań. Możesz użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantu Windows Forms z kontrolkami zakotwiczenia w okienku Akcje. Można również zakotwiczyć kontrolek Windows Forms na kontrolkę użytkownika w taki sam sposób. Aby uzyskać więcej informacji, zobacz [jak: Kotwiczenie formantów na formularzach Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resize-the-actions-pane"></a>Zmień rozmiar okienka akcji  
 Nie można bezpośrednio zmienić rozmiar <xref:Microsoft.Office.Tools.ActionsPane> ponieważ <xref:Microsoft.Office.Tools.ActionsPane> jest osadzony w okienku zadań. Jednak można zmienić programistycznie szerokość panelu zadań, ustawiając <xref:Microsoft.Office.Core.CommandBar.Width%2A> właściwość <xref:Microsoft.Office.Core.CommandBar> reprezentujący okienka zadań. Można zmienić wysokość okienka zadań, jeśli jest zadokowany poziomo lub jest liczb zmiennoprzecinkowych.  

 Programowe zmienianie rozmiaru w okienku zadań nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wyboru rozmiar okienka zadań, który najlepiej odpowiada jego potrzebom. Jeśli należy zmienić rozmiar szerokość panelu zadań, można jednak użyć poniższego kodu do wykonania tego zadania.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="reposition-the-actions-pane"></a>Zmienia położenie okienka akcji  
 Nie można bezpośrednio zmienić położenie <xref:Microsoft.Office.Tools.ActionsPane> ponieważ jest osadzony w okienku zadań. Jednak programowo można przenieść w okienku zadań, ustawiając <xref:Microsoft.Office.Core.CommandBar.Position%2A> właściwość <xref:Microsoft.Office.Core.CommandBar> reprezentujący okienka zadań.  

 Programowe zmienianie pozycji w okienku zadań nie jest zalecane, ponieważ użytkownik powinien mieć możliwość wybierz odpowiednią pozycję okienko zadań na ekranie, który najlepiej odpowiada jego potrzebom. Jeśli musisz przejść do określonej pozycji w okienku zadań, można jednak użyć poniższego kodu do wykonania tego zadania.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Użytkownicy końcowi mogą ręcznie zmienić położenie okienka zadań w dowolnym momencie. Nie istnieje żaden sposób zapewnić, że w okienku zadań pozostaną zadokowany w położeniu wskazanej programowo. Jednak możesz sprawdzić zmiany orientacji i upewnij się, czy kontrolek w okienku Akcje są ułożone w odpowiednim kierunku. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Ustawienie <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> i <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> właściwości <xref:Microsoft.Office.Tools.ActionsPane> nie powoduje zmiany położenia, ponieważ <xref:Microsoft.Office.Tools.ActionsPane> obiekt jest osadzony w okienku zadań.  

 Jeśli nie jest zadokowany w okienku zadań, możesz ustawić <xref:Microsoft.Office.Core.CommandBar.Top%2A> i <xref:Microsoft.Office.Core.CommandBar.Left%2A> właściwości <xref:Microsoft.Office.Core.CommandBar> reprezentujący okienka zadań. Poniższy kod powoduje okienka zadań niezadokowane do lewego górnego rogu dokumencie.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>Zobacz także  
 [Użyj kontrolek WPF w rozwiązaniach pakietu Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Przewodnik: Wiązanie danych z kontrolkami w okienku akcji programu Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Instrukcje: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
