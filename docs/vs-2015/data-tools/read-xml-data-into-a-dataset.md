---
title: Odczytywanie danych XML do zestawu danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652901"
---
# <a name="read-xml-data-into-a-dataset"></a>Odczytywanie danych XML do zestawu danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET zapewnia proste metody pracy z danymi XML. W tym instruktażu utworzysz aplikację systemu Windows, która ładuje dane XML do zestawu danych. Zestaw danych jest następnie wyświetlany w kontrolce <xref:System.Windows.Forms.DataGridView>. Na koniec schemat XML na podstawie zawartości pliku XML jest wyświetlany w polu tekstowym.

 Ten przewodnik składa się z pięciu głównych kroków:

1. Tworzenie nowego projektu

2. Tworzenie pliku XML, który ma zostać odczytany do zestawu danych

3. Tworzenie interfejsu użytkownika

4. Tworzenie zestawu danych, odczytywanie pliku XML i wyświetlanie go w kontrolce <xref:System.Windows.Forms.DataGridView>

5. Dodawanie kodu do wyświetlania schematu XML na podstawie pliku XML w kontrolce <xref:System.Windows.Forms.TextBox>

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub używanej wersji. Aby zmienić ustawienia, w menu **Narzędzia** wybierz pozycję**Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 W tym kroku utworzysz Visual Basic lub projekt wizualny C# , który zawiera ten przewodnik.

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. W menu **plik** Utwórz nowy projekt.

2. Nadaj nazwę projektowi `ReadingXML`.

3. Wybierz pozycję **aplikacja systemu Windows**, a następnie wybierz przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **ReadingXML** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generuj plik XML, który ma zostać odczytany do zestawu danych
 Ponieważ ten przewodnik koncentruje się na odczytywaniu danych XML w zestawie danych, zostanie udostępniona zawartość pliku XML.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Aby utworzyć plik XML, który zostanie odczytany do zestawu danych

1. W menu **projekt** wybierz polecenie**Dodaj nowy element**.

2. Wybierz pozycję **plik XML**, nazwij plik `authors.xml`, a następnie wybierz pozycję **Dodaj**.

     Plik XML jest ładowany do projektanta i jest gotowy do edycji.

3. Wklej następujący kod do edytora poniżej deklaracji XML:

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

4. W menu **plik** wybierz pozycję**Zapisz autorów. XML**.

## <a name="create-the-user-interface"></a>Tworzenie interfejsu użytkownika
 Interfejs użytkownika dla tej aplikacji składa się z następujących elementów:

- Kontrolka <xref:System.Windows.Forms.DataGridView>, która wyświetla zawartość pliku XML jako dane.

- Kontrolka <xref:System.Windows.Forms.TextBox>, która wyświetla schemat XML dla pliku XML.

- Dwie <xref:System.Windows.Forms.Button> kontrolki.

  - Jeden przycisk odczytuje plik XML do zestawu danych i wyświetla go w kontrolce <xref:System.Windows.Forms.DataGridView>.

  - Drugi przycisk wyodrębnia schemat z zestawu danych, a za pomocą <xref:System.IO.StringWriter> wyświetla go w kontrolce <xref:System.Windows.Forms.TextBox>.

#### <a name="to-add-controls-to-the-form"></a>Aby dodać kontrolki do formularza

1. Otwórz `Form1` w widoku projektu.

2. Z **przybornika**przeciągnij następujące kontrolki na formularz:

    - Jedna <xref:System.Windows.Forms.DataGridView> kontrolka

    - Jedna <xref:System.Windows.Forms.TextBox> kontrolka

    - Dwie <xref:System.Windows.Forms.Button> kontrolki

3. Ustaw następujące właściwości:

    |formant|Właściwość|Ustawienie|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Paski przewijania**|**Pionow**|
    |`Button1`|**Nazwa**|`ReadXmlButton`|
    ||**Tekst**|`Read XML`|
    |`Button2`|**Nazwa**|`ShowSchemaButton`|
    ||**Tekst**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Tworzenie zestawu danych thatreceives dane XML
 W tym kroku utworzysz nowy zestaw danych o nazwie `authors`. Aby uzyskać więcej informacji na temat zestawów danych, zobacz [Narzędzia DataSet w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Aby utworzyć nowy zestaw danych, który odbiera dane XML

1. W **Eksplorator rozwiązań**wybierz plik źródłowy dla **Form1**, a następnie wybierz przycisk **przeglądaj projektanta** na pasku narzędzi **Eksplorator rozwiązań** .

2. Z [przybornika, na karcie dane](../ide/reference/toolbox-data-tab.md)przeciągnij **zestaw danych** na **formularz Form1**.

3. W oknie dialogowym **Dodawanie zestawu danych** wybierz opcję **niewpisany zestaw danych**, a następnie wybierz przycisk **OK**.

     Do zasobnika składników zostanie dodany **pozycję DataSet1** .

4. W oknie **Właściwości** Ustaw **nazwę** i <xref:System.Data.DataSet.DataSetName%2A> właściwości `AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Utwórz procedurę obsługi zdarzeń, aby odczytać plik XML do zestawu danych
 Przycisk **Odczytaj XML** odczytuje plik XML do zestawu danych. Następnie ustawia właściwości kontrolki <xref:System.Windows.Forms.DataGridView>, która wiąże ją z zestawem danych.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Aby dodać kod do programu obsługi zdarzeń ReadXmlButton_Click

1. W **Eksplorator rozwiązań**wybierz pozycję **Form1**, a następnie wybierz przycisk **wyświetl projektanta** na pasku narzędzi **Eksplorator rozwiązań** .

2. Wybierz przycisk **Wczytaj plik XML** .

     **Edytor kodu** zostanie otwarty w obsłudze zdarzeń `ReadXmlButton_Click`.

3. Wpisz następujący kod do programu obsługi zdarzeń `ReadXmlButton_Click`:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. W `ReadXMLButton_Click` kodzie programu obsługi zdarzeń Zmień wpis `filepath =` na poprawną ścieżkę.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Utwórz procedurę obsługi zdarzeń, aby wyświetlić schemat w kontrolce TextBox
 Przycisk **Pokaż schemat** tworzy obiekt <xref:System.IO.StringWriter>, który jest wypełniony schematem i jest wyświetlany w <xref:System.Windows.Forms.TextBox>control.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Aby dodać kod do programu obsługi zdarzeń ShowSchemaButton_Click

1. W **Eksplorator rozwiązań**wybierz pozycję **Form1**, a następnie wybierz przycisk **Wyświetl projektanta** .

2. Wybierz przycisk **Pokaż schemat** .

     **Edytor kodu** zostanie otwarty w obsłudze zdarzeń `ShowSchemaButton_Click`.

3. Wpisz następujący kod w obsłudze zdarzeń `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

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
 [Instruktaż dotyczący danych](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [uzyskujących dostęp do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [Przygotowywanie aplikacji do odbierania](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [narzędzi XML danych w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
