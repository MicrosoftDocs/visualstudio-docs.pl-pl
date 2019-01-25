---
title: 'Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki'
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
ms.openlocfilehash: 5b92c3ff12ab284ac208b012f3e03975b4eddd7c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871991"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki
  W tym instruktażu pokazano, jak utworzyć niestandardową kartę Wstążki przy użyciu **wstążki (XML)** elementu.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Dodawanie przycisków do **Add-Ins** kartę. **Add-Ins** karta jest domyślną kartę, która jest zdefiniowana w pliku XML wstążki.  
  
-   Automatyzowanie programu Microsoft Office Word za pomocą przycisków na **Add-Ins** kartę.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO programu Word. Później będzie można dostosowywać **Add-Ins** kartę tego dokumentu.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie **dodatku programu Word** projekt o nazwie **MyRibbonAddIn**.  
  
     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** plik kodu i dodaje **MyRibbonAddIn** projekt **Eksploratora rozwiązań**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>Utwórz kartę dodatków narzędzi VSTO  
 Aby utworzyć **Add-Ins** kartę, należy dodać **wstążki (XML)** elementu do projektu. W dalszej części tego przewodnika niektóre przyciski doda do tej karty.  
  
### <a name="to-create-the-add-ins-tab"></a>Aby utworzyć kartę Dodatki  
  
1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **wstążki (XML)**.  
  
3.  Zmień nazwę nowego wstążki do **MyRibbon**i kliknij przycisk **Dodaj**.  
  
     **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w projektancie. Plik XML, który nosi nazwę **MyRibbon.xml** jest także dodawane do projektu.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisAddin.cs** lub **ThisAddin.vb**, a następnie kliknij przycisk **Wyświetl kod**.  
  
5.  Dodaj następujący kod do **ThisAddin** klasy. Ten kod zastępuje `CreateRibbonExtensibilityObject` metodę i zwraca XML wstążki klasy do aplikacji pakietu Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbonAddIn** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt zostanie skompilowany bez błędów.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Dodawanie przycisków do karta dodatki  
 Celem tego dodatku narzędzi VSTO dla programów jest pozwala użytkownikom sposób, aby dodać standardowy tekst i określonej tabeli do aktywnego dokumentu. Zapewnia interfejs użytkownika, należy dodać dwa przyciski **Add-Ins** kartę, modyfikując plik XML wstążki. W dalszej części tego przewodnika będą definiować metody wywołania zwrotnego dla przycisków. Aby uzyskać więcej informacji na temat pliku XML wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>Aby dodać przyciski do karta dodatki  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbon.xml** a następnie kliknij przycisk **Otwórz**.  
  
2.  Zastąp zawartość **kartę** element z następujący kod XML. Poniższy kod XML zmienia etykiety domyślnej grupy formantu do **zawartości**, i dodaje dwa nowe przyciski z etykietami **Wstaw tekst** i **Wstaw tabelę**.  
  
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
  
## <a name="automate-the-document-by-using-the-buttons"></a>Automatyzowanie dokument, korzystając z przycisków  
 Należy dodać `onAction` metody wywołania zwrotnego dla **Wstaw tekst** i **Wstaw tabelę** przycisków, aby wykonać akcje, kiedy użytkownik kliknie je. Aby uzyskać więcej informacji na temat metody wywołania zwrotnego dla formantów wstążki, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Aby dodać metody wywołania zwrotnego dla przycisków  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyRibbon.cs** lub **MyRibbon.vb**, a następnie kliknij przycisk **Otwórz**.  
  
2.  Dodaj następujący kod na górze **MyRibbon.cs** lub **MyRibbon.vb** pliku. Ten kod tworzy alias dla <xref:Microsoft.Office.Interop.Word> przestrzeni nazw.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla **Wstaw tekst** przycisku, który dodaje ciąg do aktywnego dokumentu w bieżącej lokalizacji kursora.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Dodaj następującą metodę do `MyRibbon` klasy. Jest to metoda wywołania zwrotnego dla **Wstaw tabelę** przycisku, który dodaje tabelę do aktywnego dokumentu w bieżącej lokalizacji kursora.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Testowanie dodatku narzędzi VSTO  
 Po uruchomieniu projektu, zostanie otwarty program Word i kartę o nazwie **Add-Ins** pojawia się na Wstążce. Kliknij przycisk **Wstaw tekst** i **Wstaw tabelę** przyciski na **Add-Ins** kartę, aby przetestować kod.  
  
### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że **Add-Ins** karta jest wyświetlana na Wstążce.  
  
3.  Kliknij przycisk **Add-Ins** kartę.  
  
4.  Upewnij się, że **zawartości** grupa jest widoczna na Wstążce.  
  
5.  Kliknij przycisk **Wstaw tekst** znajdujący się w **zawartości** grupy.  
  
     Ciąg jest dodawany do dokumentu w bieżącej lokalizacji kursora.  
  
6.  Kliknij przycisk **Wstaw tabelę** znajdujący się w **zawartości** grupy.  
  
     Tabela jest dodawany do dokumentu w bieżącej lokalizacji kursora.  
  
## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej na temat sposobu dostosowywania interfejsu użytkownika pakietu Office w tych tematach:  
  
-   Dostosuj Wstążkę w innej aplikacji pakietu Office. Aby uzyskać więcej informacji na temat aplikacji, które obsługuje dostosowywania wstążki, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
-   Dostosowywanie Wstążki aplikacji pakietu Office przy użyciu projektanta wstążki. Aby uzyskać więcej informacji, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).  
  
-   Utwórz okienka akcji niestandardowych. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).  
  
-   Dostosowywanie interfejsu użytkownika programu Microsoft Office Outlook przy użyciu regionach formularzy programu Outlook. Aby uzyskać więcej informacji, zobacz [instruktażu: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [XML — Wstążka](../vsto/ribbon-xml.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
