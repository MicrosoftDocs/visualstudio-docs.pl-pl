---
title: Wyświetlanie tekstu w polu tekstowym w dokumencie przy użyciu przycisku
description: Dowiedz się, jak używać przycisków i pól tekstowych w dostosowywaniu na poziomie dokumentu dla programu Microsoft Word.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 716d0ed0b203d55932fef4d6e3e22eabf1137ded
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824201"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Przewodnik: wyświetlanie tekstu w polu tekstowym w dokumencie przy użyciu przycisku
  W tym przewodniku pokazano, jak używać przycisków i pól tekstowych w dostosowywaniu na poziomie dokumentu dla Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie kontrolek do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.

- Wypełnianie pola tekstowego po kliknięciu przycisku.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokument programu Word o nazwie **Przycisk wyrazu.** W kreatorze wybierz **pozycję Utwórz nowy dokument.**

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otwiera nowy dokument programu Word w projektancie i dodaje projekt **Przycisk** wyrazu do Eksplorator rozwiązań **.**

## <a name="add-controls-to-the-word-document"></a>Dodawanie kontrolek do dokumentu programu Word
 Kontrolki interfejsu użytkownika składają się z przycisku i pola tekstowego w dokumencie programu Word.

### <a name="to-add-a-button-and-a-text-box"></a>Aby dodać przycisk i pole tekstowe

1. Sprawdź, czy dokument jest otwarty w Visual Studio projektanta.

2. Na karcie **Typowe kontrolki** **przybornika** przeciągnij <xref:Microsoft.Office.Tools.Word.Controls.TextBox> kontrolkę do dokumentu.

   > [!NOTE]
   > W programie Word kontrolki są domyślnie porzucane w wierszu z tekstem. Sposób wstawienia kontrolek i obiektów kształtów można zmodyfikować, zmieniając wartość domyślną na karcie Edycja okna **dialogowego** Opcje w programie Word. 

3. W menu **Widok** kliknij pozycję **Okno właściwości.**

4. Znajdź **pole TextBox1** w **polu listy rozwijanej** Okno właściwości i zmień właściwość **Name** pola tekstowego na **displayText**.

5. Przeciągnij **kontrolkę Przycisk** do dokumentu i zmień następujące właściwości.

   |Właściwość|Wartość|
   |--------------|-----------|
   |**Nazwa**|**insertText**|
   |**Tekst**|**Wstaw tekst**|

   Teraz możesz napisać kod, który będzie uruchamiany po kliknięciu przycisku.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Wypełnij pole tekstowe po kliknięciu przycisku
 Za każdym razem, gdy użytkownik kliknie przycisk, **Hello world!** zostanie dodany do pola tekstowego.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Aby zapisać w polu tekstowym po kliknięciu przycisku

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument**, a następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet7":::

3. W języku C# należy dodać program obsługi zdarzeń dla przycisku do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet8":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby upewnić się, że komunikat **Hello world!** w polu tekstowym po kliknięciu przycisku.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Kliknij przycisk .

3. Potwierdź, **że Hello world!** w polu tekstowym.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy używania przycisków i pól tekstowych w dokumentach programu Word. Oto kilka zadań, które mogą pojawić się w następnej części:

- Zmiana formatowania przy użyciu pola kombi. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

- Używanie przycisków radiowych do wybierania stylów wykresu. Aby uzyskać więcej informacji, zobacz [Przewodnik: aktualizowanie wykresu w dokumencie przy użyciu przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz też
- [Windows Forms kontroli w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](../vsto/office-development-samples-and-walkthroughs.md)
- [Jak dodać kontrolki Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
