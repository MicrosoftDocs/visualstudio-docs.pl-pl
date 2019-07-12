---
title: Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5cb4bf5788e1d30933a807e2e97e064118fc076
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823410"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office

Istnieją pewne różnice między kontrolek Windows Forms, które są dodawane do dokumentów programu Microsoft Office Word lub arkuszy programu Microsoft Office Excel i formanty Windows Forms, które są dodawane do formularzy Windows Forms. Na przykład po dodaniu <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolować do dokumentu, właściwości, takie jak <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, i <xref:System.Windows.Forms.Control.TabIndex> nie zachowywać się zgodnie z oczekiwaniami.

Wiele z tych różnic są spowodowane przez sposób tego formularze Windows znajdują się formanty w dokumentach. Po dodaniu kontrolki Windows Forms do dokumentów, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] osadza formantu ActiveX, który następnie obsługuje kontrolki formularzy Windows w dokumencie. Kontrolki Windows Forms nie jest zagnieżdżony bezpośrednio w dokumencie.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ograniczenia dotyczące metod i właściwości kontrolek formularzy Windows Forms

Istnieje wiele metod i właściwości formantów formularzy Windows, które nie działają tak samo w dokumencie na formularzu Windows, a w związku z tym, zalecane jest, że mogą nie być stosowane. Na przykład, takie jak ustawienie właściwości <xref:System.Windows.Forms.Control.Dock> i <xref:System.Windows.Forms.Control.Anchor> ma wpływ tylko na położenie formantu względem formantu ActiveX w kontenerze, a nie dokumentu. Oto lista nieobsługiwanych metod i właściwości formantów formularzy Windows dla programu Word i Excel:

- Nieobsługiwane właściwości kontrolki programu Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nieobsługiwana metod i właściwości kontrolki programu Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Ponadto nie można ustawić <xref:System.Windows.Forms.Control.Left> lub <xref:System.Windows.Forms.Control.Top> właściwości formantów formularzy Windows, które są zgodne z tekstu w dokumencie programu Word. Kontrolek formularzy Windows Forms zostaną dodane zgodnie z tekstem w następujących przypadkach:

- Programowe Dodawanie kontrolki do dokumentu programu Word i użyć metody, która określa zakres dla lokalizacji.

- Dodajesz formant programu Windows Forms do dokumentów programu Word w czasie projektowania. Można to zmienić, modyfikując formantu w projektancie.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Różnice w kontrolkach formularzy Windows Forms w dokumentach pakietu Office

Kontrolek formularzy Windows Forms zazwyczaj mają takie samo zachowanie w dokumencie programu Word robią w formularzu Windows, ale istnieją pewne różnice. W poniższej tabeli opisano różnice, które istnieją dla formantów Windows Forms w dokumentach pakietu Office.

|Funkcja|Różnica|
|-------------------|----------------|
|Kolejność tabulacji kontrolki|Nie można przełączać się między formanty umieszczone na arkusza programu Excel lub dokumentu programu Word.|
|Grupowanie kontroli|Nie można użyć <xref:System.Windows.Forms.GroupBox> kontroli zawiera inne kontrolki na dokumencie programu Word. Po dodaniu wielokrotnych przycisków radiowych bezpośrednio do dokumentu, przyciski radiowe nie wykluczają się wzajemnie. Można napisać kod, aby przyciski radiowe wzajemnie się wykluczają; jednak jest preferowanym podejściem jest dodawanie przycisków radiowych do kontrolki użytkownika, a następnie dodaj formant użytkownika do dokumentu. Aby uzyskać więcej informacji, zobacz przykładowy formanty programu Word lub próbki formanty programu Excel w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).|
|Typ formantu|Formanty Windows Forms używane w dokumentach są opakowane w dostarczonych przez klasę [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] daje dodatkową funkcjonalność określonych formantów do arkusza programu Excel lub dokumentu programu Word. Na przykład, jeśli masz **przycisk** sterowania w arkuszu programu Excel, należy określić typ jako <xref:Microsoft.Office.Tools.Excel.Controls.Button> zamiast <xref:System.Windows.Forms.Button> przy odwoływaniu się lub Rzutowanie obiektu.|
|Kontrolka położenie i rozmiar|Rozmiar i położenie kontrolki jest określany przez właściwości, które są częścią kontenera kontrolki ActiveX. Właściwości formantu ActiveX podjąć różne wartości niż równoważne właściwości formantu Windows Forms. Po ustawieniu `Top`, `Left`, `Height`, lub `Width` właściwości formantu, jest on mierzony w wskazuje zamiast pikseli.|
|Położenie kontrolki w dokumentach programu Word|Jeśli dodasz kontrolki na układ, oparte na przepływie pamiętać, że formanty będą przepływać z zawartością zgodnie ze zmianami zawartości. Nie można zakotwiczyć kontrolki akapitu podczas przeciągania go z **przybornika** ponieważ formant został dodany do dokumentu programu Word z tekstu. Jeśli używasz innej metody, aby dodać kontrolki, na przykład dwukrotne kliknięcie formantu, formant jest wstawiany zgodnie z opcją programu Word, skonfigurowanych do wstawiania obrazów.<br /><br /> Nie można ustawić `Left` lub `Top` właściwości formantu, który jest wbudowany z tekstem.<br /><br /> Nie można umieścić kontrolek, w nagłówku lub stopce lub w ramach podrzędnego.|
|Zdarzenia obiektu Controls|Po wybraniu kontrolki wywołuje zdarzenia w następującej kolejności:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Gdy kontrolka nie jest zaznaczona, wywołuje zdarzenia w następującej kolejności:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Skalowanie kontroli|Po zmianie ustawienia powiększenia dokumentu na coś innego niż 100%, formanty są wyłączone, mimo że wydają się skalować w dokumencie. Na przykład po kliknięciu przycisku, gdy dokument wynosi 130% powiększenia, będzie wyświetlany komunikat, kontrolka została wyłączona do momentu powiększenia jest ustawiony na 100%. Formanty będzie działać poprawnie po zmianie poziomu powiększenia do 100%.|
|Wartości właściwości kontrolki|Mimo że właściwości kontrolek w formularzu Windows są ustawione na wartość całkowitą, są one ustawione pojedynczej dla formantów w dokumencie programu Word. W programie Excel wartości właściwości kontrolki są ustawiane na wartość typu double. Jeśli `Height` i `Width` właściwości formantu w arkuszu przekracza rozmiar okna arkusza lub ekranu, wartość zostanie obcięta.|
|Zmiana rozmiaru formantu|Jeżeli zmienisz rozmiar formantu w dokumencie przy użyciu jednej z ośmioma uchwytami zmiany rozmiaru, nowe kontrolki wymiary nie są odzwierciedlane w **właściwości** okna, aż formant jest wybierane ponownie.|
|Zachowanie kontroli|Kontrolki w arkuszu programu Excel może być nieprzewidywalne zachowanie, gdy okno Arkusz zostanie podzielona. Na przykład dostęp do <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> w arkuszu mogą być dostępne tylko w jednym z systemu windows.|
|Nazwy formantów|Nie można użyć słów zastrzeżonych nazw kontrolek. Na przykład jeśli dodasz <xref:Microsoft.Office.Tools.Excel.Controls.Button> do arkusza i Zmień nazwę na **systemu**, wystąpi błąd podczas tworzenia projektu.|
|Programowe Dodawanie kontrolek|Nie należy używać konstruktora kontrolki Aby dodać kontrolki do dokumentu w czasie wykonywania. Zamiast tego należy użyć metody pomocnika, dostarczone przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład użyć <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metodę, aby dodać przycisk do arkusza. Jeśli chcesz dodać kontrolkę, która nie jest obsługiwana przez te metody pomocnika, możesz użyć `AddControl` metody. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopiowanie kontrolki|Jeśli kopiowanie kontrolki Windows Forms i wkleić go do dokumentu w czasie wykonywania, pustego kontenera kontrolki ActiveX jest wklejany do dokumentu. Kontrolki Windows Forms jest niewidoczny w nowej lokalizacji, a kod związany z oryginalnego formantu nie jest kopiowany do kontenera kontrolki ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Ograniczenia w projektach na poziomie dokumentu

Niektóre ograniczenia za pomocą formantów formularzy Windows w dokumentach są unikatowe dla projektów na poziomie dokumentu.

### <a name="control-support-at-design-time"></a>Lepsza obsługa kontroli w czasie projektowania

Niektóre formanty Windows Forms, są usuwane z **przybornika** gdy arkusza programu Excel lub dokumentu programu Word jest otwarty w Projektancie Visual Studio. Jest to spowodowane ograniczenia techniczne lub ponieważ ta funkcja jest już dostępne w programie Word lub Excel. Projekty programu Excel i Word obsługuje wszystkich kontrolek Windows Forms i inne składniki, które pojawiają się w **przybornika** kiedy dokument ma fokus, a formanty innych firm można również dodać do arkusza lub dokumentu.

> [!NOTE]
> Wszystkie kontrolki są usuwane z **przybornika** gdy dokument jest chroniony. Aby uzyskać informacji na temat ochrony dokumentu, zobacz [dokumentu ochrona w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Formanty innych firm musi mieć <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną wartość atrybutu **true** aby możliwe było użycie w rozwiązaniach pakietu Office.

Nie są dostępne w następujących kontrolek i składników **przybornika**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Obsługa starszych kontrolek ActiveX

Jeśli tworzysz projekt Office poziomie dokumentu, który korzysta z istniejącego dokumentu programu Word lub skoroszytu programu Excel, który zawiera kontrolki ActiveX, funkcje kontrolek ActiveX nie zostaną utracone; jednak istnieje nie jest obsługiwane dodawanie nowych kontrolek ActiveX do dokumentów z poziomu programu Visual Studio. Na przykład, jeśli dokument programu Word znajduje się przycisk z **kontroli** Przybornik uruchomionym makra Visual Basic for Applications (VBA), nadal będzie uruchomić makro, gdy dokument została użyta w projekcie programu pakietu Office. Jednak zalecane jest, Usuń formantów ActiveX i makra VBA i zastąp je kontrolek formularzy Windows Forms i kod zarządzany.

## <a name="see-also"></a>Zobacz także

- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
