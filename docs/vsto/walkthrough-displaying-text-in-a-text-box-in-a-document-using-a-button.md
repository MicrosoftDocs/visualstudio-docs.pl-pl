---
title: 'Przewodnik: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku'
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
ms.openlocfilehash: f6a9b62c62b863448bb1333b162c6706c48cd72b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071762"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Przewodnik: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku
  W tym instruktażu pokazano, jak używać przycisków i pola tekstowe w dostosowaniu na poziomie dokumentu dla programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie formantów do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.

- Wypełnianie pola tekstowego, po kliknięciu przycisku.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Utwórz projekt
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Tworzenie projektu dokument programu Word z nazwą **przycisk Moje Word**. W kreatorze Wybierz **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **przycisk Moje Word** projekt **Eksploratora rozwiązań**.

## <a name="add-controls-to-the-word-document"></a>Dodawanie formantów do dokumentów programu Word
 Kontrolek interfejsu użytkownika składają się z przycisk i pole tekstowe w dokumencie programu Word.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Sprawdź, czy dokument jest otwarty w Projektancie Visual Studio.

2. Z **wspólnych formantów** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Controls.TextBox> kontrolki do dokumentu.

   > [!NOTE]
   >  W programie Word, formanty są porzucane wiersz z tekstem domyślnym. Można zmodyfikować formantów i kształtów obiekty są wstawiane przez zmianę domyślnych na **Edytuj** karcie **opcje** okno dialogowe w programie Word.

3. Na **widoku** menu, kliknij przycisk **okno właściwości**.

4. Znajdź **TextBox1** w **właściwości** pole listy rozwijanej w oknie i zmień **nazwa** właściwości pola tekstowego **Wyświetlany_tekst**.

5. Przeciągnij **przycisk** kontroli w dokumencie i Zmień następujące właściwości.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Text**|**Wstaw tekst**|

   Teraz można napisać kod, który będzie uruchamiany po kliknięciu przycisku.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pola tekstowego, po kliknięciu przycisku
 Za każdym razem, gdy użytkownik kliknie przycisk, **Witaj, świecie!** zostanie dodany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać do pola tekstowego, po kliknięciu przycisku

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń przycisku.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. W C#, należy dodać program obsługi zdarzeń dla przycisku, aby <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby upewnić się, że komunikat **Witaj, świecie!** Po kliknięciu przycisku, zostanie wyświetlony w polu tekstowym.

### <a name="to-test-your-document"></a>Aby przetestować dokumentu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Kliknij przycisk.

3. Upewnij się, że **Hello World!** zostanie wyświetlony w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawy używania przycisków i pola tekstowe w dokumentach programu Word. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Za pomocą pola kombi, aby zmienić formatowanie. Aby uzyskać więcej informacji, zobacz [instruktażu: Dokument Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Za pomocą przycisków radiowych, aby wybrać styl wykresu. Aby uzyskać więcej informacji, zobacz [instruktażu: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz także
- [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
