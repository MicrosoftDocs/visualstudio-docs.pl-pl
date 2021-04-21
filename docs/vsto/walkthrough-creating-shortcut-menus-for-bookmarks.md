---
title: 'Przewodnik: tworzenie menu skrótów dla zakładek'
description: Dowiedz się, jak tworzyć menu skrótów dla kontrolek zakładki w dostosowywaniu na poziomie dokumentu dla programu Microsoft Word.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 48381d452b0c67a34581092a47896aba60e7125c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826307"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Przewodnik: tworzenie menu skrótów dla zakładek
  W tym przewodniku pokazano, jak tworzyć menu skrótów dla kontrolek w dostosowywaniu na poziomie <xref:Microsoft.Office.Tools.Word.Bookmark> dokumentu dla programu Word. Gdy użytkownik kliknie prawym przyciskiem myszy tekst w zakładce, zostanie wyświetlone menu skrótów z opcjami formatowania tekstu.

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
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word w Visual Studio.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

- Utwórz projekt dokumentu programu Word o nazwie **My Bookmark Shortcut Menu (Moje menu skrótów do zakładek).** W kreatorze wybierz **pozycję Utwórz nowy dokument.** Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otwiera nowy dokument programu Word w projektancie i dodaje projekt **Menu skrótów** do zakładek do **Eksplorator rozwiązań**.

## <a name="add-text-and-bookmarks-to-the-document"></a><a name="BKMK_addtextandbookmarks"></a> Dodawanie tekstu i zakładek do dokumentu
 Dodaj tekst do dokumentu, a następnie dodaj dwie nakładające się zakładki.

### <a name="to-add-text-to-your-document"></a>Aby dodać tekst do dokumentu

- W dokumencie wyświetlonym w projektancie projektu wpisz następujący tekst.

     **Jest to przykład tworzenia menu skrótów po kliknięciu prawym przyciskiem myszy tekstu w zakładce.**

### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę Zakładka do dokumentu

1. W **przyborniku** na karcie **Kontrolki programu Word** przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

    Zostanie **wyświetlone okno dialogowe Dodawanie kontrolki** zakładki.

2. Wybierz wyrazy "tworzenie menu skrótów po kliknięciu prawym przyciskiem myszy tekstu", a następnie kliknij przycisk **OK**.

    `bookmark1` zostanie dodany do dokumentu.

3. Dodaj kolejną <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do wyrazów "kliknij prawym przyciskiem myszy tekst w zakładce".

    `bookmark2` zostanie dodany do dokumentu.

   > [!NOTE]
   > Wyrazy "kliknij prawym przyciskiem myszy tekst" znajdują się zarówno w wyrazie `bookmark1` , jak i `bookmark2` .

   Po dodaniu zakładki do dokumentu w czasie projektowania tworzona <xref:Microsoft.Office.Tools.Word.Bookmark> jest kontrolka. Możesz zaprogramować pod względem kilku zdarzeń zakładki. Możesz napisać kod w przypadku zakładki, dzięki czemu gdy użytkownik kliknie prawym przyciskiem myszy tekst w <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> zakładce, zostanie wyświetlone menu skrótów.

## <a name="add-commands-to-a-shortcut-menu"></a><a name="BKMK_AddCmndsShortMenu"></a> Dodawanie poleceń do menu skrótów
 Dodaj przyciski do menu skrótów, które jest wyświetlane po kliknięciu dokumentu prawym przyciskiem myszy.

### <a name="to-add-commands-to-a-shortcut-menu"></a>Aby dodać polecenia do menu skrótów

1. Dodaj element **XML wstążki** do projektu. Aby uzyskać więcej informacji, [zobacz Temat Jak rozpocząć dostosowywanie wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. W **Eksplorator rozwiązań** wybierz **pozycję ThisDocument.cs** lub **ThisDocument.vb.**

3. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik **klasy ThisDocument** zostanie otwarty w Edytorze kodu.

4. Dodaj następujący kod do **klasy ThisDocument.** Ten kod zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasę XML wstążki do aplikacji pakietu Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet1":::

5. W **Eksplorator rozwiązań** wybierz plik XML wstążki. Domyślnie plik XML wstążki ma nazwę Ribbon1.xml.

6. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik XML wstążki zostanie otwarty w Edytorze kodu.

7. W Edytorze kodu zastąp zawartość pliku XML wstążki następującym kodem.

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

     Ten kod dodaje dwa przyciski do menu skrótów wyświetlanego po kliknięciu dokumentu prawym przyciskiem myszy.

8. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy `ThisDocument` pozycję , a następnie kliknij polecenie Wyświetl **kod.**

9. Zadeklaruj następujące zmienne i zmienną zakładki na poziomie klasy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet2":::

10. W **Eksplorator rozwiązań** wybierz plik kodu wstążki. Domyślnie plik kodu wstążki ma nazwę **Ribbon1.cs** lub **Ribbon1.vb.**

11. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik kodu wstążki zostanie otwarty w Edytorze kodu.

12. W pliku kodu wstążki dodaj następującą metodę. Jest to metoda wywołania zwrotnego dla dwóch przycisków dodanych do menu skrótów dokumentu. Ta metoda określa, czy te przyciski są wyświetlane w menu skrótów. Przyciski pogrubione i kursywą są wyświetlane tylko po kliknięciu prawym przyciskiem myszy tekstu w zakładce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet5":::

## <a name="format-the-text-in-the-bookmark"></a><a name="BKMK_formattextbkmk"></a> Formatowanie tekstu w zakładce

### <a name="to-format-the-text-in-the-bookmark"></a>Aby sformatować tekst w zakładce

1. W pliku kodu wstążki dodaj program obsługi `ButtonClick` zdarzeń, aby zastosować formatowanie do zakładki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb" id="Snippet6":::

2. **Eksplorator rozwiązań** wybierz pozycję **ThisDocument.cs** lub **ThisDocument.vb.**

3. Na pasku menu wybierz pozycję **Wyświetl**  >  **kod.**

     Plik **klasy ThisDocument** zostanie otwarty w Edytorze kodu.

4. Dodaj następujący kod do **klasy ThisDocument.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb" id="Snippet3":::

    > [!NOTE]
    > Musisz napisać kod, aby obsłużyć przypadek, w którym zakładki nakładają się na siebie. Jeśli tego nie zrobisz, domyślnie kod będzie wywoływany dla wszystkich zakładek w zaznaczeniu.

5. W języku C# należy dodać procedury obsługi zdarzeń dla kontrolek zakładek do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs" id="Snippet4":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Przetestuj dokument, aby sprawdzić, czy elementy menu z pogrubieniem i kursywą są wyświetlane w menu skrótów po kliknięciu prawym przyciskiem myszy tekstu w zakładce i prawidłowo sformatowanym tekście.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Kliknij prawym przyciskiem myszy pierwszą zakładkę, a następnie kliknij pozycję **Bold (Pogrubienie).**

3. Sprawdź, czy cały tekst w pliku `bookmark1` jest sformatowany jako pogrubiony.

4. Kliknij prawym przyciskiem myszy tekst, w którym zakładki nakładają się na siebie, a następnie kliknij pozycję **Kursywa.**

5. Sprawdź, czy cały tekst w programie jest kursywą i że tylko część tekstu w nakładaniu się `bookmark2` `bookmark1` jest `bookmark2` kursywa.

## <a name="next-steps"></a>Następne kroki
 Oto kilka zadań, które mogą się pojawić w następnej części:

- Napisz kod, aby reagować na zdarzenia kontrolek hosta w programie Excel. Aby uzyskać więcej informacji, [zobacz Walkthrough: Program against events of a NamedRange control (Przewodnik: programowanie względem zdarzeń kontrolki NamedRange).](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)

- Użyj pola wyboru, aby zmienić formatowanie w zakładce. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
