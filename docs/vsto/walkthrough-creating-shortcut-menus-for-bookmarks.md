---
title: 'Przewodnik: Tworzenie menu skrótów dla zakładek'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b4b412d2e9456142c1be1af388e2803634d15c0
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "64834312"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Przewodnik: Tworzenie menu skrótów dla zakładek
  W tym instruktażu przedstawiono sposób tworzenia menu skrótów dla <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek w dostosowaniu na poziomie dokumentu dla programu Word. Gdy użytkownik kliknie prawym przyciskiem myszy tekst w zakładce, pojawi się menu skrótów i nadaje Opcje użytkownika do formatowania tekstu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- [Utwórz projekt](#BKMK_CreateProject).

- [Dodaj tekst i zakładki do dokumentu](#BKMK_addtextandbookmarks).

- [Dodaj polecenia do menu skrótów](#BKMK_AddCmndsShortMenu).

- [Sformatuj tekst w zakładce](#BKMK_formattextbkmk).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]

## <a name="create-the-project"></a><a name="BKMK_CreateProject"></a> Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word w programie Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

- Utwórz projekt dokumentu programu Word, który ma **menu skrótów Nazwa My zakładka**. W kreatorze wybierz pozycję **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **menu skrótów moje zakładki** do **Eksplorator rozwiązań**.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Dodaj tekst i zakładki do dokumentu
 Dodaj tekst do dokumentu, a następnie Dodaj dwa nakładające się zakładki.

### <a name="to-add-text-to-your-document"></a>Aby dodać tekst do dokumentu

- W dokumencie, który pojawia się w projektancie projektu, wpisz następujący tekst.

     **Jest to przykład tworzenia menu skrótów po kliknięciu prawym przyciskiem myszy tekstu w zakładce.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę zakładki do dokumentu

1. W **przyborniku**, na karcie **formanty programu Word** przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

    Zostanie wyświetlone okno dialogowe **Dodawanie kontrolki zakładki** .

2. Wybierz słowa "Tworzenie menu skrótów po kliknięciu prawym przyciskiem myszy tekstu", a następnie kliknij przycisk **OK**.

    `bookmark1` jest dodawany do dokumentu.

3. Dodaj kolejną <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do wyrazów "kliknij prawym przyciskiem myszy tekst w zakładce".

    `bookmark2` jest dodawany do dokumentu.

   > [!NOTE]
   > Słowa "kliknij prawym przyciskiem myszy tekst" znajdują się w obu `bookmark1` i `bookmark2` .

   Po dodaniu zakładki do dokumentu w czasie projektowania, <xref:Microsoft.Office.Tools.Word.Bookmark> zostanie utworzony formant. Można programować na kilka zdarzeń zakładki. Można napisać kod w <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> zdarzeniu zakładki, aby po kliknięciu prawym przyciskiem myszy tekstu w zakładce pojawiło się menu skrótów.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Dodawanie poleceń do menu skrótów
 Dodaj przyciski do menu skrótów, które pojawia się po kliknięciu prawym przyciskiem myszy dokumentu.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Aby dodać polecenia do menu skrótów

1. Dodaj element **XML wstążki** do projektu. Aby uzyskać więcej informacji, zobacz [How to: wprowadzenie dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. W **Eksplorator rozwiązań**wybierz pozycję **ThisDocument.cs** lub **ThisDocument. vb**.

3. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik klasy **ThisDocument** zostanie otwarty w edytorze kodu.

4. Dodaj następujący kod do klasy **ThisDocument** . Ten kod przesłania metodę CreateRibbonExtensibilityObject i zwraca klasę XML wstążki do aplikacji pakietu Office.

     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]

5. W **Eksplorator rozwiązań**wybierz plik XML wstążki. Domyślnie plik XML wstążki ma nazwę Ribbon1.xml.

6. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik XML wstążki zostanie otwarty w edytorze kodu.

7. W edytorze kodu Zastąp zawartość pliku XML wstążki poniższym kodem.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="BoldButton" label="Bold" onAction="ButtonClick"
               getVisible="GetVisible" />
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"
              getVisible="GetVisible"/>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

     Ten kod dodaje dwa przyciski do menu skrótów, które pojawia się po kliknięciu prawym przyciskiem myszy dokumentu.

8. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy `ThisDocument` , a następnie kliknij polecenie **Wyświetl kod**.

9. Zadeklaruj następujące zmienne i zmienną zakładki na poziomie klasy.

     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]

10. W **Eksplorator rozwiązań**wybierz plik kodu wstążki. Domyślnie plik kodu wstążki ma nazwę **Ribbon1.cs** lub **Ribbon1. vb**.

11. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik kodu wstążki zostanie otwarty w edytorze kodu.

12. W pliku kodu wstążki Dodaj następującą metodę. Jest to metoda wywołania zwrotnego dla dwóch przycisków, które zostały dodane do menu skrótów dokumentu. Ta metoda określa, czy te przyciski są wyświetlane w menu skrótów. Przyciski pogrubiania i kursywy są wyświetlane tylko po kliknięciu prawym przyciskiem myszy tekstu w zakładce.

     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Formatowanie tekstu w zakładce

### <a name="to-format-the-text-in-the-bookmark"></a>Aby sformatować tekst w zakładce

1. W pliku kodu wstążki Dodaj `ButtonClick` procedurę obsługi zdarzeń, aby zastosować formatowanie do zakładki.

     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]

2. **Eksplorator rozwiązań**, wybierz pozycję **ThisDocument.cs** lub **ThisDocument. vb**.

3. Na pasku menu wybierz polecenie **Wyświetl**  >  **kod**.

     Plik klasy **ThisDocument** zostanie otwarty w edytorze kodu.

4. Dodaj następujący kod do klasy **ThisDocument** .

     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]

    > [!NOTE]
    > Musisz napisać kod, aby obsłużyć przypadek, w którym zakładki nakładają się. W przeciwnym razie kod zostanie wywołany dla wszystkich zakładek w zaznaczeniu.

5. W języku C# należy dodać procedury obsługi zdarzeń dla kontrolek zakładek do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Przetestuj dokument, aby sprawdzić, czy elementy menu pogrubienia i kursywy pojawiają się w menu skrótów po kliknięciu prawym przyciskiem myszy tekstu w zakładce oraz że tekst jest poprawnie sformatowany.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Kliknij prawym przyciskiem myszy pierwszą zakładkę, a następnie kliknij pozycję **pogrubienie**.

3. Upewnij się, że cały tekst w `bookmark1` jest sformatowany jako pogrubiony.

4. Kliknij prawym przyciskiem myszy tekst, w którym nakładają się zakładki, a następnie kliknij **kursywę**.

5. Upewnij się, że cały tekst w `bookmark2` jest kursywą, a tylko część tekstu w tym zasobie `bookmark1` `bookmark2` jest kursywą.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Napisz kod, aby odpowiedzieć na zdarzenia formantów hosta w programie Excel. Aby uzyskać więcej informacji, zobacz [Przewodnik: program dla zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

- Użyj pola wyboru, aby zmienić formatowanie w zakładce. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz także
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
