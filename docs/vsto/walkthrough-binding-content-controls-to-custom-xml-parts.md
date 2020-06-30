---
title: 'Wskazówki: powiązywanie kontrolek zawartości z niestandardowymi częściami XML'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80488408f680530ed3c9b4094b2997e97484ce3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544446"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Wskazówki: powiązywanie kontrolek zawartości z niestandardowymi częściami XML
  W tym instruktażu pokazano, jak powiązać kontrolki zawartości w dostosowaniu na poziomie dokumentu dla programu Word na dane XML, które są przechowywane w dokumencie.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Program Word umożliwia przechowywanie danych XML o nazwach *niestandardowych części XML*w dokumencie. Można kontrolować wyświetlanie tych danych przez wiązanie kontrolek zawartości do elementów w niestandardowym składniku XML. Przykładowy dokument w tym instruktażu przedstawia informacje o pracownikach, które są przechowywane w niestandardowym składniku XML. Po otwarciu dokumentu kontrolki zawartości wyświetlają wartości elementów XML. Wszelkie zmiany wprowadzane do tekstu w kontrolkach zawartości są zapisywane w niestandardowym składniku XML.

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie kontrolek zawartości do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.

- Tworzenie pliku danych XML i schematu XML, który definiuje elementy do powiązania z kontrolkami zawartości.

- Dołączanie schematu XML do dokumentu w czasie projektowania.

- Dodawanie zawartości pliku XML do niestandardowej części XML w dokumencie w czasie wykonywania.

- Powiązywanie kontrolek zawartości z elementami w niestandardowym składniku XML.

- Powiązanie a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> z zestawem wartości, które są zdefiniowane w schemacie XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Utwórz nowy projekt dokumentu programu Word
 Utwórz dokument programu Word, który będzie używany w przewodniku.

### <a name="to-create-a-new-word-document-project"></a>Aby utworzyć nowy projekt dokumentu programu Word

1. Utwórz projekt dokumentu programu Word o nazwie **EmployeeControls**. Utwórz nowy dokument dla rozwiązania. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]otwiera nowy dokument programu Word w Projektancie i dodaje projekt **EmployeeControls** do **Eksplorator rozwiązań**.

## <a name="add-content-controls-to-the-document"></a>Dodawanie kontrolek zawartości do dokumentu
 Utwórz tabelę zawierającą trzy różne typy kontrolek zawartości, w których użytkownik może wyświetlać lub edytować informacje o pracowniku.

### <a name="to-add-content-controls-to-the-document"></a>Aby dodać kontrolki zawartości do dokumentu

1. W dokumencie programu Word, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, na wstążce wybierz kartę **Wstawianie** .

2. W grupie **tabele** wybierz **tabelę**i Wstaw tabelę z 2 kolumnami i 3 wierszami.

3. Wpisz tekst w pierwszej kolumnie, tak aby wyglądał następująco:

   ||
   |-|
   |**Nazwa pracownika**|
   |**Data zatrudnienia**|
   |**Tytuł**|

4. W drugiej kolumnie tabeli wybierz pierwszy wiersz (obok pozycji **Nazwa pracownika**).

5. Na wstążce wybierz kartę **deweloper** .

   > [!NOTE]
   > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. W grupie **formanty** wybierz przycisk **tekst** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do pierwszej komórki.

7. W drugiej kolumnie tabeli wybierz drugi wiersz (obok pozycji **Data zatrudnienia**).

8. W grupie **formanty** wybierz przycisk **selektora dat** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.

9. W drugiej kolumnie tabeli wybierz trzeci wiersz (obok pozycji **tytuł**).

10. W grupie **formanty** wybierz przycisk **listy rozwijanej** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") , aby dodać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do ostatniej komórki.

    To jest cały interfejs użytkownika dla tego projektu. Jeśli teraz uruchamiasz projekt, możesz wpisać tekst w pierwszym wierszu i wybrać datę w drugim wierszu. Następnym krokiem jest dołączenie danych, które mają być wyświetlane do dokumentu w pliku XML.

## <a name="create-the-xml-data-file"></a>Utwórz plik danych XML
 Zwykle dane XML będą przechowywane w niestandardowym składniku XML ze źródła zewnętrznego, takiego jak plik lub baza danych. W tym instruktażu utworzysz plik XML zawierający dane pracownika, oznaczone przez elementy, które zostaną powiązane z kontrolkami zawartości w dokumencie. Aby udostępnić dane w czasie wykonywania, Osadź plik XML jako zasób w zestawie dostosowywania.

#### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku **Szablony** wybierz pozycję **plik XML**.

3. Nazwij plik **employees.xml**a następnie wybierz przycisk **Dodaj** .

     Plik **employees.xml** zostanie otwarty w edytorze kodu.

4. Zastąp zawartość pliku **employees.xml** następującym tekstem.

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

5. W **Eksplorator rozwiązań**wybierz plik **employees.xml** .

6. W oknie **Właściwości** wybierz właściwość **Akcja kompilacji** , a następnie zmień wartość na **zasób osadzony**.

     Ten krok powoduje osadzenie pliku XML jako zasobu w zestawie podczas kompilowania projektu. Dzięki temu można uzyskać dostęp do zawartości pliku XML w czasie wykonywania.

## <a name="create-an-xml-schema"></a>Tworzenie schematu XML
 Jeśli chcesz powiązać formant zawartości z pojedynczym elementem w niestandardowej części XML, nie musisz używać schematu XML. Jednak aby powiązać <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> z zestawem wartości, należy utworzyć schemat XML, który sprawdza poprawność utworzonego wcześniej pliku danych XML. Schemat XML definiuje możliwe wartości dla `title` elementu. Ten element zostanie powiązany z <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> tym elementem w dalszej części tego przewodnika.

#### <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku **Szablony** wybierz pozycję **schemat XML**.

3. Nazwij schemat **Employees. xsd** i wybierz przycisk **Dodaj** .

     Zostanie otwarty projektant schematów.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **Employees. xsd**, a następnie wybierz polecenie **Wyświetl kod**.

5. Zastąp zawartość pliku **Employees. xsd** następującym schematem.

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

6. W menu **plik** kliknij polecenie **Zapisz wszystko** , aby zapisać zmiany do **employees.xml** i plików **XSD Employees** .

## <a name="attach-the-xml-schema-to-the-document"></a>Dołącz schemat XML do dokumentu
 Aby powiązać z <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> prawidłowymi wartościami elementu, należy dołączyć schemat XML do dokumentu `title` .

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Aby dołączyć schemat XML do dokumentu ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Aktywuj **EmployeeControls.docx** w projektancie.

2. Na wstążce wybierz kartę **deweloper** , a następnie wybierz przycisk **Dodatki** .

3. W oknie dialogowym **Szablony i dodatki** wybierz kartę **schemat XML** , a następnie wybierz przycisk **Dodaj schemat** .

4. Przejdź do schematu **. xsd** utworzonego wcześniej, który znajduje się w katalogu projektu, a następnie wybierz przycisk **Otwórz** .

5. Wybierz przycisk **OK** w oknie dialogowym **Ustawienia schematu** .

6. Wybierz przycisk **OK** , aby zamknąć okno dialogowe **Szablony i dodatki** .

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Aby dołączyć schemat XML do dokumentu (Word 2010)

1. Aktywuj **EmployeeControls.docx** w projektancie.

2. Na wstążce wybierz kartę **deweloper** .

3. W grupie **XML** wybierz przycisk **schemat** .

4. W oknie dialogowym **Szablony i dodatki** wybierz kartę **schemat XML** , a następnie wybierz przycisk **Dodaj schemat** .

5. Przejdź do schematu **. xsd** utworzonego wcześniej, który znajduje się w katalogu projektu, a następnie wybierz przycisk **Otwórz** .

6. Wybierz przycisk **OK** w oknie dialogowym **Ustawienia schematu** .

7. Wybierz przycisk **OK** , aby zamknąć okno dialogowe **Szablony i dodatki** .

     Zostanie otwarte okienko zadań **Struktura XML** .

8. Zamknij okienko zadań **Struktura XML** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Dodaj niestandardową część XML do dokumentu
 Aby można było powiązać kontrolki zawartości z elementami w pliku XML, należy dodać zawartość pliku XML do nowej niestandardowej części XML w dokumencie.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Aby dodać niestandardową część XML do dokumentu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **ThisDocument.cs** lub **ThisDocument. vb**, a następnie wybierz polecenie **Wyświetl kod**.

2. Dodaj następujące deklaracje do `ThisDocument` klasy. Ten kod deklaruje kilka obiektów, które zostaną użyte do dodania niestandardowej części XML do dokumentu.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda pobiera zawartość pliku danych XML, który jest osadzony jako zasób w zestawie, i zwraca zawartość jako ciąg XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. Dodaj następującą metodę do `ThisDocument` klasy. `AddCustomXmlPart`Metoda tworzy nową niestandardową część XML, która zawiera ciąg XML, który jest przesyłany do metody.

     Aby zapewnić, że niestandardowa część XML zostanie utworzona tylko raz, metoda tworzy niestandardową część XML tylko wtedy, gdy niestandardowa część XML o pasującym identyfikatorze GUID nie istnieje już w dokumencie. Gdy ta metoda jest wywoływana po raz pierwszy, zapisuje wartość <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> właściwości do `employeeXMLPartID` ciągu. Wartość `employeeXMLPartID` ciągu jest utrwalana w dokumencie, ponieważ została zadeklarowana przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Powiązywanie kontrolek zawartości z elementami w niestandardowej części XML
 Powiąż każdą kontrolkę zawartości z elementem w niestandardowej części XML przy użyciu właściwości **XMLMapping** dla każdej kontrolki zawartości.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Aby powiązać kontrolki zawartości z elementami w niestandardowej części XML

1. Dodaj następującą metodę do `ThisDocument` klasy. Ta metoda wiąże każdy formant zawartości z elementem w niestandardowej części XML i ustawia format wyświetlania daty <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> .

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>Uruchom kod, gdy dokument zostanie otwarty
 Utwórz niestandardową część XML i powiąż niestandardowe kontrolki z danymi, gdy dokument zostanie otwarty.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Aby uruchomić kod, gdy dokument zostanie otwarty

1. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy. Ten kod pobiera ciąg XML z pliku **employees.xml** , dodaje ciąg XML do nowej NIESTANDARDOWEJ części XML w dokumencie i wiąże kontrolki zawartości z elementami w niestandardowym składniku XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>Testowanie projektu
 Po otwarciu dokumentu kontrolki zawartości wyświetlają dane z elementów w niestandardowym składniku XML. Możesz kliknąć, <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Aby wybrać jedną z trzech prawidłowych wartości dla `title` elementu, które są zdefiniowane w pliku **Employees. xsd** . Jeśli edytujesz dane w dowolnej kontrolce zawartości, nowe wartości są zapisywane w niestandardowej części XML w dokumencie.

### <a name="to-test-the-content-controls"></a>Aby przetestować kontrolki zawartości

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Sprawdź, czy tabela w dokumencie jest podobna do poniższej tabeli. Każdy ciąg w drugiej kolumnie jest uzyskiwany z elementu w niestandardowej części XML w dokumencie.

    |Kolumna|Wartość|
    |-|-|
    |**Nazwa pracownika**|**Karina Leal**|
    |**Data zatrudnienia**|**1 kwietnia 1999**|
    |**Tytuł**|**Manager**|

3. Wybierz komórkę z prawej strony komórki **Nazwa pracownika** i wpisz inną nazwę.

4. Wybierz komórkę z prawej strony komórki **Data zatrudnienia** i wybierz inną datę w selektorze daty.

5. Wybierz komórkę z prawej strony **tytułu** i wybierz nowy element z listy rozwijanej.

6. Zapisz i Zamknij dokument.

7. W Eksploratorze plików otwórz folder *\bin\debug* w lokalizacji projektu.

8. Otwórz menu skrótów dla **EmployeeControls.docx** a następnie wybierz **Zmień nazwę**.

9. Nadaj plikowi nazwę **EmployeeControls.docx.zip**.

     Dokument **EmployeeControls.docx** jest zapisywany w otwartym formacie XML. Zmiana nazwy tego dokumentu z rozszerzeniem nazwy pliku *zip* pozwala na sprawdzenie zawartości dokumentu. Aby uzyskać więcej informacji na temat otwartego pliku XML, zobacz artykuł techniczny [z pakietem Open XML (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Otwórz plik **EmployeeControls.docx.zip** .

11. Otwórz folder **customXml** .

12. Otwórz menu skrótów dla **item2.xml** a następnie wybierz polecenie **Otwórz**.

     Ten plik zawiera niestandardową część XML dodaną do dokumentu.

13. Sprawdź, czy `name` `hireDate` elementy, i `title` zawierają nowe wartości wprowadzone do kontrolek zawartości w dokumencie.

14. Zamknij plik **item2.xml** .

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat używania formantów zawartości można znaleźć w następujących tematach:

- Użyj wszystkich dostępnych kontrolek zawartości, aby utworzyć szablon. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie szablonu za pomocą kontrolek zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Zmodyfikuj dane w niestandardowych częściach XML, gdy dokument jest zamknięty. Przy następnym otwarciu dokumentu, formanty zawartości powiązane z elementami XML będą wyświetlały nowe dane.

- Użyj kontrolek zawartości do ochrony części dokumentu. Aby uzyskać więcej informacji, zobacz [jak: ochrona części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Instrukcje: ochrona części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
