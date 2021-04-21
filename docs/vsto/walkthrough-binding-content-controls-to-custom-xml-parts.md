---
title: 'Przewodnik: wiązanie kontrolek zawartości z niestandardowymi częściami XML'
description: Dowiedz się, jak powiązać kontrolki zawartości w dostosowywaniu na poziomie dokumentu dla danych programu Word do formatu XML przechowywanych w dokumencie.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e4a10949f463cc769890b828ba39de30a9b4c1c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824578"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Przewodnik: wiązanie kontrolek zawartości z niestandardowymi częściami XML
  W tym przewodniku pokazano, jak powiązać kontrolki zawartości w dostosowywaniu na poziomie dokumentu dla danych xml programu Word przechowywanych w dokumencie.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Program Word umożliwia przechowywanie w dokumencie danych XML o nazwach niestandardowych części *XML.* Możesz kontrolować wyświetlanie tych danych, wiążąc kontrolki zawartości z elementami w niestandardowej części XML. W przykładowym dokumencie w tym przewodniku są wyświetlane informacje o pracownikach przechowywane w niestandardowej części XML. Po otwarciu dokumentu kontrolki zawartości wyświetlają wartości elementów XML. Wszelkie zmiany wprowadzone w tekście w kontrolkach zawartości są zapisywane w niestandardowej części XML.

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie kontrolek zawartości do dokumentu programu Word w projekcie na poziomie dokumentu w czasie projektowania.

- Tworzenie pliku danych XML i schematu XML definiującego elementy do powiązania z kontrolkami zawartości.

- Dołączanie schematu XML do dokumentu w czasie projektowania.

- Dodawanie zawartości pliku XML do niestandardowej części XML w dokumencie w czasie uruchamiania.

- Powiązanie kontrolek zawartości z elementami w niestandardowej części XML.

- Powiązanie <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> z zestawem wartości, które są zdefiniowane w schemacie XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Tworzenie nowego projektu dokumentu programu Word
 Utwórz dokument programu Word, który będzie używać w przewodniku.

### <a name="to-create-a-new-word-document-project"></a>Aby utworzyć nowy projekt dokumentu programu Word

1. Utwórz projekt dokumentu programu Word o nazwie **EmployeeControls**. Utwórz nowy dokument dla rozwiązania. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera nowy dokument programu Word w projektancie i dodaje projekt **EmployeeControls** do **Eksplorator rozwiązań**.

## <a name="add-content-controls-to-the-document"></a>Dodawanie kontrolek zawartości do dokumentu
 Utwórz tabelę zawierającą trzy różne typy kontrolek zawartości, w których użytkownik może wyświetlać lub edytować informacje o pracowniku.

### <a name="to-add-content-controls-to-the-document"></a>Aby dodać kontrolki zawartości do dokumentu

1. W dokumencie programu Word hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie na wstążce wybierz **kartę Wstawianie.**

2. W grupie **Tabele** wybierz pozycję **Tabela** i wstaw tabelę z 2 kolumnami i 3 wierszami.

3. Wpisz tekst w pierwszej kolumnie, aby był podobny do następującej kolumny:

   ||
   |-|
   |**Nazwisko pracownika**|
   |**Data zatrudnienia**|
   |**Tytuł**|

4. W drugiej kolumnie tabeli wybierz pierwszy wiersz (obok **kolumny Employee Name ).**

5. Na wstążce wybierz **kartę Deweloper.**

   > [!NOTE]
   > Jeśli karta **Deweloper** nie jest widoczna, należy ją najpierw wyświetlić. Aby uzyskać więcej informacji, [zobacz Jak: pokazywać kartę dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. W grupie **Kontrolki** wybierz przycisk **Text** ![PlainTextContentControl,](../vsto/media/plaintextcontrol.gif "Plaintextcontentcontrol") aby dodać do pierwszej <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> komórki.

7. W drugiej kolumnie tabeli wybierz drugi wiersz (obok pola **Data zatrudnienia).**

8. W grupie **Kontrolki** wybierz przycisk **s** wyboru daty ![DatePickerContentControl,](../vsto/media/datepicker.gif "Datepickercontentcontrol") aby dodać kontrolkę <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do drugiej komórki.

9. W drugiej kolumnie tabeli wybierz trzeci wiersz (obok pola **Tytuł).**

10. W grupie **Kontrolki** wybierz przycisk **Lista rozwijana** ![DropDownListContentControl,](../vsto/media/dropdownlist.gif "Dropdownlistcontentcontrol") aby dodać kontrolkę <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do ostatniej komórki.

    Jest to cały interfejs użytkownika dla tego projektu. Jeśli teraz uruchamiasz projekt, możesz wpisać tekst w pierwszym wierszu i wybrać datę w drugim wierszu. Następnym krokiem jest dołączenie danych, które mają być wyświetlane do dokumentu w pliku XML.

## <a name="create-the-xml-data-file"></a>Tworzenie pliku danych XML
 Zazwyczaj uzyskuje się dane XML do przechowywania w niestandardowej części XML ze źródła zewnętrznego, takiego jak plik lub baza danych. W tym przewodniku utworzysz plik XML zawierający dane pracowników oznaczone elementami, które zostaną powiązać z kontrolkami zawartości w dokumencie. Aby udostępnić dane w czasie uruchamiania, osadź plik XML jako zasób w zestawie dostosowywania.

#### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych

1. W menu **Project** (Projekt) wybierz pozycję **Add New Item (Dodaj nowy element).**

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W **okienku Szablony** wybierz pozycję **Plik XML.**

3. Nazwij **plikemployees.xml**, a następnie wybierz **przycisk** Dodaj.

     Plik **employees.xml** zostanie otwarty w Edytorze kodu.

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

5. W **Eksplorator rozwiązań** wybierz **employees.xml** plik.

6. W **oknie Właściwości** wybierz właściwość **Akcja kompilacji,** a następnie zmień wartość na **Zasób osadzony.**

     Ten krok osadza plik XML jako zasób w zestawie podczas kompilowania projektu. Dzięki temu można uzyskać dostęp do zawartości pliku XML w czasie uruchamiania.

## <a name="create-an-xml-schema"></a>Tworzenie schematu XML
 Jeśli chcesz powiązać kontrolkę zawartości z pojedynczym elementem w niestandardowej części XML, nie musisz używać schematu XML. Jednak aby powiązać element z zestawem wartości, należy utworzyć schemat XML, który weryfikuje utworzony wcześniej plik danych <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> XML. Schemat XML definiuje możliwe wartości `title` elementu. Powiąż <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> element z tym elementem w dalszej części tego przewodnika.

#### <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. W menu **Project (Projekt)** wybierz **pozycję Add New Item (Dodaj nowy element).**

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W **okienku Szablony** wybierz pozycję **Schemat XML.**

3. Nadaj **schematowi nazwę employees.xsd** i wybierz **przycisk** Dodaj.

     Zostanie otwarty projektant schematu.

4. W **Eksplorator rozwiązań** otwórz menu skrótów **dla pliku employees.xsd,** a następnie wybierz **pozycję Wyświetl kod.**

5. Zastąp zawartość pliku **employees.xsd** poniższym schematem.

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

6. W menu **Plik** kliknij pozycję **Zapisz** wszystko, aby zapisać zmiany w **employees.xml** i **plikach employees.xsd.**

## <a name="attach-the-xml-schema-to-the-document"></a>Dołączanie schematu XML do dokumentu
 Należy dołączyć schemat XML do dokumentu, aby powiązać z <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> prawidłowymi wartościami `title` elementu.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Aby dołączyć schemat XML do dokumentu ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. **AktywujEmployeeControls.docx** w projektancie.

2. Na wstążce wybierz **kartę Deweloper,** a następnie wybierz przycisk **Dodatki.**

3. W **oknie dialogowym** Szablony i dodatki wybierz kartę **Schemat XML,** a następnie wybierz przycisk **Dodaj** schemat.

4. Przejdź do utworzonego wcześniej schematu **employees.xsd,** który znajduje się w katalogu projektu, a następnie wybierz **przycisk** Otwórz.

5. Wybierz przycisk **OK** w **oknie dialogowym Ustawienia** schematu.

6. Wybierz przycisk **OK,** aby zamknąć okno dialogowe Szablony **i** dodatki.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Aby dołączyć schemat XML do dokumentu (Word 2010)

1. **AktywujEmployeeControls.docx** w projektancie.

2. Na wstążce wybierz **kartę Deweloper.**

3. W grupie **XML** wybierz **przycisk** Schemat.

4. W **oknie dialogowym** Szablony i dodatki wybierz kartę **Schemat XML,** a następnie wybierz przycisk **Dodaj** schemat.

5. Przejdź do utworzonego wcześniej schematu **employees.xsd,** który znajduje się w katalogu projektu, a następnie wybierz **przycisk** Otwórz.

6. Wybierz przycisk **OK** w **oknie dialogowym Ustawienia** schematu.

7. Wybierz przycisk **OK,** aby zamknąć okno dialogowe Szablony **i** dodatki.

     Zostanie **otwarte okienko zadań Struktura XML.**

8. Zamknij okienko **zadań Struktura XML.**

## <a name="add-a-custom-xml-part-to-the-document"></a>Dodawanie niestandardowej części XML do dokumentu
 Aby można było powiązać kontrolki zawartości z elementami w pliku XML, należy dodać zawartość pliku XML do nowej niestandardowej części XML w dokumencie.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Aby dodać niestandardową część XML do dokumentu

1. W **Eksplorator rozwiązań** menu skrótów **ThisDocument.cs** lub **ThisDocument.vb** otwórz menu skrótów, a następnie wybierz **pozycję Wyświetl kod.**

2. Dodaj następujące deklaracje do `ThisDocument` klasy . Ten kod deklaruje kilka obiektów, których będziesz używać do dodawania niestandardowej części XML do dokumentu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet1":::

3. Dodaj następującą metodę do `ThisDocument` klasy . Ta metoda pobiera zawartość pliku danych XML osadzonego jako zasób w zestawie i zwraca zawartość jako ciąg XML.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet3":::

4. Dodaj następującą metodę do `ThisDocument` klasy . Metoda `AddCustomXmlPart` tworzy nową niestandardową część XML zawierającą ciąg XML, który jest przekazywany do metody .

     Aby upewnić się, że niestandardowa część XML jest tworzona tylko raz, metoda tworzy niestandardową część XML tylko wtedy, gdy niestandardowa część XML o zgodnym identyfikatorze GUID nie istnieje jeszcze w dokumencie. Przy pierwszym wywołaeniu tej metody zapisuje ona wartość <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> właściwości w `employeeXMLPartID` ciągu. Wartość ciągu jest `employeeXMLPartID` utrwalana w dokumencie, ponieważ została zadeklarowana przy użyciu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atrybutu .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet4":::

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Wiązanie kontrolek zawartości z elementami w niestandardowej części XML
 Powiąż każdą kontrolkę zawartości z elementem w niestandardowej części XML przy użyciu **właściwości XMLMapping** każdej kontrolki zawartości.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Aby powiązać kontrolki zawartości z elementami w niestandardowej części XML

1. Dodaj następującą metodę do `ThisDocument` klasy . Ta metoda wiąże każdą kontrolkę zawartości z elementem w niestandardowej części XML i ustawia format wyświetlania daty <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> elementu .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet5":::

## <a name="run-your-code-when-the-document-is-opened"></a>Uruchamianie kodu po otwarciu dokumentu
 Utwórz niestandardową część XML i powiąż kontrolki niestandardowe z danymi po otwarciu dokumentu.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Aby uruchomić kod po otwarciu dokumentu

1. Dodaj następujący kod do `ThisDocument_Startup` metody `ThisDocument` klasy . Ten kod pobiera ciąg XML z pliku **employees.xml,** dodaje ciąg XML do nowej niestandardowej części XML w dokumencie i wiąże kontrolki zawartości z elementami w niestandardowej części XML.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet2":::

## <a name="test-the-project"></a>Testowanie projektu
 Po otwarciu dokumentu kontrolki zawartości wyświetlają dane z elementów w niestandardowej części XML. Możesz kliknąć przycisk , aby wybrać jedną z trzech prawidłowych wartości elementu <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> , które są zdefiniowane w pliku `title` **employees.xsd.** W przypadku edytowania danych w dowolnej kontrolce zawartości nowe wartości są zapisywane w niestandardowej części XML w dokumencie.

### <a name="to-test-the-content-controls"></a>Aby przetestować kontrolki zawartości

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Sprawdź, czy tabela w dokumencie przypomina następującą tabelę. Każdy z ciągów w drugiej kolumnie jest uzyskiwany z elementu w niestandardowej części XML w dokumencie.

    |Kolumna|Wartość|
    |-|-|
    |**Nazwisko pracownika**|**Karina Leal**|
    |**Data zatrudnienia**|**1 kwietnia 1999 r.**|
    |**Tytuł**|**Menedżer**|

3. Wybierz komórkę z prawej strony komórki **Employee Name (Imię pracownika)** i wpisz inne imię.

4. Wybierz komórkę z prawej strony komórki **Data zatrudnienia** i wybierz inną datę w selektorze dat.

5. Wybierz komórkę z prawej strony komórki **Title** i wybierz nowy element z listy rozwijanej.

6. Zapisz i zamknij dokument.

7. W Eksplorator plików otwórz folder *\bin\Debug* w lokalizacji projektu.

8. Otwórz menu skrótów dla **EmployeeControls.docx** a następnie wybierz pozycję **Zmień nazwę**.

9. Nazwij **plikEmployeeControls.docx.zip**.

     Dokument **EmployeeControls.docx** jest zapisywany w formacie Open XML. Zmiana nazwy tego dokumentu przy użyciu *rozszerzenia nazwy pliku zip* umożliwia zbadanie jego zawartości. Aby uzyskać więcej informacji na temat formatu Open XML, zobacz artykuł techniczny [Introducing the Office (2007) Open XML file formats (Wprowadzenie do formatów plików Open XML pakietu Office (2007) ).](/previous-versions/office/developer/office-2007/aa338205(v=office.12))

10. Otwórz **EmployeeControls.docx.zip** plik.

11. Otwórz folder **customXml.**

12. Otwórz menu skrótów dla **item2.xml** a następnie wybierz pozycję **Otwórz**.

     Ten plik zawiera niestandardową część XML dodaną do dokumentu.

13. Sprawdź, czy elementy , i zawierają nowe wartości wprowadzone `name` `hireDate` w `title` kontrolkach zawartości w dokumencie.

14. Zamknij **item2.xml** plik.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat używania kontrolek zawartości można znaleźć w tych tematach:

- Użyj wszystkich dostępnych kontrolek zawartości, aby utworzyć szablon. Aby uzyskać więcej informacji, [zobacz Przewodnik: tworzenie szablonu przy użyciu kontrolek zawartości.](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)

- Modyfikowanie danych w niestandardowych częściach XML podczas zamknięcia dokumentu. Następnym razem, gdy użytkownik otworzy dokument, kontrolki zawartości powiązane z elementami XML będą wyświetlać nowe dane.

- Używanie kontrolek zawartości do ochrony części dokumentu. Aby uzyskać więcej informacji, [zobacz Jak chronić części dokumentów za pomocą kontrolek zawartości.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Kontrolki zawartości](../vsto/content-controls.md)
- [How to: Add content controls to Word documents (Jak dodać kontrolki zawartości do dokumentów programu Word)](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Jak chronić części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania](../vsto/adding-controls-to-office-documents-at-run-time.md)
