---
title: Znajdź zmiany w kodzie i inne historyczne z CodeLens | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8876a0a3c2b978443ee4bc74097dbc9fdd410b8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655999"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadbaj o pracę, gdy dowiesz się, co się stało z kodem — bez opuszczania edytora. Znajdź odwołania i zmiany w kodzie, połączone błędy, elementy robocze, przeglądy kodu i testy jednostkowe.

> [!NOTE]
> CodeLens jest dostępny tylko w wersjach Visual Studio Enterprise i Visual Studio Professional. Nie jest on dostępny w programie Visual Studio Community Edition.

 Zobacz, gdzie i w jaki sposób poszczególne części kodu są używane w rozwiązaniu:

 ![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelensoverview.png "CodeLensOverview")

 Skontaktuj się z zespołem, aby dowiedzieć się o zmianach w kodzie bez opuszczania edytora:

 ![CodeLens &#45; skontaktować się z zespołem](../ide/media/codelensovervew2.png "CodeLensOvervew2")

 Aby wybrać wskaźniki, które mają być wyświetlane, lub aby wyłączyć funkcję CodeLens, przejdź do pozycji **Narzędzia**, **Opcje**, **Edytor tekstu**, **wszystkie języki**, **CodeLens**.

## <a name="find-references-to-your-code"></a><a name="FindReferences"></a> Znajdowanie odwołań do kodu
 Potrzebne będą następujące elementy:

- Visual Studio Enterprise lub Visual Studio Professional

- Visual C# .NET lub Visual Basic kod .NET

  Wybierz wskaźnik **odwołań** (**ALT + 2**). Jeśli widzisz **0 odwołań**, nie masz żadnych odwołań z kodu Visual C# lub Visual Basic Code. Nie obejmuje to odwołań z innych elementów, takich jak pliki XAML i ASPX.

  ![CodeLens &#45; wybierz wskaźnik odwołań](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")

  Aby wyświetlić kod odwołujący się, przesuń wskaźnik myszy na górę odwołania.

  ![&#45; CodeLens wgląd w informacje](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")

  Aby otworzyć plik zawierający odwołanie, kliknij dwukrotnie odwołanie.

  Aby wyświetlić relacje między tym kodem i jego odwołaniami, [Utwórz mapę kodu](../modeling/map-dependencies-across-your-solutions.md) i wybierz polecenie **Pokaż wszystkie odwołania** w menu skrótów mapy kodu.

  ![CodeLens &#45; odwołania na mapie kodu](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")

## <a name="find-your-codes-history-and-linked-items"></a><a name="FindCodeHistory"></a> Znajdź historię kodu i połączone elementy
 Przejrzyj historię kodu, aby dowiedzieć się, co się stało z kodem. Możesz też przejrzeć zmiany przed ich scaleniem z kodem, aby lepiej zrozumieć, jak zmiany w innych gałęziach mogą wpłynąć na kod.

 Potrzebne będą następujące elementy:

- Visual Studio Enterprise lub Visual Studio Professional

- Team Foundation Server 2013 lub nowszy, Visual Studio Team Services lub git

- [Lync 2010 lub nowszy albo Skype dla firm](https://technet.microsoft.com/lync), aby skontaktować się z zespołem w edytorze kodu

  W przypadku języka Visual C# .NET lub Visual Basic kodu .NET, który jest przechowywany w programie Team Foundation Version Control (TFVC) lub git, można uzyskać szczegóły CodeLens na poziomach klas i metod (wskaźniki*poziomu elementów kodu* ). Jeśli repozytorium git jest hostowane w usłudze TfGit, uzyskasz także linki do elementów roboczych TFS.

  ![Wskaźniki poziomu&#45;elementu kodu](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")

  Dla wszystkich innych typów plików, które można otworzyć w edytorze programu Visual Studio, uzyskasz CodeLens szczegóły dotyczące całego pliku w jednym miejscu w dolnej części okna (wskaźniki*poziomu plików* ).

  ![Wskaźniki CodeLens na poziomie pliku&#45;](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")

  Aby wybrać wskaźniki przy użyciu klawiatury, naciśnij i przytrzymaj klawisz **Alt** , aby wyświetlić powiązane klucze liczbowe.

  ![Naciśnij klawisz ALT, aby wyświetlić numery dostępu klawiaturowego](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")

### <a name="find-changes-in-your-code"></a>Znajdowanie zmian w kodzie
 Znajdź, kto zmienił kod C# lub Visual Basic, oraz wprowadzone zmiany, w wskaźnikach poziomu elementów kodu. Jest to widoczne w przypadku korzystania z programu Team Foundation Version Control (TFVC) w Team Foundation Server lub Visual Studio Team Services.

 ![CodeLens: Pobierz historię zmian dla kodu w TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")

 Domyślny okres to ostatnie 12 miesięcy. Jeśli kod jest przechowywany w Team Foundation Server, można go zmienić, uruchamiając [Polecenie TFSConfig](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) z [poleceniem CodeIndex](../ide/codeindex-command.md) i flagą **/indexHistoryPeriod** .

 Aby wyświetlić szczegółową historię wszystkich zmian, włącznie z tymi, które pochodzą z więcej niż roku temu, wybierz **Pokaż wszystkie zmiany plików**.

 ![Pokaż wszystkie zmiany kodu](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")

 Spowoduje to otwarcie okna Historia grup zmian.

 ![Okno historii dla wszystkich zmian kodu](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")

 Gdy pliki znajdują się w repozytorium git i wybierasz wskaźnik zmian na poziomie elementu kodu, zobaczysz to, co widzisz.

 ![CodeLens: Pobierz historię zmian dla kodu w usłudze git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")

 Znajdź zmiany dla całego pliku (z wyjątkiem plików C# i Visual Basic) w wskaźnikach poziomu plików w dolnej części okna.

 ![CodeLens: Pobierz szczegóły pliku kodu](../ide/media/codelensfilelevel.png "CodeLensFileLevel")

 Aby uzyskać więcej szczegółowych informacji na temat zmiany, kliknij prawym przyciskiem myszy ten element. W zależności od tego, czy korzystasz z usługi TFVC, czy git uzyskasz szereg opcji do porównania wersji pliku, wyświetlania szczegółów i śledzenia zestawu zmian, pobierania wybranej wersji pliku i wysyłania wiadomości e-mail do autora tej zmiany. Niektóre z tych szczegółów są wyświetlane w Team Explorer.

 Możesz również zobaczyć, kto zmienił swój kod w czasie. Może to pomóc znaleźć wzorce w zmianach zespołu i ocenić ich wpływ.

 ![CodeLens: Zobacz historię zmian kodu jako Graf](../ide/media/codelens.png "CodeLens")

#### <a name="find-changes-in-your-current-branch"></a>Znajdź zmiany w bieżącej gałęzi
 Załóżmy, że zespół ma wiele rozgałęzień — główną gałąź i programowanie potomne — aby zmniejszyć ryzyko związanego z uszkodzeniem stabilnego kodu:

 ![CodeLens: Znajdź, kiedy nastąpiło rozgałęzienie kodu](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")

 Dowiedz się, ile osób zmieniło swój kod i ile wprowadzonych zmian (**ALT + 6**) w gałęzi głównej:

 ![CodeLens: Znajdź, ile zmian w gałęzi](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")

#### <a name="find-when-your-code-was-branched"></a>Znajdź, kiedy nastąpiło rozgałęzienie kodu
 Przejdź do kodu w gałęzi podrzędnej, na przykład w gałęzi dev. Wybierz wskaźnik zmian (**ALT + 6**):

 ![CodeLens: Znajdź, kiedy nastąpiło rozgałęzienie kodu](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")

#### <a name="find-incoming-changes-from-other-branches"></a>Znajdź przychodzące zmiany z innych gałęzi
 ![CodeLens: Znajdź zmiany kodu w innych gałęziach](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")

 ... Podobnie jak w przypadku tej poprawki błędów w gałęzi dev:

 ![CodeLens: Zmień zaznaczenie na inną gałąź](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")

 Tę zmianę można przejrzeć bez opuszczania bieżącej gałęzi (głównej):

 ![CodeLens: Zobacz zmiany przychodzące z innej gałęzi](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")

#### <a name="find-when-changes-got-merged"></a>Znajdź, kiedy zmiany zostały scalone
 Możesz zobaczyć, które zmiany są zawarte w gałęzi:

 ![CodeLens &#45; scalone zmiany między gałęziami](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")

 Na przykład kod w gałęzi głównej zawiera teraz poprawkę błędu z gałęzi dev:

 ![CodeLens &#45; scalonych chagnes między gałęziami](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Porównaj zmiany przychodzące z wersją lokalną (Shift + F10)
 ![CodeLens: Porównaj przychodzące zmiany z lokalną](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")

 Możesz również kliknąć dwukrotnie zestaw zmian.

#### <a name="what-do-the-icons-mean"></a>Co oznaczają ikony?

|**Ikona**|**Skąd pochodzi zmiana?**|
|--------------|-----------------------------------------|
|![CodeLens: Zmień ikonę z bieżącej gałęzi](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Bieżąca gałąź|
|![CodeLens &#45; zmienić z ikony gałęzi nadrzędnej](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Gałąź nadrzędna|
|![CodeLens: Zmień z ikony gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Gałąź podrzędna|
|![CodeLens &#45; zmienić ikony gałęzi równorzędnej](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Gałąź równorzędna|
|![CodeLens &#45; zmienić z gałęzi do dalszych ikon](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Gałąź poza elementem nadrzędnym, podrzędnym lub równorzędnym|
|![CodeLens: Scal z ikony nadrzędnej](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Scalanie z gałęzi nadrzędnej z gałęzią podrzędną|
|![CodeLens: Scal z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|
|![CodeLens: scalanie z ikony niepowiązanej gałęzi](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Scalanie z niepowiązanej gałęzi (bez podstawy merge)|

### <a name="find-linked-work-items"></a>Znajdź połączone elementy robocze
 ![CodeLens &#45; Znajdź elementy robocze dla określonego kodu](../ide/media/codelensworkitems.png "CodeLensWorkItems")

### <a name="find-linked-code-reviews"></a>Znajdowanie połączonych przeglądów kodu
 ![CodeLens &#45; Wyświetl żądania przeglądu kodu](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")

### <a name="find-linked-bugs"></a>Znajdź połączone usterki
 ![CodeLens &#45; znajdować błędy połączone z zestawami zmian](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")

### <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem elementu
 ![Skontaktuj się z właścicielem elementu](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")

 Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz zainstalowany program Lync lub Skype dla firm, zobaczysz następujące opcje:

 ![Opcje kontaktu dla elementu](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")

## <a name="find-unit-tests-for-your-code"></a><a name="FindRunUnitTests"></a> Znajdowanie testów jednostkowych dla kodu
 Dowiedz się więcej o testach jednostkowych istniejących dla kodu bez otwierania Eksploratora testów. Potrzebne będą następujące elementy:

- Visual Studio Enterprise lub Visual Studio Professional

- Visual C# .NET lub Visual Basic kod .NET

- [Projekt testu jednostkowego](../test/unit-test-your-code.md) , który zawiera testy jednostkowe dla kodu aplikacji

1. Przejdź do kodu aplikacji, który ma testy jednostkowe.

2. Przejrzyj testy dla tego kodu (**ALT + 3**).

     ![CodeLens &#45; wybierz stan testu w edytorze kodu](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")

3. Jeśli zostanie wyświetlona ikona ostrzeżenia ![CodeLens &#45; testy jednostkowe nie zostały jeszcze wykonane](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), Uruchom testy.

     ![Testy jednostkowe CodeLensego widoku &#45; nie zostały jeszcze uruchomione](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")

4. Aby przejrzeć definicję testu, kliknij dwukrotnie element testu w oknie wskaźnika CodeLens, aby otworzyć plik kodu w edytorze.

     ![CodeLens &#45; przejdź do definicji testu jednostkowego](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")

5. Przejrzyj wyniki testu. Wybierz pozycję wskaźnik stanu testu (![CodeLens &#45; test jednostki zakończone niepowodzeniem](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") lub ![ikonę CodeLens testu jednostkowego &#45;](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) lub naciśnij klawisze **Alt + 1**.

     ![CodeLens &#45; Zobacz wyniki testu jednostkowego](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")

6. Aby zobaczyć, ile osób zmieniło ten test, kto zmienił ten test lub ile zmian zostało wprowadzonych w tym teście, [Znajdź historię kodu i połączone elementy](#FindCodeHistory).

## <a name="q--a"></a><a name="QA"></a> P & A

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a><a name="ChangeOrTurnOff"></a> P: Jak mogę wyłączyć lub włączyć CodeLens? Lub wybrać wskaźniki, które mają być wyświetlane?
 Odp **.:**  Można wyłączyć lub włączyć wskaźniki, z wyjątkiem wskaźnika odwołań. Przejdź do **Narzędzia**, **Opcje**, **Edytor tekstu**, **wszystkie języki**, **CodeLens**.

 Po włączeniu wskaźników można także otworzyć Opcje CodeLens z wskaźników.

 ![CodeLens &#45; włączać lub włączać wskaźniki](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")

 Włącz i Wyłącz wskaźniki na poziomie plików CodeLens przy użyciu ikon Pagon u dołu okna edytora.

 ![Włącz i Wyłącz wskaźniki poziomu&#45;plików](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")

### <a name="q-where-is-codelens"></a><a name="NoIndicators"></a> P: gdzie jest CodeLens?
 Odp **.:** CodeLens pojawia się w języku Visual C# .NET i Visual Basic kodzie .NET na poziomie metody, klasy, indeksatora i właściwości. CodeLens pojawia się na poziomie pliku dla wszystkich innych typów plików.

- Upewnij się, że CodeLens jest włączona. Przejdź do **Narzędzia**, **Opcje**, **Edytor tekstu**, **wszystkie języki**, **CodeLens**.

- Jeśli kod jest przechowywany w programie TFS, upewnij się, że indeksowanie kodu jest włączone przy użyciu [polecenia CodeIndex](../ide/codeindex-command.md) z [poleceniem TFS config](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).

- Wskaźniki związane z TFS pojawiają się tylko wtedy, gdy elementy robocze są połączone z kodem, a użytkownik ma uprawnienia do otwierania połączonych elementów roboczych. [Upewnij się, że masz uprawnienia członka zespołu.](/azure/devops/organizations/security/view-permissions)

- Wskaźniki testów jednostkowych nie są wyświetlane, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji ma testy jednostkowe, ale nie pojawiają się wskaźniki testów, spróbuj skompilować rozwiązanie (**Ctrl + Shift + B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>P: Dlaczego nie widzę szczegółów elementu pracy dla zatwierdzenia?
 Odp **.:** Może się tak zdarzyć, ponieważ CodeLens nie może znaleźć elementów roboczych w programie TFS. Sprawdź, czy masz połączenie z projektem zespołowym, który ma te elementy robocze i czy masz uprawnienia do wyświetlania tych elementów roboczych. Taka sytuacja może wystąpić również, jeśli opis zatwierdzenia zawiera nieprawidłowe informacje o identyfikatorach elementów roboczych w programie TFS.

### <a name="q-why-dont-i-see-the-lync-or-skype-indicators"></a><a name="NoLync"></a> P: Dlaczego nie widzę wskaźników Lync lub Skype?
 Odp **.:** Nie są wyświetlane, jeśli nie zarejestrowano Cię w usłudze Lync lub Skype dla firm, nie zainstalowano jednego z nich lub nie masz obsługiwanej konfiguracji. Jednak nadal możesz wysyłać wiadomości e-mail:

 ![CodeLens &#45; skontaktować się z właścicielem grupy zmian przez pocztę](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")

 **Które konfiguracje Lync i Skype są obsługiwane?**

- Skype dla firm (32-bitowe lub 64-bitowe)

- Program Lync 2010 lub nowszy (32-bitowy lub 64-bitowy), ale nie Lync Basic 2013 z Windows 8.1

  CodeLens nie obsługuje różnych wersji programu Lync lub Skype zainstalowanych. Mogą nie być zlokalizowane dla wszystkich zlokalizowanych wersji programu Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>P: Jak mogę zmienić czcionkę i kolor dla CodeLens?
 Odp **.:** Przejdź do **Narzędzia**, **Opcje**, **środowisko**, **czcionki i kolory**.

 ![CodeLens &#45; zmienić ustawień czcionki i koloru](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")

 Aby użyć klawiatury:

1. Naciśnij klawisze **Alt + T + o** , aby otworzyć okno **Opcje** .

2. Naciśnij strzałkę w **górę** lub **strzałkę w dół** , aby przejść do węzła **środowisko** , a następnie naciśnij **strzałkę w lewo** , aby rozwinąć węzeł.

3. Naciśnij **strzałkę w dół** , aby przejść do **czcionek i kolorów**.

4. Naciśnij klawisz **Tab** , aby przejść do listy **Pokaż ustawienia dla** , a następnie naciśnij **strzałkę w dół** , aby wybrać **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Pyt.: Czy można przesunąć ekran projekcyjny CodeLens?
 Odp **.:** Tak, wybierz ![CodeLens &#45; Dock jako okno](../ide/media/codelensdockwindow.png "CodeLensDockWindow") , aby zadokować CodeLens jako okno.

 ![Zadokuj okno wskaźnika CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")

 ![Okno zadokowanych odwołań CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")

### <a name="q-how-do-i-refresh-the-indicators"></a>Pyt.: Jak odświeżyć wskaźniki?
 Odp **.:** Jest to zależne od wskaźnika:

- **Odwołania**: ten wskaźnik jest aktualizowany automatycznie po zmianie kodu. Jeśli ten wskaźnik jest zadokowany jako oddzielne okno, Odśwież wskaźnik ręcznie w tym miejscu:

     ![CodeLens &#45; Zadokuj jako okno](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")

- **Zespół**: Odśwież te wskaźniki ręcznie w tym miejscu:

     ![CodeLens wskaźniki odświeżania &#45;](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")

- **Test**: [Znajdź testy jednostkowe dla kodu](#FindRunUnitTests) , aby odświeżyć ten wskaźnik.

### <a name="q-whats-local-version"></a><a name="LocalVersion"></a> P: co to jest "lokalna wersja"?
 Odp **.:** Strzałka **wersja lokalna** wskazuje najnowszą grupę zmian w lokalnej wersji tego pliku. Gdy serwer ma nowsze zestawy zmian, są one wyświetlane powyżej lub poniżej strzałki **wersji lokalnej** , w zależności od kolejności użytej do sortowania zestawów zmian.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>P: Czy mogę zarządzać sposobem, w jaki CodeLens przetwarza kod, aby pokazać historię i połączone elementy?
 Odp **.:** Tak, Jeśli Twój kod znajduje się w programie TFS, użyj [polecenia CodeIndex](../ide/codeindex-command.md) z [poleceniem TFS config](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).
