---
title: Kontrolki Windows Forms w dokumentach pakietu Office — omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a101f22bccb3624eccff1edcea502c9350991392
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254916"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Kontrolki Windows Forms w dokumentach pakietu Office — omówienie
  Kontrolki Windows Forms są obiektami, z którymi użytkownicy mogą wprowadzać dane lub manipulować nimi. W projektach na poziomie dokumentu dla Microsoft Office Excel i Microsoft Office Word, można dodać kontrolki Windows Forms do dokumentu lub skoroszytu w projekcie w czasie projektowania lub można programowo dodać te kontrolki w czasie wykonywania. Można programowo dodać te kontrolki do dowolnego otwartego dokumentu lub arkusza w czasie wykonywania w dodatku narzędzi VSTO dla programu Excel lub Word.

 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów Windows Forms do dokumentów](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)pakietu Office.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="use-windows-forms-controls"></a>Użyj kontrolek Windows Forms

Można dodawać kontrolki Windows Forms do dokumentów oraz do dostosowywalnych elementów interfejsu użytkownika, takich jak okienka akcji, niestandardowe okienka zadań i Windows Forms. Formanty Windows Forms zwykle mają takie samo zachowanie w przypadku dokumentów jak w przypadku innych elementów interfejsu użytkownika, ale istnieją pewne różnice. Aby uzyskać więcej informacji, zobacz [ograniczenia formantów Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

Decyzja o tym, czy dodać kontrolki Windows Forms do dokumentu lub innego elementu interfejsu użytkownika, zależy od kilku czynników. Podczas projektowania interfejsu użytkownika rozwiązania należy rozważyć użycie formantów Windows Forms, zgodnie z opisem w poniższej tabeli.

W dokumencie.
- Gdy chcesz wyświetlić kontrolki przez 100% czasu.

- Jeśli chcesz, aby użytkownicy wprowadzali dane bezpośrednio w dokumencie, na przykład w dokumentach opartych na formularzach, w których powierzchnia edycji jest zablokowana.

- Gdy chcesz, aby kontrolki były wyświetlane w wierszu z danymi w dokumencie. Na przykład, jeśli dodajesz przyciski do każdego wiersza obiektu listy, chcesz je umieścić w wierszu każdego elementu listy.

W okienku Akcje lub w niestandardowym okienku zadań.
- Jeśli chcesz podać użytkownikowi informacje kontekstowe.

- Jeśli chcesz, aby tylko wyniki były widoczne w dokumencie, a nie formanty i dane zapytania.

- Gdy chcesz upewnić się, że kontrolki nie są drukowane z dokumentem.

- Gdy chcesz mieć pewność, że formanty nie zakłócają widoku dokumentu.

W formularzu systemu Windows.
- Gdy chcesz kontrolować rozmiar interfejsu użytkownika.

- Gdy chcesz uniemożliwić użytkownikom ukrywanie lub usuwanie kontrolek.

- Gdy chcesz uzyskać dane wejściowe od użytkownika i uniemożliwić użytkownikowi wykonywanie jakichkolwiek czynności w dokumencie do momentu odebrania danych wejściowych.

## <a name="add-windows-forms-controls-programmatically"></a>Programowe dodawanie formantów Windows Forms
 Możesz dodać kontrolki Windows Forms do dokumentów programu Word i arkuszy programu Excel w czasie wykonywania. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapewnia metody pomocnika do dodawania najpopularniejszych formantów Windows Forms. Te metody pomocnika umożliwiają szybkie dodawanie kontrolek do dokumentu pakietu Office oraz uzyskiwanie dostępu do połączonych funkcji kontroli Windows Forms i funkcji związanych z pakietem Office tych kontrolek.

 Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="use-windows-forms-controls-in-document-level-projects"></a>Używanie formantów Windows Forms w projektach na poziomie dokumentu
 Niektóre aspekty używania formantów Windows Forms w dokumentach są unikatowe dla projektów na poziomie dokumentu, które umożliwiają projektowanie interfejsu użytkownika dokumentu przy użyciu projektanta programu Visual Studio.

### <a name="create-custom-user-controls"></a>Tworzenie niestandardowych kontrolek użytkownika
 Do projektu można dodać kontrolkę użytkownika, a następnie dodać ją do **przybornika**. Następnie możesz przeciągnąć kontrolkę użytkownika bezpośrednio do dokumentu w taki sam sposób, jak dodać kontrolkę Windows Forms do dokumentu. Podczas tworzenia kontrolek użytkownika należy pamiętać o kilku kwestiach:

- Nie należy tworzyć **zapieczętowanej** kontrolki użytkownika. Po przeciągnięciu kontrolki do dokumentu program Visual Studio generuje klasę otoki pochodzącą od kontrolki użytkownika, aby ją rozwinąć i wspierać jej użycie w dokumencie. Jeśli kontrolka użytkownika jest **zapieczętowana**, program Visual Studio nie może wygenerować klasy otoki.

- Kontrolki użytkownika muszą mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut ustawiony na **wartość true**. Formanty użytkownika utworzone w ramach projektu pakietu Office mają ten atrybut domyślnie ustawiony na **wartość true** , ale kontrolki użytkownika, które są częścią projektów zewnętrznych, mogą nie mieć tego atrybutu ustawionego na **wartość true**.

- Po dodaniu kontrolki użytkownika do dokumentu nie zmieniaj ani nie usuwaj <xref:System.Windows.Forms.UserControl> klasy z projektu. Jeśli trzeba zmienić nazwę kontrolki użytkownika, należy najpierw usunąć ją z dokumentu, a następnie dodać ją ponownie po zmianie nazwy.

### <a name="arrange-controls-at-design-time"></a>Rozmieszczanie formantów w czasie projektowania
 Jeśli dodasz wiele kontrolek do dokumentów programu Word i programu Excel w czasie projektowania, możesz szybko ustawić wyrównanie wszystkich zaznaczonych kontrolek przy użyciu narzędzi **Microsoft Office Word** i **Microsoft Office Excel** w programie Visual Studio. Te paski narzędzi są dostępne tylko wtedy, gdy dokument lub arkusz jest otwarty w projektancie.

 Po wybraniu wielu formantów w projektancie, można użyć następujących przycisków na tych paskach narzędzi, aby rozmieścić formanty:

- **Wyrównaj do lewej**

- **Wyrównaj centra**

- **Wyrównaj prawa**

- **Wyrównaj do góry**

- **Wyrównaj środki**

- **Wyrównaj do dołu**

- **Wyrównaj poziome odstępy**

- **Wyrównaj odstępy w pionie**

> [!NOTE]
> W projektach programu Word przyciski te są włączone tylko wtedy, gdy wybrane kontrolki nie są w wierszu z tekstem. Domyślnie kontrolki dodawane do dokumentu w czasie projektowania są zgodne z tekstem.

### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Zapobiegaj wyświetlaniu starych danych w skoroszytach programu Excel podczas ładowania
 Gdy dodasz kontrolki Windows Forms do dokumentów lub arkuszy w czasie projektowania, formanty pozostaną w dokumencie, gdy użytkownik zamknie dokument. Kontrolki dodawane w czasie projektowania są również nazywane *kontrolkami statycznymi*.

 Gdy otwierany jest skoroszyt programu Excel, który zawiera formanty statyczne, w skoroszycie zostanie wyświetlona mapa bitowa kontrolki w kontrolce ActiveX do momentu uruchomienia kodu dostosowania i załadowania rzeczywistej kontrolki. Program Excel tworzy tę mapę bitową i zapisuje ją w skoroszycie za każdym razem, gdy skoroszyt zostanie zapisany. Mapa bitowa pokazuje kontrolkę, która pojawiła się podczas ostatniego zapisywania skoroszytu, włącznie z danymi wyświetlanymi przez formant. Aby uzyskać więcej informacji na temat kontrolki ActiveX, która zawiera Windows Forms kontrolki i mapy bitowe, zobacz [ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

 W pewnych warunkach kod nie zostanie załadowany i zostanie wyświetlona tylko mapa bitowa, na przykład gdy użytkownik otworzy skoroszyt w trybie projektowania. Ponadto, jeśli użytkownik otworzy skoroszyt na komputerze, na którym nie zainstalowano programu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , nie można uruchomić dostosowania w celu załadowania formantów i dlatego tylko mapa bitowa kontrolki jest widoczna. Przed zapisaniem skoroszytu i wysłaniem go do innego użytkownika w celu upewnienia się, że dane osobowe nie zostaną przypadkowo ujawnione, należy usunąć dane osobowe z formantów w skoroszytach.

### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Dopasowanie rozmiaru kontrolki do rozmiaru komórki w arkuszu programu Excel
 Można ustawić zmianę rozmiaru kontrolki automatycznie, gdy zmieni się rozmiar komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [jak: Zmień rozmiar kontrolek w](../vsto/how-to-resize-controls-within-worksheet-cells.md)komórkach arkusza.

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodaj składniki, które są współużytkowane przez wszystkie arkusze
 Możesz dodać składniki, które mają być udostępniane między wszystkimi arkuszami, takimi jak <xref:System.Data.DataSet>, do projektanta skoroszytów, a nie arkuszami. Składnik będzie widoczny na pasku składnika.

### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formuła osadzania formantów w arkuszu programu Excel
 Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

### <a name="layout-style-of-controls-on-a-word-document"></a>Styl układu formantów w dokumencie programu Word
 Po dodaniu kontrolki do dokumentu programu Word w projekcie na poziomie dokumentu przy użyciu projektanta programu Visual Studio, formant jest dodawany w wierszu z tekstem. Aby zmienić styl układu kontrolki, kliknij prawym przyciskiem myszy kontrolkę, a następnie kliknij polecenie **Formatuj formant**. Wybierz styl zawijania na stronie **Układ** okna dialogowego **Formatowanie obiektu** .

 Gdy dodajesz formant do dokumentu programu Word w czasie wykonywania, możesz `Add`określić styl układu nowej kontrolki przy użyciu innej \< <xref:Microsoft.Office.Tools.Word.ControlCollection> *klasy sterującej*, > przeciążenia metody klasy:

- Aby dodać formant w wierszu z tekstem, Użyj przeciążenia, które akceptuje element <xref:Microsoft.Office.Interop.Word.Range> określający lokalizację formantu.

- Aby dodać formant jako kształt swobodny, Użyj przeciążenia, które akceptuje współrzędne lewej i najwyższego poziomu formantu.

  Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

  Jeśli otworzysz szablon programu Word w projektancie programu Visual Studio, formanty niewbudowane na szablonie mogą nie być widoczne, ponieważ program Visual Studio otwiera szablon w widoku **normalnym** . Aby wyświetlić kontrolki, Zmień widok na **Układ wydruku**.

### <a name="controls-outside-the-main-document-body"></a>Kontrolki poza treścią dokumentu głównego
 Kontrolki Windows Forms nie są obsługiwane wewnątrz nagłówka lub stopki ani w dokumencie podrzędnym.

### <a name="add-components-at-design-time"></a>Dodawanie składników w czasie projektowania
 Niektóre kontrolki lub składniki nie są widoczne w dokumencie i są wyświetlane w zasobniku składników. Program Visual Studio udostępnia zasobnik składników dla każdego okna dokumentu. Zasobnik składnika pojawia się na ekranie tylko wtedy, gdy składniki istnieją w dokumencie.

## <a name="see-also"></a>Zobacz także
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Kontrolki Windows Forms](/dotnet/framework/winforms/controls/index)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Instrukcje: Zmień rozmiar kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Instrukcje: Ukryj kontrolki w arkuszach podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Przewodnik: Zmiana formatowania arkusza za pomocą kontrolek CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Przewodnik: Zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)
- [Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu przy użyciu przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Przewodnik: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
- [Przewodnik: Aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)
- [Przewodnik: Aktualizowanie wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
