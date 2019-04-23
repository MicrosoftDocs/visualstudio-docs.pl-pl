---
title: 'Przewodnik: Projektowanie regionów formularzy programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6ad8a11e736595912b1b6c8757bd75dca1e53e6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097430"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Przewodnik: Projektowanie regionów formularzy programu Outlook
  Regiony formularza niestandardowego rozszerzenie standardowych lub niestandardowych formularzy programu Microsoft Office Outlook. W tym przewodniku projektujesz region formularza niestandardowego, który jest wyświetlany jako nową stronę w oknie Inspektora, skontaktuj się z elementu. Ten region formularza jest wyświetlenie mapy każdego adresu, który znajduje się do kontaktu, wysyłając informacje o adresach do witryny Windows Live lokalnego wyszukiwania w przeglądarce. Aby uzyskać informacji na temat regionów formularzy, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie nowego projektu dodatku narzędzi VSTO dla programu Outlook.

- Dodawanie regionu formularza do projektu dodatku narzędzi VSTO dla programów.

- Projektowanie układu regionu formularza.

- Dostosowywanie zachowania regionu formularza.

- Testowanie region formularza programu Outlook.

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] lub nowszej.

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") wersja wideo tego tematu, zobacz [wideo jak: Projektowanie regionów formularzy programu Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Utwórz nowy projekt dodatku narzędzi VSTO dla programu Outlook
 Najpierw należy utworzyć podstawowy projekt dodatku narzędzi VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO dla programu Outlook

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt dodatku narzędzi VSTO dla programu Outlook o nazwie **MapItAddIn**.

2. W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.

3. Zapisz projekt do dowolnego katalogu.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Dodawanie regionu formularza w projekcie dodatku narzędzi VSTO dla programu Outlook
 Rozwiązanie dodatku narzędzi VSTO dla programu Outlook może zawierać jeden lub więcej elementów regionu formularza programu Outlook. Dodaj element regionu formularza do projektu przy użyciu **nowy Region formularza programu Outlook** kreatora.

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aby dodać regionu formularza do projektu dodatku narzędzi VSTO dla programu Outlook

1. W **Eksploratora rozwiązań**, wybierz opcję **MapItAddIn** projektu.

2. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

3. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Region formularza programu Outlook**, nadaj plikowi nazwę **MapIt**, a następnie kliknij przycisk **Dodaj**.

     **Regionu formularza NewOutlook** uruchamiany jest Kreator.

4. Na **wybierz sposób tworzenia regionu formularza** kliknij **projektowania nowy region formularza**, a następnie kliknij przycisk **dalej**.

5. Na **wybierz typ regionu formularza chcesz utworzyć** kliknij **oddzielnych**, a następnie kliknij przycisk **dalej**.

     A *oddzielnych* regionu formularza dodaje nową stronę do formularza programu Outlook. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

6. Na **tekst opisu i wybierz preferencje wyświetlania** wpisz **mapy go** w **nazwa** pole.

     Nazwa ta pojawia się na Wstążce okna inspektora po otwarciu elementu kontaktu.

7. Wybierz **inspektorzy w trybie redagowania** i **inspektorzy w trybie do odczytu**, a następnie kliknij przycisk **dalej**.

8. Na **Określ klasy wiadomości, które będzie wyświetlany ten region formularza** strony, wyczyść **wiadomość E-mail**, wybierz opcję **skontaktuj się z pomocą**, a następnie kliknij przycisk **Zakończ**.

     A *MapIt.cs* lub *MapIt.vb* plik zostanie dodany do projektu.

## <a name="design-the-layout-of-the-form-region"></a>Projektowanie układu regionu formularza
 Wizualne Tworzenie regionów formularzy przy użyciu *projektanta regionów formularza*. Możesz przeciągnąć zarządzane formanty do powierzchni projektanta regionów formularza. Za pomocą projektanta i **właściwości** okna, aby dostosować formant układ i wygląd.

### <a name="to-design-the-layout-of-the-form-region"></a>Aby zaprojektować układ regionu formularza

1. W **Eksploratora rozwiązań**, rozwiń węzeł **MapItAddIn** projektu, a następnie kliknij dwukrotnie *MapIt.cs* lub *MapIt.vb* otworzyć regionu formularza Projektant.

2. Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij przycisk **właściwości**.

3. W **właściwości** oknie **rozmiar** do **664, 469**.

     Daje to gwarancję, że region formularza będzie wystarczająco duży, aby wyświetlić mapę.

4. Na **widoku** menu, kliknij przycisk **przybornika**.

5. Z **wspólnych formantów** karcie **przybornika**, Dodaj **WebBrowser** do regionu formularza.

     **WebBrowser** spowoduje wyświetlenie mapy dla każdego adresu, który znajduje się na liście kontaktu.

## <a name="customize-the-behavior-of-the-form-region"></a>Dostosowywanie zachowania dotyczącego regionu formularza
 Dodaj kod do obsługi zdarzeń regionu formularza, aby dostosować sposób regionu formularza, który zachowuje się w czasie wykonywania. Dla tego regionu formularza kod sprawdza, czy właściwości elementu programu Outlook i określa, czy do wyświetlania regionu formularza mapy go. Jeśli Wyświetla regionu formularza, kod przechodzi do Windows Live Search lokalnych i ładuje mapę każdego adresu, na liście elementu kontaktów programu Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Aby dostosować zachowanie regionu formularza

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *MapIt.cs* lub *MapIt.vb*, a następnie kliknij przycisk **Wyświetl kod**.

    *MapIt.cs* lub *MapIt.vb* zostanie otwarty w edytorze kodu.

2. Rozwiń **fabryka regionów formularza** kodu regionu.

    Klasa fabryka regionów formularza o nazwie `MapItFactory` jest widoczna.

3. Dodaj następujący kod do `MapItFactory_FormRegionInitializing` programu obsługi zdarzeń. Ta procedura obsługi zdarzeń jest wywoływana, gdy użytkownik otwiera element kontaktu. Poniższy kod określa, czy skontaktuj się z pomocą element zawiera adres. Jeśli element kontaktu nie zawiera adresu, ten kod ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy **true** regionu formularza nie jest wyświetlany. W przeciwnym razie dodatku narzędzi VSTO zgłasza <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzeń i wyświetla regionu formularza.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Dodaj następujący kod do <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> programu obsługi zdarzeń. Kod będzie wykonywał następujące zadania:

   - Łączy każdy adres w elemencie skontaktuj się z pomocą i tworzy ciąg adresu URL.

   - Wywołania <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody <xref:System.Windows.Forms.WebBrowser> obiektu i przekazuje ciągu adresu URL jako parametr.

     Witryną lokalną wyszukiwania pojawi się w regionie formularza mapy go i przedstawia każdy adres w konsoli do zera.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Testowanie region formularza programu Outlook
 Kiedy uruchamiasz projekt, Visual Studio zostanie otwarty program Outlook. Otwórz element kontaktu do wyświetlania regionu formularza mapy go. Wyświetlania regionu formularza mapy ją jako stronę w formularzu, skontaktuj się z elementu, który zawiera adres.

### <a name="to-test-the-map-it-form-region"></a>Aby przetestować regionu formularza mapy go

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

     Zostanie otwarty program Outlook.

2. W programie Outlook na **Home** kliknij pozycję **nowe elementy**, a następnie kliknij przycisk **skontaktuj się z pomocą**.

3. W formularzu kontaktu wpisz **Beebe pods** jako kontakt nazwę, a następnie określ następujące trzy adresy.

    |Typ adresu|Adres|
    |------------------|-------------|
    |**biznesowe**|**Saint Main 4567 pole, Polska**|
    |**Strona główna**|**1234 North St. Buffalo, NY**|
    |**Inne**|**Saint Main 3456 Seattle, WA**|

4. Zapisz i Zamknij element kontaktu.

5. Otwórz ponownie **Beebe pods** kontakt.

    W programie Outlook, można to zrobić **znaleźć** grupy książki adresowej kontaktów, otwierając albo wpisując Beebe pods do **wyszukiwanie osób**.

6. W **Pokaż** grupy elementów wstążki, kliknij przycisk **mapy go** regionu formularza mapy go otworzyć.

     Region formularza mapy go pojawia się i wyświetla witrynę lokalnego wyszukiwania. **Firm**, **Home**, i **innych** adresy są wyświetlane w konsoli do zera. W konsoli podstaw wybierz adres który ma być mapowany.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook w tych tematach:

- Aby dowiedzieć się więcej na temat dostosowywania na Wstążce elementu programu Outlook, zobacz [Dostosuj Wstążkę dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Zobacz także
- [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
