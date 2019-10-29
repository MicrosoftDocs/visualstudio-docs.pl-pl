---
title: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e78594a98066dec6cedff6da6f3f1de823bec796
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985013"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint
  W poniższych procedurach pokazano, jak utworzyć niestandardowe kolumny witryny programu SharePoint — lub *pola*— a także typ zawartości, która używa kolumn witryny. Przedstawiono w nim również sposób tworzenia listy korzystającej z nowego typu zawartości.

 Ten instruktaż zawiera następujące zagadnienia:

- [Utwórz niestandardowe kolumny witryny](#create-custom-site-columns).

- [Utwórz niestandardowy typ zawartości](#create-a-custom-content-type).

- [Utwórz listę](#create-a-list).

- [Przetestuj aplikację](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Tworzenie niestandardowych kolumn witryny
 Ten przykład tworzy listę do zarządzania pacjentami w szpitalu. Najpierw należy utworzyć projekt programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i dodać do niego kolumny witryny w następujący sposób.

#### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. W menu **plik** [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wybierz pozycję **Nowy** > **projekt**.

2. W oknie **dialogowym Nowy projekt** w obszarze **Wizualizacja C#**  lub **Visual Basic**rozwiń węzeł **SharePoint** , a następnie wybierz pozycję **2010**.

3. W okienku **Szablony** wybierz pozycję **projekt programu SharePoint 2010**, Zmień nazwę projektu na **klinikę**, a następnie wybierz przycisk **OK** .

     Szablon projektu programu SharePoint 2010 jest pustym projektem używanym w tym przykładzie do przechowywania kolumn lokacji i innych elementów projektu, które są dodawane później.

4. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź adres URL lokalnej witryny programu SharePoint, do której chcesz dodać nowy element pola niestandardowego, lub Użyj domyślnej lokalizacji (`http://<`*SystemName*`>/)`.

5. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** Użyj wartości domyślnej **wdrożonej jako rozwiązanie w trybie piaskownicy**.

     Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy i farmie, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

6. Wybierz przycisk **Zakończ** . Projekt jest teraz wymieniony w **Eksplorator rozwiązań**.

#### <a name="to-add-site-columns"></a>Aby dodać kolumny witryny

1. Dodaj nową kolumnę witryny. W tym celu w **Eksplorator rozwiązań**Otwórz menu skrótów dla **kliniki**, a następnie wybierz polecenie **Dodaj** > **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz **kolumnę lokacja**, Zmień nazwę na **nazwę pacjenta**, a następnie wybierz przycisk **Dodaj** .

3. W pliku *. XML* kolumny witryny pozostaw ustawienie **Typ** jako **tekst**i zmień ustawienie **grupy** na **kolumny witryny kliniki**. Po zakończeniu, plik *. XML* kolumny witryny powinien wyglądać podobnie do poniższego przykładu.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4. Korzystając z tej samej procedury, Dodaj dwie więcej kolumn lokacji do projektu: **pacjenta ID** (Type = "Integer") i **nazwisko lekarza** (Type = "text"). Ustaw wartość grupy na **kolumny witryny kliniki**.

## <a name="create-a-custom-content-type"></a>Tworzenie niestandardowego typu zawartości
 Następnie Utwórz typ zawartości — na podstawie typu zawartości kontakty — zawierającego kolumny lokacji utworzone w poprzedniej procedurze. Tworząc typ zawartości w istniejącym typie zawartości, można zaoszczędzić czas, ponieważ podstawowy typ zawartości udostępnia kilka kolumn witryny do użycia w nowym typie zawartości.

#### <a name="to-create-a-custom-content-type"></a>Aby utworzyć niestandardowy typ zawartości

1. Dodaj typ zawartości do projektu. W tym celu w **Eksplorator rozwiązań**wybierz węzeł projektu

2. Na pasku menu wybierz **projekt**  > **Dodaj nowy element**.

3. W obszarze **Wizualizacja C#**  lub **Visual Basic**rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. W okienku **Szablony** wybierz szablon **Typ zawartości** , Zmień nazwę na dane **pacjenta**, a następnie wybierz przycisk **Dodaj** .

     Zostanie otwarty **Kreator dostosowania programu SharePoint** .

5. W **której podstawowym typie zawartości powinien dziedziczyć ten typ zawartości z** listy, wybierz opcję **kontakt** jako typ zawartości, dla której ma zostać utworzony nowy typ zawartości, a następnie wybierz przycisk **Zakończ** .

     W ten sposób można uzyskać dostęp do innych potencjalnie przydatnych kolumn witryny w typie zawartości kontakt, a także zdefiniowanych wcześniej kolumn lokacji.

6. Po pojawieniu się projektanta typów zawartości na karcie **kolumny** Dodaj trzy zdefiniowane wcześniej kolumny lokacji: **nazwę pacjenta**, **identyfikator pacjenta**i **nazwę lekarza**. Aby dodać te kolumny, wybierz pierwsze pole listy z listy kolumny witryny w obszarze **Nazwa wyświetlana**, a następnie wybierz kolumnę każdej witryny na liście po jednej naraz.

    > [!TIP]
    > Aby szybciej wybierać kolumny witryny, przefiltruj listę, wprowadzając kilka pierwszych liter nazwy kolumny.

7. Oprócz trzech niestandardowych kolumn lokacji, Dodaj kolumnę Witryna **Komentarze** z listy kolumny witryny.

8. Zaznacz pole wyboru **wymagane** dla kolumny **Nazwa pacjenta** i **identyfikator pacjenta** , aby wprowadzić wymagane pola.

9. Na karcie **Typ zawartości** upewnij się, że nazwa typu zawartości to dane **pacjenta**, a następnie Zmień opis na **kartę Informacje o pacjentach**.

10. Zmień **nazwę grupy** na **typy zawartości kliniki**, a pozostałe ustawienia pozostaw wartości domyślne.

11. Na pasku menu wybierz kolejno opcje **plik** > **Zapisz wszystko**, a następnie zamknij projektanta typów zawartości.

## <a name="create-a-list"></a>Utwórz listę
 Teraz Utwórz listę, która używa nowego typu zawartości i kolumn lokacji.

#### <a name="to-create-a-list"></a>Aby utworzyć listę

1. Dodaj listę do projektu. W tym celu w **Eksplorator rozwiązań**wybierz węzeł projektu.

2. Na pasku menu wybierz **projekt**  > **Dodaj nowy element**.

3. W obszarze **Wizualizacja C#**  lub **Visual Basic**rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. W okienku **Szablony** wybierz szablon **listy** , Zmień nazwę na **pacjentów**, a następnie wybierz przycisk **Dodaj** .

5. Pozostaw pole wyboru **Dostosuj listę na podstawie** ustawienia jako **domyślne (puste)** , a następnie wybierz przycisk **Zakończ** .

6. W projektancie listy wybierz przycisk **typy zawartości** , aby wyświetlić okno dialogowe **Ustawienia typu zawartości** .

7. Wybierz nowy wiersz, wybierz typ zawartości **Informacje o pacjentach** z listy typów zawartości, a następnie wybierz przycisk **OK** .

     Spowoduje to dodanie wszystkich kolumn witryny z typu zawartości **Informacje o pacjentu** do listy.

8. Usuń wszystkie kolumny witryny z listy, z wyjątkiem następujących:

    - Identyfikator pacjenta

    - Nazwa pacjenta

    - Telefon domowy

    - E-Mail

    - Nazwa lekarza

    - Komentarze

9. W obszarze **Nazwa wyświetlana kolumny**Wybierz pusty wiersz, Dodaj niestandardową kolumnę listy i nadaj jej nazwę **Szpital**. Pozostaw swój typ danych jako **pojedynczy wiersz tekstu**.

     Niestandardowa kolumna listy ma zastosowanie tylko do tej listy. Po dodaniu niestandardowej kolumny listy do listy jest tworzony i ustawiany nowy typ zawartości listy, w tym wszystkie kolumny dodane do listy.

    > [!TIP]
    > W przypadku wybrania kolumny z listy kolumn lokacji zostanie użyta istniejąca kolumna witryny. Jeśli jednak wprowadzisz wartość nazwy kolumny bez wybierania kolumn na liście, zostanie utworzona niestandardowa kolumna listy, nawet jeśli kolumna o takiej samej nazwie już istnieje na liście.

     Opcjonalnie, zamiast ustawiać typ danych dla niestandardowej kolumny listy na **pojedynczy wiersz tekstu**, zamiast tego można ustawić typ danych dla tej kolumny na odnośnik, a jego wartości zostaną pobrane z tabeli lub innej listy. Aby uzyskać informacje na temat kolumn odnośników, zobacz [Lista relacji w programie SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) , [Wyszukiwanie i relacje listy](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Obok pola **identyfikator pacjenta** i **Nazwa pacjenta** zaznacz pole wyboru **wymagane** .

11. Na karcie **widoki** Wybierz pusty wiersz, aby utworzyć widok. Wprowadź **szczegóły pacjenta**.

     Na karcie **widoki** możesz określić kolumny, które mają być wyświetlane na liście programu SharePoint.

12. Wybierz wiersz **szczegóły nowego pacjenta** , a następnie wybierz przycisk **Ustaw jako domyślny** .

     Nowy widok jest teraz widokiem domyślnym listy.

13. Dodaj następujące kolumny do listy **wybrane kolumny** w następującej kolejności:

    - Identyfikator pacjenta

    - Nazwa pacjenta

    - Telefon domowy

    - E-Mail

    - Nazwa lekarza

    - Warunkach

    - Komentarze

14. Na liście **Właściwości** wybierz właściwość **Sortowanie i grupowanie** , a następnie wybierz ikonę wielokropka ![ikony](../sharepoint/media/ellipsisicon.gif "Ikona wielokropka") wielokropka, aby wyświetlić okno dialogowe **Sortowanie i grupowanie** .

15. Na liście **Nazwa kolumny** wybierz pozycję **Nazwa pacjenta**, upewnij się, że w **kolumnie sortowanie** jest ustawiona wartość **rosnąco**, a następnie wybierz przycisk **OK** .

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz, gdy niestandardowe kolumny witryny, typ zawartości i lista są gotowe, wdróż je w programie SharePoint i uruchom aplikację w celu jej przetestowania.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Na pasku menu wybierz kolejno opcje **plik**  > **Zapisz wszystko**.

2. Wybierz klawisz **F5** , aby uruchomić aplikację.

     Aplikacja została skompilowana, a następnie jej funkcje są wdrażane w programie SharePoint i aktywowane.

3. Na pasku Szybki pasek nawigacyjny wybierz łącze **pacjentów** , aby wyświetlić listę **pacjentów** .

     Nazwy kolumn na liście powinny być zgodne z ustawieniami wprowadzonymi na karcie **widoki** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4. Wybierz link **Dodaj nowy element** , aby utworzyć kartę informacji pacjenta.

5. Wprowadź informacje w polach, a następnie wybierz przycisk **Zapisz** .

     Nowy rekord zostanie wyświetlony na liście.

## <a name="see-also"></a>Zobacz także
- [Tworzenie kolumn witryn, typów zawartości i list dla programu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Instrukcje: Tworzenie niestandardowego typu pola](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Typy zawartości](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
