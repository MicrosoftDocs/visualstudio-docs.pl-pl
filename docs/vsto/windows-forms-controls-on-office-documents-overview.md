---
title: Formanty Windows Forms na przegląd dokumentów pakietu Office
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 48778074587e5cf6e4a51ff2386a437e9c3922d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902496"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Formanty Windows Forms na przegląd dokumentów pakietu Office
  Kontrolek formularzy Windows Forms są obiekty, które użytkownicy mogą wchodzić w interakcje z wprowadzać ani wykonywać operacje na danych. W projektach na poziomie dokumentu dla programu Microsoft Office Excel i Microsoft Office Word dodaniem kontrolek formularzy Windows Forms do dokumentów lub skoroszytu w projekcie w czasie projektowania lub można programowo dodać tych formantów w czasie wykonywania. Programowe można dodać te formanty do dowolnego otwartego dokumentu lub arkusza w czasie wykonywania w dodatku narzędzi VSTO dla programu Excel lub Word.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Użyj kontrolek formularzy Windows Forms  
 Możesz dodać kontrolek formularzy Windows Forms do dokumentów oraz do elementów interfejsu użytkownika można dostosowywać, łącznie z okienka akcji niestandardowych okienek zadań i formularzy Windows. Kontrolek formularzy Windows Forms zazwyczaj mają takie samo zachowanie w dokumentach jako na inne elementy interfejsu użytkownika, ale istnieją pewne różnice. Aby uzyskać informacje, zobacz [ograniczenia Windows Forms kontrolki w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 Decyzja, czy należy dodać kontrolek formularzy Windows Forms do dokumentu lub innego elementu interfejsu użytkownika zależy od wielu czynników. Podczas projektowania interfejsu użytkownika rozwiązania, należy wziąć pod uwagę używa formantów Windows Forms zgodnie z opisem w poniższej tabeli.  
  
 W dokumencie.  
 -   Kiedy chcesz wyświetlić kontrolki 100% czasu.  
  
- Kiedy chcesz użytkownikom na wprowadzanie danych bezpośrednio w dokumencie, na przykład w dokumentach opartego na formularzach, gdzie edycji powierzchni jest zablokowany.  
  
- Kiedy chcesz formantów do wyświetlania tworzone są dane w dokumencie. Na przykład jeśli chcesz dodać przyciski do każdego wiersza w obiekcie listy, należy je zgodnie z każdego elementu listy.  
  
  W okienku Akcje lub niestandardowego okienka zadań.  
  -   Kiedy chcesz udostępniać kontekstowe informacje do użytkownika.  
  
- Jeśli chcesz tylko wyniki były wyświetlane w dokumencie i nie formanty zapytania i danych.  
  
- Jeśli chcesz upewnić się, że formanty nie są drukowane w dokumencie.  
  
- Kiedy chcesz upewnić się, że formanty nie przeszkadzają ze stanowiskiem dokumentu.  
  
  W formularzu Windows.  
  -   Jeśli chcesz kontrolować rozmiar interfejsu użytkownika.  
  
- Kiedy chcesz uniemożliwić użytkownikom ukrywanie lub usuwanie kontrolek.  
  
- Jeśli chcesz pobrać dane wejściowe od użytkownika i uniemożliwić wykonywanie wszystko w dokumencie, do momentu otrzymania danych wejściowych przez użytkownika.  
  
## <a name="add-windows-forms-controls-programmatically"></a>Programowe Dodawanie kontrolek formularzy Windows Forms  
 Można dodać kontrolek formularzy Windows Forms do dokumentów programu Word i arkusze programu Excel w czasie wykonywania. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapewnia metody pomocnika do dodawania najczęstsze formanty Windows Forms. Te metody pomocnika umożliwiają szybko dodać kontrolki do dokumentu pakietu Office i dostęp do połączonych funkcjonalność formantu Windows Forms i funkcji związanych ze Office tych kontrolek.  
  
 Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>Użyj kontrolek formularzy Windows Forms w projektach na poziomie dokumentu  
 Niektóre aspekty za pomocą formantów formularzy Windows w dokumentach są unikatowe dla projektów na poziomie dokumentu, które pozwalają na projektowanie interfejsu użytkownika w dokumencie przy użyciu projektanta programu Visual Studio.  
  
### <a name="create-custom-user-controls"></a>Tworzenie niestandardowych formantów użytkownika  
 Można dodać kontrolkę użytkownika do projektu, a następnie dodać go do **przybornika**. Kontrolki użytkownika można następnie przeciągnąć bezpośrednio do dokumentu w taki sam sposób, należy dodać formant programu Windows Forms do dokumentu. Istnieje kilka kwestii, o których należy pamiętać, po utworzeniu kontrolki użytkownika:  
  
-   Nie należy tworzyć **zapieczętowanego** kontrolki użytkownika. Przeciągnięcie formantu do dokumentu programu Visual Studio generuje klasę otoki pochodną klasy formantu użytkownika, aby rozszerzać go i obsługiwać jego użycia w dokumencie. Jeśli kontrolka użytkownika znajduje się **zapieczętowanego**, Visual Studio nie można wygenerować klasy otoki.  
  
-   Formanty użytkownika musi mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną wartość atrybutu **true**. Formanty użytkownika utworzone w projekcie programu pakietu Office mają ten atrybut ustawiony na **true** przez domyślne, ale użytkownik formantów, które są częścią projektów poza może nie mieć tego atrybutu, wartość **true**.  
  
-   Po dodaniu kontrolki użytkownika do dokumentu nie zmieniaj nazwy ani usunąć <xref:System.Windows.Forms.UserControl> klasy z projektu. Jeśli musisz zmienić nazwę kontrolki użytkownika należy najpierw usunąć z dokumentu i dodać je ponownie po zmianie nazwy.  
  
### <a name="arrange-controls-at-design-time"></a>Rozmieszczanie formantów w czasie projektowania  
 Jeśli dodasz kilka formantów do dokumentów programu Word i Excel w czasie projektowania, można szybko ustawić wyrównanie wszystkich wybranych kontrolek przy użyciu **Microsoft Office Word** i **Microsoft Office Excel**paski narzędzi w programie Visual Studio. Te paski narzędzi są dostępne tylko wtedy, gdy dokument lub skoroszyt jest otwarty w projektancie.  
  
 Po wybraniu wielu formantów w projektancie, kontrolki będą ułożone za pomocą następujących przycisków na te paski narzędzi:  
  
-   **Wyrównaj wej**  
  
-   **Wyrównaj do centrów**  
  
-   **Wyrównaj prawa**  
  
-   **Wyrównaj górne krawędzie**  
  
-   **Wyrównaj lewych**  
  
-   **Wyrównaj do dołu**  
  
-   **Wprowadź równe odstępy w poziomie**  
  
-   **Wprowadź odstępy w pionie**  
  
> [!NOTE]  
>  W projektach programu Word przyciski te są włączone tylko wtedy, gdy wybrane formanty nie są zgodne z tekstu. Formanty, które dodają do dokumentu w czasie projektowania są domyślnie tworzone są tekstu.  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>Uniemożliwić stare dane w skoroszytach programu Excel podczas ładowania  
 Po dodaniu kontrolek formularzy Windows Forms do dokumentów lub arkuszy w czasie projektowania formanty pozostają w dokumencie po użytkownik zamyka dokument. Dodane w czasie projektowania formanty są również nazywane *formantów statycznych*.  
  
 Po otwarciu skoroszytu programu Excel zawierający statyczne formanty skoroszyt wyświetlać mapę bitową kontrolki w kontrolce ActiveX, dopóki kod dostosowania działa i ładuje rzeczywistego formantu. Excel tworzy tę mapę bitową i przechowuje ją w skoroszycie, zawsze wtedy, gdy skoroszyt jest zapisywany. Mapy bitowej zawiera kontrolki, w jakim występowały podczas ostatniego zapisania skoroszytu, łącznie z danymi, w którym był wyświetlany formantu. Aby uzyskać więcej informacji na temat formantu ActiveX, który zawiera formanty Windows Forms i mapy bitowe, zobacz [ograniczenia Windows Forms kontrolki w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
 W pewnych okolicznościach kod nie zostanie załadowany i jest wyświetlany tylko mapy bitowej, np. gdy użytkownik otwiera skoroszyt w trybie projektowania. Ponadto jeśli użytkownik otwiera skoroszyt na komputerze, który nie ma [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowany, dostosowanie nie można uruchomić ładowanie kontrolek i w związku z tym tylko mapy bitowej kontrolka jest widoczna. Zawsze należy usunąć dane osobowe z formantów do skoroszytów przed zapisanie skoroszytu i wysłanie go do innego użytkownika, aby upewnić się, że informacje osobiste nie jest przypadkowo ujawnione.  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Rozmiar kontrolki dopasowania do rozmiaru komórek w arkuszu programu Excel  
 Możesz ustawić kontroli rozmiaru automatycznie po zmianie rozmiaru komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [jak: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodawanie składników, które są współużytkowane przez wszystkie arkusze  
 Możesz dodać składniki, które chcesz udostępnić wśród wszystkich arkuszy, takich jak <xref:System.Data.DataSet>, aby Projektant skoroszytów zamiast do arkuszy. Składnik pojawi się w zasobniku składnika.  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Formuła dla osadzania kontrolek w arkuszu programu Excel  
 Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Styl układu kontrolek w dokumencie programu Word  
 Po dodaniu kontrolki do dokumentu programu Word w projekcie na poziomie dokumentu przy użyciu funkcji Projektant Visual Studio, kontrolka zostanie dodana tworzone są tekstu. Aby zmienić styl układu formantu, kliknij prawym przyciskiem myszy formant, a następnie kliknij przycisk **kontroli formatu**. Wybierz styl zawijania **układ** strony **Format obiektu** okno dialogowe.  
  
 Po dodaniu kontrolki do dokumentu programu Word w czasie wykonywania, można określić styl układu nowego formantu przy użyciu różnych `Add` \< *kontrolować klasy*> przeciążenia metody <xref:Microsoft.Office.Tools.Word.ControlCollection> klasy:  
  
- Aby dodać formant z tekstu, użyj przeciążenia, które akceptuje <xref:Microsoft.Office.Interop.Word.Range> określająca położenie formantu.  
  
- Aby dodać kontrolkę jako kształt zmiennoprzecinkowe, użyj przeciążenia, które akceptuje lewym i górnym współrzędne formantu.  
  
  Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
  Jeśli otworzysz szablon programu Word w Projektancie Visual Studio niewbudowana formantów na szablon może nie być widoczna ponieważ Visual Studio otwiera szablon w **normalny** widoku. Aby wyświetlać kontrolki, należy zmienić widok, aby **układ wydruku**.  
  
### <a name="controls-outside-the-main-document-body"></a>Kontrolki poza treścią dokumentu głównego  
 Kontrolek formularzy Windows Forms, nie są obsługiwane w nagłówku lub stopce lub w ramach podrzędnego.  
  
### <a name="add-components-at-design-time"></a>Dodawanie składników w czasie projektowania  
 Niektórych kontrolek lub składniki nie są widoczne w dokumencie i zamiast tego są wyświetlane w zasobniku składnika. Program Visual Studio udostępnia zasobnik składnika dla każdego okna dokumentu. W zasobniku składnika wyświetlane na ekranie, tylko wtedy, gdy składniki istnieje w dokumencie.  
  
## <a name="see-also"></a>Zobacz także  
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/index)   
 [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Instrukcje: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Instrukcje: Ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Przewodnik: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Przewodnik: Zmiana formatowania dokumentu za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Przewodnik: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [Przewodnik: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [Przewodnik: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
