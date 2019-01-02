---
title: 'Przewodnik: Tworzenie szablonu za pomocą formantów zawartości'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0ad53a4e3e834959cbc37d2063a5dd2d1b0d7f6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931989"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Przewodnik: Tworzenie szablonu za pomocą formantów zawartości
  W tym instruktażu pokazano, jak utworzyć dostosowywania poziomie dokumentu, który używa kontrolek zawartości do tworzenia zawartości ze strukturą i wielokrotnego użytku w szablonie programu Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word umożliwia tworzenie kolekcji części dokumentu wielokrotnego użytku, o nazwie *bloki konstrukcyjne*. W tym instruktażu przedstawiono sposób tworzenia dwóch tabel jako bloków konstrukcyjnych. Każda tabela zawiera kilka kontrolek zawartości, które mogą pomieścić różnych typów zawartości, takiej jak zwykły tekst lub daty. Jednej z tabel, zawiera informacje dotyczące pracownika, a druga tabela opinie klientów.  
  
 Po utworzeniu dokumentu z szablonu, można dodać tabel do dokumentu za pomocą kilku <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiekty, do których wyświetlania dostępnych bloków konstrukcyjnych w szablonie.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Tworzenie tabel, które zawierają zawartość kontrolki wyraz szablonu w czasie projektowania.  
  
- Programowe wypełnianie kontrolkę zawartości pola kombi i kontrolki zawartości listy rozwijanej.  
  
- Uniemożliwianie użytkownikom edytowanie określonej tabeli.  
  
- Dodawanie tabel do kolekcji bloków konstrukcyjnych szablonu.  
  
- Tworzenie formantu zawartości, który wyświetla dostępne bloków konstrukcyjnych w szablonie.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Word.  
  
## <a name="create-a-new-word-template-project"></a>Utwórz nowy projekt szablonu programu Word  
 Utwórz szablon programu Word, dzięki czemu użytkownicy mogą łatwo tworzyć własne kopie.  
  
### <a name="to-create-a-new-word-template-project"></a>Aby utworzyć nowy projekt szablonu programu Word  
  
1.  Utwórz projekt szablonu programu Word o nazwie **MyBuildingBlockTemplate**. W kreatorze należy utworzyć nowy dokument w rozwiązaniu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zostanie otwarty nowy szablon programu Word w Projektancie i dodaje **MyBuildingBlockTemplate** projekt **Eksploratora rozwiązań**.  
  
## <a name="create-the-employee-table"></a>Tworzenie tabeli pracowników  
 Utwórz tabelę, która zawiera cztery różne typy kontrolek zawartości, w której użytkownik może wprowadzić informacje o pracownika.  
  
### <a name="to-create-the-employee-table"></a>Aby utworzyć tabelę pracownika  
  
1. W szablonie programu Word, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer na wstążce kliknij **Wstaw** kartę.  
  
2. W **tabel** grupy, kliknij przycisk **tabeli**i Wstaw tabelę z dwiema kolumnami i wierszami cztery.  
  
3. Wpisz tekst w pierwszej kolumnie tak, aby wyglądała jak następujące kolumny:  
  
   ||  
   |-|  
   |**Nazwisko pracownika**|  
   |**Data zatrudnienia**|  
   |**Tytuł**|  
   |**Obraz**|  
  
4. Kliknij pierwszą komórkę w drugiej kolumnie (obok **nazwiska pracownika**).  
  
5. Na wstążce kliknij **Developer** kartę.  
  
   > [!NOTE]  
   >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. W **kontrolki** grupy, kliknij przycisk **tekstu** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
7. Kliknij komórkę drugi w drugiej kolumnie (obok **Data zatrudnienia**).  
  
8. W **kontrolki** grupy, kliknij przycisk **selektora daty** przycisk ![DatePickerContentControl —](../vsto/media/datepicker.gif "DatePickerContentControl —") dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórce.  
  
9. Kliknij przycisk trzeciej komórce w drugiej kolumnie (obok **tytuł**).  
  
10. W **kontrolki** grupy, kliknij przycisk **pola kombi** przycisk ![comboboxcontentcontrol —](../vsto/media/combobox.gif "comboboxcontentcontrol —") dodać <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>do trzeciej komórce.  
  
11. Kliknij ostatnią komórkę w drugiej kolumnie (obok **obraz**).  
  
12. W **kontrolki** grupy, kliknij przycisk **formantu zawartości obrazu** przycisk ![PictureContentControl —](../vsto/media/pictcontentcontrol.gif "PictureContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.PictureContentControl> do ostatniej komórki.  
  
## <a name="create-the-customer-feedback-table"></a>Utwórz tabelę opinie klientów  
 Utwórz tabelę, która zawiera trzy różne typy kontrolek zawartości, w której użytkownik może wprowadzić informacje o kliencie opinii.  
  
### <a name="to-create-the-customer-feedback-table"></a>Aby utworzyć tabelę opinie klientów  
  
1. W szablonie programu Word, kliknij wiersz pod tabelą pracownika, który dodano wcześniej, a następnie naciśnij klawisz **Enter** Aby dodać nowy akapit.  
  
2. Na wstążce kliknij **Wstaw** kartę.  
  
3. W **tabel** grupy, kliknij przycisk **tabeli**i Wstaw tabelę z kolumnami i trzema wierszami.  
  
4. Wpisz tekst w pierwszej kolumnie tak, aby wyglądała jak następujące kolumny:  
  
   ||  
   |-|  
   |**Nazwa klienta**|  
   |**Ocena zadowolenia użytkowników**|  
   |**Komentarze**|  
  
5. Kliknij pierwszą komórkę drugiej kolumny (obok **nazwa klienta**).  
  
6. Na wstążce kliknij **Developer** kartę.  
  
7. W **kontrolki** grupy, kliknij przycisk **tekstu** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
8. Kliknij w drugiej komórce drugiej kolumny (obok **oceny zadowolenia**).  
  
9. W **kontrolki** grupy, kliknij przycisk **listy rozwijanej** przycisk ![DropDownListContentControl —](../vsto/media/dropdownlist.gif "DropDownListContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do drugiej komórce.  
  
10. Kliknij komórkę ostatniego drugiej kolumny (obok **komentarze**).  
  
11. W **kontrolki** grupy, kliknij przycisk **tekstu sformatowanego** przycisk ![RichTextContentControl —](../vsto/media/richtextcontrol.gif "RichTextContentControl —") dodać <xref:Microsoft.Office.Tools.Word.RichTextContentControl>do ostatniej komórki.  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Wypełnij pola kombi i listy rozwijanej programowe  
 Formanty zawartości można zainicjować w czasie projektowania, używając **właściwości** okna [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ponadto można zainicjować w czasie wykonywania, co pozwala na dynamiczne ustawianie ich początkowych stanów. W ramach tego przewodnika należy użyć kodu, wypełnij pola w <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w czasie wykonywania, aby mogli przeglądać obiekty te działania.  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Do programowego modyfikowania zawartości kontrolki interfejsu użytkownika  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.cs** lub **ThisDocument.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
2.  Dodaj następujący kod do `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które będą używane w dalszej części tego przewodnika.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod dodaje wpisy do <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> i <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> w tabelach i ustawia tekst symbolu zastępczego, który jest wyświetlane w każdym z tych kontrolek, zanim użytkownik edytuje je.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>Uniemożliwić użytkownikom edytowanie tabeli pracowników  
 Użyj <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiektu została zadeklarowana wcześniej, aby chronić tabeli pracowników. Po ochrony w tabeli, można nadal edytować formanty zawartości w tabeli. Jednak nie można edytować tekst w pierwszej kolumnie lub zmodyfikuj inne sposoby, takie jak dodawanie lub usuwanie wierszy i kolumn w tabeli. Aby uzyskać więcej informacji o sposobie używania <xref:Microsoft.Office.Tools.Word.GroupContentControl> w celu ochrony części dokumentu, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>Aby uniemożliwić użytkownikom edytowanie tabeli pracowników  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod uniemożliwia użytkownikom edytowanie tabeli pracowników, umieszczając tabeli w ramach <xref:Microsoft.Office.Tools.Word.GroupContentControl> obiektu zadeklarowanej wcześniej.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>Dodać tabele do kolekcji bloków konstrukcyjnych  
 Dodać tabele do kolekcji moduły konstrukcyjne dokumentów w szablonie, dzięki czemu użytkownicy mogą wstawić tabel, które zostały utworzone z dokumentem. Aby uzyskać więcej informacji na temat moduły konstrukcyjne dokumentów zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Aby dodać tabele do bloków konstrukcyjnych w szablonie  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod dodaje nowe bloki konstrukcyjne, które znajdują się tabele do kolekcji Microsoft.Office.Interop.Word.BuildingBlockEntries, który zawiera wszystkie wielokrotnego użytku bloków konstrukcyjnych w szablonie. Nowe bloki konstrukcyjne są definiowane w nowej kategorii o nazwie **pracowników i informacje o kliencie** i przypisywany jest typ bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod usuwa tabel z szablonu. Tabele nie są już konieczne, ponieważ mają być dodane do galerii wielokrotnego użytku bloków konstrukcyjnych w szablonie. Kod najpierw powoduje umieszczenie dokumentu w trybie projektowania, dzięki czemu można usunąć tabeli pracowników chronionych.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Utworzyć kontrolkę zawartości, która wyświetla bloki konstrukcyjne  
 Utworzyć kontrolkę zawartości, który zapewnia dostęp do bloków konstrukcyjnych (tabele), które zostały utworzone wcześniej. Użytkownicy mogą kliknąć ten formant, aby dodać tabele do dokumentu.  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Aby utworzyć kontrolkę zawartości, która wyświetla bloki konstrukcyjne  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy po kodzie dodanym w poprzednim kroku. Ten kod inicjalizuje <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> obiektu zadeklarowanej wcześniej. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Wyświetla wszystkie bloki konstrukcyjne, które są zdefiniowane w kategorii **pracowników i informacje o kliencie** , które mają typ bloku konstrukcyjnego `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>Projekt testowy  
 Użytkownicy mogą kliknąć kontrolek galerii bloku konstrukcyjnego w dokumencie, aby wstawić tabeli pracowników lub tabeli opinii klientów. Użytkownicy mogą wpisz lub wybierz odpowiedzi w formantach zawartości w obu tabelach. Użytkownicy mogą modyfikować inne części tabeli opinie klientów, ale nie należy modyfikować inne części tabeli pracowników.  
  
### <a name="to-test-the-employee-table"></a>Aby przetestować tabeli pracowników  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Kliknij przycisk **wybierz pierwszego bloku konstrukcyjnego** do wyświetlenia pierwszą kontrolkę zawartości galerii bloków konstrukcyjnych.  
  
3.  Kliknij strzałkę listy rozwijanej obok **1 Galeria niestandardowa** nagłówka w formancie, a następnie wybierz **tabeli pracowników**.  
  
4.  Kliknij w komórce po prawej stronie **nazwiska pracownika** komórki, a następnie wpisz nazwę.  
  
     Upewnij się, że do tej komórki, można dodać tylko tekst. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> Umożliwia użytkownikom dodawanie tylko tekst, nie innych typów zawartości, takiej jak grafika lub tabeli.  
  
5.  Kliknij w komórce po prawej stronie **Data zatrudnienia** komórki, a następnie wybierz datę oznaczoną pogrubioną selektora daty.  
  
6.  Kliknij w komórce po prawej stronie **tytuł** komórki, a następnie wybierz jedno z stanowiska w polu kombi.  
  
     Opcjonalnie wpisz nazwę stanowisko, który nie jest na liście. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> umożliwia użytkownikom wybranie z listy wpisów lub wpisz swoje wpisy.  
  
7.  Kliknij ikonę w komórce po prawej stronie **obraz** komórki, a następnie przejdź do obrazu, aby go wyświetlić.  
  
8.  Spróbuj dodać wiersze lub kolumny do tabeli, a następnie spróbuj usunąć wiersze i kolumny z tabeli. Upewnij się, że nie można zmodyfikować tabeli. <xref:Microsoft.Office.Tools.Word.GroupContentControl> Zapobiega przed dokonaniem jakichkolwiek modyfikacji.  
  
### <a name="to-test-the-customer-feedback-table"></a>Aby przetestować tabeli opinie klientów  
  
1.  Kliknij przycisk **Wybierz drugi bloku konstrukcyjnego** do wyświetlenia drugi formant zawartości galerii bloków konstrukcyjnych.  
  
2.  Kliknij strzałkę listy rozwijanej obok **1 Galeria niestandardowa** nagłówka w formancie, a następnie wybierz **tabeli klientów**.  
  
3.  Kliknij w komórce po prawej stronie **nazwa klienta** komórki, a następnie wpisz nazwę.  
  
4.  Kliknij w komórce po prawej stronie **oceny zadowolenia** komórki, a następnie wybierz jedną z dostępnych opcji.  
  
     Upewnij się, że nie można wpisać własny tekst. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Umożliwia użytkownikom tylko po to wybrać z listy wpisów.  
  
5.  Kliknij w komórce po prawej stronie **komentarze** komórki, a następnie wpisz niektóre komentarze.  
  
     Opcjonalnie dodaj część zawartości innego niż tekstu, takie jak grafika lub osadzonej tabeli. Jest to możliwe, ponieważ <xref:Microsoft.Office.Tools.Word.RichTextContentControl> umożliwia użytkownikom dodawanie zawartości innych niż tekst.  
  
6.  Sprawdź, można dodać wiersze lub kolumny w tabeli i że można usunąć wiersze i kolumny z tabeli. Jest to możliwe, ponieważ tabela ma nie chronione przez umieszczenie go w <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Zamknij szablon.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej na temat sposobu używania kontrolek zawartości z tego tematu:  
  
-   Powiązywanie kontrolek zawartości do elementów XML, a także o nazwie niestandardowe elementy XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji, zobacz [instruktażu: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Instrukcje: Ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
