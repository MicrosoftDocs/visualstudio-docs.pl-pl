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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588658"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens

CodeLens pozwala skupić się na swojej pracy, podczas gdy&ndash;dowiesz się, co się stało z kodem bez opuszczania edytora. Można znaleźć odwołania do fragmentu kodu, zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens jest dostępny w wersji społeczności programu Visual Studio, jednak wskaźniki *kontroli źródła* nie są dostępne w tej wersji.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> Funkcja CodeLens jest dostępna tylko w wersjach visual studio enterprise i professional. Nie jest dostępna w programie Visual Studio Community edition.

::: moniker-end

Zobacz, gdzie i jak poszczególne części kodu są używane w rozwiązaniu:

![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelens-overview.png)

Skontaktuj się z zespołem w sprawie zmian w kodzie bez wychodzenia z edytora:

![CodeLens - Skontaktuj się ze swoim zespołem](../ide/media/codelens-contact-info.png)

Aby wybrać wskaźniki, które chcesz zobaczyć lub wyłączyć i włączyć funkcję CodeLens, przejdź do **pozycji** > **Opcje** > narzędzi**Edytor** > tekstu**Wszystkie języki** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Znajdowanie odniesień do kodu

Odwołania można znaleźć w kodzie języka C# lub Visual Basic.

1. Wybierz wskaźnik **odniesień** lub naciśnij klawisz **Alt**+**2**.

   ![Odwołania do funkcji CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Jeśli wskaźnik pokazuje **0 odwołania**, nie masz żadnych odwołań z kodu C# lub Visual Basic. Jednak mogą istnieć odwołania w innych elementach, takich jak *pliki xaml* i *.aspx.*

2. Aby wyświetlić kod odwołujący się, najedź myszką na odwołanie na liście.

   ![CodeLens — odwołanie do wglądu](../ide/media/codelens-peek-reference.png)

3. Aby otworzyć plik zawierający odwołanie, kliknij dwukrotnie odwołanie.

### <a name="code-maps"></a>Mapy kodu

Aby wyświetlić relacje między kodem a jego odwołaniami, [utwórz mapę kodu](../modeling/map-dependencies-across-your-solutions.md). W menu skrótów mapy kodu wybierz polecenie **Pokaż wszystkie odwołania**.

![CodeLens - Odwołania na mapie kodu](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Znajdowanie zmian w kodzie

Sprawdź historię kodu, aby dowiedzieć się, co się stało z twoim kodem. Możesz też przejrzeć zmiany przed scaleniem ich z kodem, aby lepiej zrozumieć, jak zmiany w innych gałęziach mogą wpływać na kod.

Potrzebne elementy:

- Visual Studio Enterprise lub Professional edition

- Usługi Azure DevOps, Team Foundation Server 2013 lub nowsze lub Git

- [Skype dla firm,](/skypeforbusiness/) aby skontaktować się z zespołem z edytora kodu

Dla kodu Języka C# lub Visual Basic, który jest przechowywany z Team Foundation Version Control (TFVC) lub Git, otrzymasz szczegóły CodeLens na poziomach klasy i metody (wskaźniki*na poziomie elementu kodu).* Jeśli repozytorium Git jest hostowane w TfGit, można również uzyskać łącza do elementów roboczych TFS.

![Wskaźniki na poziomie elementu kodu](../ide/media/codelens-element-level-indicators.png)

W przypadku typów plików innych niż *.cs* lub *.vb*otrzymasz szczegóły CodeLens dla całego pliku w jednym miejscu u dołu okna (wskaźniki*na poziomie pliku).*

![Wskaźniki CodeLens na poziomie pliku](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Wskaźniki na poziomie elementu kodu

Wskaźniki na poziomie elementu kodu pozwalają zobaczyć, kto zmienił kod i jakie zmiany zostały wprowadzone. Wskaźniki na poziomie elementu kodu są dostępne dla kodu Języka C# i Visual Basic.

Jest to, co widać podczas korzystania z Team Foundation Version Control (TFVC) w Team Foundation Server lub Usługi Azure DevOps:

![CodeLens: Pobierz historię zmian dla kodu w TFVC](../ide/media/codelens-code-changes.png)

Domyślny okres jest ostatnim 12 miesięcy. Jeśli kod jest przechowywany w team foundation server, można zmienić okres czasu, uruchamiając [polecenie TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) za pomocą [polecenia CodeIndex](../ide/codeindex-command.md) i **/indexHistoryPeriod** flagi.

Aby wyświetlić szczegółową historię wszystkich zmian, w tym tych sprzed ponad roku, wybierz pozycję **Pokaż wszystkie zmiany pliku:**

![Pokaż wszystkie zmiany kodu](../ide/media/codelens-show-all-file-changes.png)

Zostanie otwarte okno **Historia:**

![Okno Historia dla wszystkich zmian kodu](../ide/media/codelenscodechangeshistory.png)

Gdy pliki znajdują się w repozytorium Git i wybierasz wskaźnik zmian na poziomie elementu kodu, to jest to, co widzisz:

![CodeLens: Pobierz historię zmian dla kodu w Git](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Wskaźniki na poziomie pliku

Znajdź zmiany dla całego pliku we wskaźnikach na poziomie pliku w dolnej części okna:

![CodeLens: Pobierz szczegóły pliku kodu](../ide/media/codelens-file-level.png)

> [!NOTE]
> Wskaźniki na poziomie pliku nie są dostępne dla plików C# i Visual Basic.

Aby uzyskać więcej informacji na temat zmiany, kliknij prawym przyciskiem myszy ten element. W zależności od tego, czy używasz TFVC lub Git, istnieją opcje porównywania wersji pliku, przeglądania szczegółów i śledzenia changeet, uzyskania wybranej wersji pliku i wysłania wiadomości e-mail do autora tej zmiany. Niektóre z tych szczegółów są wyświetlane w **Eksploratorze zespołu.**

Możesz również zobaczyć, kto zmienił twój kod w czasie. Może to pomóc ci znaleźć wzorce zmian w zespole i ocenić ich wpływ.

![CodeLens: Zobacz historię zmian kodu jako wykres](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Znajdowanie zmian w bieżącej gałęzi

Twój zespół może mieć wiele gałęzi, na przykład głównej gałęzi i gałęzi rozwoju podrzędnego, aby zmniejszyć ryzyko złamania kodu stabilnego.

![CodeLens: Znajdź, kiedy kod został rozgałęziony](../ide/media/codelensfirstbranchconceptual.png)

Możesz dowiedzieć się, ile osób zmieniło twój kod i ile zmian zostało wprowadzonych w głównej gałęzi, naciskając **klawisz Alt**+**6**:

![CodeLens: Znajdź liczbę zmian w gałęzi](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Znajdowanie, kiedy kod został rozgałęziony

Aby znaleźć, kiedy kod został rozgałęziony, przejdź do kodu w gałęzi podrzędnej. Następnie wybierz wskaźnik **zmian** lub naciśnij klawisz **Alt**+**6**:

![CodeLens: Znajdź, kiedy kod został rozgałęziony](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Znajdowanie zmian przychodzących z innych gałęzi

![CodeLens: Znajdź zmiany kodu w innych oddziałach](../ide/media/codelensbranchchangecheckinconceptual.png)

Można wyświetlić zmiany przychodzące. Na poniższym zrzucie ekranu została podjęta poprawka błędu w gałęzi "Dev":

![CodeLens: Zmiana zaewidencjonowana w innej gałęzi](../ide/media/codelens-branch-changes-dev.png)

Możesz przejrzeć zmianę bez opuszczania bieżącej gałęzi ("Main"):

![CodeLens: Zobacz przychodzące zmiany z innej gałęzi](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Znajdowanie, kiedy zmiany zostały scalone

Możesz zobaczyć, kiedy zmiany zostały scalone, dzięki czemu można określić, które zmiany są uwzględnione w gałęzi:

![CodeLens — scalone zmiany między gałęziami](../ide/media/codelensbranchmergedconceptual.png)

Na przykład kod w gałęzi głównej ma teraz poprawkę błędu z gałęzi "Dev":

![CodeLens — scalone zmiany między gałęziami](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porównanie zmiany przychodzącej z wersją lokalną

Porównaj nadchodzącą zmianę z wersją lokalną, naciskając **klawisz Shift**+**F10**lub klikając dwukrotnie wstawki.

![CodeLens: Porównaj zmiany przychodzące z lokalnymi](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony gałęzi

Ikona w kolumnie **Gałąź** informuje, jak gałąź jest powiązana z gałęzią, w której pracujesz.

|**Ikona**:|**Zmiana nastąpiła z:**|
|--------------| - |
|![CodeLens: Zmień z bieżącej ikony gałęzi](../ide/media/codelensbranchcurrenticon.png)|Bieżąca gałąź|
|![CodeLens: Zmień ikonę gałęzi nadrzędnej](../ide/media/codelensbranchparenticon.png)|Oddział nadrzędny|
|![CodeLens: Zmień ikonę gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png)|Gałąź podrzędna|
|![CodeLens: Zmień ikonę gałęzi elementu równorzędnego](../ide/media/codelensbranchpeericon.png)|Gałąź elementu równorzędnego|
|![CodeLens: Zmień ikonę gałęzi dalej](../ide/media/codelensbranchfurtherawayicon.png)|Gałąź dalej niż rodzic, dziecko lub element równorzędny|
|![CodeLens: Scalanie z ikony nadrzędnej](../ide/media/codelensbranchmergefromparenticon.png)|Scalanie z gałęzi nadrzędnej do gałęzi podrzędnej|
|![CodeLens: Scalanie z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png)|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|
|![CodeLens: Scalanie z niepowiązanej gałęzi ikony](../ide/media/codelensbranchmergefromunrelatedicon.png)|Scalanie z niepowiązanej gałęzi (scalanie bezpodstawne)|

## <a name="linked-work-items"></a>Połączone elementy robocze

Znajdź połączone elementy robocze, wybierając wskaźnik **elementów roboczych** lub naciskając klawisz **Alt**+**8**.

![CodeLens — znajdowanie elementów roboczych dla określonego kodu](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Połączone recenzje kodu

Znajdź połączone recenzje kodu, wybierając wskaźnik **recenzji.** Aby użyć klawiatury, przytrzymaj klawisz **Alt,** a następnie naciśnij **strzałkę w lewo** lub **strzałkę w prawo,** aby poruszać się po opcjach wskaźnika.

![CodeLens — wyświetlanie żądań przeglądu kodu](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Połączone błędy

Znajdź połączone błędy, wybierając wskaźnik **błędów** lub naciskając **klawisz Alt**+**7**.

![CodeLens — znajdowanie błędów połączonych ze zmianami](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem towaru

Znajdź autora elementu, wybierając wskaźnik **autorów** lub naciskając klawisz **Alt**+**5**.

![Skontaktuj się z właścicielem towaru](../ide/media/codelens-contact-item-owner.png)

Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz zainstalowany program Lync lub Skype dla firm, zostaną wyświetlonych następujące opcje:

![Opcje kontaktu dla towaru](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Skojarzone testy jednostkowe

Można odkryć testy jednostkowe, które istnieją dla kodu Języka C# lub Visual Basic bez **otwierania Eksploratora testów**.

1. Przejdź do kodu aplikacji, który ma skojarzony [kod testu jednostkowego](../test/unit-test-your-code.md).

2. Jeśli jeszcze tego nie zrobiłeś, skompiluj aplikację, aby załadować wskaźniki testowe CodeLens. 

3. Przejrzyj testy kodu, naciskając klawisz **Alt**+**3**.

     ![CodeLens - Wybierz stan testu w edytorze kodu](../ide/media/codelens-choose-test-indicator.png)

4. Jeśli widzisz ikonę ostrzeżenia ![ikona ostrzeżenia](../ide/media/codelenstestwarningicon.png), testy jeszcze nie zostały uruchomione, więc uruchom je.

     ![CodeLens — wyświetlanie testów jednostkowych nie jest jeszcze uruchomionych](../ide/media/codelens-tests-not-yet-run.png)

5. Aby przejrzeć definicję testu, kliknij dwukrotnie element testu w oknie wskaźnika CodeLens, aby otworzyć plik kodu w edytorze.

     ![CodeLens — przejdź do definicji testu jednostkowego](../ide/media/codelens-unit-test-definition.png)

6. Aby przejrzeć wyniki testu, wybierz wskaźnik![stanu testu](../ide/media/codelenstestfailedicon.png) (ikona](../ide/media/codelenstestpassedicon.png)testu nie powiodło się lub ![ikona testu zdają) lub naciśnij klawisz **Alt**+**1**.

     ![CodeLens — zobacz wynik testu jednostkowego](../ide/media/codelens-unit-test-result.png)

7. Aby zobaczyć, ile osób zmieniło ten test, kto zmienił ten test lub ile zmian zostało wprowadzonych w tym teście, [znajdź historię kodu](#find-changes-in-your-code) i połączone elementy.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Aby użyć klawiatury do wybierania wskaźników, naciśnij i przytrzymaj klawisz **Alt,** aby wyświetlić powiązane klawisze numeryczne, a następnie naciśnij numer odpowiadający wskaźnikowi, który chcesz wybrać.

![Numery dostępu do klawiatury](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Aby wybrać wskaźnik **recenzji,** przytrzymaj naciśnięty **klawisz Alt** podczas korzystania z klawiszy strzałek w lewo i w prawo do nawigacji.

## <a name="q--a"></a>Pytania i odpowiedzi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Pyt.: Jak wyłączyć lub włączyć funkcję CodeLens lub wybrać wskaźniki, które mają być widoczne?

**Odp.:**  Wskaźniki można wyłączyć lub włączyć, z wyjątkiem wskaźnika odwołań. Przejdź do **narzędzia** > **Opcje** > **Edytor** > tekstu**Wszystkie języki** > **CodeLens**.

Gdy wskaźniki są włączone, można również otworzyć opcje CodeLens ze wskaźników.

![CodeLens - Wyłącz lub włącz wskaźniki](../ide/media/codelensturnoffonindicatorsfromcode.png)

Włączanie i wyłączanie wskaźników na poziomie pliku CodeLens przy użyciu ikon szewronu u dołu okna edytora.

![Włączanie i wyłączanie wskaźników poziomu plików](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>P: Gdzie jest CodeLens?

**Odp.:** CodeLens pojawia się w kodzie Języka C# i Visual Basic na poziomie metody, klasy, indeksatora i właściwości. Funkcja CodeLens jest wyświetlana na poziomie pliku dla wszystkich innych typów plików.

- Upewnij się, że funkcja CodeLens jest włączona. Przejdź do **narzędzia** > **Opcje** > **Edytor** > tekstu**Wszystkie języki** > **CodeLens**.

- Jeśli kod jest przechowywany w programie TFS, upewnij się, że indeksowanie kodu jest włączone za pomocą [polecenia CodeIndex](../ide/codeindex-command.md) za pomocą [polecenia TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

- Wskaźniki związane z devops pojawiają się tylko wtedy, gdy elementy robocze są połączone z kodem i gdy masz uprawnienia do otwierania połączonych elementów pracy. Potwierdź, że masz [uprawnienia członka zespołu](/azure/devops/organizations/security/view-permissions?view=vsts).

- Wskaźniki testu jednostkowego nie są wyświetlane, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji zawiera testy jednostkowe, ale wskaźniki testowe nie są wyświetlane, spróbuj zbudować rozwiązanie **(Ctrl**+**Shift**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens jest dostępny w wersji społeczności programu Visual Studio, jednak wskaźniki *kontroli źródła* nie są dostępne w tej wersji.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Funkcja CodeLens nie jest dostępna w programie Visual Studio Community edition.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Pyt.: Dlaczego nie widzę szczegółów elementu pracy dla zatwierdzenia?

**Odp.:** Może się tak zdarzyć, ponieważ codelens nie można znaleźć elementów roboczych w usłudze Azure Tablice lub TFS. Sprawdź, czy masz połączenie z projektem, który ma te elementy robocze i czy masz uprawnienia do wyświetlania tych elementów pracy. Szczegóły elementu pracy może również nie pokazać, jeśli opis zatwierdzenia ma niepoprawne informacje o identyfikatorach elementu pracy w usłudze Azure Boards lub TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>P: Dlaczego nie widzę wskaźników Skype?P: Why don't i see the Skype indicators?

**Odp.:** Wskaźniki programu Skype nie są wyświetlane, jeśli nie jesteś zalogowany w programie Skype dla firm, nie masz go zainstalowanego lub nie masz obsługiwanej konfiguracji. Nadal jednak możesz wysyłać wiadomości e-mail:

![CodeLens — skontaktuj się z właścicielem zmiany za pośrednictwem poczty](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Które konfiguracje Skype i Lync są obsługiwane?**

- Skype dla firm (32-bitowy lub 64-bitowy)

- Program Lync 2010 lub nowszy (32-bitowy lub 64-bitowy), ale nie program Lync Basic 2013 z systemem Windows 8.1

Funkcja CodeLens nie obsługuje instalowania różnych wersji programu Lync lub Skype. Mogą one nie być zlokalizowane dla wszystkich zlokalizowanych wersji programu Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>P: Jak zmienić czcionkę i kolor funkcji CodeLens?

**Odp.:** Przejdź do**pozycji Opcje** >  **narzędzi** > **Czcionki i kolory****środowiska** > .

![CodeLens - Zmienianie ustawień czcionek i kolorów](../ide/media/codelensoptionsfontscolorssettings.png)

Aby użyć klawiatury:

1. Naciśnij **klawisz Alt**+**T**+**O,** aby otworzyć okno dialogowe **Opcje.**

2. Naciśnij **strzałkę w górę** lub **strzałkę w dół,** aby przejść do **węzła Środowisko,** a następnie naciśnij strzałkę w **lewo,** aby rozwinąć węzeł.

3. Naciśnij **klawisz Strzałka w dół,** aby przejść do **pozycji Czcionki i kolory**.

4. Naciśnij **klawisz Tab,** aby przejść do listy **Pokaż ustawienia,** a następnie naciśnij **klawisz Strzałka w dół,** aby wybrać **pozycję CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Pyt.: Czy można przesunąć ekran projekcyjny CodeLens?

**Odp.:** Tak, ![wybierz](../ide/media/codelensdockwindow.png) ikonę Docka, aby zadokować kod CodeLens jako okno.

![Przycisk Dokowania w oknie wskaźnika CodeLens](../ide/media/codelensselectdockwindow.png)

![Okno Zadokowane odwołania do funkcji CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Pyt.: Jak odświeżyć wskaźniki?

**Odp.:** Zależy to od wskaźnika:

- **Odwołania:** Ten wskaźnik jest aktualizowany automatycznie po zmianie kodu. Jeśli wskaźnik **Odwołania** jest zadokowany jako oddzielne okno, odśwież wskaźnik, wybierając **przycisk Odśwież:**

   ![Przycisk Odśwież w odwołaniach do funkcji CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Zespół**: Odśwież te wskaźniki, wybierając **polecenie Odśwież wskaźniki zespołu CodeLens** z menu po kliknięciu prawym przyciskiem myszy:

   ![Odśwież element menu Wskaźniki zespołu CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test:** [Znajdź testy jednostkowe dla kodu,](#associated-unit-tests) aby odświeżyć wskaźnik **testu.**

### <a name="q-whats-local-version"></a>P: Co to jest "wersja lokalna"?

**Odp.:** Strzałka **Wersja lokalna** wskazuje najnowszy numer zmian w lokalnej wersji pliku. Gdy serwer ma nowsze zestawy zmian, pojawiają się one powyżej lub poniżej strzałki **Wersja lokalna,** w zależności od kolejności używanej do sortowania grup zmian.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Pyt.: Czy mogę zarządzać, jak CodeLens przetwarza kod, aby pokazać historię i połączone elementy?

**Odpowiedź:** tak. Jeśli kod znajduje się w systemie TFS, użyj [polecenia CodeIndex](../ide/codeindex-command.md) z [poleceniem TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>P: Wskaźniki testu CodeLens nie są już wyświetlane w moim pliku, gdy po raz pierwszy otwieram rozwiązanie. Jak mogę je załadować?

**Odp.:** Odbuduj swój projekt, aby uzyskać wskaźniki testu CodeLens do załadowania do pliku. Aby zwiększyć wydajność, visual studio nie pobiera już informacji źródłowych dla wskaźników testowych podczas ładowania plików kodu. Wskaźniki testowe są ładowane po kompilacji lub po przejściu do testu przez dwukrotne kliknięcie na niego w **Eksploratorze testów**.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
