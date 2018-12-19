---
title: 'Wskazówki: Powiązywanie kontrolek zawartości do niestandardowych części XML'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 05d7c3cc2c391eee6ceeba492cd083efd3c00015
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916754"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Wskazówki: Powiązywanie kontrolek zawartości do niestandardowych części XML
  W tym instruktażu pokazano, jak powiązać formanty zawartości w dostosowaniu na poziomie dokumentu dla programu Word z danymi XML, który znajduje się w dokumencie.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word umożliwia przechowywanie danych XML o nazwie *niestandardowe elementy XML*, w dokumencie. Wyświetlanie tych danych można kontrolować przez powiązanie kontrolek zawartości do elementów w niestandardowym elementem XML. Przykładowy dokument, w tym przewodniku Wyświetla informacje dotyczące pracowników, która jest przechowywana w niestandardowym elementem XML. Po otwarciu dokumentu, formanty zawartości umożliwia wyświetlanie wartości elementów XML. Wszelkie zmiany wprowadzone w tekście w formantach zawartości są zapisywane w niestandardowym elementem XML.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
- Dodawanie kontrolek zawartości do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.  
  
- Tworzenie pliku danych XML i schematu XML, który określa elementy, aby powiązać formanty zawartości.  
  
- Dołączanie do dokumentu schematu XML, w czasie projektowania.  
  
- Dodawanie zawartości pliku XML z niestandardowym elementem XML w dokumencie w czasie wykonywania.  
  
- Powiązanie kontrolek zawartości do elementów w niestandardowym elementem XML.  
  
- Powiązanie <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> zbiór wartości, które są zdefiniowane w schemacie XML.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Program Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Tworzenie nowego projektu dokumentu programu Word  
 W instruktażu, należy utworzyć dokument programu Word, która będzie używana.  
  
### <a name="to-create-a-new-word-document-project"></a>Aby utworzyć nowy projekt dokumentu programu Word  
  
1.  Tworzenie projektu dokumentu programu Word z nazwą **EmployeeControls**. Utwórz nowy dokument dla rozwiązania. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projekty pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zostanie otwarty nowy dokument programu Word w Projektancie i dodaje **EmployeeControls** projekt **Eksploratora rozwiązań**.  
  
## <a name="add-content-controls-to-the-document"></a>Dodawanie kontrolek zawartości do dokumentu  
 Utwórz tabelę, która zawiera trzy różne typy kontrolek zawartości, gdzie użytkownika umożliwia wyświetlenie i edytowanie informacji na temat pracownika.  
  
### <a name="to-add-content-controls-to-the-document"></a>Aby dodać formanty zawartości do dokumentu  
  
1. W dokumencie programu Word, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer na Wstążce, wybierz **Wstaw** kartę.  
  
2. W **tabel** grupy, wybierz **tabeli**i Wstaw tabelę z kolumnami 2 i 3 wiersze.  
  
3. Wpisz tekst w pierwszej kolumnie tak, aby wyglądała jak następujące kolumny:  
  
   ||  
   |-|  
   |**Nazwisko pracownika**|  
   |**Data zatrudnienia**|  
   |**Tytuł**|  
  
4. W drugiej kolumnie tabeli, wybierz pierwszy wiersz (obok **nazwiska pracownika**).  
  
5. Na Wstążce, wybierz **Developer** kartę.  
  
   > [!NOTE]  
   >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. W **kontrolki** grupy, wybierz **tekstu** przycisk ![PlainTextContentControl —](../vsto/media/plaintextcontrol.gif "PlainTextContentControl —") dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do pierwszej komórki.  
  
7. W drugiej kolumnie tabeli, wybierz drugi wiersz (obok **Data zatrudnienia**).  
  
8. W **kontrolki** grupy, wybierz **selektora daty** przycisk ![DatePickerContentControl —](../vsto/media/datepicker.gif "DatePickerContentControl —") dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórce.  
  
9. W drugiej kolumnie tabeli, wybierz trzeciego wiersza (obok **tytuł**).  
  
10. W **kontrolki** grupy, wybierz **listy rozwijanej** przycisk ![DropDownListContentControl —](../vsto/media/dropdownlist.gif "DropDownListContentControl —") do dodania <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do ostatniej komórki.  
  
    To już cały interfejs użytkownika dla tego projektu. Po uruchomieniu projektu można teraz wpisz tekst w pierwszym wierszu i wybierz datę w drugim wierszu. Następnym krokiem jest, aby dołączyć dane, które mają być wyświetlane w dokumencie w pliku XML.  
  
## <a name="create-the-xml-data-file"></a>Utwórz plik danych XML  
 Zwykle będą uzyskiwać dane XML do przechowywania w niestandardowym elementem XML z zewnętrznego źródła, takich jak plik lub bazy danych. W tym instruktażu utworzysz plik XML, który zawiera dane pracowników, oznaczony przez elementy, które zostaną powiązane z kontrolkami zawartości w dokumencie. Aby udostępnić dane w czasie wykonywania, należy osadzić pliku XML jako zasób w zestawie dostosowywania.  
  
#### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
2.  W **szablony** okienku wybierz **pliku XML**.  
  
3.  Nadaj plikowi nazwę **employees.xml**, a następnie wybierz **Dodaj** przycisku.  
  
     **Employees.xml** plik zostanie otwarty w edytorze kodu.  
  
4.  Zastąp zawartość **employees.xml** pliku z następującym tekstem.  
  
    ```xml 
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  W **Eksploratora rozwiązań**, wybierz **employees.xml** pliku.  
  
6.  W **właściwości** wybierz **Build Action** właściwości, a następnie zmień wartość na **zasób osadzony**.  
  
     W tym kroku osadza plik XML jako zasób, w zestawie, podczas kompilowania projektu. Dzięki temu można uzyskać dostęp do zawartości pliku XML w czasie wykonywania.  
  
## <a name="create-an-xml-schema"></a>Tworzenie schematu XML  
 Jeśli chcesz powiązać kontrolkę zawartości do pojedynczego elementu w niestandardowym elementem XML, nie trzeba użyć schematu XML. Jednak aby powiązać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do zestawu wartości, należy utworzyć schemat XML, który sprawdza poprawność pliku danych XML, który został utworzony wcześniej. Schemat XML definiuje możliwych wartości dla `title` elementu. Zostaną powiązane <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do tego elementu w dalszej części tego przewodnika.  
  
#### <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML  
  
1.  Na **projektu** menu, wybierz **Dodaj nowy element**.  
  
     **Dodaj nowy element** pojawi się okno dialogowe.  
  
2.  W **szablony** okienku wybierz **schematu XML**.  
  
3.  Nazwa schematu **employees.xsd** i wybierz polecenie **Dodaj** przycisku.  
  
     Zostanie otwarty projektant schematu.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **employees.xsd**, a następnie wybierz **Wyświetl kod**.  
  
5.  Zastąp zawartość **employees.xsd** pliku przy użyciu następującego schematu.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Aby zapisać zmiany w **employees.xml** i **employees.xsd** plików.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Dołącz schemat XML w dokumencie  
 Należy dołączyć schematu XML w dokumencie, aby powiązać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> na prawidłowe wartości `title` elementu.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Aby dołączyć schematu XML w dokumencie ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Aktywuj **EmployeeControls.docx** w projektancie.  
  
2.  Na Wstążce, wybierz **Developer** kartę, a następnie wybierz **Add-Ins** przycisku.  
  
3.  W **szablony i dodatki** okna dialogowego wybierz **schematu XML** kartę, a następnie wybierz **schemat Dodaj** przycisku.  
  
4.  Przejdź do **employees.xsd** schemat został utworzony wcześniej, który znajduje się w katalogu projektu, a następnie wybierz **Otwórz** przycisku.  
  
5.  Wybierz **OK** znajdujący się w **schemat ustawień** okno dialogowe.  
  
6.  Wybierz **OK** przycisk, aby zamknąć **szablony i dodatki** okno dialogowe.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Aby dołączyć schematu XML do dokumentów (program Word 2010)  
  
1.  Aktywuj **EmployeeControls.docx** w projektancie.  
  
2.  Na Wstążce, wybierz **Developer** kartę.  
  
3.  W **XML** grupy, wybierz **schematu** przycisku.  
  
4.  W **szablony i dodatki** okna dialogowego wybierz **schematu XML** kartę, a następnie wybierz **schemat Dodaj** przycisku.  
  
5.  Przejdź do **employees.xsd** schemat, który został utworzony wcześniej, który znajduje się w katalogu projektu, a następnie wybierz **Otwórz** przycisku.  
  
6.  Wybierz **OK** znajdujący się w **schemat ustawień** okno dialogowe.  
  
7.  Wybierz **OK** przycisk, aby zamknąć **szablony i dodatki** okno dialogowe.  
  
     **Struktury XML** zostanie otwarte okienko zadań.  
  
8.  Zamknij **struktury XML** okienka zadań.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Dodawanie niestandardowych części XML do dokumentu  
 Przed formanty zawartości można powiązać z elementami w pliku XML, należy dodać zawartość pliku XML, nowe niestandardowym elementem XML w dokumencie.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Aby dodać niestandardowe części XML do dokumentu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ThisDocument.cs** lub **ThisDocument.vb**, a następnie wybierz **Wyświetl kod**.  
  
2.  Dodaj następujące deklaracje na `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które będą używane do dodania z niestandardowym elementem XML w dokumencie.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda pobiera zawartość pliku danych XML, który jest osadzony jako zasób w zestaw i zwraca zawartość jako ciąg znaków XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Dodaj następującą metodę do `ThisDocument` klasy. `AddCustomXmlPart` Metoda tworzy nowy niestandardowym elementem XML, który zawiera ciąg XML, który jest przekazywany do metody.  
  
     Aby upewnić się, że niestandardowym elementem XML jest tworzony tylko jeden raz, ta metoda tworzy niestandardowy kod XML część tylko wtedy, gdy z niestandardowym elementem XML przy użyciu zgodnych identyfikator GUID już istnieje w dokumencie. Ta metoda jest wywoływana, po raz pierwszy zapisuje wartość <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> właściwość `employeeXMLPartID` ciągu. Wartość `employeeXMLPartID` ciągu są utrwalane w dokumencie, ponieważ została zadeklarowana przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Powiązywanie kontrolek zawartości do elementów w niestandardowym elementem XML  
 Należy powiązać każdy formant zawartości elementu w niestandardowym elementem XML przy użyciu **XMLMapping** właściwości każdego formantu zawartości.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Aby powiązać formanty zawartości do elementów w niestandardowym elementem XML  
  
1.  Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda wiąże każdy formant zawartości elementu w niestandardowym elementem XML i ustawia format wyświetlania daty <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Uruchomienia kodu po otwarciu dokumentu  
 Tworzenie niestandardowych części XML i powiązać formanty niestandardowe do danych, po otwarciu dokumentu.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Aby uruchomić kod po otwarciu dokumentu  
  
1.  Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod pobiera parametry XML z **employees.xml** plik, dodaje ciągu XML do nowego, niestandardowym elementem XML w dokumencie i wiąże kontrolek zawartości do elementów w niestandardowym elementem XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Projekt testowy  
 Po otwarciu dokumentu, formanty zawartości wyświetlane dane z elementów w niestandardowym elementem XML. Możesz kliknąć pozycję <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> można wybrać jedną z trzech prawidłowe wartości dla `title` element, który zdefiniowano w **employees.xsd** pliku. Jeśli edytujesz danych we wszystkich kontrolek zawartości, nowe wartości są zapisywane w niestandardowym elementem XML w dokumencie.  
  
### <a name="to-test-the-content-controls"></a>Aby przetestować formanty zawartości  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że tabela w dokumencie przypomina poniższą tabelę. Ciągi w drugiej kolumnie są uzyskiwane z elementu w niestandardowym elementem XML w dokumencie.  
  
    |||  
    |-|-|  
    |**Nazwisko pracownika**|**Karina Leal**|  
    |**Data zatrudnienia**|**1 kwietnia 1999 r.**|  
    |**Tytuł**|**Menedżer**|  
  
3.  Wybierz komórkę z prawej strony **nazwiska pracownika** komórki, a następnie wpisz inną nazwę.  
  
4.  Wybierz komórkę z prawej strony **Data zatrudnienia** komórki, a następnie wybierz inną datę w selektora daty.  
  
5.  Wybierz komórkę z prawej strony **tytuł** komórki, a następnie wybierz nowy element z listy rozwijanej.  
  
6.  Zapisz i zamknij dokument.  
  
7.  W Eksploratorze plików otwórz *\bin\Debug* folderu znajdujące się w lokalizacji projektu.  
  
8.  Otwórz menu skrótów dla **EmployeeControls.docx** , a następnie wybierz **Zmień nazwę**.  
  
9. Nadaj plikowi nazwę **EmployeeControls.docx.zip**.  
  
     **EmployeeControls.docx** dokument zostanie zapisany w formacie Open XML. Zmieniając ten dokument z *zip* rozszerzenie nazwy pliku, można sprawdzić zawartość dokumentu. Aby uzyskać więcej informacji dotyczących Open XML, zobacz artykuł techniczny [Przedstawiamy Open XML pakietu Office (2007) formaty plików](http://msdn.microsoft.com/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Otwórz **EmployeeControls.docx.zip** pliku.  
  
11. Otwórz **customXml** folderu.  
  
12. Otwórz menu skrótów dla **item2.xml** , a następnie wybierz **Otwórz**.  
  
     Ten plik zawiera niestandardowym elementem XML, który został dodany do dokumentu.  
  
13. Upewnij się, że `name`, `hireDate`, i `title` elementy zawierają nowe wartości, które zostały wprowadzone do formantów zawartości w dokumencie.  
  
14. Zamknij **item2.xml** pliku.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej na temat sposobu używania kontrolek zawartości w tych tematach:  
  
-   Wszystkie dostępne kontrolki zawartości umożliwia utworzenie szablonu. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modyfikowanie danych w niestandardowe elementy XML, gdy dokument zostanie zamknięty. Przy następnym otwarciu dokumentu, formanty zawartości, które są powiązane elementy XML będą wyświetlane nowe dane.  
  
-   Użyj kontroli zawartości w celu ochrony części dokumentu. Aby uzyskać więcej informacji, zobacz [porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Formanty zawartości](../vsto/content-controls.md)   
 [Porady: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Porady: ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  