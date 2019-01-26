---
title: Odczytywanie danych XML do zestawu danych
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: dec6b30eec5e36212ec2e1a6a16d395a698f332c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946106"
---
# <a name="read-xml-data-into-a-dataset"></a>Odczytywanie danych XML do zestawu danych

ADO.NET zapewnia proste metody do pracy z danymi XML. W tym instruktażu utworzysz aplikację Windows, która ładuje dane XML do zestawu danych. Zestaw danych jest następnie wyświetlana w <xref:System.Windows.Forms.DataGridView> kontroli. Na koniec schematu XML na podstawie zawartości pliku XML jest wyświetlany w polu tekstowym.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

W tym kroku utworzysz projekt języka Visual Basic lub Visual C#.

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **ReadingXML**, a następnie wybierz **OK**.

   **ReadingXML** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generuj plik XML do odczytu do zestawu danych

Ponieważ w tym przewodniku skupiono się na odczytywanie danych XML do zestawu danych, znajduje się zawartość pliku XML.

1. Na **projektu** menu, wybierz opcję **Dodaj nowy element**.

2. Wybierz **pliku XML**, nadaj plikowi nazwę **authors.xml**, a następnie wybierz pozycję **Dodaj**.

   Plik XML ładuje do projektanta i jest gotowy do edycji.

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

4. Na **pliku** menu, wybierz opcję **Zapisz authors.xml**.

## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika

Interfejs użytkownika dla tej aplikacji składa się z następujących czynności:

-   A <xref:System.Windows.Forms.DataGridView> formant, który wyświetla zawartość pliku XML jako dane.

-   A <xref:System.Windows.Forms.TextBox> kontrolkę wyświetlającą schematu XML w pliku XML.

-   Dwa <xref:System.Windows.Forms.Button> kontrolki.

    -   Jeden przycisk odczytuje plik XML do zestawu danych i wyświetla go w <xref:System.Windows.Forms.DataGridView> kontroli.

    -   Drugi przycisk wyodrębnia schematu z zestawu danych, a także za pośrednictwem <xref:System.IO.StringWriter> wyświetla go w <xref:System.Windows.Forms.TextBox> kontroli.

### <a name="to-add-controls-to-the-form"></a>Aby dodać formanty do formularza

1.  Otwórz `Form1` w widoku Projekt.

2.  Z **przybornika**, przeciągnij następujące kontrolki na formularzu:

    -   Jeden <xref:System.Windows.Forms.DataGridView> kontroli

    -   Jeden <xref:System.Windows.Forms.TextBox> kontroli

    -   Dwa <xref:System.Windows.Forms.Button> formantów

3.  Ustaw następujące właściwości:

    |Formant|Właściwość|Ustawienie|
    |-------------|--------------|-------------|
    |`TextBox1`|**Wielowierszowy**|`true`|
    ||**Paski przewijania**|**W pionie**|
    |`Button1`|**Nazwa**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Nazwa**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Tworzenie zestawu danych, który odbiera dane XML

W tym kroku utworzysz nowy zestaw danych o nazwie `authors`. Aby uzyskać więcej informacji na temat zestawów danych, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1.  W **Eksploratora rozwiązań**, wybierz plik źródłowy **Form1**, a następnie wybierz pozycję **Projektant widoków** znajdujący się na **Eksploratora rozwiązań** pasek narzędzi.

2.  Z [przybornik, karta dane](../ide/reference/toolbox-data-tab.md), przeciągnij **DataSet** na **Form1**.

3.  W **Dodaj zestaw danych** okno dialogowe, wybierz opcję **Nietypizowany zestaw danych**, a następnie wybierz pozycję **OK**.

     **DataSet1** jest dodawana do zasobnika składnika.

4.  W **właściwości** oknie **nazwa** i <xref:System.Data.DataSet.DataSetName%2A> właściwości`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Utwórz procedurę obsługi zdarzeń do odczytania pliku XML do zestawu danych

**Odczytu XML** przycisk odczytuje plik XML do zestawu danych. Następnie ustawia właściwości w <xref:System.Windows.Forms.DataGridView> formant, który powiązać do zestawu danych.

1.  W **Eksploratora rozwiązań**, wybierz opcję **Form1**, a następnie wybierz pozycję **Projektant widoków** znajdujący się na **Eksploratora rozwiązań** narzędzi.

2.  Wybierz **odczytu XML** przycisku.

     **Edytor kodu** o `ReadXmlButton_Click` programu obsługi zdarzeń.

3.  Wpisz następujący kod do `ReadXmlButton_Click` program obsługi zdarzeń:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  W `ReadXMLButton_Click` kod procedury obsługi zdarzeń, zmiana `filepath =` wpisu do prawidłowej ścieżki.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Tworzenie obsługi zdarzeń, aby wyświetlić schemat w polu tekstowym

**Pokaż schemat** przycisk tworzy <xref:System.IO.StringWriter> obiekt, który zostanie wypełniony kolorem schematu i jest wyświetlany w <xref:System.Windows.Forms.TextBox>kontroli.

1.  W **Eksploratora rozwiązań**, wybierz opcję **Form1**, a następnie wybierz pozycję **Projektant widoków** przycisku.

2.  Wybierz **Pokaż schemat** przycisku.

     **Edytor kodu** o `ShowSchemaButton_Click` programu obsługi zdarzeń.

3.  Wklej następujący kod do `ShowSchemaButton_Click` programu obsługi zdarzeń.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Przetestuj formularz

Teraz można przetestować formularz, aby upewnić się, że działa zgodnie z oczekiwaniami.

1.  Wybierz **F5** do uruchomienia aplikacji.

2.  Wybierz **odczytu XML** przycisku.

     Zawartość pliku XML jest wyświetlana w formancie DataGridView.

3.  Wybierz **Pokaż schemat** przycisku.

     Pole tekstowe wyświetla schematu XML w pliku XML.

## <a name="next-steps"></a>Następne kroki

W tym instruktażu dowiesz się, podstawowe informacje dotyczące odczytywania pliku XML do zestawu danych, a także do tworzenia schematów na podstawie zawartości pliku XML. Poniżej przedstawiono niektóre zadania, które użytkownik może zrobić dalej:

-   Edytowanie danych w zestawie danych i zapisu go wycofać jako XML. Aby uzyskać więcej informacji, zobacz <xref:System.Data.DataSet.WriteXml%2A>.

-   Edytowanie danych w zestawie danych, a następnie zapisać ją z bazą danych.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Narzędzia XML w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)