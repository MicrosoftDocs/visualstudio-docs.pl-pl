---
title: Ograniczenia Windows Forms formantów w dokumentach pakietu Office
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
ms.openlocfilehash: 81a7da585f49b2a2d1f7df4df11d0c78b7a35d69
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251916"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Ograniczenia Windows Forms formantów w dokumentach pakietu Office

Istnieją pewne różnice między kontrolkami Windows Forms, które są dodawane do Microsoft Office dokumentów programu Word lub arkuszy programu Excel, a Microsoft Office także formantów Windows Forms, które są dodawane do Windows Forms. Na przykład <xref:Microsoft.Office.Tools.Word.Controls.Button> , gdy dodasz kontrolkę do dokumentu, właściwości takie jak <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>i <xref:System.Windows.Forms.Control.TabIndex> nie zachowywać się w oczekiwany sposób.

Wiele z tych różnic jest spowodowanych sposobem, w jaki formanty Windows Forms są hostowane w dokumentach. Po dodaniu kontrolki Windows Forms do dokumentu program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] osadzi formant ActiveX, który następnie hostuje kontrolkę Windows Forms w dokumencie. Formant Windows Forms nie jest osadzony bezpośrednio w dokumencie.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ograniczenia metod i właściwości formantów Windows Forms

Istnieje kilka metod i właściwości formantów Windows Forms, które nie działają w taki sam sposób, jak w przypadku formularza systemu Windows i dlatego zaleca się, aby nie były używane. Na przykład ustawienia właściwości, takie jak <xref:System.Windows.Forms.Control.Dock> i <xref:System.Windows.Forms.Control.Anchor> , mają wpływ tylko na pozycję formantu, w odniesieniu do kontrolki ActiveX kontenera, a nie dokumentu. Poniżej znajduje się lista nieobsługiwanych metod i właściwości formantów Windows Forms dla programów Word i Excel:

- Nieobsługiwane właściwości formantów programu Excel:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nieobsługiwane metody i właściwości formantów programu Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Nie można również ustawić <xref:System.Windows.Forms.Control.Left> właściwości or <xref:System.Windows.Forms.Control.Top> formantów Windows Forms, które są w wierszu z tekstem w dokumencie programu Word. Kontrolki Windows Forms są dodawane w wierszu z tekstem w następujących przypadkach:

- Użytkownik programowo dodaje formant do dokumentu programu Word i używa metody, która określa zakres lokalizacji.

- Do dokumentu programu Word można dodać formant Windows Forms w czasie projektowania. Można to zmienić, modyfikując formant w projektancie.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Różnice w kontrolkach Windows Forms w dokumentach pakietu Office

Formanty Windows Forms zwykle mają takie samo zachowanie w dokumencie pakietu Office jak w formularzu systemu Windows, ale istnieją pewne różnice. W poniższej tabeli opisano różnice występujące w przypadku formantów Windows Forms w dokumentach pakietu Office.

|Funkcja|Występują|
|-------------------|----------------|
|Kolejność tabulacji kontrolki|Nie można tabulatorować formantów umieszczonych w arkuszu programu Excel lub dokumencie programu Word.|
|Grupowanie formantów|Nie można użyć <xref:System.Windows.Forms.GroupBox> kontrolki, aby zawierać inne kontrolki dokumentu pakietu Office. Po dodaniu wielu przycisków radiowych bezpośrednio do dokumentu, przyciski radiowe nie wykluczają się wzajemnie. Można napisać kod, aby przyciski radiowe wykluczają się wzajemnie. Jednak preferowanym podejściem jest dodanie przycisków radiowych do kontrolki użytkownika, a następnie dodanie kontrolki użytkownika do dokumentu. Aby uzyskać więcej informacji, zobacz przykładowe kontrolki programu Word lub kontrolki programu Excel w przykładach na potrzeby [tworzenia i instruktażu pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).|
|Typ formantu|Kontrolki Windows Forms używane w dokumentach są opakowane w klasę dostarczaną [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] przez program, która daje kontrolki dodatkowe funkcje specyficzne dla arkusza programu Excel lub dokumentu programu Word. Na przykład, jeśli masz kontrolkę **przycisku** w arkuszu programu Excel, pamiętaj, aby określić typ jako, <xref:Microsoft.Office.Tools.Excel.Controls.Button> a nie <xref:System.Windows.Forms.Button> odwołanie lub rzutowanie obiektu.|
|Położenie i rozmiar kontrolki|Rozmiar i położenie formantu są określane przez właściwości, które są częścią kontrolki ActiveX kontenera. Właściwości kontrolki ActiveX mają różne wartości niż równoważne właściwości kontrolki Windows Forms. Po ustawieniu `Top`właściwości, `Left`, `Height`, lub `Width` kontrolce, jest mierzona w punktach, a nie w pikselach.|
|Pozycja kontrolki w dokumentach programu Word|W przypadku dodawania formantów do układu opartego na przepływie należy pamiętać, że kontrolki będą przepływać z zawartością w miarę zmiany zawartości. Nie można zakotwiczyć kontrolki w akapicie, gdy przeciągniesz ją z **przybornika** , ponieważ formant jest dodawany do dokumentu programu Word w wierszu z tekstem. Jeśli używasz innej metody do dodania kontrolki, takiej jak dwukrotne kliknięcie kontrolki, formant zostanie wstawiony zgodnie z opcją słowa ustawioną dla wstawiania obrazów.<br /><br /> Nie można ustawić `Left` właściwości lub `Top` kontrolki, która jest wbudowana z tekstem.<br /><br /> Nie można umieścić kontrolek w nagłówku lub stopce ani w dokumencie podrzędnym.|
|Zdarzenia kontroli|Po wybraniu kontrolki wywołuje ona zdarzenia w następującej kolejności:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Gdy formant zostanie odzaznaczony, wywołuje zdarzenia w następującej kolejności:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Skalowanie formantów|Gdy zmienisz ustawienie powiększenia dokumentu na inne niż 100%, formanty są wyłączone, chociaż wyglądają na skalowanie w dokumencie. Jeśli na przykład klikniesz przycisk, gdy dokument jest o 130% zoom, zostanie wyświetlony komunikat informujący, że formant został wyłączony, dopóki powiększenie nie zostanie ustawione na 100%. Kontrolki będą działać prawidłowo, gdy zmienisz powiększenie na 100%.|
|Wartości właściwości kontrolki|Mimo że właściwości kontrolek w formularzu systemu Windows są ustawione na wartość całkowitą, są one ustawiane jako pojedyncze dla kontrolek w dokumencie programu Word. W programie Excel wartości właściwości formantów są ustawiane na wartość Double. Jeśli właściwość `Width` i kontrolka w arkuszu przekracza rozmiar arkusza lub ekranu, wartość zostanie obcięta. `Height`|
|Zmienianie rozmiarów kontrolki|Jeśli zmienisz rozmiar kontrolki w dokumencie przy użyciu jednego z ośmiu uchwytów rozmiaru, nowe wymiary kontrolki nie zostaną odzwierciedlone w oknie **Właściwości** do momentu ponownego wybrania kontrolki.|
|Zachowanie kontrolki|Kontrolki w arkuszu programu Excel mogą zachowywać się nieprzewidywalne podczas dzielenia okna arkusza. Na przykład dostęp do <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> arkusza może być dostępny tylko w jednym z okien.|
|Określanie nazw kontrolek|Nie można używać słów zarezerwowanych do kontroli nazw. Na przykład jeśli dodasz <xref:Microsoft.Office.Tools.Excel.Controls.Button> do arkusza i zmienisz nazwę na **system**, wystąpią błędy podczas kompilowania projektu.|
|Programistyczne Dodawanie kontrolek|Nie używaj konstruktora formantu, aby dodać kontrolkę do dokumentu w czasie wykonywania. Zamiast tego należy użyć metod pomocnika dostarczonych przez [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Na przykład użyj <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metody, aby dodać przycisk do arkusza. Jeśli chcesz dodać formant, który nie jest obsługiwany przez te metody pomocnika, możesz użyć `AddControl` metody. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopiowanie kontrolek|Jeśli skopiujesz kontrolkę Windows Forms i wkleisz ją do dokumentu w czasie wykonywania, pusty formant ActiveX kontenera zostanie wklejony do dokumentu. Formant Windows Forms nie pojawia się w nowej lokalizacji, a kod związany z oryginalnym formantem nie jest kopiowany do kontrolki ActiveX kontenera.|

## <a name="limitations-in-document-level-projects"></a>Ograniczenia w projektach na poziomie dokumentu

Niektóre ograniczenia dotyczące używania formantów Windows Forms w dokumentach są unikatowe dla projektów na poziomie dokumentu.

### <a name="control-support-at-design-time"></a>Obsługa kontroli w czasie projektowania

Niektóre formanty Windows Forms są usuwane z **przybornika** po otwarciu arkusza programu Excel lub dokumentu programu Word w projektancie programu Visual Studio. Wynika to z ograniczeń technicznych lub, ponieważ funkcje są już dostępne w programie Word lub Excel. Projekty programów Excel i Word obsługują wszystkie Windows Forms kontrolki i inne składniki, które pojawiają się w **przyborniku** , gdy dokument ma fokus, i można również dodać kontrolki innych firm do arkusza lub dokumentu.

> [!NOTE]
> Wszystkie kontrolki są usuwane z **przybornika** , gdy dokument jest chroniony. Aby uzyskać informacje o ochronie dokumentów, zobacz [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Kontrolki innych firm muszą mieć atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawiony na **wartość true** , aby można było go używać w rozwiązaniu z pakietem Office.

Następujące kontrolki i składniki nie są dostępne w **przyborniku**:

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

W przypadku utworzenia projektu pakietu Office na poziomie dokumentu korzystającego z istniejącego dokumentu programu Word lub skoroszytu programu Excel, który zawiera kontrolki ActiveX, funkcjonalność kontrolek ActiveX nie zostanie utracona; nie jest jednak obsługiwane dodawanie nowych formantów ActiveX do dokumentów z poziomu programu Visual Studio. Jeśli na przykład dokument programu Word ma przycisk z przybornika **formantów** , który uruchamia makro Visual Basic for Applications (VBA), będzie nadal uruchamiać makro po użyciu dokumentu w projekcie pakietu Office. Zaleca się jednak usuwanie formantów ActiveX i makr języka VBA oraz zastępowanie ich przy użyciu formantów Windows Forms i kodu zarządzanego.

## <a name="see-also"></a>Zobacz także

- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
