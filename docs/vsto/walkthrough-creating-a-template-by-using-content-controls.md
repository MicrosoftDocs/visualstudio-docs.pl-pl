---
title: 'Przewodnik: tworzenie szablonu przy użyciu kontrolek zawartości'
description: Dowiedz się, jak utworzyć dostosowanie na poziomie dokumentu, które używa kontrolek zawartości do tworzenia ustrukturyzowanej zawartości wielokrotnego użytku w szablonie programu Microsoft Word.
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7f78ca406d19461de7fa8e2a8c147b1003c9c852
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826970"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Przewodnik: tworzenie szablonu przy użyciu kontrolek zawartości
  W tym przewodniku pokazano, jak utworzyć dostosowanie na poziomie dokumentu, które używa kontrolek zawartości do tworzenia ustrukturyzowanej zawartości wielokrotnego użytku w szablonie Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Program Word umożliwia utworzenie kolekcji części dokumentów wielokrotnego użytku o nazwach *bloków konstrukcyjnych*. W tym przewodniku przedstawiono sposób tworzenia dwóch tabel jako bloków konstrukcyjnych. Każda tabela zawiera kilka kontrolek zawartości, które mogą przechowywać różne typy zawartości, takie jak zwykły tekst lub daty. Jedna z tabel zawiera informacje o pracowniku, a druga zawiera opinie klientów.

 Po utworzeniu dokumentu na podstawie szablonu można dodać do dokumentu jedną z tabel przy użyciu kilku obiektów, które wyświetlają dostępne bloki konstrukcyjne <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> w szablonie.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie tabel zawierających kontrolki zawartości w szablonie programu Word w czasie projektowania.

- Programowe wypełnianie kontrolki zawartości pola kombi i kontrolki zawartości listy rozwijanej.

- Uniemożliwianie użytkownikom edytowania określonej tabeli.

- Dodawanie tabel do kolekcji bloków budynku szablonu.

- Tworzenie kontrolki zawartości, która wyświetla dostępne bloki konstrukcyjne w szablonie.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-template-project"></a>Tworzenie nowego projektu szablonu programu Word
 Utwórz szablon programu Word, aby użytkownicy mogą łatwo tworzyć własne kopie.

### <a name="to-create-a-new-word-template-project"></a>Aby utworzyć nowy projekt szablonu programu Word

1. Utwórz projekt szablonu programu Word o nazwie **MyBuildingBlockTemplate.** W kreatorze utwórz nowy dokument w rozwiązaniu. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera nowy szablon programu Word w projektancie i dodaje projekt **MyBuildingBlockTemplate** do **Eksplorator rozwiązań**.

## <a name="create-the-employee-table"></a>Tworzenie tabeli pracowników
 Utwórz tabelę zawierającą cztery różne typy kontrolek zawartości, w których użytkownik może wprowadzać informacje o pracowniku.

### <a name="to-create-the-employee-table"></a>Aby utworzyć tabelę pracowników

1. W szablonie programu Word hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie na wstążce kliknij **kartę Wstawianie.**

2. W grupie **Tabele** kliknij pozycję **Tabela** i wstaw tabelę z dwiema kolumnami i czterema wierszami.

3. Wpisz tekst w pierwszej kolumnie, aby był podobny do następującej kolumny:

   ||
   |-|
   |**Nazwisko pracownika**|
   |**Data zatrudnienia**|
   |**Tytuł**|
   |**Obraz**|

4. Kliknij pierwszą komórkę w drugiej kolumnie (obok **pola Employee Name ).**

5. Na wstążce kliknij **kartę Deweloper.**

   > [!NOTE]
   > Jeśli karta **Deweloper** nie jest widoczna, należy ją najpierw wyświetlić. Aby uzyskać więcej informacji, [zobacz Jak: pokazywać kartę dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. W grupie **Kontrolki** kliknij przycisk **Text** ![PlainTextContentControl,](../vsto/media/plaintextcontrol.gif "Plaintextcontentcontrol") aby dodać do pierwszej <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> komórki.

7. Kliknij drugą komórkę w drugiej kolumnie (obok **pola Data zatrudnienia).**

8. W grupie **Kontrolki** kliknij przycisk **S** wyboru daty ![DatePickerContentControl,](../vsto/media/datepicker.gif "Datepickercontentcontrol") aby dodać kontrolkę <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.

9. Kliknij trzecią komórkę w drugiej kolumnie (obok pola **Tytuł).**

10. W grupie **Kontrolki** kliknij przycisk **Pole** kombi ![ComboBoxContentControl,](../vsto/media/combobox.gif "Comboboxcontentcontrol") aby dodać do <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> trzeciej komórki.

11. Kliknij ostatnią komórkę w drugiej kolumnie (obok pola **Obraz).**

12. W grupie **Kontrolki** kliknij przycisk **Kontrolka** zawartości obrazu ![PictureContentControl,](../vsto/media/pictcontentcontrol.gif "Picturecontentcontrol") aby dodać kontrolkę <xref:Microsoft.Office.Tools.Word.PictureContentControl> do ostatniej komórki.

## <a name="create-the-customer-feedback-table"></a>Tworzenie tabeli opinii klientów
 Utwórz tabelę zawierającą trzy różne typy kontrolek zawartości, w których użytkownik może wprowadzać informacje zwrotne klientów.

### <a name="to-create-the-customer-feedback-table"></a>Aby utworzyć tabelę opinii klientów

1. W szablonie programu Word kliknij wiersz po dodanej wcześniej tabeli pracowników, a następnie naciśnij klawisz **Enter,** aby dodać nowy akapit.

2. Na wstążce kliknij **kartę Wstawianie.**

3. W grupie **Tabele** kliknij pozycję **Tabela** i wstaw tabelę z dwiema kolumnami i trzema wierszami.

4. Wpisz tekst w pierwszej kolumnie, aby przypominał następującą kolumnę:

   ||
   |-|
   |**Nazwa klienta**|
   |**Ocena zadowolenia**|
   |**Komentarze**|

5. Kliknij pierwszą komórkę drugiej kolumny (obok **pola Customer Name ).**

6. Na wstążce kliknij **kartę Deweloper.**

7. W grupie **Kontrolki** kliknij przycisk **Tekst** ![PlainTextContentControl,](../vsto/media/plaintextcontrol.gif "Plaintextcontentcontrol") aby dodać kontrolkę do pierwszej <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> komórki.

8. Kliknij drugą komórkę drugiej kolumny (obok pola **Ocena zadowolenia).**

9. W grupie **Kontrolki** kliknij przycisk **Lista rozwijana** ![DropDownListContentControl,](../vsto/media/dropdownlist.gif "Dropdownlistcontentcontrol") aby dodać kontrolkę do <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> drugiej komórki.

10. Kliknij ostatnią komórkę drugiej kolumny (obok pola **Komentarze).**

11. W grupie **Kontrolki** kliknij przycisk **Tekst sformatowany** ![RichTextContentControl,](../vsto/media/richtextcontrol.gif "Richtextcontentcontrol") aby dodać kontrolkę do <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ostatniej komórki.

## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Programowe wypełnianie pola kombi i listy rozwijanej
 Kontrolki zawartości można zainicjować w czasie projektowania przy użyciu **okna Właściwości** w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Można je również zainicjować w czasie uruchamiania, co umożliwia dynamiczne ustawianie ich stanów początkowych. W tym przewodniku użyj kodu, aby wypełnić wpisy w obiektach i w czasie działania, aby zobaczyć, <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> jak działają te obiekty.

### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Aby programowo zmodyfikować interfejs użytkownika kontrolek zawartości

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument.cs** lub **ThisDocument.vb,** a następnie kliknij **polecenie Wyświetl kod.**

2. Dodaj poniższy kod do klasy `ThisDocument`. Ten kod deklaruje kilka obiektów, których użyjemy w dalszej części tego przewodnika.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet1":::

3. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy . Ten kod dodaje wpisy do elementów i w tabelach i ustawia tekst zastępczy, który jest wyświetlany w każdej z tych kontrolek, zanim <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> użytkownik je zedytuje.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet2":::

## <a name="prevent-users-from-editing-the-employee-table"></a>Uniemożliwianie użytkownikom edytowania tabeli pracowników
 Użyj <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiektu, który został zadeklarowany wcześniej, aby chronić tabelę pracowników. Po ochronie tabeli użytkownicy mogą nadal edytować kontrolki zawartości w tabeli. Nie mogą jednak edytować tekstu w pierwszej kolumnie ani modyfikować tabeli w inny sposób, na przykład dodając lub usuwając wiersze i kolumny. Aby uzyskać więcej informacji na temat sposobu używania kontrolki do ochrony części <xref:Microsoft.Office.Tools.Word.GroupContentControl> dokumentu, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

### <a name="to-prevent-users-from-editing-the-employee-table"></a>Aby uniemożliwić użytkownikom edytowanie tabeli pracowników

1. Dodaj następujący kod do metody klasy po kodzie dodanym `ThisDocument_Startup` `ThisDocument` w poprzednim kroku. Ten kod uniemożliwia użytkownikom edytowanie tabeli pracowników przez umieszczenie tabeli wewnątrz <xref:Microsoft.Office.Tools.Word.GroupContentControl> zadeklarowanego wcześniej obiektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet3":::

## <a name="add-the-tables-to-the-building-block-collection"></a>Dodawanie tabel do kolekcji bloków bloków budynku
 Dodaj tabele do kolekcji bloków konstrukcyjnych dokumentów w szablonie, aby użytkownicy mieli możliwość wstawiania utworzonych tabel do dokumentu. Aby uzyskać więcej informacji na temat bloków konstrukcyjnych dokumentów, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Aby dodać tabele do bloków konstrukcyjnych w szablonie

1. Dodaj następujący kod do metody klasy po kodzie dodanym `ThisDocument_Startup` `ThisDocument` w poprzednim kroku. Ten kod dodaje nowe bloki konstrukcyjne zawierające tabele do kolekcji Microsoft.Office.Interop.Word.BuildingBlockEntries, która zawiera wszystkie bloki konstrukcyjne wielokrotnego użytku w szablonie. Nowe bloki konstrukcyjne są zdefiniowane w nowej kategorii o nazwie **Employee (Pracownik)** i Customer Information (Informacje o kliencie) i mają przypisany typ bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet4":::

2. Dodaj następujący kod do metody klasy po kodzie dodanym `ThisDocument_Startup` `ThisDocument` w poprzednim kroku. Ten kod usuwa tabele z szablonu. Tabele nie są już potrzebne, ponieważ zostały dodane do galerii bloków konstrukcyjnych wielokrotnego użytku w szablonie. Kod najpierw umieszcza dokument w trybie projektowania, aby można było usunąć chronioną tabelę pracowników.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet5":::

## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Tworzenie kontrolki zawartości wyświetlacej bloki konstrukcyjne
 Utwórz kontrolkę zawartości, która zapewnia dostęp do utworzonych wcześniej bloków konstrukcyjnych (czyli tabel). Użytkownicy mogą kliknąć tę kontrolkę, aby dodać tabele do dokumentu.

### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Aby utworzyć kontrolkę zawartości, która wyświetla bloki konstrukcyjne

1. Dodaj następujący kod do metody klasy po kodzie dodanym `ThisDocument_Startup` `ThisDocument` w poprzednim kroku. Ten kod inicjuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> zadeklarowany wcześniej obiekt . W pliku są wyświetlane wszystkie bloki konstrukcyjne zdefiniowane w kategorii Employee (Pracownik) i Customer Information (Informacje o <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> **kliencie),** które mają typ bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-project"></a>Testowanie projektu
 Użytkownicy mogą kliknąć kontrolki galerii bloków budynku w dokumencie, aby wstawić tabelę pracowników lub tabelę opinii klientów. Użytkownicy mogą wpisywać lub wybierać odpowiedzi w kontrolkach zawartości w obu tabelach. Użytkownicy mogą modyfikować inne części tabeli opinii klientów, ale nie powinni mieć możliwości modyfikowania innych części tabeli pracowników.

### <a name="to-test-the-employee-table"></a>Aby przetestować tabelę pracowników

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Kliknij **pozycję Wybierz swój pierwszy blok blokowy,** aby wyświetlić pierwszą kontrolkę zawartości galerii bloków.

3. Kliknij strzałkę listy rozwijanej obok nagłówka **Galeria niestandardowa 1** w kontrolce, a następnie wybierz pozycję **Tabela pracowników**.

4. Kliknij komórkę z prawej strony komórki Employee Name (Nazwisko **pracownika)** i wpisz nazwę.

     Sprawdź, czy do tej komórki można dodać tylko tekst. Umożliwia <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> użytkownikom dodawanie tylko tekstu, a nie innych typów zawartości, takich jak grafiki lub tabela.

5. Kliknij komórkę z prawej strony komórki **Data zatrudnienia** i wybierz datę w selektorze dat.

6. Kliknij komórkę z prawej strony komórki **Tytuł** i wybierz jeden z tytułów zadań w polu kombi.

     Opcjonalnie wpisz nazwę stanowiska, które nie znajduje się na liście. Jest to możliwe, ponieważ umożliwia użytkownikom wybieranie z listy wpisów <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> lub wpisywanie własnych wpisów.

7. Kliknij ikonę w komórce po prawej stronie komórki **Picture** (Obraz) i przejdź do obrazu, aby go wyświetlić.

8. Spróbuj dodać wiersze lub kolumny do tabeli, a następnie spróbuj usunąć wiersze i kolumny z tabeli. Sprawdź, czy nie można zmodyfikować tabeli. Uniemożliwia <xref:Microsoft.Office.Tools.Word.GroupContentControl> wprowadzenie jakichkolwiek modyfikacji.

### <a name="to-test-the-customer-feedback-table"></a>Aby przetestować tabelę opinii klientów

1. Kliknij **pozycję Wybierz drugi blok blokowy,** aby wyświetlić drugą kontrolkę zawartości galerii bloków.

2. Kliknij strzałkę listy rozwijanej obok nagłówka **Galeria niestandardowa 1** w kontrolce, a następnie wybierz pozycję **Tabela klientów**.

3. Kliknij komórkę po prawej stronie komórki **Customer Name** (Nazwa klienta) i wpisz nazwę.

4. Kliknij komórkę po prawej stronie komórki **Ocena zadowolenia** i wybierz jedną z dostępnych opcji.

     Sprawdź, czy nie możesz wpisać własnego wpisu. Umożliwia <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> użytkownikom tylko wybieranie z listy wpisów.

5. Kliknij komórkę z prawej strony komórki **Komentarze** i wpisz kilka komentarzy.

     Opcjonalnie możesz dodać zawartość inną niż tekst, na przykład obraz lub osadzoną tabelę. Jest to możliwe, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ponieważ umożliwia użytkownikom dodawanie zawartości innej niż tekst.

6. Sprawdź, czy możesz dodać wiersze lub kolumny do tabeli oraz czy możesz usunąć wiersze i kolumny z tabeli. Jest to możliwe, ponieważ tabela nie była chroniona przez umieszczenie jej w tabeli <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

7. Zamknij szablon.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat używania kontrolek zawartości można znaleźć w tym temacie:

- Powiąż kontrolki zawartości z elementami XML, nazwami również niestandardowymi częściami XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji, zobacz [Przewodnik: wiązanie kontrolek zawartości z niestandardowymi częściami XML.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [How to: Add content controls to Word documents (Jak dodać kontrolki zawartości do dokumentów programu Word)](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Jak chronić części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania](../vsto/adding-controls-to-office-documents-at-run-time.md)
