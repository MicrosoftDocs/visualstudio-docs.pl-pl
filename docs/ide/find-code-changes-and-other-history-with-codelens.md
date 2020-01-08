---
title: Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9859366f6e4b9a0d1c219adc2080e6415b1e44a7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588658"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens

Usługa CodeLens umożliwia skoncentrowanie się na pracy w czasie, gdy dowiesz się, co się stało z kodem&ndash;bez opuszczania edytora. Można znaleźć odwołania do fragmentu kodu, zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens jest dostępny w programie Visual Studio Community Edition, jednak wskaźniki *kontroli źródła* nie są dostępne w tej wersji.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens jest dostępna tylko w wersjach Visual Studio Enterprise i Professional. Nie jest on dostępny w programie Visual Studio Community Edition.

::: moniker-end

Zobacz, gdzie i w jaki sposób poszczególne części kodu są używane w rozwiązaniu:

![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelens-overview.png)

Skontaktuj się z zespołem, aby dowiedzieć się o zmianach w kodzie bez opuszczania edytora:

![CodeLens — skontaktuj się z zespołem](../ide/media/codelens-contact-info.png)

Aby wybrać wskaźniki, które chcesz wyświetlić, lub aby wyłączyć CodeLens i włączony, przejdź do pozycji **narzędzia** > **Opcje** > **edytor tekstów** > **wszystkie języki** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Znajdowanie odwołań do kodu

Odwołania można znaleźć w C# kodzie lub Visual Basic.

1. Wybierz wskaźnik **odwołania** lub naciśnij **Alt**+**2**.

   ![Odwołania CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Jeśli wskaźnik pokazuje **0 odwołań**, nie masz odwołań C# ani Visual Basic kodzie. Mogą jednak znajdować się odwołania w innych elementach, takich jak pliki *. XAML* i *. aspx* .

2. Aby wyświetlić kod odwołujący, wskaźnik myszy nad odwołaniem na liście.

   ![CodeLens — odwołanie](../ide/media/codelens-peek-reference.png)

3. Aby otworzyć plik, który zawiera odwołanie, kliknij dwukrotnie odwołanie.

### <a name="code-maps"></a>Mapy kodu

Aby wyświetlić relacje między kodem i jego odwołaniami, [Utwórz mapę kodu](../modeling/map-dependencies-across-your-solutions.md). W menu skrótów mapy kodu wybierz pozycję **Pokaż wszystkie odwołania**.

![CodeLens — odwołania na mapie kodu](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Znajdowanie zmian w kodzie

Sprawdź historię kodu, aby dowiedzieć się, co się stało z kodem. Możesz też przejrzeć zmiany przed ich scaleniem z kodem, aby lepiej zrozumieć, jak zmiany w innych gałęziach mogą wpłynąć na kod.

Potrzebne elementy:

- Visual Studio Enterprise lub wersja Professional

- Azure DevOps Services, Team Foundation Server 2013 lub nowszy lub git

- [Skype dla firm](/skypeforbusiness/) , aby skontaktować się z zespołem w edytorze kodu

W C# przypadku kodu lub Visual Basic, który jest przechowywany za pomocą Kontrola wersji serwera Team Foundation (TFVC) lub git, uzyskasz szczegóły CodeLens na poziomach klasy i metody (wskaźniki*poziomu elementów kodu* ). Jeśli repozytorium git jest hostowane w usłudze TfGit, uzyskasz także linki do elementów roboczych TFS.

![Wskaźniki poziomu elementów kodu](../ide/media/codelens-element-level-indicators.png)

W przypadku typów plików innych niż *. cs* lub *. vb*uzyskasz CodeLens szczegóły dotyczące całego pliku w jednym miejscu w dolnej części okna (wskaźniki*poziomu plików* ).

![Wskaźniki CodeLens na poziomie plików](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Wskaźniki poziomu elementów kodu

Wskaźniki poziomu elementów kodu pozwalają zobaczyć, kto zmienił swój kod i jakie zmiany zostały wprowadzone. Wskaźniki poziomu elementów kodu są dostępne dla C# i Visual Basic kodzie.

Jest to widoczne w przypadku używania Kontrola wersji serwera Team Foundation (TFVC) w Team Foundation Server lub Azure DevOps Services:

![CodeLens: Pobierz historię zmian dla kodu w TFVC](../ide/media/codelens-code-changes.png)

Domyślny okres to ostatnie 12 miesięcy. Jeśli kod jest przechowywany w Team Foundation Server, można zmienić okres, uruchamiając [Polecenie TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) z [poleceniem CodeIndex](../ide/codeindex-command.md) i flagą **/indexHistoryPeriod** .

Aby wyświetlić szczegółową historię wszystkich zmian, włącznie z tymi, które pochodzą z więcej niż roku temu, wybierz **Pokaż wszystkie zmiany plików**:

![Pokaż wszystkie zmiany kodu](../ide/media/codelens-show-all-file-changes.png)

Zostanie otwarte okno **historia** :

![Okno historii dla wszystkich zmian kodu](../ide/media/codelenscodechangeshistory.png)

Gdy pliki znajdują się w repozytorium git i wybierasz wskaźnik zmian na poziomie elementu kodu, zobaczysz, co widzisz:

![CodeLens: Pobierz historię zmian dla kodu w usłudze git](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Wskaźniki poziomu plików

Znajdź zmiany dla całego pliku w wskaźnikach poziomu plików w dolnej części okna:

![CodeLens: Pobierz szczegóły pliku kodu](../ide/media/codelens-file-level.png)

> [!NOTE]
> Wskaźniki poziomu plików są niedostępne dla C# plików i Visual Basic.

Aby uzyskać więcej szczegółowych informacji na temat zmiany, kliknij prawym przyciskiem myszy ten element. W zależności od tego, czy korzystasz z usługi TFVC, czy git, dostępne są opcje porównywania wersji pliku, wyświetlania szczegółów i śledzenia zestawu zmian, pobierania wybranej wersji pliku i wysyłania wiadomości e-mail do autora tej zmiany. Niektóre z tych szczegółów są wyświetlane w **Team Explorer**.

Możesz również zobaczyć, kto zmienił swój kod w czasie. Może to pomóc Ci znaleźć wzorce w zmiany swojego zespołu i ocena ich skutków.

![CodeLens: Zobacz historię zmian kodu jako Graf](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Znajdź zmiany w bieżącej gałęzi

Zespół może mieć wiele rozgałęzień, na przykład główną gałąź i podrzędną gałąź programistyczną, aby zmniejszyć ryzyko związanego z uszkodzeniem stabilnego kodu.

![CodeLens: Znajdź, kiedy nastąpiło rozgałęzienie kodu](../ide/media/codelensfirstbranchconceptual.png)

Aby dowiedzieć się, ile osób zmieniło kod i ile zmian zostało wprowadzonych w głównej gałęzi, naciśnij **Alt**+**6**:

![CodeLens: Znajdź, ile zmian w gałęzi](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Znajdź, kiedy nastąpiło rozgałęzienie kodu

Aby sprawdzić, kiedy kod został rozgałęzienia, przejdź do kodu w gałęzi podrzędnej. Następnie wybierz wskaźnik **zmiany** lub naciśnij **Alt**+**6**:

![CodeLens: Znajdź, kiedy nastąpiło rozgałęzienie kodu](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Znajdź przychodzące zmiany z innych gałęzi

![CodeLens: Znajdź zmiany kodu w innych gałęziach](../ide/media/codelensbranchchangecheckinconceptual.png)

Można przeglądać zmiany przychodzące. Na poniższym zrzucie ekranu wprowadzono poprawkę błędu w gałęzi "dev":

![CodeLens: Zmień zaznaczenie na inną gałąź](../ide/media/codelens-branch-changes-dev.png)

Możesz przejrzeć zmiany bez opuszczania bieżącej gałęzi ("Main"):

![CodeLens: Zobacz zmiany przychodzące z innej gałęzi](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Znajdź, kiedy zmiany zostały scalone

Możesz zobaczyć, kiedy zmiany zostały scalone, więc możesz określić, które zmiany są zawarte w gałęzi:

![CodeLens — scalone zmiany między gałęziami](../ide/media/codelensbranchmergedconceptual.png)

Na przykład kod w gałęzi głównej zawiera teraz poprawkę błędu z gałęzi "dev":

![CodeLens — scalone zmiany między gałęziami](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porównanie przychodzącej zmiany z wersją lokalną

Porównaj zmiany przychodzące z lokalną wersją, naciskając klawisz **Shift**+**F10**lub klikając dwukrotnie zestaw zmian.

![CodeLens: Porównaj przychodzące zmiany z lokalną](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony gałęzi

Ikona w kolumnie **rozgałęzienie** informuje, w jaki sposób gałąź jest związana z gałęzią, w której pracujesz.

|**Ikona**|**Zmiana pochodzi z:**|
|--------------| - |
|![CodeLens: Zmień ikonę z bieżącej gałęzi](../ide/media/codelensbranchcurrenticon.png)|Bieżąca gałąź|
|![CodeLens: Zmień z ikony gałęzi nadrzędnej](../ide/media/codelensbranchparenticon.png)|Gałąź nadrzędna|
|![CodeLens: Zmień z ikony gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png)|Gałąź podrzędna|
|![CodeLens: Zmień ikonę gałęzi równorzędnej](../ide/media/codelensbranchpeericon.png)|Gałąź równorzędna|
|![CodeLens: Przejdź do dalszej ikony gałęzi](../ide/media/codelensbranchfurtherawayicon.png)|Gałąź poza elementem nadrzędnym, podrzędnym lub równorzędnym|
|![CodeLens: Scal z ikony nadrzędnej](../ide/media/codelensbranchmergefromparenticon.png)|Scalanie z gałęzi nadrzędnej z gałęzią podrzędną|
|![CodeLens: Scal z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png)|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|
|![CodeLens: scalanie z ikony niepowiązanej gałęzi](../ide/media/codelensbranchmergefromunrelatedicon.png)|Scalanie z niepowiązanej gałęzi (bez podstawy merge)|

## <a name="linked-work-items"></a>Połączone elementy robocze

Znajdź połączone elementy robocze, wybierając wskaźnik **elementów roboczych** lub naciskając **Alt**+**8**.

![CodeLens — Wyszukiwanie elementów roboczych dla określonego kodu](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Recenzje kodu połączonego

Znajdź połączone przeglądy kodu, wybierając wskaźnik **Recenzje** . Aby użyć klawiatury, przytrzymaj klawisz **Alt** , a następnie naciśnij strzałkę w **lewo** lub **strzałkę w prawo** , aby przejść do opcji wskaźnika.

![CodeLens — Wyświetl żądania przeglądu kodu](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Połączone usterki

Znajdź połączone usterki poprzez wybranie wskaźnika **błędów** lub naciśnięcie klawisza **Alt**+**7**.

![CodeLens — Znajdź usterki połączone z zestawami zmian](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem elementu

Znajdź autora elementu, wybierając wskaźnik **autorów** lub naciskając klawisz **Alt**+**5**.

![Skontaktuj się z właścicielem elementu](../ide/media/codelens-contact-item-owner.png)

Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz zainstalowany program Lync lub Skype dla firm, zobaczysz następujące opcje:

![Opcje kontaktu dla elementu](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Skojarzone testy jednostkowe

Możesz odnaleźć testy jednostkowe, które istnieją dla C# kodu lub Visual Basic, bez otwierania **Eksploratora testów**.

1. Przejdź do kodu aplikacji, który ma skojarzony [kod testu jednostkowego](../test/unit-test-your-code.md).

2. Jeśli jeszcze tego nie zrobiono, skompiluj aplikację w celu załadowania wskaźników testu CodeLens. 

3. Przejrzyj testy dla kodu, naciskając klawisz **Alt**+**3**.

     ![CodeLens — wybierz stan testu w edytorze kodu](../ide/media/codelens-choose-test-indicator.png)

4. Jeśli zostanie wyświetlona ikona ostrzeżenia ![ikona ostrzeżenia](../ide/media/codelenstestwarningicon.png)testy nie zostały jeszcze uruchomione, dlatego należy je uruchomić.

     ![CodeLens — testy jednostkowe nie zostały jeszcze uruchomione](../ide/media/codelens-tests-not-yet-run.png)

5. Aby przejrzeć definicję testu, kliknij dwukrotnie element testu w oknie wskaźnika CodeLens, aby otworzyć plik kodu w edytorze.

     ![CodeLens — przejdź do definicji testu jednostkowego](../ide/media/codelens-unit-test-definition.png)

6. Aby przejrzeć wyniki testu, wybierz ikonę wskaźnik stanu testu (![nie powiodła się ikona](../ide/media/codelenstestfailedicon.png) lub ![zakończono test](../ide/media/codelenstestpassedicon.png)) lub naciśnij **kombinację klawiszy Alt**+**1**.

     ![CodeLens — Zobacz wyniki testu jednostkowego](../ide/media/codelens-unit-test-result.png)

7. Aby zobaczyć, ile osób zmieniło ten test, kto zmienił ten test lub ile zmian zostało wprowadzonych w tym teście, [Znajdź historię kodu](#find-changes-in-your-code) i połączone elementy.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Aby wybrać wskaźniki przy użyciu klawiatury, naciśnij i przytrzymaj klawisz **Alt** , aby wyświetlić powiązane klucze liczbowe, a następnie naciśnij liczbę odpowiadającą wskaźnikowi, który chcesz wybrać.

![Numery dostępu klawiaturowego](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Aby wybrać wskaźnik **przeglądów** , przytrzymaj wciśnięty klawisz **Alt** przy użyciu klawiszy strzałek w lewo i w prawo, aby przejść.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>P: Jak mogę wyłączyć lub włączyć CodeLens lub wybrać wskaźniki, które mają być wyświetlane?

Odp **.:**  Można wyłączyć lub włączyć wskaźniki, z wyjątkiem wskaźnika odwołań. Przejdź do pozycji **narzędzia** > **Opcje** > **edytor tekstów** > **wszystkie języki** > **CodeLens**.

Po włączeniu wskaźników można także otworzyć Opcje CodeLens z wskaźników.

![CodeLens — włącza lub wyłącza wskaźniki](../ide/media/codelensturnoffonindicatorsfromcode.png)

Włącz i Wyłącz wskaźniki na poziomie plików CodeLens przy użyciu ikon Pagon u dołu okna edytora.

![Włącz i Wyłącz wskaźniki na poziomie plików](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>P: gdzie jest CodeLens?

Odp **.:** CodeLens pojawia się C# w i Visual Basic kod na poziomie metody, klasy, indeksatora i właściwości. CodeLens pojawia się na poziomie pliku dla wszystkich innych typów plików.

- Upewnij się, że CodeLens jest włączona. Przejdź do pozycji **narzędzia** > **Opcje** > **edytor tekstów** > **wszystkie języki** > **CodeLens**.

- Jeśli kod jest przechowywany w programie TFS, upewnij się, że indeksowanie kodu jest włączone przy użyciu [polecenia CodeIndex](../ide/codeindex-command.md) z [poleceniem TFS config](/azure/devops/server/command-line/tfsconfig-cmd).

- Wskaźniki powiązane z DevOps są wyświetlane tylko wtedy, gdy elementy robocze są połączone z kodem i gdy masz uprawnienia do otwierania połączonych elementów roboczych. Upewnij się, że masz [uprawnienia członka zespołu](/azure/devops/organizations/security/view-permissions?view=vsts).

- Wskaźniki testów jednostkowych nie są wyświetlane, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji ma testy jednostkowe, ale nie pojawiają się wskaźniki testów, spróbuj skompilować rozwiązanie (**Ctrl**+**SHIFT**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens jest dostępny w programie Visual Studio Community Edition, jednak wskaźniki *kontroli źródła* nie są dostępne w tej wersji.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens nie jest dostępna w programie Visual Studio Community Edition.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>P: Dlaczego nie widzę szczegółów elementu pracy dla zatwierdzenia?

Odp **.:** Może się tak zdarzyć, ponieważ CodeLens nie może znaleźć elementów roboczych w Azure Boards lub TFS. Sprawdź, czy nawiązano połączenie z projektem zawierającym te elementy robocze i czy masz uprawnienia do wyświetlania tych elementów roboczych. Szczegóły elementu pracy mogą również nie być wyświetlane, jeśli opis zatwierdzenia zawiera nieprawidłowe informacje o identyfikatorach elementów roboczych w Azure Boards lub TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>P: Dlaczego nie widzę wskaźników Skype'a?

Odp **.:** Wskaźniki Skype nie są wyświetlane, jeśli nie zarejestrowano Cię w usłudze Skype dla firm, nie zainstalowano jej lub nie masz obsługiwanej konfiguracji. Nadal jednak możesz wysyłać wiadomości e-mail:

![CodeLens — skontaktuj się z właścicielem grupy zmian przez pocztę](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Które konfiguracje Skype'a i Lync są obsługiwane?**

- Skype dla firm (32-bitowe lub 64-bitowe)

- Program Lync 2010 lub nowszy (32-bitowy lub 64-bitowy), ale nie Lync Basic 2013 z Windows 8.1

CodeLens nie obsługuje różnych wersji programu Lync lub Skype zainstalowanych. Mogą nie być zlokalizowane dla wszystkich zlokalizowanych wersji programu Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>P: Jak mogę zmienić czcionkę i kolor dla CodeLens?

Odp **.:** Przejdź do pozycji **narzędzia** > **opcje** > **środowisko** > **czcionki i kolory**.

![CodeLens — Zmień ustawienia czcionek i kolorów](../ide/media/codelensoptionsfontscolorssettings.png)

Aby użyć klawiatury:

1. Naciśnij klawisz **Alt**+**t**+**o** , aby otworzyć okno dialogowe **Opcje** .

2. Naciśnij strzałkę w **górę** lub **strzałkę w dół** , aby przejść do węzła **środowisko** , a następnie naciśnij **strzałkę w lewo** , aby rozwinąć węzeł.

3. Naciśnij **strzałkę w dół** , aby przejść do **czcionek i kolorów**.

4. Naciśnij klawisz **Tab** , aby przejść do listy **Pokaż ustawienia dla** , a następnie naciśnij **strzałkę w dół** , aby wybrać **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Pyt.: Czy można przesunąć ekran projekcyjny CodeLens?

Odp **.:** Tak, wybierz ![ikonę dokowania](../ide/media/codelensdockwindow.png), aby zadokować CodeLens jako okno.

![Przycisk Dock w oknie wskaźnika CodeLens](../ide/media/codelensselectdockwindow.png)

![Okno zadokowanych odwołań CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Pyt.: Jak odświeżyć wskaźniki?

Odp **.:** Jest to zależne od wskaźnika:

- **Odwołania**: ten wskaźnik jest aktualizowany automatycznie po zmianie kodu. Jeśli wskaźnik **odwołań** jest zadokowany jako osobne okno, Odśwież wskaźnik, wybierając pozycję **Odśwież**:

   ![Przycisk Odśwież w odwołaniach CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Zespół**: Odśwież te wskaźniki, wybierając pozycję **Odśwież wskaźniki zespołu CodeLens** w menu rozwijanym prawym przyciskiem myszy:

   ![Element menu Odśwież wskaźniki zespołu CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [Znajdź testy jednostkowe dla kodu](#associated-unit-tests) , aby odświeżyć wskaźnik **testu** .

### <a name="q-whats-local-version"></a>P: co to jest "lokalna wersja"?

Odp **.:** Strzałka **wersja lokalna** wskazuje najnowszą grupę zmian w lokalnej wersji pliku. Gdy serwer ma nowsze zestawy zmian, są one wyświetlane powyżej lub poniżej strzałki **wersji lokalnej** , w zależności od kolejności użytej do sortowania zestawów zmian.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>P: Czy mogę zarządzać sposobem, w jaki CodeLens przetwarza kod, aby pokazać historię i połączone elementy?

**Odpowiedź:** tak. Jeśli Twój kod znajduje się w programie TFS, użyj [polecenia CodeIndex](../ide/codeindex-command.md) z [poleceniem TFS config](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>P: moje CodeLens wskaźniki testowe nie pojawiają się już w moim pliku po pierwszym otwarciu rozwiązania. Jak można je załadować?

Odp **.:** Skompiluj ponownie projekt, aby uzyskać CodeLens wskaźniki testów do załadowania pliku. Aby zwiększyć wydajność, program Visual Studio nie pobiera więcej informacji o źródłach dla wskaźników testów podczas ładowania plików kodu. Wskaźniki testowe są ładowane po kompilacji lub po przejściu do testu przez dwukrotne kliknięcie go w **Eksploratorze testów**.

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
