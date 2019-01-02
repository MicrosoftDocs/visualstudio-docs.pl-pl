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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cf987c458fb3a79c17fc6efedb34fefd8a53179
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940558"
---
# <a name="walkthrough-create-shortcut-menus-for-bookmarks"></a>Przewodnik: Tworzenie menu skrótów dla zakładek
  W tym instruktażu przedstawiono sposób tworzenia menu skrótów dla <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek w dostosowywania poziomie dokumentu dla programu Word. Gdy użytkownik kliknie prawym przyciskiem myszy tekst w zakładki, menu skrótów pojawia się i oferuje opcje użytkownika dotyczące formatowania tekstu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- [Utwórz projekt](#BKMK_CreateProject).  
  
- [Dodawanie tekstu i zakładki w dokumencie](#BKMK_addtextandbookmarks).  
  
- [Dodawanie poleceń do menu skrótów](#BKMK_AddCmndsShortMenu).  
  
- [Formatowanie tekstu w zakładce](#BKMK_formattextbkmk).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word w programie Visual Studio.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
-   Tworzenie projektu dokumentu programu Word, który ma nazwę **Moje Menu skrótów zakładki**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **Moje Menu skrótów zakładki** projekt **Eksploratora rozwiązań**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Dodawanie tekstu i zakładki do dokumentu  
 Dodaj jakiś tekst do dokumentu, a następnie dodaj dwie nakładające się zakładek.  
  
### <a name="to-add-text-to-your-document"></a>Dodawanie tekstu do dokumentu  
  
-   W dokumencie, który pojawia się w Projektancie projektu wpisz następujący tekst.  
  
     **Jest to przykład tworzenia menu skrótów, po kliknięciu prawym przyciskiem myszy tekstu w zakładce.**  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę zakładki w dokumencie  
  
1. W **przybornika**, z **formanty programu Word** kartę, przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu.  
  
    **Dodaj kontrolkę zakładki** pojawi się okno dialogowe.  
  
2. Zaznaczanie słów "Tworzenie menu skrótów, po kliknięciu prawym przyciskiem myszy tekst", a następnie kliknij przycisk **OK**.  
  
    `bookmark1` zostanie dodany do dokumentu.  
  
3. Dodaj kolejną <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolę słowa "right-click tekstu zakładki".  
  
    `bookmark2` zostanie dodany do dokumentu.  
  
   > [!NOTE]  
   >  Wyrazy "right-click tekst" znajdują się w obu `bookmark1` i `bookmark2`.  
  
   Po dodaniu zakładki do dokumentu w czasie projektowania <xref:Microsoft.Office.Tools.Word.Bookmark> formant zostanie utworzony. Można programować względem kilka zdarzeń zakładki. Można wpisać kod w <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> zdarzeń zakładki, aby po użytkownik kliknie prawym przyciskiem myszy tekst w zakładki, zostanie wyświetlone menu skrótów.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Dodawanie poleceń do menu skrótów  
 Dodawanie przycisków do menu skrótów, które pojawia się po kliknięciu prawym przyciskiem myszy dokument.  
  
### <a name="to-add-commands-to-a-shortcut-menu"></a>Aby dodać polecenia do menu skrótów  
  
1.  Dodaj **kodu XML wstążki** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz opcję **ThisDocument.cs** lub **ThisDocument.vb**.  
  
3.  Na pasku menu wybierz **widoku** > **kodu**.  
  
     **ThisDocument** plik klas zostanie otwarty w edytorze kodu.  
  
4.  Dodaj następujący kod do **ThisDocument** klasy. Ten kod zastępuje metodę CreateRibbonExtensibilityObject i zwraca klasę kodu XML wstążki do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  W **Eksploratora rozwiązań**, wybierz plik XML wstążki. Domyślnie nosi nazwę pliku XML wstążki Ribbon1.xml.  
  
6.  Na pasku menu wybierz **widoku** > **kodu**.  
  
     Plik xml wstążki, zostanie otwarty w edytorze kodu.  
  
7.  W edytorze kodu Zastąp zawartość pliku XML wstążki z następującym kodem.  
  
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
  
     Ten kod dodaje dwa przyciski do menu skrótów, które pojawia się po kliknięciu prawym przyciskiem myszy dokument.  
  
8.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `ThisDocument`, a następnie kliknij przycisk **Wyświetl kod**.  
  
9. Zadeklaruj następujące zmienne i zmienną zakładki na poziomie klasy.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. W **Eksploratora rozwiązań**, zaznacz plik kodu wstążki. Domyślnie plik kodu wstążki o nazwie **Ribbon1.cs** lub **Ribbon1.vb**.  
  
11. Na pasku menu wybierz **widoku** > **kodu**.  
  
     Plik kodu wstążki, zostanie otwarty w edytorze kodu.  
  
12. W pliku kodu wstążki Dodaj następującą metodę. Jest to metoda wywołania zwrotnego dla dwóch przycisków, które zostały dodane do menu skrótów w dokumencie. Ta metoda określa, czy przyciski te są wyświetlane w menu skrótów. Pogrubiony i kursywę przyciski są wyświetlane tylko wtedy, gdy kliknij prawym przyciskiem myszy tekstu w zakładce.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Formatowanie tekstu w zakładce  
  
### <a name="to-format-the-text-in-the-bookmark"></a>Do formatowania tekstu w zakładce  
  
1.  W pliku kodu wstążki, Dodaj `ButtonClick` program obsługi zdarzeń, aby zastosować formatowanie do zakładki.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **Eksplorator rozwiązań**, wybierz opcję **ThisDocument.cs** lub **ThisDocument.vb**.  
  
3.  Na pasku menu wybierz **widoku** > **kodu**.  
  
     **ThisDocument** plik klas zostanie otwarty w edytorze kodu.  
  
4.  Dodaj następujący kod do **ThisDocument** klasy.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Należy napisać kod, aby obsłużyć przypadek, w którym nakładają się zakładek. W przeciwnym razie, domyślnie, kod będzie wywoływana dla wszystkie zakładki w zaznaczeniu.  
  
5.  W języku C#, należy dodać procedury obsługi zdarzeń dla kontrolek zakładek do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Przetestuj dokumencie, aby sprawdzić, czy elementy menu pogrubiony i kursywę są wyświetlane w menu skrótów, po kliknięciu prawym przyciskiem myszy tekstu zakładki i tekst jest poprawnie sformatowana.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Kliknij prawym przyciskiem myszy w pierwszej zakładce, a następnie kliknij przycisk **Bold**.  
  
3.  Upewnij się, że cały tekst w `bookmark1` jest formatowana jako pogrubiony.  
  
4.  Kliknij prawym przyciskiem myszy tekstu zakładki nakładają się, a następnie kliknij przycisk **Kursywa**.  
  
5.  Upewnij się, że cały tekst w `bookmark2` kursywa i tylko część tekstu w `bookmark1` która nakłada `bookmark2` jest pochylony.  
  
## <a name="next-steps"></a>Następne kroki  
 Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:  
  
-   Pisanie kodu w celu reagowania na zdarzenia kontrolki hosta w programie Excel. Aby uzyskać więcej informacji, zobacz [instruktażu: Program w odniesieniu do zdarzeń kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Pole wyboru umożliwia zmienianie formatowania w zakładki. Aby uzyskać więcej informacji, zobacz [instruktażu: Dokument Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)   
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [BOOKMARK, kontrolka](../vsto/bookmark-control.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
