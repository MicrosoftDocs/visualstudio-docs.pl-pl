---
title: Odczytywanie danych XML do zestawu danych
description: Odczytaj dane XML do zestawu danych. W tym instruktażu utworzysz aplikację systemu Windows, która ładuje dane XML do zestawu danych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9fb859d61ab31a554579f72121a18a541b2995a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858556"
---
# <a name="read-xml-data-into-a-dataset"></a>Odczytywanie danych XML do zestawu danych

ADO.NET zapewnia proste metody pracy z danymi XML. W tym instruktażu utworzysz aplikację systemu Windows, która ładuje dane XML do zestawu danych. Zestaw danych jest następnie wyświetlany w <xref:System.Windows.Forms.DataGridView> kontrolce. Na koniec schemat XML na podstawie zawartości pliku XML jest wyświetlany w polu tekstowym.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Utwórz nowy projekt **aplikacji Windows Forms** dla języka C# lub Visual Basic. Nazwij projekt **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generuj plik XML, który ma zostać odczytany do zestawu danych

Ponieważ ten przewodnik koncentruje się na odczytywaniu danych XML w zestawie danych, zostanie udostępniona zawartość pliku XML.

1. W menu **projekt** wybierz polecenie **Dodaj nowy element**.

2. Wybierz pozycję **plik XML**, nazwij plik **authors.xml**, a następnie wybierz pozycję **Dodaj**.

   Plik XML jest ładowany do projektanta i jest gotowy do edycji.

3. Wklej następujące dane XML do edytora poniżej deklaracji XML:

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. W menu **plik** wybierz polecenie **Zapisz authors.xml**.

## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika

Interfejs użytkownika dla tej aplikacji składa się z następujących elementów:

- <xref:System.Windows.Forms.DataGridView>Kontrolka, która wyświetla zawartość pliku XML jako dane.

- <xref:System.Windows.Forms.TextBox>Kontrolka, która wyświetla schemat XML dla pliku XML.

- Dwie <xref:System.Windows.Forms.Button> kontrolki.

  - Jeden przycisk odczytuje plik XML do zestawu danych i wyświetla go w <xref:System.Windows.Forms.DataGridView> kontrolce.

  - Drugi przycisk wyodrębnia schemat z zestawu danych i <xref:System.IO.StringWriter> wyświetla go w <xref:System.Windows.Forms.TextBox> kontrolce.

### <a name="to-add-controls-to-the-form"></a>Aby dodać kontrolki do formularza

1. Otwórz `Form1` w widoku projektu.

2. Z **przybornika** przeciągnij następujące kontrolki na formularz:

    - Jeden <xref:System.Windows.Forms.DataGridView> formant

    - Jeden <xref:System.Windows.Forms.TextBox> formant

    - Dwie <xref:System.Windows.Forms.Button> kontrolki

3. Ustaw następujące właściwości:

    |Kontrola|Właściwość|Ustawienie|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Paski przewijania**|**Pionowa**|
    |`Button1`|**Nazwa**|`ReadXmlButton`|
    ||**Tekst**|`Read XML`|
    |`Button2`|**Nazwa**|`ShowSchemaButton`|
    ||**Tekst**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Tworzenie zestawu danych, który odbiera dane XML

W tym kroku utworzysz nowy zestaw danych o nazwie `authors` . Aby uzyskać więcej informacji na temat zestawów danych, zobacz [Narzędzia DataSet w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. W **Eksplorator rozwiązań** wybierz plik źródłowy dla **Form1**, a następnie wybierz przycisk **przeglądaj projektanta** na pasku narzędzi **Eksplorator rozwiązań** .

2. Z [przybornika, na karcie dane](../ide/reference/toolbox-data-tab.md)przeciągnij **zestaw danych** na **formularz Form1**.

3. W oknie dialogowym **Dodawanie zestawu danych** wybierz opcję **niewpisany zestaw danych**, a następnie wybierz przycisk **OK**.

     Do zasobnika składników zostanie dodany **pozycję DataSet1** .

4. W oknie **Właściwości** Ustaw **nazwę** i <xref:System.Data.DataSet.DataSetName%2A> właściwości dla `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Utwórz procedurę obsługi zdarzeń, aby odczytać plik XML do zestawu danych

Przycisk **Odczytaj XML** odczytuje plik XML do zestawu danych. Następnie ustawia właściwości <xref:System.Windows.Forms.DataGridView> kontrolki, która wiąże ją z zestawem danych.

1. W **Eksplorator rozwiązań** wybierz pozycję **Form1**, a następnie wybierz przycisk **wyświetl projektanta** na pasku narzędzi **Eksplorator rozwiązań** .

2. Wybierz przycisk **Wczytaj plik XML** .

     **Edytor kodu** zostanie otwarty w programie `ReadXmlButton_Click` obsługi zdarzeń.

3. Wpisz następujący kod w programie `ReadXmlButton_Click` obsługi zdarzeń:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. W `ReadXMLButton_Click` kodzie programu obsługi zdarzeń Zmień `filepath =` wpis na poprawną ścieżkę.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Utwórz procedurę obsługi zdarzeń, aby wyświetlić schemat w kontrolce TextBox

Przycisk **Pokaż schemat** tworzy <xref:System.IO.StringWriter> obiekt, który jest wypełniony schematem i jest wyświetlany w <xref:System.Windows.Forms.TextBox> kontrolce.

1. W **Eksplorator rozwiązań** wybierz pozycję **Form1**, a następnie wybierz przycisk **Wyświetl projektanta** .

2. Wybierz przycisk **Pokaż schemat** .

     **Edytor kodu** zostanie otwarty w programie `ShowSchemaButton_Click` obsługi zdarzeń.

3. Wklej poniższy kod do `ShowSchemaButton_Click` programu obsługi zdarzeń.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testowanie formularza

Teraz można testować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

1. Wybierz klawisz **F5** , aby uruchomić aplikację.

2. Wybierz przycisk **Wczytaj plik XML** .

     Formant DataGridView wyświetla zawartość pliku XML.

3. Wybierz przycisk **Pokaż schemat** .

     W polu tekstowym zostanie wyświetlony schemat XML dla pliku XML.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu przedstawiono podstawowe informacje dotyczące odczytywania pliku XML do zestawu danych, a także tworzenia schematu na podstawie zawartości pliku XML. Poniżej przedstawiono kilka zadań, które można wykonać w następnej kolejności:

- Edytuj dane w zestawie danych i napisz je ponownie jako kod XML. Aby uzyskać więcej informacji, zobacz <xref:System.Data.DataSet.WriteXml%2A>.

- Edytuj dane w zestawie danych i Zapisz je w bazie danych.

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Narzędzia XML w Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
