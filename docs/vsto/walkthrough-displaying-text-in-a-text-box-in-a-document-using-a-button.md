---
title: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku
description: Dowiedz się, jak używać przycisków i pól tekstowych w dostosowaniu na poziomie dokumentu dla programu Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cda1fe3e7430ff30dcc3b3921eb2bcd4d31b699
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522754"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Przewodnik: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku
  W tym instruktażu pokazano, jak używać przycisków i pól tekstowych w dostosowaniu na poziomie dokumentu dla programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie formantów do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.

- Wypełnienie pola tekstowego po kliknięciu przycisku.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word z **przyciskiem Nazwa My Word**. W kreatorze wybierz pozycję **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **przycisku my Word** do **Eksplorator rozwiązań**.

## <a name="add-controls-to-the-word-document"></a>Dodawanie formantów do dokumentu programu Word
 Kontrolki interfejsu użytkownika składają się z przycisku i pola tekstowego w dokumencie programu Word.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Sprawdź, czy dokument jest otwarty w projektancie programu Visual Studio.

2. Na karcie **Formanty standardowe** **przybornika** przeciągnij <xref:Microsoft.Office.Tools.Word.Controls.TextBox> kontrolkę do dokumentu.

   > [!NOTE]
   > W programie Word formanty są domyślnie upuszczane z tekstem. Można zmodyfikować sposób, w jaki kontrolki i obiekty kształtu są wstawiane przez zmianę wartości domyślnej na karcie **Edycja** okna dialogowego **Opcje** w programie Word.

3. W menu **Widok** kliknij **okno właściwości**.

4. Znajdź **TextBox1** w oknie dialogowym **Właściwości** i zmień właściwość **Nazwa** pola tekstowego na **DisplayText**.

5. Przeciągnij kontrolkę **Button** do dokumentu i Zmień następujące właściwości.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Tekst**|**Wstaw tekst**|

   Teraz można napisać kod, który będzie uruchamiany po kliknięciu przycisku.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pole tekstowe po kliknięciu przycisku
 Za każdym razem, gdy użytkownik kliknie przycisk, **Hello World!** zostanie dodany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać w polu tekstowym po kliknięciu przycisku

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. W języku C# należy dodać procedurę obsługi zdarzeń dla przycisku do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby upewnić się, że komunikat **Hello World!** pojawia się w polu tekstowym po kliknięciu przycisku.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Kliknij przycisk.

3. Potwierdź, że **Hello World!** pojawia się w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje dotyczące używania przycisków i pól tekstowych w dokumentach programu Word. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Za pomocą pola kombi, aby zmienić formatowanie. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Używanie przycisków radiowych do wybierania stylów wykresu. Aby uzyskać więcej informacji, zobacz [Przewodnik: aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz też
- [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
