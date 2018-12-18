---
title: 'Porady: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f70511d0490032204789dc037a13847a10b5cbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948364"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Porady: dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel
  Aby dodać okienek akcji do dokumentu programu Microsoft Office Word lub skoroszytu programu Microsoft Excel, należy najpierw utworzyć formant użytkownika interfejsu Windows Forms. Następnie dodaj formant użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwość `ThisDocument.ActionsPane` pola (w programie Word) lub `ThisWorkbook.ActionsPane` pola (Excel) w projekcie.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Tworzenie kontrolki użytkownika  
 Poniższa procedura pokazuje, jak utworzyć formant użytkownika w programie lub projektu w programie Excel. Ponadto dodaje przycisk do formantu użytkownika, który zapisuje tekst na dokument lub skoroszyt, po kliknięciu.  
  
#### <a name="to-create-the-user-control"></a>Aby utworzyć formant użytkownika  
  
1.  Otwórz projekt poziomu dokumentu programu Word lub Excel w programie Visual Studio.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **kontrolki okienka akcji**, nadaj jej nazwę **HelloControl**i kliknij przycisk **Dodaj**.  
  
    > [!NOTE]  
    >  Możesz też dodać **kontrolki użytkownika** elementu do projektu. Klasy generowane przez **kontrolki okienka akcji** i **kontrolki użytkownika** elementy są funkcjonalnie równoważne.  
  
4.  Z **Windows Forms** karcie **przybornika** przeciągnij **przycisk** kontrolki na kontrolkę.  
  
    > [!NOTE]  
    >  Jeśli formant nie jest widoczny w projektancie, kliknij dwukrotnie **HelloControl** w **Eksploratora rozwiązań**.  
  
5.  Dodaj kod, aby <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń przycisku. Poniższy przykład pokazuje kod dla dokumentu programu Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  W języku C# należy dodać moduł obsługi zdarzenia kliknięcia przycisku. Możesz umieścić ten kod w `HelloControl` konstruktora, po wywołaniu `InitializeComponent`.  
  
     Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [porady: Tworzenie procedury obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Dodaj kontrolkę użytkownika w okienku Akcje  
 Aby pokazać okienko akcji, Dodaj formant użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwość `ThisDocument.ActionsPane` pola (w programie Word) lub `ThisWorkbook.ActionsPane` pola (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Aby dodać kontrolkę użytkownika w okienku Akcje  
  
1.  Dodaj następujący kod do `ThisDocument` lub `ThisWorkbook` klasy jako deklaracja klasy poziomie (nie należy dodawać kod do metody).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Dodaj następujący kod do `ThisDocument_Startup` program obsługi zdarzeń `ThisDocument` klasy lub `ThisWorkbook_Startup` program obsługi zdarzeń `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Porady: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Wskazówki: Wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  