---
title: 'Przewodnik: aktualizowanie kontrolek na wstążce w czasie uruchamiania'
description: Dowiedz się, jak za pomocą modelu obiektów wstążki zaktualizować kontrolki na wstążce po załadowaniu wstążki do aplikacji pakietu Office.
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
ms.openlocfilehash: 7cf9bbe73bd43fa01aec8e7d0dec42fd8301ff30
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827529"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>Przewodnik: aktualizowanie kontrolek na wstążce w czasie uruchamiania

W tym przewodniku pokazano, jak za pomocą modelu obiektów wstążki zaktualizować kontrolki na wstążce po załadowaniu wstążki do aplikacji pakietu Office.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Przykład pobiera dane z przykładowej bazy danych Northwind w celu wypełnienia pola kombi i menu w Microsoft Office Outlook. Elementy wybrane w tych kontrolkach automatycznie wypełnią pola, takie jak **Do** i **Temat,** w wiadomości e-mail.

W instruktażu przedstawiono następujące zagadnienia:

- Utwórz nowy projekt dodatku VSTO programu Outlook.

- Zaprojektuj niestandardową grupę wstążki.

- Dodaj grupę niestandardową do karty wbudowanej.

- Aktualizowanie kontrolek na wstążce w czasie uruchamiania.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Tworzenie nowego projektu dodatku VSTO programu Outlook

Najpierw utwórz projekt dodatku VSTO programu Outlook.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Outlook

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programie utwórz projekt dodatku VSTO programu Outlook o nazwie **Ribbon_Update_At_Runtime**.

2. W **oknie dialogowym Nowy** projekt wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w domyślnym katalogu projektu.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Projektowanie niestandardowej grupy wstążki

Wstążka dla tego przykładu będzie wyświetlana, gdy użytkownik s napisze nową wiadomość e-mail. Aby utworzyć grupę niestandardową dla wstążki, najpierw dodaj element Wstążki do projektu, a następnie zaprojektuj grupę w Projektancie wstążki. Ta grupa niestandardowa pomoże Ci wygenerować kolejne wiadomości e-mail do klientów, ściągając nazwy i historie zamówień z bazy danych.

### <a name="to-design-a-custom-group"></a>Aby zaprojektować grupę niestandardową

1. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję **Wstążka (Projektant wizualny).**

3. Zmień nazwę nowej wstążki na **CustomerRibbon,** a następnie kliknij przycisk **Dodaj**.

     Plik *CustomerRibbon.cs* lub *CustomerRibbon.vb* zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i grupa.

4. Kliknij projektanta wstążki, aby go zaznaczyć.

5. W **oknie** Właściwości kliknij strzałkę listy rozwijanej obok właściwości **RibbonType,** a następnie kliknij pozycję **Microsoft.Outlook.Mail.Compose.**

     Dzięki temu wstążka będzie wyświetlana, gdy użytkownik schowa nową wiadomość e-mail w programie Outlook.

6. W Projektancie wstążki kliknij pozycję **Grupa1,** aby ją zaznaczyć.

7. W **oknie Właściwości** ustaw **wartość Etykieta** **na Wartość Zakupów klienta.**

8. Na karcie **Kontrolki wstążki pakietu Office** **przybornika** przeciągnij kontrolkę **ComboBox** do **grupy Zakupy** klientów.

9. Kliknij **pozycję ComboBox1,** aby ją zaznaczyć.

10. W **oknie Właściwości** ustaw wartość **Etykieta** na **Klienci.**

11. Na karcie **Kontrolki wstążki pakietu Office** **przybornika** przeciągnij **menu** do grupy **Zakupy** klientów.

12. W **oknie Właściwości** ustaw wartość **Etykieta** na **Produkt zakupiony**.

13. Ustaw **wartość dynamiczna** na **true**.

     Umożliwia to dodawanie i usuwanie kontrolek w menu w czasie uruchamiania po załadowaniu wstążki do aplikacji pakietu Office.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Dodawanie grupy niestandardowej do karty wbudowanej

Wbudowana karta to karta, która znajduje się już na wstążce eksploratora programu Outlook lub narzędzia Inspector. W tej procedurze dodasz grupę niestandardową do karty wbudowanej, a następnie określisz pozycję grupy niestandardowej na karcie.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Aby dodać grupę niestandardową do karty wbudowanej

1. Kliknij **kartę TabAddins (wbudowane),** aby ją zaznaczyć.

2. W **oknie Właściwości** rozwiń właściwość **ControlId,** a następnie ustaw dla właściwości **OfficeId** wartość **TabNewMailMessage.**

     Powoduje to dodanie **grupy Zakupy klientów** do karty **Wiadomości** na wstążce wyświetlanej w nowej wiadomości e-mail.

3. Kliknij **grupę Customer Purchases (Zakupy klientów),** aby ją wybrać.

4. W **oknie Właściwości** rozwiń właściwość **Position,** kliknij strzałkę listy rozwijanej obok właściwości **PositionType,** a następnie kliknij pozycję **BeforeOfficeId.**

5. Ustaw właściwość **OfficeId** na **GroupClipboard.**

     Ta pozycja **umieszcza grupę Zakupy klientów** przed grupą **Schowka** na **karcie** Komunikaty.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

Użyj okna **Źródła danych,** aby dodać typowany zestaw danych do projektu.

### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **Dane** kliknij pozycję **Dodaj nowe źródło danych.**

     Zostanie uruchomiony **Kreator konfiguracji źródła danych**.

2. Wybierz **pozycję Baza** danych , a następnie kliknij przycisk **Dalej.**

3. Wybierz **pozycję Dataset**(Zestaw danych), a następnie kliknij przycisk Next **(Dalej).**

4. Wybierz połączenie danych z przykładową bazą danych Northwind Microsoft SQL Server Compact 4.0 lub dodaj nowe połączenie przy użyciu **przycisku Nowe** połączenie.

5. Po wybraniu lub utworzeniu połączenia kliknij przycisk **Dalej.**

6. Kliknij **przycisk Dalej,** aby zapisać ciąg połączenia.

7. Na stronie **Wybieranie obiektów bazy danych** rozwiń pozycję **Tabele**.

8. Zaznacz pole wyboru obok każdej z następujących tabel:

    1. **Klienci**

    2. **Szczegóły zamówienia**

    3. **Orders (Zamówienia)**

    4. **Produkty**

9. Kliknij przycisk **Finish** (Zakończ).

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Aktualizowanie kontrolek w grupie niestandardowej w czasie uruchamiania

Użyj modelu obiektów wstążki, aby wykonać następujące zadania:

- Dodaj nazwy klientów do **pola kombi** Klienci.

- Dodaj kontrolki menu i przycisku do menu **Produkty zakupione,** które reprezentują zamówienia sprzedaży i sprzedane produkty.

- Wypełnij pola Do, Temat i Treść nowych wiadomości e-mail przy użyciu danych z pola kombi Klienci i menu **Produkty zakupione.** 

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Aby zaktualizować kontrolki w grupie niestandardowej przy użyciu modelu obiektów wstążki

1. W menu **Project (Projekt)** kliknij pozycję **Add Reference (Dodaj odwołanie).**

2. W **oknie dialogowym Dodawanie** odwołania kliknij **kartę .NET,** wybierz zestaw **System.Data.Linq,** a następnie kliknij przycisk **OK.**

    Ten zestaw zawiera klasy do używania Language-Integrated zapytań (LINQ). Użyjemy linq do wypełnienia kontrolek w grupie niestandardowej danymi z bazy danych Northwind.

3. W **Eksplorator rozwiązań** kliknij pozycję **CustomerRibbon.cs** lub **CustomerRibbon.vb,** aby ją wybrać.

4. W menu **View (Widok)** kliknij pozycję **Code (Kod).**

    Plik kodu wstążki zostanie otwarty w Edytorze kodu.

5. Dodaj następujące instrukcje na początku pliku kodu wstążki. Instrukcje te zapewniają łatwy dostęp do przestrzeni nazw LINQ i przestrzeni nazw podstawowego zestawu międzyoptykowego (PIA) programu Outlook.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet1":::

6. Dodaj następujący kod wewnątrz `CustomerRibbon` klasy . Ten kod deklaruje tabele danych i karty tabel, których będziesz używać do przechowywania informacji z tabel Customer (Klient), Orders (Zamówienia), Order Details (Szczegóły zamówienia) i Product (Produkt) w bazie danych Northwind.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet2":::

7. Dodaj następujący blok kodu do `CustomerRibbon` klasy . Ten kod dodaje trzy metody pomocnika, które tworzą kontrolki dla wstążki w czasie uruchamiania.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet3":::

8. Zastąp metodę `CustomerRibbon_Load` procedury obsługi zdarzeń poniższym kodem. Ten kod używa zapytania LINQ do wykonywania następujących zadań:

   - Wypełnij pole **kombi Klienci,** używając identyfikatora i nazwy 20 klientów w bazie danych Northwind.

   - Wywołuje `PopulateSalesOrderInfo` metodę pomocnika . Ta metoda aktualizuje menu **ProductsPurchased o** numery zamówień sprzedaży dotyczące aktualnie wybranego klienta.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet4":::

9. Dodaj poniższy kod do klasy `CustomerRibbon`. Ten kod używa zapytań LINQ do wykonywania następujących zadań:

   - Dodaje podmenu do **ProductsPurchased** menu dla każdego zamówienia sprzedaży powiązanego z wybranym klientem.

   - Dodaje przyciski do każdego podmenu dla produktów powiązanych z zamówieniem sprzedaży.

   - Dodaje procedury obsługi zdarzeń do każdego przycisku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet6":::

10. W **Eksplorator rozwiązań** kliknij dwukrotnie plik kodu wstążki.

     Zostanie otwarty Projektant wstążki.

11. W Projektancie wstążki kliknij dwukrotnie pole **kombi** Klienci.

     Plik kodu wstążki zostanie otwarty w Edytorze kodu i zostanie `ComboBox1_TextChanged` wyświetlony program obsługi zdarzeń.

12. Zastąp program `ComboBox1_TextChanged` obsługi zdarzeń następującym kodem. Ten kod wykonuje następujące zadania:

    - Wywołuje `PopulateSalesOrderInfo` metodę pomocnika . Ta metoda aktualizuje menu **Produkty zakupione** przy użyciu zamówień sprzedaży, które odnoszą się do wybranego klienta.

    - Wywołuje metodę `PopulateMailItem` pomocnika i przekazuje bieżący tekst, który jest wybraną nazwą klienta. Ta metoda wypełnia pola Do, Temat i Treść nowych wiadomości e-mail.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet5":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet5":::

13. Dodaj następującą `Click` obsługę zdarzeń do klasy `CustomerRibbon` . Ten kod dodaje nazwy wybranych produktów do pola Treść nowych wiadomości e-mail.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet8":::

14. Dodaj poniższy kod do klasy `CustomerRibbon`. Ten kod wykonuje następujące zadania:

    - Wypełnia wiersz Do nowych wiadomości e-mail przy użyciu adresu e-mail aktualnie wybranego klienta.

    - Dodaje tekst do pól Temat i Treść nowych wiadomości e-mail.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet7":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet7":::

## <a name="test-the-controls-in-the-custom-group"></a>Testowanie kontrolek w grupie niestandardowej

Po otwarciu nowego formularza poczty w programie Outlook na  karcie Wiadomości na wstążce zostanie wyświetlona grupa niestandardowa o nazwie **Zakupy** klientów.

Aby utworzyć wiadomość e-mail z kolejnej wiadomości e-mail klienta, wybierz klienta, a następnie wybierz produkty zakupione przez klienta. Kontrolki w grupie **Zakupy klientów** są aktualizowane w czasie rzeczywistym przy użyciu danych z bazy danych Northwind.

### <a name="to-test-the-controls-in-the-custom-group"></a>Aby przetestować kontrolki w grupie niestandardowej

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

     Program Outlook jest uruchamiany.

2. W programie Outlook w menu **Plik** wskaż pozycję **Nowy,** a następnie kliknij pozycję **Wiadomość e-mail.**

     Wykonywane są następujące akcje:

    - Zostanie wyświetlone nowe okno Inspektor wiadomości e-mail.

    - Na karcie **Komunikat** na wstążce grupa **Zakupy** klienta zostanie wyświetlona przed grupą **Schowek.**

    - Pole **kombi** Klienci w grupie zostanie zaktualizowane o nazwy klientów w bazie danych Northwind.

3. Na karcie **Komunikat** na wstążce w grupie **Zakupy** klienta wybierz klienta z **pola kombi** Klienci.

     Wykonywane są następujące akcje:

    - Menu **Zakupione produkty** zostanie zaktualizowane w celu pokazania każdego zamówienia sprzedaży dla wybranego klienta.

    - Każde podmenu zamówienia sprzedaży jest aktualizowane w celu pokazania produktów zakupionych w tym zamówieniu.

    - Wybrany adres e-mail klienta zostanie  dodany do wiersza Do wiadomości e-mail, a temat i treść wiadomości e-mail zostaną wypełnione tekstem.

4. Kliknij menu **Zakupy produktów,** wskaż dowolne zamówienie sprzedaży, a następnie kliknij produkt w zamówieniu sprzedaży.

     Nazwa produktu jest dodawana do treści wiadomości e-mail.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat dostosowywania interfejsu użytkownika pakietu Office można znaleźć w tych tematach:

- Dodaj kontekstowy interfejs użytkownika do dowolnego dostosowania na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md).

- Rozszerzanie standardowego lub niestandardowego Microsoft Office formularza programu Outlook. Aby uzyskać więcej informacji, zobacz [Przewodnik: projektowanie regionu formularza programu Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

- Dodaj niestandardowe okienko zadań do programu Outlook. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Zapytanie o języku zintegrowanym (LINQ)](/dotnet/csharp/linq/index)
- [Przewodnik: wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md)
- [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Jak zmienić położenie karty na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Jak dostosować wbudowaną kartę](../vsto/how-to-customize-a-built-in-tab.md)
- [Jak dodać kontrolki do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [How to: Export a ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcji: pokazywanie błędów interfejsu użytkownika dodatku](../vsto/how-to-show-add-in-user-interface-errors.md)