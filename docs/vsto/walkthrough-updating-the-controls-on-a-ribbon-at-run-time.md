---
title: 'Wskazówki: Aktualizowanie kontrolek na Wstążce w czasie wykonywania'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 40072b1dcd6b24f552a3c87c8241ea4498229053
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389153"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Wskazówki: Aktualizowanie kontrolek na Wstążce w czasie wykonywania

W tym instruktażu pokazano, jak aktualizowanie formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office przy użyciu modelu obiektu wstążki.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Przykład ściąga dane z przykładowej bazy danych Northwind do wypełnienia pola kombi i menu w programie Microsoft Office Outlook. Elementy wybrane w tych kontrolek automatycznie wypełnić pola, takie jak **do** i **podmiotu** w wiadomości e-mail.

W instruktażu przedstawiono następujące zagadnienia:

-   Utwórz nowy projekt dodatku narzędzi VSTO dla programu Outlook.

-   Projektowanie niestandardowych grupy wstążki.

-   Dodaj niestandardową grupę do wbudowanej karty.

-   Aktualizowanie formantów na Wstążce w czasie wykonywania.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   Program Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Utwórz nowy projekt dodatku narzędzi VSTO dla programu Outlook

Najpierw utwórz projekt dodatku narzędzi VSTO dla programu Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO dla programu Outlook

1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt dodatku narzędzi VSTO dla programu Outlook o nazwie **Ribbon_Update_At_Runtime**.

2.  W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.

3.  Zapisz projekt do domyślnego katalogu projektu.

     Aby uzyskać więcej informacji, zobacz [porady: tworzenie projekty pakietu Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Projektowanie niestandardowych grupy wstążki

Wstążka, w tym przykładzie pojawi się po użytkownik Redaguj nową wiadomość e-mail. Aby utworzyć grupę niestandardową dla wstążki, najpierw należy dodać element wstążki do projektu, a następnie zaprojektujesz grupy w Projektancie wstążki. Ta grupa niestandardowe pomoże generowanie wiadomości monitującą wiadomość e-mail do klientów przez pobieranie nazwy i kolejność historii z bazy danych.

### <a name="to-design-a-custom-group"></a>Aby zaprojektować grupę niestandardową

1.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)**.

3.  Zmień nazwę nowego wstążki do **CustomerRibbon**, a następnie kliknij przycisk **Dodaj**.

     *CustomerRibbon.cs* lub *CustomerRibbon.vb* plik zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.

4.  Kliknij projektanta wstążki, aby go zaznaczyć.

5.  W **właściwości** okna, kliknij strzałkę listy rozwijanej obok **RibbonType** właściwości, a następnie kliknij **Microsoft.Outlook.Mail.Compose**.

     Dzięki temu wstążki, które będą wyświetlane po użytkownik Redaguj nową wiadomość e-mail w programie Outlook.

6.  W Projektancie Wstążki kliknij **grupa1** aby go zaznaczyć.

7.  W **właściwości** oknie **etykiety** do **zakupów klientów**.

8.  Z **formanty wstążki Office** karcie **przybornika**, przeciągnij **ComboBox** na **zakupów klientów** grupy.

9. Kliknij przycisk **ComboBox1** aby go zaznaczyć.

10. W **właściwości** oknie **etykiety** do **klientów**.

11. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij **Menu** na **zakupów klientów** grupy.

12. W **właściwości** oknie **etykiety** do **zakupionych produktów**.

13. Ustaw **dynamiczne** do **true**.

     Dzięki temu można dodawać i usuwać kontrolek w menu w czasie wykonywania po załadowaniu wstążki do aplikacji pakietu Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Dodaj niestandardową grupę do wbudowanej karty

Wbudowana karty to karta, która jest już na wstążce programu Outlook Explorer lub Inspektora. W tej procedurze zostanie dodaj niestandardową grupę do wbudowanej karty, a następnie określ położenie niestandardową grupę na karcie.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Aby dodać grupę niestandardową do wbudowanej karty

1.  Kliknij przycisk **TabAddins (wbudowane)** kartę, aby go zaznaczyć.

2.  W **właściwości** okna, rozwiń węzeł **ControlId** właściwości, a następnie ustaw **OfficeId** do **TabNewMailMessage**.

     Spowoduje to dodanie **zakupów klientów** grupy **wiadomości** karty wstążki, który pojawia się w nową wiadomość e-mail.

3.  Kliknij przycisk **zakupów klientów** grupy, aby go zaznaczyć.

4.  W **właściwości** okna, rozwiń węzeł **pozycji** właściwości, kliknij strzałkę listy rozwijanej obok **PositionType** właściwości, a następnie kliknij  **BeforeOfficeId**.

5.  Ustaw **OfficeId** właściwości **GroupClipboard**.

     To umieszcza **zakupów klientów** grupy przed **Schowka** grupy **wiadomości** kartę.

## <a name="create-the-data-source"></a>Utwórz źródło danych

Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1.  Na **danych** menu, kliknij przycisk **Dodaj nowe źródło danych**.

     Spowoduje to uruchomienie **Kreatora konfiguracji źródła danych**.

2.  Wybierz **bazy danych**, a następnie kliknij przycisk **dalej**.

3.  Wybierz **Dataset**, a następnie kliknij przycisk **dalej**.

4.  Wybierz połączenie danych z bazie danych programu Microsoft SQL Server Compact 4.0 Northwind lub Dodaj nowe połączenie przy użyciu **nowe połączenie** przycisku.

5.  Po zostało wybrane lub utworzyć połączenie, kliknij przycisk **dalej**.

6.  Kliknij przycisk **dalej** można zapisać parametry połączenia.

7.  Na **wybierz obiekty bazy danych** rozwiń **tabel**.

8.  Zaznacz pole wyboru obok każdego z następujących tabel:

    1.  **Klienci**

    2.  **Szczegóły zamówienia**

    3.  **Zamówienia**

    4.  **Produkty

9. Kliknij przycisk **Zakończ**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Zaktualizuj Kontrolki niestandardowe grupy w czasie wykonywania

Model obiektu Wstążka umożliwia wykonywanie następujących zadań:

-   Dodaj nazwy klienta do **klientów** pola kombi.

-   Dodaj przycisk i menu kontrolki do **zakupionych produktów** menu, które reprezentują zamówień sprzedaży i produkty sprzedawane.

-   Wypełnij na, temat i treść pola nowe wiadomości e-mail przy użyciu danych z **klientów** pola kombi i **zakupionych produktów** menu.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aby zaktualizować formantów w niestandardowej grupie za pomocą modelu obiektów wstążki

1. Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.

2. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** zaznacz **System.Data.Linq** zestawu, a następnie kliknij **OK**.

    Ten zestaw zawiera klasy dla przy użyciu Language-Integrated zapytania (LINQ). Użyjesz programu LINQ do wypełnienia Kontrolki niestandardowe grupy przy użyciu danych z bazy danych Northwind.

3. W **Eksploratora rozwiązań**, kliknij przycisk **CustomerRibbon.cs** lub **CustomerRibbon.vb** aby go zaznaczyć.

4. Na **widoku** menu, kliknij przycisk **kodu**.

    Plik kodu wstążki, zostanie otwarty w edytorze kodu.

5. Dodaj następujące instrukcje na górze pliku kodu wstążki. Instrukcje te zapewniają łatwy dostęp do przestrzeni nazw LINQ i przestrzeń nazw programu Outlook podstawowego zestawu międzyoperacyjnego (PIA).

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Dodaj następujący kod wewnątrz `CustomerRibbon` klasy. Ten kod deklaruje tabelą danych i adapterów tabel, które będą używane do przechowywania informacji od klientów, zamówień, szczegółów zamówienia i tabele produktów w bazie danych Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Dodaj następujący blok kodu w celu `CustomerRibbon` klasy. Ten kod dodaje trzy metody pomocnika, które utworzyć formanty do wstążki w czasie wykonywania.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Zastąp `CustomerRibbon_Load` metody obsługi zdarzeń z następującym kodem. Ten kod korzysta z zapytania LINQ do wykonywania następujących zadań:

   - Wypełnij **klientów** pola kombi przy użyciu Identyfikatora i nazwy 20 klientów w bazie danych Northwind.

   - Wywołania `PopulateSalesOrderInfo` metody pomocnika. Ta metoda aktualizuje **ProductsPurchased** menu numerami zamówienia sprzedaży, które odnoszą się do aktualnie wybranego odbiorcy.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Dodaj następujący kod do `CustomerRibbon` klasy. Ten kod używa zapytań LINQ do wykonywania następujących zadań:

   - Dodaje podmenu do **ProductsPurchased** menu dla każdego zamówienia sprzedaży związane z wybranym klientem.

   - Dodaje przyciski do każdego podmenu produktów związanych z zamówienia sprzedaży.

   - Dodaje obsługę zdarzeń do każdego przycisku.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu wstążki.

     Zostanie otwarty projektant wstążki.

11. W Projektancie wstążki, kliknij dwukrotnie **klientów** pola kombi.

     Plik kodu wstążki, zostanie otwarty w edytorze kodu i `ComboBox1_TextChanged` pojawia się program obsługi zdarzeń.

12. Zastąp `ComboBox1_TextChanged` programu obsługi zdarzeń z następującym kodem. Kod będzie wykonywał następujące zadania:

    - Wywołania `PopulateSalesOrderInfo` metody pomocnika. Ta metoda aktualizuje **zakupionych produktów** menu z zamówień sprzedaży, które odnoszą się do wybranego klienta.

    - Wywołania `PopulateMailItem` metody pomocnika i przekazuje w bieżącej tekstu, która jest nazwą wybranego klienta. Ta metoda wypełni na, temat i treść pola nowe wiadomości e-mail.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Dodaj następujący kod `Click` procedurę obsługi zdarzeń do `CustomerRibbon` klasy. Ten kod dodaje nazwę wybranych produktów do pola treści nowe wiadomości e-mail.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Dodaj następujący kod do `CustomerRibbon` klasy. Kod będzie wykonywał następujące zadania:

    - Wypełnia wiersz na nowe wiadomości e-mail przy użyciu adresu e-mail aktualnie wybranego odbiorcy.

    - Dodaje tekst do pola temat i treść nowe wiadomości e-mail.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testowanie Kontrolki niestandardowe grupy

Po otwarciu nowego formularza wiadomości e-mail w programie Outlook grupy niestandardowej o nazwie **zakupów klientów** pojawia się na **wiadomości** karty wstążki.

Aby utworzyć wiadomość monitującą wiadomość e-mail klienta, wybierz klienta, a następnie wybierz produktów zakupionych przez klienta. Formanty w **zakupów klientów** grupy są aktualizowane w czasie wykonywania przy użyciu danych z bazy danych Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Aby przetestować formanty niestandardowe grupy

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.

     Uruchamia program Outlook.

2.  W programie Outlook na **pliku** menu wskaż **New**, a następnie kliknij przycisk **wiadomość E-mail**.

     Są wykonywane następujące akcje:

    -   Pojawi się nowe okno Inspektora wiadomość poczty.

    -   Na **komunikat** karcie na wstążce **zakupów klientów** grupa pojawia się przed **Schowka** grupy.

    -   **Klientów** pola kombi w grupie będą aktualizowane przy użyciu nazwy klientów w bazie danych Northwind.

3.  Na **komunikat** karty wstążki w **zakupów klientów** grupy, wybierz klienta z **klientów** pola kombi.

     Są wykonywane następujące akcje:

    -   **Zakupionych produktów** menu jest aktualizowana w celu wyświetlenia każdego zamówienia sprzedaży dla zaznaczonego klienta.

    -   Podmenu każdego zamówienia sprzedaży jest aktualizowana w celu wyświetlenia produktów zakupionych w tej kolejności.

    -   Adres e-mail wybranego klienta zostanie dodany do **do** wiersza wiadomość e-mail, tematu i treści wiadomości e-mail są wypełniane przy użyciu tekstu.

4.  Kliknij przycisk **zakupów produktów** menu, wskaż polecenie wszystkie zamówienia sprzedaży, a następnie kliknij produkt z zamówienia sprzedaży.

     Nazwa produktu jest dodawany do treści wiadomości e-mail.

## <a name="next-steps"></a>Następne kroki

Możesz dowiedzieć się więcej na temat sposobu dostosowywania interfejsu użytkownika pakietu Office w tych tematach:

-   Dodaj oparte na kontekście interfejsu użytkownika do jakiegokolwiek dostosowywania poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md).

-   Rozszerz standardowy lub niestandardowy formularz programu Microsoft Office Outlook. Aby uzyskać więcej informacji, zobacz [wskazówki: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

-   Dodawanie niestandardowego okienka zadań do programu Outlook. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz także

- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Porady: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md)
- [Dostosowywanie wstążki do programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Porady: zmiana położenia zakładki na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Porady: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Porady: dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Porady: dodatek Pokaż błędy interfejsu użytkownika](../vsto/how-to-show-add-in-user-interface-errors.md)