---
title: 'Przewodnik: Projektowanie regionu formularza programu Outlook'
description: Dowiedz się, w jaki sposób można zaprojektować niestandardowy region formularza programu Microsoft Outlook, który pojawia się jako nowa strona w oknie Inspektora elementu kontaktu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e306814512c6cab2d331a26128f22bb94d7dbbf4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524211"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Przewodnik: Projektowanie regionu formularza programu Outlook
  Niestandardowe regiony formularzy poszerzają standardowe lub niestandardowe formularze programu Outlook Microsoft Office. W tym instruktażu zaprojektujesz niestandardowy region formularza, który pojawia się jako nowa strona w oknie Inspektora elementu kontaktu. Ten region formularza przedstawia mapę każdego adresu wymienionego dla kontaktu, wysyłając informacje o adresie do witryny sieci Web lokalnego wyszukiwania w usłudze Windows Live. Aby uzyskać informacje na temat regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie nowego projektu dodatku VSTO dla programu Outlook.

- Dodawanie regionu formularza do projektu dodatku VSTO.

- Projektowanie układu regionu formularza.

- Dostosowywanie zachowania regionu formularza.

- Testowanie regionu formularza programu Outlook.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] lub nowszy.

  ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby uzyskać wersję wideo tego tematu, zobacz [wideo How to: Design the Outlook form](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90)).

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Utwórz nowy projekt dodatku VSTO dla programu Outlook
 Najpierw Utwórz podstawowy projekt dodatku VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt dodatku VSTO programu Outlook o nazwie **MapItAddIn**.

2. W oknie dialogowym **Nowy projekt** wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w dowolnym katalogu.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Dodawanie regionu formularza do projektu dodatku VSTO programu Outlook
 Rozwiązanie dodatku VSTO dla programu Outlook może zawierać jeden lub więcej elementów regionu formularza programu Outlook. Dodaj element regionu formularza do projektu za pomocą kreatora **nowego regionu formularza programu Outlook** .

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aby dodać region formularza do projektu dodatku VSTO programu Outlook

1. W **Eksplorator rozwiązań** wybierz projekt **MapItAddIn** .

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **region formularza programu Outlook**, Nazwij plik **MAPI**, a następnie kliknij przycisk **Dodaj**.

     Zostanie uruchomiony Kreator **regionu formularza NewOutlook** .

4. Na stronie **Wybierz, jak chcesz utworzyć region formularza** kliknij pozycję **Projektuj nowy region formularza**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz typ regionu formularza, który chcesz utworzyć** kliknij przycisk **Rozdziel**, a następnie kliknij przycisk **dalej**.

     *Osobny* region formularza dodaje nową stronę do formularza programu Outlook. Aby uzyskać więcej informacji na temat typów regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

6. Na stronie **podaj tekst opisowy i wybierz Preferencje wyświetlania** , wpisz **Mapuj ją** w polu **Nazwa** .

     Ta nazwa jest wyświetlana na Wstążce okna inspektora, gdy element kontaktu jest otwarty.

7. Wybierz **inspektorów znajdujących się w trybie redagowania** i **inspektorów, które są w trybie odczytu**, a następnie kliknij przycisk **dalej**.

8. Na stronie **Zidentyfikuj klasy komunikatów, które będą wyświetlać ten region formularza** , wyczyść **wiadomość e-mail**, wybierz pozycję **kontakt**, a następnie kliknij przycisk **Zakończ**.

     Do projektu zostanie dodany plik *MapIt.cs* lub *MAPI. vb* .

## <a name="design-the-layout-of-the-form-region"></a>Projektowanie układu regionu formularza
 Wizualnie Rozwijaj regiony formularzy przy użyciu *projektanta regionów formularza*. Formanty zarządzane można przeciągnąć na powierzchnię projektanta regionów formularza. Użyj projektanta i okna **Właściwości** , aby dostosować układ i wygląd formantu.

### <a name="to-design-the-layout-of-the-form-region"></a>Aby zaprojektować układ regionu formularza

1. W **Eksplorator rozwiązań** rozwiń projekt **MapItAddIn** , a następnie kliknij dwukrotnie pozycję *MapIt.cs* lub *MAPI. vb* , aby otworzyć projektanta regionów formularza.

2. Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij polecenie **Właściwości**.

3. W oknie **Właściwości** Ustaw **rozmiar** na **664, 469**.

     Dzięki temu region formularza jest wystarczająco duży, aby można było wyświetlić mapę.

4. W menu **Widok** kliknij pozycję **Przybornik**.

5. Na karcie **Formanty standardowe** **przybornika** Dodaj do regionu formularza **formant WebBrowser** .

     Program **WebBrowser** wyświetli mapę każdego adresu, który jest wyświetlany na liście dla kontaktu.

## <a name="customize-the-behavior-of-the-form-region"></a>Dostosuj zachowanie regionu formularza
 Dodaj kod do obsługi zdarzeń regionów formularza, aby dostosować sposób, w jaki region formularza zachowuje się w czasie wykonywania. W przypadku tego regionu formularza kod sprawdza właściwości elementu programu Outlook i określa, czy ma być wyświetlany region formularza Mapa IT. Jeśli zostanie wyświetlony region formularza, kod przechodzi do lokalnego wyszukiwania w usłudze Windows Live i ładuje mapę każdego adresu wymienionego w elemencie Contact programu Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Aby dostosować zachowanie regionu formularza

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję *MapIt.cs* lub *MAPI. vb*, a następnie kliknij polecenie **Wyświetl kod**.

    *MapIt.cs* lub *MAPI. vb* zostanie otwarty w edytorze kodu.

2. Rozwiń węzeł region kod **fabryczny regionu formularza** .

    Klasa fabryki regionów formularza o nazwie `MapItFactory` jest udostępniona.

3. Dodaj następujący kod do `MapItFactory_FormRegionInitializing` programu obsługi zdarzeń. Ta procedura obsługi zdarzeń jest wywoływana, gdy użytkownik otworzy element Contact. Poniższy kod określa, czy element Contact zawiera adres. Jeśli element Contact nie zawiera adresu, ten kod ustawia <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Właściwość <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> klasy na **true** , a region formularza nie jest wyświetlany. W przeciwnym razie dodatek VSTO wywołuje <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzenie i wyświetla region formularza.

    [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
    [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

4. Dodaj następujący kod do <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> programu obsługi zdarzeń. Ten kod wykonuje następujące zadania:

   - Łączy każdy adres w elemencie Contact i tworzy ciąg adresu URL.

   - Wywołuje <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metodę <xref:System.Windows.Forms.WebBrowser> obiektu i przekazuje ciąg adresu URL jako parametr.

     Lokalna witryna sieci Web wyszukiwania zostanie wyświetlona w regionie formularza Mapa IT i przedstawia każdy adres w konsoli.

     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]

## <a name="test-the-outlook-form-region"></a>Testowanie regionu formularza programu Outlook
 Kiedy uruchamiasz projekt, program Visual Studio otwiera program Outlook. Otwórz element Contact, aby wyświetlić region formularza Mapa IT. Region formularza Mapa IT pojawia się jako strona w postaci dowolnego elementu kontaktowego, który zawiera adres.

### <a name="to-test-the-map-it-form-region"></a>Aby przetestować region formularza Mapa IT

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

     Zostanie otwarty program Outlook.

2. W programie Outlook na karcie **Narzędzia główne** kliknij pozycję **nowe elementy**, a następnie kliknij pozycję **kontakt**.

3. W formularzu Contact wpisz **Ann Beebe** jako nazwę kontaktu, a następnie określ następujące trzy adresy.

    |Typ adresu|Adres|
    |------------------|-------------|
    |**Firmowe**|**4567 Main St. Buffalo, NY**|
    |**Ekran główny**|**1234 północny St. Buffalo, NY**|
    |**Inne**|**3456 Main St. Seattle, WA**|

4. Zapisz i Zamknij element Contact.

5. Otwórz ponownie element Contact **Ann Beebe** .

    W programie Outlook można to zrobić w grupie **Znajdź** , otwierając książkę adresową dla kontaktów lub wpisując Ann Beebe w polu **Wyszukaj osoby**.

6. W grupie **Pokaż** Wstążkę elementu kliknij pozycję **Mapuj ją** , aby otworzyć region formularza Mapa IT.

     Zostanie wyświetlony region formularza Mapa IT i zostanie wyświetlona lokalna witryna sieci Web wyszukiwania. **Firma**, **Strona główna** i **inne** adresy są wyświetlane w konsoli. W konsoli do wykreślania wybierz adres, który chcesz zmapować.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook można znaleźć w następujących tematach:

- Aby dowiedzieć się, jak dostosować Wstążkę elementu programu Outlook, zobacz [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

## <a name="see-also"></a>Zobacz też
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
