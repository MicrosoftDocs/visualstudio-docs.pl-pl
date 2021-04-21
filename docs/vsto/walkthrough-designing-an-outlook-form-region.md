---
title: 'Przewodnik: projektowanie regionu formularza programu Outlook'
description: Dowiedz się, jak zaprojektować niestandardowy region formularza programu Microsoft Outlook, który jest wyświetlany jako nowa strona w oknie Inspector (Inspektor) elementu kontaktu.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 80c574799029f3fe8c4769d852886a625ffd93aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824286"
---
# <a name="walkthrough-design-an-outlook-form-region"></a>Przewodnik: projektowanie regionu formularza programu Outlook
  Niestandardowe regiony formularzy rozszerzają standardowe lub niestandardowe Microsoft Office formularzy programu Outlook. W tym przewodniku zaprojektujemy niestandardowy region formularza, który będzie wyświetlany jako nowa strona w oknie Inspector (Inspektor) elementu kontaktu. W tym regionie formularza jest wyświetlana mapa każdego adresu, który jest wyświetlany dla kontaktu, wysyłając informacje o adresie do witryny wyszukiwania lokalnego systemu Windows Live. Aby uzyskać informacje o regionach formularzy, zobacz [Create Outlook form regions (Tworzenie regionów formularzy programu Outlook).](../vsto/creating-outlook-form-regions.md)

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie nowego projektu dodatku VSTO programu Outlook.

- Dodawanie regionu formularza do projektu dodatku VSTO.

- Projektowanie układu obszaru formularza.

- Dostosowywanie zachowania regionu formularza.

- Testowanie regionu formularza programu Outlook.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)] lub nowsze.

  ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby uzyskać informacje na temat wersji wideo tego tematu, zobacz [Wideo, jak zaprojektować region formularza programu Outlook.](/previous-versions/visualstudio/visual-studio-2008/cc837160(v=vs.90))

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Tworzenie nowego projektu dodatku VSTO programu Outlook
 Najpierw utwórz podstawowy projekt dodatku VSTO.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Outlook

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programie utwórz projekt dodatku VSTO programu Outlook o nazwie **MapItAddIn**.

2. W **oknie dialogowym Nowy** projekt wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w dowolnym katalogu.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Dodawanie regionu formularza do projektu dodatku Outlook VSTO
 Rozwiązanie dodatku VSTO dla programu Outlook może zawierać co najmniej jeden element regionu formularza programu Outlook. Dodaj element regionu formularza do projektu przy użyciu kreatora Nowy region formularza **programu Outlook.**

### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>Aby dodać region formularza do projektu dodatku Outlook VSTO

1. W **Eksplorator rozwiązań** wybierz projekt **MapItAddIn.**

2. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję Region formularza programu **Outlook,** nadaj plikowi nazwę **MapIt,** a następnie kliknij przycisk **Dodaj**.

     Zostanie **uruchomiony kreator NewOutlook Form Region (Nowy region formularza).**

4. Na stronie **Wybierz sposób tworzenia** regionu formularza kliknij pozycję Zaprojektuj nowy region **formularza, a** następnie kliknij przycisk **Dalej.**

5. Na stronie **Wybierz typ regionu formularza, który chcesz utworzyć,** kliknij pozycję **Oddziel,** a następnie kliknij przycisk **Dalej.**

     Oddzielny *region* formularza dodaje nową stronę do formularza programu Outlook. Aby uzyskać więcej informacji na temat typów regionów formularzy, zobacz [Create Outlook form regions (Tworzenie regionów formularzy programu Outlook).](../vsto/creating-outlook-form-regions.md)

6. Na stronie **Dostarczanie tekstu opisowego i wybierania preferencji** wyświetlania wpisz **Mapuj go** w **polu** Nazwa.

     Ta nazwa jest wyświetlana na wstążce okna Inspector (Inspektor), gdy element kontaktu jest otwarty.

7. Wybierz **pozycję Inspektorzy w trybie redagowania i** Inspektorzy w trybie **odczytu,** a następnie kliknij przycisk **Dalej.**

8. Na stronie **Identyfikowanie klas komunikatów, które będą** wyświetlać ten region formularza, wyczyść pole **Wyboru** wiadomości e-mail, wybierz pozycję **Kontakt,** a następnie kliknij przycisk **Zakończ.**

     Do projektu zostanie dodany *plik MapIt.cs lub MapIt.vb.* 

## <a name="design-the-layout-of-the-form-region"></a>Projektowanie układu obszaru formularza
 Wizualne tworzenie regionów formularzy przy użyciu *projektanta regionów formularzy*. Kontrolki zarządzane można przeciągać na powierzchnię projektanta regionu formularza. Użyj projektanta i okna **Właściwości,** aby dostosować układ i wygląd kontrolki.

### <a name="to-design-the-layout-of-the-form-region"></a>Aby zaprojektować układ obszaru formularza

1. W **Eksplorator rozwiązań** rozwiń projekt **MapItAddIn,** a następnie kliknij dwukrotnie pozycję *MapIt.cs* lub *MapIt.vb,* aby otworzyć Projektanta regionów formularzy.

2. Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij pozycję **Właściwości.**

3. W **oknie** Właściwości ustaw **rozmiar** **na 664, 469.**

     Dzięki temu obszar formularza będzie wystarczająco duży, aby wyświetlić mapę.

4. W menu **Widok** kliknij pozycję **Przybornik.**

5. Na karcie **Typowe kontrolki** **przybornika** dodaj narzędzie **WebBrowser** do regionu formularza.

     Przeglądarka **WebBrowser** wyświetli mapę każdego adresu, który jest wymieniony dla kontaktu.

## <a name="customize-the-behavior-of-the-form-region"></a>Dostosowywanie zachowania obszaru formularza
 Dodaj kod do obsługi zdarzeń w regionie, aby dostosować sposób, w jaki region formularza zachowuje się w czasie uruchamiania. W przypadku tego regionu formularza kod sprawdza właściwości elementu programu Outlook i określa, czy ma być wyświetlany region formularza Mapuj go. Jeśli zostanie wyświetlony region formularza, kod przechodzi do funkcji Wyszukiwania lokalnego w systemie Windows Live i ładuje mapę każdego adresu wymienionego w pozycji kontaktu programu Outlook.

### <a name="to-customize-the-behavior-of-the-form-region"></a>Aby dostosować zachowanie obszaru formularza

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy *pozycję MapIt.cs* lub *MapIt.vb,* a następnie kliknij polecenie **Wyświetl kod.**

    *Plik MapIt.cs* lub *MapIt.vb* zostanie otwarty w edytorze kodu.

2. Rozwiń **region kodu fabryki regionów** formularzy.

    Klasa fabryki regionów formularza o `MapItFactory` nazwie jest ujawniona.

3. Dodaj następujący kod do procedury `MapItFactory_FormRegionInitializing` obsługi zdarzeń. Ta procedura obsługi zdarzeń jest wywoływana, gdy użytkownik otwiera element kontaktu. Poniższy kod określa, czy element kontaktu zawiera adres. Jeśli element kontaktu nie zawiera adresu, ten kod ustawia właściwość klasy na wartość true i <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> region formularza nie jest <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> wyświetlany.  W przeciwnym razie dodatek VSTO zgłasza zdarzenie <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> i wyświetla region formularza.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::

4. Dodaj następujący kod do procedury <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> obsługi zdarzeń. Ten kod wykonuje następujące zadania:

   - Łączy każdy adres w elementie kontaktu i tworzy ciąg adresu URL.

   - Wywołuje <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metodę obiektu <xref:System.Windows.Forms.WebBrowser> i przekazuje ciąg adresu URL jako parametr.

     Witryna sieci Web wyszukiwania lokalnego zostanie wyświetlona w regionie formularza Mapowanie i będzie przedstawiać każdy adres w witrynie na początku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet2":::

## <a name="test-the-outlook-form-region"></a>Testowanie regionu formularza programu Outlook
 Po uruchomieniu projektu program Visual Studio Program Outlook. Otwórz element kontaktu, aby wyświetlić region formularza Mapuj go. Obszar formularza Mapuj jest wyświetlany jako strona w postaci dowolnego elementu kontaktu, który zawiera adres.

### <a name="to-test-the-map-it-form-region"></a>Aby przetestować region formularza Mapuj

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

     Zostanie otwarty program Outlook.

2. W programie Outlook na karcie **Narzędzia** główne kliknij pozycję **Nowe elementy,** a następnie kliknij pozycję **Kontakt.**

3. W formularzu kontaktu wpisz **Ann Beebe** jako nazwę kontaktu, a następnie określ następujące trzy adresy.

    |Typ adresu|Adres|
    |------------------|-------------|
    |**Firmowe**|**4567 Main St. Zamów, Nowy Jork**|
    |**Ekran główny**|**1234 North St. Dob, NY**|
    |**Inne**|**3456 Main St. Seattle, WA**|

4. Zapisz i zamknij element kontaktu.

5. Otwórz ponownie **element kontaktu Ann Beebe.**

    W programie Outlook można  to zrobić w grupie Znajdź, otwierając okno Książka adresowa kontaktów lub wpisując Ann Beebe w polu **Wyszukaj osoby.**

6. W grupie **Pokaż** na wstążce elementu kliknij pozycję **Mapuj** go, aby otworzyć obszar formularza Mapuj go.

     Zostanie wyświetlony region formularza Mapuj i zostanie wyświetlona witryna internetowa wyszukiwania lokalnego. Adresy **Business**( **Firma), Home**(Strona główna) i **Other** (Inne) są wyświetlane w łasce na początku. W panelu na początku wybierz adres, który chcesz zmapować.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat dostosowywania interfejsu użytkownika aplikacji Outlook można znaleźć w tych tematach:

- Aby dowiedzieć się więcej na temat dostosowywania wstążki elementu programu Outlook, zobacz [Dostosowywanie wstążki dla programu Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wskazówki dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: importowanie regionu formularza zaprojektowanego w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Jak dodać region formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą komunikatów programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Akcje niestandardowe w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Jak uniemożliwić programowi Outlook wyświetlanie regionu formularza](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
