---
title: 'Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785937"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki
  W tym instruktażu pokazano, jak utworzyć niestandardową kartę wstążki przy użyciu elementu **wstążki (XML)** .

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie przycisków do karty **Dodatki** . Karta **Dodatki** jest domyślną kartą, która jest zdefiniowana w pliku XML wstążki.

- Automatyzowanie Microsoft Office Word przy użyciu przycisków na karcie **Dodatki** .

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Word. Później zostanie dostosowana karta **Dodatki** tego dokumentu.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt **dodatku programu Word** o nazwie **MyRibbonAddIn**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn. vb** i dodaje projekt **MyRibbonAddIn** do **Eksplorator rozwiązań**.

## <a name="create-the-vsto-add-ins-tab"></a>Tworzenie karty dodatków narzędzi VSTO
 Aby utworzyć kartę **Dodatki** , Dodaj element **wstążki (XML)** do projektu. W dalszej części tego instruktażu dodasz kilka przycisków do tej karty.

### <a name="to-create-the-add-ins-tab"></a>Aby utworzyć kartę Dodatki

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (XML)**.

3. Zmień nazwę nowej wstążki **na Wstążkę, a**następnie kliknij przycisk **Dodaj**.

     Plik **MyRibbon.cs** lub **webwstążka. vb** zostanie otwarty w projektancie. Plik XML o nazwie **MyRibbon.xml** jest również dodawany do projektu.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ThisAddIn.cs** lub **ThisAddIn. vb**, a następnie kliknij polecenie **Wyświetl kod**.

5. Dodaj następujący kod do klasy **ThisAddIn** . Ten kod przesłania `CreateRibbonExtensibilityObject` metodę i zwraca klasę XML wstążki do aplikacji pakietu Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **MyRibbonAddIn** , a następnie kliknij pozycję **Kompiluj**. Upewnij się, że projekt kompiluje się bez błędów.

## <a name="add-buttons-to-the-add-ins-tab"></a>Dodawanie przycisków do karty Dodatki
 Celem tego dodatku VSTO jest nadanie użytkownikom sposobu na dodawanie tekstu standardowego i konkretnej tabeli do aktywnego dokumentu. Aby zapewnić interfejs użytkownika, Dodaj dwa przyciski do karty **Dodatki** , MODYFIKUJĄC plik XML wstążki. W dalszej części tego instruktażu określisz metody wywołania zwrotnego dla przycisków. Aby uzyskać więcej informacji na temat pliku XML wstążki, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Aby dodać przyciski do karty Dodatki

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **MyRibbon.xml** a następnie kliknij polecenie **Otwórz**.

2. Zamień zawartość elementu **Tab** na następujący kod XML. Ten kod XML zmienia etykietę domyślnej grupy formantów na **zawartość**i dodaje dwa nowe przyciski z etykietami **Wstaw tekst** i **Wstaw**.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Automatyzowanie dokumentu przy użyciu przycisków
 Należy dodać `onAction` metody wywołania zwrotnego dla przycisków **Wstaw tekst** i **Wstaw tabelę** , aby wykonać akcje po ich kliknięciu przez użytkownika. Aby uzyskać więcej informacji o metodach wywołania zwrotnego dla kontrolek wstążki, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Aby dodać metody wywołania zwrotnego dla przycisków

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyRibbon.cs** lub **wstążka. vb**, a następnie kliknij polecenie **Otwórz**.

2. Dodaj następujący kod na górze pliku **MyRibbon.cs** lub **webwstążkę. vb** . Ten kod tworzy alias dla <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla przycisku **wstawiania tekstu** , który dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursora.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla przycisku **Wstaw tabelę** , który dodaje tabelę do aktywnego dokumentu w bieżącej lokalizacji kursora.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Testowanie dodatku VSTO
 Po uruchomieniu projektu zostanie otwarty program Word, a na Wstążce pojawi się karta o nazwie **Dodatki** . Kliknij przyciski **Wstaw tekst** i **Wstaw tabelę** na karcie **Dodatki** , aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że na Wstążce jest widoczna karta **Dodatki** .

3. Kliknij kartę **Dodatki** .

4. Upewnij się, że grupa **zawartości** jest widoczna na Wstążce.

5. Kliknij przycisk **Wstaw tekst** w grupie **zawartość** .

     Do dokumentu zostanie dodany ciąg w bieżącej lokalizacji kursora.

6. Kliknij przycisk **Wstaw tabelę** w grupie **zawartości** .

     Tabela zostanie dodana do dokumentu w bieżącej lokalizacji kursora.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office można znaleźć w następujących tematach:

- Dostosuj Wstążkę innej aplikacji pakietu Office. Aby uzyskać więcej informacji o aplikacjach, które obsługują Dostosowywanie wstążki, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

- Dostosuj Wstążkę aplikacji pakietu Office przy użyciu projektanta wstążki. Aby uzyskać więcej informacji, zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

- Utwórz okienko akcji niestandardowych. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Dostosuj interfejs użytkownika programu Microsoft Office Outlook przy użyciu regionów formularzy programu Outlook. Aby uzyskać więcej informacji, zobacz [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
