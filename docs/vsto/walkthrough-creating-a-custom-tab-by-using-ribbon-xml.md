---
title: 'Przewodnik: tworzenie karty niestandardowej przy użyciu xml wstążki'
description: Dowiedz się, jak dodawać przyciski do karty Add-Ins i automatyzować program Microsoft Word przy użyciu wstążki (XML).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5d7992462ac3ece9782b0168feedd87577c2d0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826333"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Przewodnik: tworzenie karty niestandardowej przy użyciu xml wstążki
  W tym przewodniku pokazano, jak utworzyć niestandardową kartę wstążki przy użyciu elementu **Wstążki (XML).**

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie przycisków do **karty Dodatki.** Karta **Dodatki jest domyślną** kartą zdefiniowaną w pliku XML wstążki.

- Automatyzowanie Microsoft Office Word przy użyciu przycisków na **karcie Dodatki.**

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dodatku Word VSTO. Później dostosujemy **kartę Dodatki tego** dokumentu.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt **dodatku programu Word** o nazwie **MyRibbonAddIn**.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn.vb** i dodaje projekt **MyRibbonAddIn** do **Eksplorator rozwiązań**.

## <a name="create-the-vsto-add-ins-tab"></a>Tworzenie karty dodatki VSTO
 Aby utworzyć **kartę Dodatki,** dodaj element wstążki **(XML)** do projektu. W dalszej części tego przewodnika dodasz kilka przycisków do tej karty.

### <a name="to-create-the-add-ins-tab"></a>Aby utworzyć kartę Dodatki

1. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie** nowego elementu wybierz pozycję **Wstążka (XML)**.

3. Zmień nazwę nowej wstążki na **MyRibbon,** a następnie kliknij przycisk **Dodaj**.

     Plik **MyRibbon.cs** **lub MyRibbon.vb** zostanie otwarty w projektancie. Plik XML o nazwie **MyRibbon.xml** jest również dodawany do projektu.

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję ThisAddin.cs** lub **ThisAddin.vb,** a następnie kliknij polecenie **Wyświetl kod.**

5. Dodaj następujący kod do **klasy ThisAddin.** Ten kod zastępuje metodę i zwraca klasę XML wstążki `CreateRibbonExtensibilityObject` do aplikacji pakietu Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **projekt MyRibbonAddIn,** a następnie kliknij polecenie **Build (Kompilacja).** Sprawdź, czy projekt jest kompilowany bez błędów.

## <a name="add-buttons-to-the-add-ins-tab"></a>Dodawanie przycisków do karty Dodatki
 Celem tego dodatku VSTO jest dać użytkownikom sposób dodawania określonej tabeli i tekstu do aktywnego dokumentu. Aby zapewnić interfejs użytkownika, dodaj  dwa przyciski do karty Dodatki, modyfikując plik XML wstążki. W dalszej części tego przewodnika zdefinisz metody wywołania zwrotnego dla przycisków. Aby uzyskać więcej informacji na temat pliku XML wstążki, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Aby dodać przyciski do karty Dodatki

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyRibbon.xml** a następnie kliknij polecenie **Otwórz.**

2. Zastąp zawartość elementu **karty** następującym kodem XML. Ten kod XML zmienia etykietę domyślnej grupy kontrolek na **Content** i dodaje dwa nowe przyciski z etykietami **Wstaw** tekst i Wstaw **tabelę.**

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
 Należy dodać metody wywołania zwrotnego dla przycisków Wstaw tekst i Wstaw tabelę, `onAction` aby wykonywać akcje, gdy użytkownik kliknie  je.  Aby uzyskać więcej informacji na temat metod wywołania zwrotnego dla kontrolek wstążki, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Aby dodać metody wywołania zwrotnego dla przycisków

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję MyRibbon.cs** lub **MyRibbon.vb,** a następnie kliknij polecenie **Otwórz**.

2. Dodaj następujący kod na początku pliku **MyRibbon.cs** **lub MyRibbon.vb.** Ten kod tworzy alias dla przestrzeni <xref:Microsoft.Office.Interop.Word> nazw .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb" id="Snippet1":::

3. Dodaj następującą metodę do `MyRibbon` klasy . Jest to metoda wywołania zwrotnego przycisku **Wstaw** tekst, która dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursora.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet2":::

4. Dodaj następującą metodę do `MyRibbon` klasy . Jest to metoda wywołania zwrotnego przycisku **Wstaw** tabelę, która dodaje tabelę do aktywnego dokumentu w bieżącej lokalizacji kursora.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb" id="Snippet3":::

## <a name="testing-the-vsto-add-in"></a>Testowanie dodatku VSTO
 Po uruchomieniu projektu program Word zostanie  otwarty i na wstążce zostanie wyświetlona karta o nazwie Dodatki. Kliknij przyciski **Wstaw tekst** i **Wstaw tabelę** na karcie **Dodatki,** aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, **że karta Dodatki jest** widoczna na wstążce.

3. Kliknij **kartę Dodatki.**

4. Upewnij się, **że grupa** Zawartości jest widoczna na wstążce.

5. Kliknij przycisk **Wstaw tekst** w **grupie** Zawartość.

     Ciąg jest dodawany do dokumentu w bieżącej lokalizacji kursora.

6. Kliknij przycisk **Wstaw tabelę** w **grupie** Zawartość.

     Tabela jest dodawana do dokumentu w bieżącej lokalizacji kursora.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat dostosowywania interfejsu użytkownika pakietu Office można znaleźć w tych tematach:

- Dostosowywanie wstążki innej aplikacji pakietu Office. Aby uzyskać więcej informacji na temat aplikacji, które obsługują dostosowywanie wstążki, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

- Dostosowywanie wstążki aplikacji pakietu Office przy użyciu Projektanta wstążki. Aby uzyskać więcej informacji, zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

- Utwórz okienko akcji niestandardowych. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Dostosowywanie interfejsu użytkownika aplikacji Microsoft Office Outlook przy użyciu regionów formularzy programu Outlook. Aby uzyskać więcej informacji, [zobacz Przewodnik: projektowanie regionu formularza programu Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

## <a name="see-also"></a>Zobacz też
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
