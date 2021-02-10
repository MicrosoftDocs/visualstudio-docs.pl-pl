---
title: 'Przewodnik: aktualizowanie kontrolek na Wstążce w czasie wykonywania'
description: Dowiedz się, jak można użyć modelu obiektów wstążki do aktualizowania formantów na Wstążce po załadowaniu wstążki do aplikacji pakietu Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 181fafeb55720b5a97a635a4c2322cf7343643d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937189"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Przewodnik: aktualizowanie kontrolek na Wstążce w czasie wykonywania

W tym instruktażu przedstawiono sposób użycia modelu obiektów wstążki do aktualizowania kontrolek na Wstążce po załadowaniu wstążki do aplikacji pakietu Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Przykład pobiera dane z przykładowej bazy danych Northwind, aby wypełnić pole kombi i menu w Microsoft Office Outlook. Elementy wybrane w tych kontrolkach automatycznie wypełniają **pola, takie jak** i **tematu** w wiadomości e-mail.

W instruktażu przedstawiono następujące zagadnienia:

- Utwórz nowy projekt dodatku VSTO dla programu Outlook.

- Zaprojektuj niestandardową grupę wstążki.

- Dodaj grupę niestandardową do wbudowanej karty.

- Aktualizowanie formantów na Wstążce w czasie wykonywania.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Utwórz nowy projekt dodatku VSTO dla programu Outlook

Najpierw utwórz projekt dodatku VSTO dla programu Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt dodatku VSTO programu Outlook o nazwie **Ribbon_Update_At_Runtime**.

2. W oknie dialogowym **Nowy projekt** wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w domyślnym katalogu projektu.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Projektowanie niestandardowej grupy wstążki

Wstążka dla tego przykładu będzie wyświetlana, gdy użytkownik utworzy nową wiadomość e-mail. Aby utworzyć niestandardową grupę dla wstążki, najpierw Dodaj element wstążki do projektu, a następnie Zaprojektuj grupę w Projektancie wstążki. Ta grupa niestandardowa pomoże Ci generować wiadomości e-mail z monitami dla klientów, pobierając nazwy i porządkując historie z bazy danych.

### <a name="to-design-a-custom-group"></a>Aby zaprojektować grupę niestandardową

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant wizualny)**.

3. Zmień nazwę nowej wstążki na **CustomerRibbon**, a następnie kliknij przycisk **Dodaj**.

     Plik *CustomerRibbon.cs* lub *CustomerRibbon. vb* zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

4. Kliknij projektanta wstążki, aby go zaznaczyć.

5. W oknie **Właściwości** kliknij strzałkę listy rozwijanej obok właściwości **wstążka** , a następnie kliknij pozycję **Microsoft. Outlook. mail. redagowanie**.

     Dzięki temu wstążka będzie wyświetlana, gdy użytkownik redaguje nową wiadomość e-mail w programie Outlook.

6. W Projektancie wstążki kliknij pozycję **grupa1** , aby ją zaznaczyć.

7. W oknie **Właściwości** ustaw wartość **etykieta** na **zakupy dla klientów**.

8. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij **pole kombi** na grupę **zakupy klienta** .

9. Kliknij pozycję **ComboBox1** , aby ją zaznaczyć.

10. W oknie **Właściwości** ustaw wartość **etykieta** na **klienci**.

11. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij **menu** do grupy **zakupy klienta** .

12. W oknie **Właściwości** ustaw wartość **etykieta** na **zakupione produkty**.

13. Ustaw wartość **dynamiczną** na **true**.

     Dzięki temu można dodawać i usuwać kontrolki w menu w czasie wykonywania po załadowaniu wstążki do aplikacji pakietu Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Dodawanie grupy niestandardowej do karty wbudowanej

Karta wbudowana to karta, która znajduje się już na wstążce Eksploratora lub inspektora programu Outlook. W ramach tej procedury dodasz grupę niestandardową do wbudowanej karty, a następnie określisz pozycję grupy niestandardowej na karcie.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Aby dodać grupę niestandardową do karty wbudowanej

1. Kliknij kartę **TabAddIns (wbudowane)** , aby ją zaznaczyć.

2. W oknie **Właściwości** rozwiń Właściwość **ControlID** , a następnie ustaw wartość **OfficeId** na **TabNewMailMessage**.

     Spowoduje to dodanie grupy **zakupów klienta** do karty **komunikaty** na Wstążce, która pojawia się w nowej wiadomości e-mail.

3. Kliknij grupę **zakupy klienta** , aby ją wybrać.

4. W oknie **Właściwości** rozwiń Właściwość **położenie** , kliknij strzałkę listy rozwijanej obok właściwości **PositionType** , a następnie kliknij pozycję **BeforeOfficeId**.

5. Ustaw właściwość **OfficeId** na **GroupClipboard**.

     Spowoduje to umieszczenie grupy **zakupów klienta** przed grupą **schowka** karty **komunikaty** .

## <a name="create-the-data-source"></a>Tworzenie źródła danych

Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** kliknij polecenie **Dodaj nowe źródło danych**.

     Spowoduje to uruchomienie **Kreatora konfiguracji źródła danych**.

2. Wybierz pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

3. Wybierz pozycję **zestaw danych**, a następnie kliknij przycisk **dalej**.

4. Wybierz połączenie danych z przykładową bazą danych Northwind Microsoft SQL Server Compact 4,0 lub Dodaj nowe połączenie za pomocą przycisku **nowe połączenie** .

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **dalej**.

6. Kliknij przycisk **dalej** , aby zapisać parametry połączenia.

7. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele**.

8. Zaznacz pole wyboru obok każdej z następujących tabel:

    1. **Klienci**

    2. **Szczegóły zamówienia**

    3. **Orders (Zamówienia)**

    4. **Produkty**

9. Kliknij przycisk **Finish** (Zakończ).

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aktualizuj kontrolki w grupie niestandardowej w czasie wykonywania

Użyj modelu obiektów wstążki, aby wykonać następujące zadania:

- Dodaj nazwy klientów do pola kombi **Customers** .

- Dodaj przyciski menu i przycisków do menu **zakupione produkty** , które reprezentują zamówienia sprzedaży i produkty sprzedane.

- Wypełnij pola do, temat i treść nowych wiadomości e-mail przy użyciu danych z pola kombi **klienci** i menu **zakupione produkty** .

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aby zaktualizować kontrolki w grupie niestandardowej przy użyciu modelu obiektów wstążki

1. W menu **projekt** kliknij polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **.NET** , wybierz zestaw **System. Data. LINQ** , a następnie kliknij przycisk **OK**.

    Ten zestaw zawiera klasy służące do korzystania z zapytań Language-Integrated (LINQ). Program LINQ służy do wypełniania kontrolek w grupie niestandardowej danymi z bazy danych Northwind.

3. W **Eksplorator rozwiązań** kliknij pozycję **CustomerRibbon.cs** lub **CustomerRibbon. vb** , aby ją zaznaczyć.

4. W menu **Widok** kliknij polecenie **kod**.

    Plik kodu wstążki zostanie otwarty w edytorze kodu.

5. Dodaj następujące instrukcje na górze pliku kodu wstążki. Te instrukcje zapewniają łatwy dostęp do przestrzeni nazw LINQ oraz do przestrzeni nazw podstawowego zestawu międzyoperacyjnego programu Outlook (PIA).

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Dodaj następujący kod do `CustomerRibbon` klasy. Ten kod deklaruje tabelę danych i karty tabel, które będą używane do przechowywania informacji z tabeli Customer, Orders, Order Details i Product (produkty) bazy danych Northwind.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Dodaj następujący blok kodu do `CustomerRibbon` klasy. Ten kod dodaje trzy metody pomocnika, które tworzą kontrolki dla wstążki w czasie wykonywania.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Zastąp `CustomerRibbon_Load` metodę obsługi zdarzeń poniższym kodem. Ten kod używa zapytania LINQ do wykonywania następujących zadań:

   - Wypełnij pole kombi **klientom** przy użyciu identyfikatora i nazwy 20 klientów w bazie danych Northwind.

   - Wywołuje `PopulateSalesOrderInfo` metodę pomocnika. Ta metoda aktualizuje menu **ProductsPurchased** za pomocą numerów zamówień sprzedaży odnoszących się do aktualnie wybranego klienta.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Dodaj poniższy kod do klasy `CustomerRibbon`. Ten kod używa zapytań LINQ do wykonywania następujących zadań:

   - Dodaje podmenu do menu **ProductsPurchased** dla każdego zamówienia sprzedaży powiązanego z wybranym klientem.

   - Dodaje przyciski do każdego podmenu produktów związanych z kolejnością sprzedaży.

   - Dodaje programy obsługi zdarzeń do każdego przycisku.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. W **Eksplorator rozwiązań** kliknij dwukrotnie plik kodu wstążki.

     Zostanie otwarty projektant wstążki.

11. W Projektancie wstążki kliknij dwukrotnie pole kombi **Customers** .

     Plik kodu wstążki zostanie otwarty w edytorze kodu i `ComboBox1_TextChanged` pojawi się procedura obsługi zdarzeń.

12. Zastąp `ComboBox1_TextChanged` procedurę obsługi zdarzeń poniższym kodem. Ten kod wykonuje następujące zadania:

    - Wywołuje `PopulateSalesOrderInfo` metodę pomocnika. Ta metoda aktualizuje menu **zakupione produkty** przy użyciu zamówień sprzedaży odnoszących się do wybranego klienta.

    - Wywołuje `PopulateMailItem` metodę pomocnika i przekazuje bieżący tekst, który jest wybraną nazwą klienta. Ta metoda wypełnia pola do, temat i treść nowych wiadomości e-mail.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Dodaj `Click` do klasy następujący program obsługi zdarzeń `CustomerRibbon` . Ten kod dodaje nazwę wybranych produktów do pola Body nowych wiadomości e-mail.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Dodaj poniższy kod do klasy `CustomerRibbon`. Ten kod wykonuje następujące zadania:

    - Wypełnia wiersz do nowej wiadomości e-mail przy użyciu adresu e-mail aktualnie wybranego klienta.

    - Dodaje tekst do pól temat i treść nowych wiadomości e-mail.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testowanie kontrolek w grupie niestandardowej

Po otwarciu nowej formy poczty w programie Outlook na karcie **komunikaty** na wstążce zostanie wyświetlona Grupa niestandardowa o nazwie **zakupy klienta** .

Aby utworzyć monit e-mail dotyczący klienta, wybierz klienta, a następnie wybierz produkty zakupione przez klienta. Kontrolki w grupie **zakupy klienta** są aktualizowane w czasie wykonywania z danymi z bazy danych Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Aby przetestować kontrolki w grupie niestandardowej

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

     Program Outlook zostanie uruchomiony.

2. W programie Outlook w menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **wiadomość e-mail**.

     Wykonywane są następujące akcje:

    - Zostanie wyświetlone nowe okno Inspektora wiadomości e-mail.

    - Na karcie **komunikat** na Wstążce Grupa **zakupy klienta** jest wyświetlana przed grupą **schowka** .

    - Pole kombi **klienci** w grupie zostanie zaktualizowane nazwami klientów w bazie danych Northwind.

3. Na karcie **komunikat** na Wstążce w grupie **zakupy klienta** wybierz klienta z pola kombi **klienci** .

     Wykonywane są następujące akcje:

    - Menu **zakupione produkty** zostało zaktualizowane, aby pokazać każde zamówienie sprzedaży dla wybranego klienta.

    - Każde podmenu zamówienia sprzedaży jest aktualizowane, aby pokazać produkty zakupione w tej kolejności.

    - Adres e-mail wybranego klienta zostanie dodany do wiersza **do** wiadomości e-mail, a temat i treść wiadomości e-mail są wypełniane tekstem.

4. Kliknij menu **zakupy produktów** , wskaż dowolne zamówienie sprzedaży, a następnie kliknij produkt w ramach zamówienia sprzedaży.

     Nazwa produktu jest dodawana do treści wiadomości e-mail.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat sposobu dostosowywania interfejsu użytkownika pakietu Office można znaleźć w następujących tematach:

- Dodaj interfejs użytkownika oparty na kontekście do dowolnych dostosowań na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Rozbudowa standardowego lub niestandardowego formularza programu Outlook Microsoft Office. Aby uzyskać więcej informacji, zobacz [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Dodawanie niestandardowego okienka zadań do programu Outlook. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Zapytanie o języku zintegrowanym (LINQ)](/dotnet/csharp/linq/index)
- [Instrukcje: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Instrukcje: zmiana położenia karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Instrukcje: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)
- [Instrukcje: Dodawanie kontrolek do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)