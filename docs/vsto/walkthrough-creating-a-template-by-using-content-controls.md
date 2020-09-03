---
title: 'Przewodnik: Tworzenie szablonu za pomocą kontrolek zawartości'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffb7d7f9ad5453d38709802bf5e004c07bb09622
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255591"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Przewodnik: Tworzenie szablonu za pomocą kontrolek zawartości
  W tym instruktażu pokazano, jak utworzyć dostosowanie na poziomie dokumentu, które używa formantów zawartości do tworzenia zawartości strukturalnej i wielokrotnego użytku w szablonie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Program Word umożliwia utworzenie kolekcji części dokumentu wielokrotnego użytku o nazwie *bloków konstrukcyjnych*. W tym instruktażu przedstawiono sposób tworzenia dwóch tabel jako bloków konstrukcyjnych. Każda tabela zawiera kilka kontrolek zawartości, które mogą przechowywać różne typy zawartości, takie jak zwykły tekst lub daty. Jedna z tabel zawiera informacje o pracownikach, a druga — Opinie klientów.

 Po utworzeniu dokumentu z szablonu można dodać dowolną tabelę do dokumentu przy użyciu kilku <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiektów, które wyświetla dostępne bloki konstrukcyjne w szablonie.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie tabel zawierających kontrolki zawartości w szablonie programu Word w czasie projektowania.

- Wypełnianie kontrolki zawartości pola kombi i kontrolki zawartości listy rozwijanej programowo.

- Uniemożliwianie użytkownikom edytowania określonej tabeli.

- Dodawanie tabel do kolekcji bloków konstrukcyjnych szablonu.

- Tworzenie kontrolki zawartości, która wyświetla dostępne bloki konstrukcyjne w szablonie.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Utwórz nowy projekt szablonu programu Word
 Utwórz szablon programu Word, dzięki czemu użytkownicy mogą łatwo tworzyć własne kopie.

### <a name="to-create-a-new-word-template-project"></a>Aby utworzyć nowy projekt szablonu programu Word

1. Utwórz projekt szablonu programu Word o nazwie **MyBuildingBlockTemplate**. W kreatorze Utwórz nowy dokument w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera nowy szablon programu Word w Projektancie i dodaje projekt **MyBuildingBlockTemplate** do **Eksplorator rozwiązań**.

## <a name="create-the-employee-table"></a>Tworzenie tabeli Employee
 Utwórz tabelę zawierającą cztery różne typy kontrolek zawartości, w których użytkownik może wprowadzać informacje o pracowniku.

### <a name="to-create-the-employee-table"></a>Aby utworzyć tabelę Employee

1. W szablonie programu Word, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, na wstążce kliknij kartę **Wstawianie** .

2. W grupie **tabele** kliknij pozycję **tabela**, a następnie Wstaw tabelę zawierającą dwie kolumny i cztery wiersze.

3. Wpisz tekst w pierwszej kolumnie, tak aby wyglądał następująco:

   ||
   |-|
   |**Nazwa pracownika**|
   |**Data zatrudnienia**|
   |**Tytuł**|
   |**Obraz**|

4. Kliknij pierwszą komórkę w drugiej kolumnie (obok pozycji **Nazwa pracownika**).

5. Na wstążce kliknij kartę **deweloper** .

   > [!NOTE]
   > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. W grupie **formanty** kliknij przycisk **tekst** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do pierwszej komórki.

7. Kliknij drugą komórkę w drugiej kolumnie (obok pozycji **Data zatrudnienia**).

8. W grupie **formanty** kliknij przycisk **selektora dat** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.

9. Kliknij trzecią komórkę w drugiej kolumnie (obok pozycji **tytuł**).

10. W grupie **formanty** kliknij przycisk **pole kombi** ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> do trzeciej komórki.

11. Kliknij ostatnią komórkę w drugiej kolumnie (obok pozycji **obraz**).

12. W grupie **formanty** kliknij przycisk **kontrolkę zawartość obrazu** ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.PictureContentControl> do ostatniej komórki.

## <a name="create-the-customer-feedback-table"></a>Tworzenie tabeli opinii klientów
 Utwórz tabelę zawierającą trzy różne typy kontrolek zawartości, w których użytkownik może wprowadzić informacje o opiniach klientów.

### <a name="to-create-the-customer-feedback-table"></a>Aby utworzyć tabelę opinii klientów

1. W szablonie słowa kliknij wiersz po dodanej wcześniej tabeli Employee i naciśnij klawisz **Enter** , aby dodać nowy akapit.

2. Na wstążce kliknij kartę **Wstawianie** .

3. W grupie **tabele** kliknij pozycję **tabela**, a następnie Wstaw tabelę zawierającą dwie kolumny i trzy wiersze.

4. Wpisz tekst w pierwszej kolumnie, tak aby wyglądał następująco:

   ||
   |-|
   |**Nazwa klienta**|
   |**Klasyfikacja stopnia zadowolenia**|
   |**Komentarze**|

5. Kliknij w pierwszej komórce drugiej kolumny (obok pozycji **Nazwa klienta**).

6. Na wstążce kliknij kartę **deweloper** .

7. W grupie **formanty** kliknij przycisk **tekst** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do pierwszej komórki.

8. Kliknij drugą komórkę drugiej kolumny (obok **klasyfikacji satysfakcji**).

9. W grupie **formanty** kliknij przycisk **listy rozwijanej** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do drugiej komórki.

10. Kliknij w ostatniej komórce drugiej kolumny (obok pozycji **Komentarze**).

11. W grupie **formanty** kliknij przycisk **tekstu sformatowanego** ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do ostatniej komórki.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Programowo Wypełnij pole kombi i listę rozwijaną
 Kontrolki zawartości można inicjować w czasie projektowania przy użyciu okna **Właściwości** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Można je również inicjować w czasie wykonywania, co umożliwia dynamiczne ustawianie ich początkowych Stanów. W tym instruktażu należy użyć kodu do wypełnienia wpisów w <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w czasie wykonywania, aby można było zobaczyć, jak działają te obiekty.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Aby programowo zmodyfikować interfejs użytkownika formantów zawartości

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ThisDocument.cs** lub **ThisDocument. vb**, a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujący kod do `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które zostaną użyte w dalszej części tego przewodnika.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]

3. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod dodaje wpisy do <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w tabelach i ustawia tekst zastępczy, który jest wyświetlany w każdej z tych kontrolek przed ich edycją przez użytkownika.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]

## <a name="prevent-users-from-editing-the-employee-table"></a>Uniemożliwiaj użytkownikom edytowanie tabeli pracowników
 Użyj <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiektu, który został wcześniej zadeklarowany do ochrony tabeli pracowników. Po włączeniu ochrony tabeli użytkownicy mogą nadal edytować kontrolki zawartości w tabeli. Nie mogą jednak edytować tekstu w pierwszej kolumnie ani modyfikować tabeli w inny sposób, na przykład dodając lub usuwając wiersze i kolumny. Aby uzyskać więcej informacji o używaniu programu <xref:Microsoft.Office.Tools.Word.GroupContentControl> do ochrony części dokumentu, zobacz [kontrolki zawartości](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Aby uniemożliwić użytkownikom edytowanie tabeli pracowników

1. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod uniemożliwia użytkownikom edytowanie tabeli pracowników przez umieszczenie tabeli wewnątrz <xref:Microsoft.Office.Tools.Word.GroupContentControl> zadeklarowanego wcześniej obiektu.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]

## <a name="add-the-tables-to-the-building-block-collection"></a>Dodawanie tabel do kolekcji bloków konstrukcyjnych
 Dodaj tabele do kolekcji bloków konstrukcyjnych dokumentu w szablonie, aby użytkownicy mogli wstawiać tabele, które zostały utworzone do dokumentu. Aby uzyskać więcej informacji na temat bloków konstrukcyjnych dokumentów, zobacz [formanty zawartości](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Aby dodać tabele do bloków konstrukcyjnych w szablonie

1. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod dodaje nowe bloki konstrukcyjne zawierające tabele do kolekcji Microsoft. Office. Interop. Word. BuildingBlockEntries, która zawiera wszystkie bloki konstrukcyjne wielokrotnego użytku w szablonie. Nowe bloki konstrukcyjne są zdefiniowane w nowej kategorii o nazwie **Pracownik i informacje o kliencie** i są przypisane do typu bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]

2. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod usuwa tabele z szablonu. Tabele nie są już potrzebne, ponieważ zostały dodane do galerii bloków konstrukcyjnych wielokrotnego użytku w szablonie. Kod najpierw umieszcza dokument w trybie projektowania, aby można było usunąć chronioną tabelę pracowników.

     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Tworzenie kontrolki zawartości wyświetlającej bloki konstrukcyjne
 Utwórz kontrolkę zawartości, która zapewnia dostęp do bloków konstrukcyjnych (takich jak tabele), które zostały utworzone wcześniej. Użytkownicy mogą kliknąć tę kontrolkę, aby dodać tabele do dokumentu.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Aby utworzyć kontrolkę zawartości, która wyświetla bloki konstrukcyjne

1. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod inicjuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiekt, który został zadeklarowany wcześniej. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>Wyświetla wszystkie bloki konstrukcyjne, które są zdefiniowane w kategorii **Pracownik i informacje o kliencie** , które mają typ bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]

## <a name="test-the-project"></a>Testowanie projektu
 Użytkownicy mogą kliknąć kontrolki Galeria bloków konstrukcyjnych w dokumencie, aby wstawić tabelę Pracownicy lub tabelę opinii klientów. Użytkownicy mogą wpisywać lub wybierać odpowiedzi w kontrolkach zawartości w obu tabelach. Użytkownicy mogą modyfikować inne części tabeli opinii klientów, ale nie powinny być w stanie modyfikować innych części tabeli pracowników.

### <a name="to-test-the-employee-table"></a>Aby przetestować tabelę Employee

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Kliknij pozycję **Wybierz swój pierwszy blok konstrukcyjny** , aby wyświetlić kontrolkę zawartości dla pierwszej kolekcji bloków konstrukcyjnych.

3. Kliknij strzałkę listy rozwijanej obok nagłówka **Galeria niestandardowa 1** w kontrolce, a następnie wybierz pozycję **tabela pracowników**.

4. Kliknij komórkę po prawej stronie **nazwy pracownika** i wpisz nazwę.

     Sprawdź, czy do tej komórki można dodać tylko tekst. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>Umożliwia użytkownikom dodawanie tylko tekstu, a nie innych typów zawartości, takich jak grafika lub tabela.

5. Kliknij komórkę z prawej strony komórki **Data zatrudnienia** i wybierz datę w selektorze daty.

6. Kliknij w komórce po prawej stronie **tytułu** , a następnie wybierz jeden z tytułów zadań w polu kombi.

     Opcjonalnie wpisz nazwę stanowiska, którego nie ma na liście. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> umożliwia użytkownikom wybieranie z listy wpisów lub wpisywanie własnych wpisów.

7. Kliknij ikonę w komórce po prawej stronie komórki **obraz** i przejdź do obrazu, aby go wyświetlić.

8. Spróbuj dodać wiersze lub kolumny do tabeli, a następnie spróbuj usunąć wiersze i kolumny z tabeli. Sprawdź, czy nie można zmodyfikować tabeli. <xref:Microsoft.Office.Tools.Word.GroupContentControl>Uniemożliwia wprowadzanie jakichkolwiek modyfikacji.

### <a name="to-test-the-customer-feedback-table"></a>Aby przetestować tabelę opinii klientów

1. Kliknij pozycję **Wybierz drugi blok konstrukcyjny** , aby wyświetlić drugą kontrolkę zawartości galerii bloków konstrukcyjnych.

2. Kliknij strzałkę listy rozwijanej obok nagłówka **Galeria niestandardowa 1** w kontrolce, a następnie wybierz pozycję **tabela klienta**.

3. Kliknij komórkę z prawej strony komórki **Nazwa klienta** i wpisz nazwę.

4. Kliknij w komórce po prawej stronie komórki **oceny zadowolenia** i wybierz jedną z dostępnych opcji.

     Sprawdź, czy nie możesz wpisać własnego wpisu. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>Umożliwia użytkownikom tylko wybieranie z listy wpisów.

5. Kliknij w komórce po prawej stronie komórki **Komentarze** i wpisz niektóre komentarze.

     Opcjonalnie możesz dodać zawartość inną niż tekst, na przykład kompozycję lub osadzoną tabelę. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.RichTextContentControl> umożliwia użytkownikom dodawanie zawartości innej niż tekst.

6. Sprawdź, czy można dodać wiersze lub kolumny do tabeli, a także usunąć wiersze i kolumny z tabeli. Jest to możliwe, ponieważ tabela nie jest chroniona przez umieszczenie jej w <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

7. Zamknij szablon.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat korzystania z formantów zawartości można znaleźć w tym temacie:

- Powiąż formanty zawartości z fragmentami kodu XML, które są również nazwami niestandardowych części XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji, zobacz [Przewodnik: powiązywanie kontrolek zawartości z niestandardowymi częściami XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Instrukcje: ochrona części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
