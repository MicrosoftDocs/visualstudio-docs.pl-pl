---
title: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2d24ec3a17c9e0824c6b7aaffeaaac02c1c4f76e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546227"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Porady: dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel
  Aby dodać okienko akcji do dokumentu programu Word Microsoft Office lub skoroszytu programu Microsoft Excel, najpierw utwórz Windows Forms kontrolkę użytkownika. Następnie Dodaj kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości `ThisDocument.ActionsPane` pola (Word) lub `ThisWorkbook.ActionsPane` pola (Excel) w projekcie.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Tworzenie kontrolki użytkownika
 Poniższa procedura pokazuje, jak utworzyć kontrolkę użytkownika w projekcie programu Word lub Excel. Dodaje również przycisk do kontrolki użytkownika, która zapisuje tekst do dokumentu lub skoroszytu, gdy zostanie kliknięty.

#### <a name="to-create-the-user-control"></a>Aby utworzyć kontrolkę użytkownika

1. Otwórz projekt na poziomie dokumentu programu Word lub Excel w programie Visual Studio.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **kontrolka okienka akcji**, nadaj jej nazwę **HelloControl**, a następnie kliknij przycisk **Dodaj**.

    > [!NOTE]
    > Możesz Alternatywnie dodać element **kontrolki użytkownika** do projektu. Klasy wygenerowane przez **kontrolkę okienka Akcje** i elementy **kontrolne użytkownika** są funkcjonalnie równoważne.

4. Na karcie **Windows Forms** **przybornika** przeciągnij kontrolkę **przycisk** na kontrolkę.

    > [!NOTE]
    > Jeśli formant nie jest widoczny w projektancie, kliknij dwukrotnie pozycję **HelloControl** w **Eksplorator rozwiązań**.

5. Dodaj kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku. Poniższy przykład pokazuje kod dla dokumentu programu Microsoft Office Word.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. W języku C# należy dodać procedurę obsługi zdarzeń dla przycisku. Ten kod można umieścić w `HelloControl` konstruktorze po wywołaniu `InitializeComponent` .

     Informacje o sposobach tworzenia programów obsługi zdarzeń znajdują się [w temacie How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Dodawanie kontrolki użytkownika do okienka Akcje
 Aby wyświetlić okienko akcje, Dodaj kontrolkę użytkownika do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> właściwości `ThisDocument.ActionsPane` pola (Word) lub `ThisWorkbook.ActionsPane` pola (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Aby dodać kontrolkę użytkownika do okienka Akcje

1. Dodaj następujący kod do `ThisDocument` klasy or w `ThisWorkbook` postaci deklaracji na poziomie klasy (nie dodawaj tego kodu do metody).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Dodaj następujący kod do `ThisDocument_Startup` procedury obsługi zdarzeń `ThisDocument` klasy lub `ThisWorkbook_Startup` procedury obsługi zdarzeń `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Zobacz też
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Instrukcje: zarządzanie układem sterowania w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Przewodnik: wstawianie tekstu do dokumentu z okienka akcji](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
