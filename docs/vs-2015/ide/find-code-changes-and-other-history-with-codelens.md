---
title: Znajdowanie zmian w kodzie i innych elementów historii za pomocą wskaźników CodeLens | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b090833d766e36ba597bb32e8a6c793d674add88
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383946"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Znajdowanie zmian w kodzie i innych elementów historii kodu za pomocą funkcji CodeLens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Skoncentrowanie się na pracy, chociaż możesz dowiedzieć się, co się stało z twoim kodzie — bez opuszczania edytora. Znajdować odwołania i zmian kodu, połączone usterki, elementy robocze, przeglądy kodu i testów jednostkowych.  
  
> [!NOTE]
> Funkcja CodeLens jest dostępna tylko w wersjach programu Visual Studio Enterprise i Visual Studio Professional. Nie jest dostępne w programie Visual Studio Community edition.  
  
 Zobacz, gdzie i w jaki sposób poszczególne fragmenty kodu są używane w rozwiązaniu:  
  
 ![Wskaźniki CodeLens w edytorze kodu](../ide/media/codelensoverview.png "CodeLensOverview")  
  
 Bez opuszczania edytora, skontaktuj się z zespołem o zmianach w kodzie:  
  
 ![Funkcja CodeLens &#45; skontaktuj się z zespołem](../ide/media/codelensovervew2.png "CodeLensOvervew2")  
  
 Aby wybrać wskaźników, które chcesz wyświetlić lub wyłącz i Włącz CodeLens, przejdź do **narzędzia**, **opcje**, **edytora tekstów**, **wszystkie języki** , **CodeLens**.  
  
## <a name="FindReferences"></a> Znajdowanie odwołań w kodzie  
 Będą potrzebne:  
  
- Visual Studio Enterprise or Visual Studio Professional  
  
- Visual C# .NET lub Visual Basic .NET kodu  
  
  Wybierz **odwołania** wskaźnika (**Alt + 2**). Jeśli widzisz **0 odwołań**, nie ma odwołań z kodu języka Visual C# lub Visual Basic. To nie zawiera odwołań z innych elementów, takich jak pliki ASPX i XAML.  
  
  ![Funkcja CodeLens &#45; Wybierz wskaźnik odwołań](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  
  
  Aby wyświetlić kod odwołujący się, przenieś wskaźnik myszy na górze odwołania.  
  
  ![Funkcja CodeLens &#45; wgląd w odwołania](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  
  
  Aby otworzyć plik zawierający odwołanie, kliknij dwukrotnie odwołanie.  
  
  Aby wyświetlić relacje między tym kodem i jego odwołaniami [utworzenie mapy kodu](../modeling/map-dependencies-across-your-solutions.md) i wybierz polecenie **Pokaż wszystkie odwołania** w menu skrótów mapy kodu.  
  
  ![Funkcja CodeLens &#45; odwołania na mapie kodu](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  
  
## <a name="FindCodeHistory"></a> Znajdowanie historii kodu i połączone elementy  
 Przejrzyj historią swojego kodu, aby dowiedzieć się, co się stało z kodu. Lub przejrzyj zmiany, zanim one scalane w kodzie, dzięki czemu można lepiej zrozumieć, jak zmiany w innych gałęzi, mogą mieć wpływ na kod.  
  
 Będą potrzebne:  
  
- Visual Studio Enterprise or Visual Studio Professional  
  
- Team Foundation Server 2013 or later, Visual Studio Team Services, or Git  
  
- [Lync 2010 lub nowszej lub Skype dla firm](http://technet.microsoft.com/lync), skontaktuj się z zespołem z poziomu edytora kodu  
  
  Kod Visual C# .NET lub Visual Basic .NET, który są przechowywane z kontroli wersji Team Foundation (TFVC) lub Git, Pobierz szczegóły wskaźników CodeLens na poziomie klasy i metody (*poziomie elementu kodu* wskaźniki). Jeśli repozytorium Git jest hostowana w TfGit, możesz także uzyskać łącza do elementów roboczych TFS.  
  
  ![Element kodu&#45;wskaźniki poziomu](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  
  
  Dla wszystkich innych typów plików, które można otworzyć w edytorze programu Visual Studio możesz uzyskać szczegółowe informacje CodeLens cały plik w jednym miejscu w dolnej części okna (*poziomu plików* wskaźniki).  
  
  ![Plik&#45;wskaźników CodeLens na poziomie](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  
  
  Aby wybrać wskaźników za pomocą klawiatury, naciśnij i przytrzymaj **ALT** klawisz, aby wyświetlić powiązane klawisze numeryczne.  
  
  ![Naciśnij klawisz ALT, aby wyświetlić numery dostępu do klawiatury](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  
  
### <a name="find-changes-in-your-code"></a>Znajdowanie zmian w kodzie  
 Znajdź użytkownika języka C# lub kod języka Visual Basic, kto i zmiany, które wprowadził wprowadził, wskaźniki na poziomie elementu kodu. Jest to, zobacz korzystając z kontroli wersji Team Foundation (TFVC) w Team Foundation Server lub Visual Studio Team Services.  
  
 ![CodeLens: Pobierz historię zmian przez swój kod w TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  
  
 Domyślny okres czasu jest ostatnich 12 miesięcy. Jeśli Twój kod jest przechowywany na serwerze Team Foundation Server, możesz to zmienić, uruchamiając [polecenia TFSConfig](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) z [polecenie CodeIndex](../ide/codeindex-command.md) i **/indexHistoryPeriod** flagi.  
  
 Aby wyświetlić szczegółowej historii wszystkich zmian, łącznie ze składnikami z ponad rok temu, wybierz opcję **Pokaż wszystkie zmiany pliku**.  
  
 ![Pokaż wszystkie zmiany kodu](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  
  
 Spowoduje to otwarcie w oknie historii zmian.  
  
 ![Okno Historia dla wszystkich zmian w kodzie](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  
  
 Jeśli pliki znajdują się w repozytorium Git, i wybierz wskaźnik zmian na poziomie elementu kodu, to zostanie wyświetlony.  
  
 ![CodeLens: Pobierz historię zmian przez kodu w Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  
  
 Znajdź wskaźniki poziomu plików w dolnej części okna zmian dotyczących całego pliku (z wyjątkiem plików języka C# i Visual Basic).  
  
 ![CodeLens: Pobierz kod szczegółów pliku](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
 Aby uzyskać więcej informacji na temat zmian, kliknij prawym przyciskiem myszy ten element. W zależności od tego, czy przy użyciu TFVC lub Git, możesz uzyskać szereg opcji, aby porównać wersje pliku, Wyświetl szczegóły śledzenia zmian, pobrać wybraną wersję pliku i wiadomości e-mail autora zmiany. Niektóre z tych informacji są wyświetlane w programie Team Explorer.  
  
 Widać również, kto zmienił kod, wraz z upływem czasu. Może to pomóc Ci znaleźć wzorce w zmiany swojego zespołu i ocena ich skutków.  
  
 ![CodeLens: Zobacz historię zmian kod jako Graf](../ide/media/codelens.png "CodeLens")  
  
#### <a name="find-changes-in-your-current-branch"></a>Znajdowanie zmian w gałęzi bieżącej  
 Załóżmy, że zespół ma wiele gałęzi — głównej gałęzi i rozwoju podrzędne — Aby zmniejszyć ryzyko istotne stabilnym kodem:  
  
 ![CodeLens: Dowiedz się, gdy został rozgałęziony kodu](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  
  
 Dowiedz się, ile osób zmieniało kodu oraz ile zmian (**Alt + 6**) w głównej gałęzi:  
  
 ![CodeLens: Dowiedz się, jak wiele zmian w gałęzi](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  
  
#### <a name="find-when-your-code-was-branched"></a>Dowiedz się, gdy został rozgałęziony kodu  
 Przejdź do kodu w gałęzi podrzędnej, na przykład, gałąź Dev w tym miejscu. Wybierz wskaźnik zmian (**Alt + 6**):  
  
 ![CodeLens: Dowiedz się, gdy został rozgałęziony kodu](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  
  
#### <a name="find-incoming-changes-from-other-branches"></a>Znajdź zmiany przychodzące z innych gałęzi  
 ![CodeLens: Znajdowanie zmian w kodzie w innych gałęzi,](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  
  
 ...tak jak tej poprawki w Deweloper gałęzi w tym miejscu:  
  
 ![CodeLens: Zmień zaznaczone ich z inną gałęzią](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  
  
 Możesz przejrzeć tę zmianę, bez wychodzenia z bieżącej gałęzi (główne):  
  
 ![CodeLens: Zobacz Zmiana przychodząca z inną gałęzią](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  
  
#### <a name="find-when-changes-got-merged"></a>Dowiedz się, gdy została scalona zmiany  
 Aby zobaczyć, jakie zmiany są uwzględnione w Twojej gałęzi:  
  
 ![CodeLens &#45; Merged changes between branches](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  
  
 Na przykład kod w gałęzi głównej ma teraz naprawienie usterki z gałęzi Dev:  
  
 ![Funkcja CodeLens &#45; scalone chagnes między gałęziami](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  
  
#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Porównaj zmiany przychodzące z wersją lokalną (Shift + F10)  
 ![CodeLens: Porównaj zmiany przychodzące z lokalnego](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  
  
 Można również kliknąć dwukrotnie zestaw zmian.  
  
#### <a name="what-do-the-icons-mean"></a>Co oznaczają ikony  
  
|**Ikona**|**Zmiana skąd?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Zmienić z bieżącej gałęzi ikona](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Current branch|  
|![Funkcja CodeLens &#45; zmiany z nadrzędnej gałęzi ikona](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Gałąź nadrzędna|  
|![CodeLens: Zmiana z ikony gałęzi podrzędnej](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Gałęzi podrzędnej|  
|![Funkcja CodeLens &#45; zmiany z elementów równorzędnych gałęzi ikona](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Gałęzi elementu równorzędnego|  
|![Funkcja CodeLens &#45; zmienić jedno kliknięcie ikony dalsze gałęzi](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Gałąź dalsze natychmiast niż nadrzędne, podrzędne lub elementów równorzędnych|  
|![CodeLens: Scal z ikona nadrzędnego](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Scalanie z gałęzi do gałęzi podrzędnej|  
|![CodeLens: Scal z ikony gałęzi podrzędnej](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Scalanie z gałęzi podrzędnej do gałęzi nadrzędnej|  
|![CodeLens: Scal od gałęzi niepowiązanych ikonę](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Scalanie gałęzi niepowiązanych (scalanie)|  
  
### <a name="find-linked-work-items"></a>Znaleźć połączone elementy robocze  
 ![Funkcja CodeLens &#45; Znajdź elementy robocze dla określonego kodu](../ide/media/codelensworkitems.png "CodeLensWorkItems")  
  
### <a name="find-linked-code-reviews"></a>Znajdź przeglądów kodu połączone  
 ![Funkcja CodeLens &#45; wyświetlić żądania przeglądu kodu](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  
  
### <a name="find-linked-bugs"></a>Znaleźć połączone błędy  
 ![Funkcja CodeLens &#45; Znajdź błędy połączone z zestawami zmian](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  
  
### <a name="contact-the-owner-of-an-item"></a>Skontaktuj się z właścicielem elementu  
 ![Skontaktuj się z właścicielem elementu](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  
  
 Otwórz menu skrótów dla elementu, aby wyświetlić opcje kontaktu. Jeśli masz Lync lub Skype dla firm zainstalowany, zostanie wyświetlony tych opcji:  
  
 ![Skontaktuj się z opcjami dla elementu](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  
  
## <a name="FindRunUnitTests"></a> Znajdź testów jednostkowych dla kodu  
 Dowiedz się więcej o testy jednostkowe, które istnieją w kodzie, bez konieczności otwierania Eksploratora testów. Będą potrzebne:  
  
- Visual Studio Enterprise or Visual Studio Professional  
  
- Visual C# .NET lub Visual Basic .NET kodu  
  
- A [projektu testu jednostkowego](../test/unit-test-your-code.md) zawierający testy jednostkowe dla kodu aplikacji  
  
1. Przejdź do kodu aplikacji, który ma testy jednostkowe.  
  
2. Przejrzyj testów dla tego kodu (**Alt + 3**).  
  
     ![Funkcja CodeLens &#45; wybierz stan testu w edytorze kodu](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3. Jeśli widoczna jest ikona ostrzeżenia ![CodeLens &#45; testów jednostkowych nie został jeszcze uruchomiony ostrzeżenie](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), uruchom testy.  
  
     ![Funkcja CodeLens &#45; widoku testów jednostkowych nie jeszcze uruchomione](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4. Aby przejrzeć definicję testu, kliknij dwukrotnie element testu w oknie wskaźnik CodeLens, aby otworzyć plik kodu w edytorze.  
  
     ![Funkcja CodeLens &#45; przejdź do definicji testów jednostkowych](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5. Przejrzyj wyniki testu. Wybierz wskaźnik stanu testu (![CodeLens &#45; testu jednostkowego nie powiodło się ikona](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") lub ![CodeLens &#45; testu jednostkowego przekazywane ikonę](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), lub naciśnij **Alt + 1**.  
  
     ![Funkcja CodeLens &#45; Zobacz wyniku testu jednostkowego](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6. Aby zobaczyć, ile osób zmieniło ten test, kto go zmienił lub ile zmian z tym testem [znajdowanie historii kodu i połączone elementy](#FindCodeHistory).  
  
## <a name="QA"></a> PYTANIA I ODPOWIEDZI  
  
### <a name="ChangeOrTurnOff"></a> Q: Jak włączanie i wyłączanie funkcji CodeLens? Lub wybierz wskaźników, które się?  
 **ODP.:**  Można włączyć wskaźników lub wyłączyć, z wyjątkiem wskaźnik odwołań. Przejdź do **narzędzia**, **opcje**, **edytora tekstów**, **wszystkie języki**, **CodeLens**.  
  
 Wskaźniki są włączone, można również otworzyć Opcje CodeLens, pochodzące ze wskaźników.  
  
 ![Funkcja CodeLens &#45; Włączanie i wyłączanie wskaźniki](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Włącz wskaźniki poziomu plików CodeLens, włączać i wyłączać przy użyciu ikon kół cudzysłów ostrokątny u dołu okna edytora.  
  
 ![Włącz pliku&#45;poziomu wskaźniki włączać i wyłączać](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
### <a name="NoIndicators"></a> Q: Gdzie jest CodeLens?  
 **ODP.:** CodeLens jest wyświetlana w elemencie wizualnym C# kodu .NET i Visual Basic .NET na poziomie metody, klasy, indeksatora i właściwości. Funkcja CodeLens pojawia się na poziomie pliku dla wszystkich typów plików.  
  
- Upewnij się, że jest włączona funkcja CodeLens. Przejdź do **narzędzia**, **opcje**, **edytora tekstów**, **wszystkie języki**, **CodeLens**.  
  
- Jeśli Twój kod jest przechowywany w programie TFS, upewnij się, że indeksowanie kodu jest włączone za pomocą [polecenie CodeIndex](../ide/codeindex-command.md) z [polecenia konfiguracji TFS](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).  
  
- Wskaźniki związane z TFS pojawiają się tylko wtedy, gdy elementy robocze są połączone z kodem, a użytkownik ma uprawnienia do otwierania połączonych elementów roboczych. [Upewnij się, że masz uprawnienia członka zespołu.](/azure/devops/organizations/security/view-permissions)  
  
- Nie pojawiają się wskaźniki testów jednostkowych, gdy kod aplikacji nie ma testów jednostkowych. Wskaźniki stanu testu są automatycznie wyświetlane w projektach testów. Jeśli wiesz, że kod aplikacji ma testy jednostkowe, ale nie pojawiają się wskaźniki testów, spróbuj skompilować rozwiązanie (**Ctrl + Shift + B**).  
  
### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>PYT.: Dlaczego nie widzę szczegóły elementu roboczego do zatwierdzenia  
 **ODP.:** Może się to zdarzyć, ponieważ funkcja CodeLens nie może znaleźć elementy robocze w programie TFS. Sprawdź, czy są połączone w do projektu zespołowego, który ma te elementy robocze oraz że masz uprawnienia, aby wyświetlić te elementy robocze. Może to również nastąpić, jeśli opisu zatwierdzenie ma nieprawidłowe informacje o identyfikatorach elementów roboczych w programie TFS.  
  
### <a name="NoLync"></a> Q: Dlaczego nie widzę wskaźników Lync lub Skype  
 **ODP.:** Nie są wyświetlane, jeśli nie zalogował się do usługi Lync lub Skype dla firm, nie mają jeden z nich jest zainstalowany lub nie ma obsługiwanej konfiguracji. Ale nadal można wysyłać wiadomości e-mail:  
  
 ![Funkcja CodeLens &#45; skontaktuj się z właścicielem zestawu zmian za pomocą poczty e-mail](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  
  
 **Które konfiguracje Lync i Skype są obsługiwane?**  
  
- Skype dla firm (32-bitowy lub 64-bitowy)  
  
- Lync 2010 lub nowszej samodzielnie (32-bitowy lub 64-bitowy), ale nie Lync Basic 2013 za pomocą Windows 8.1  
  
  Zainstalowany program Skype lub CodeLens nie obsługuje różnych wersji programu Lync. One może nie być zlokalizowana dla wszystkich zlokalizowanych wersji programu Visual Studio.  
  
### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>PYT.: Jak zmienić czcionkę i kolor wskaźników codelens?  
 **ODP.:** Przejdź do **narzędzia**, **opcje**, **środowiska**, **czcionki i kolory**.  
  
 ![Funkcja CodeLens &#45; zmienić ustawienia czcionek i kolorów](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  
  
 Aby użyć klawiatury:  
  
1. Naciśnij klawisz **Alt + T + O** otworzyć **opcje** pole.  
  
2. Naciśnij klawisz **Strzałka w górę** lub **strzałkę w dół** można przejść do **środowiska** węzła, naciśnij klawisz **Strzałka w lewo** Aby rozwinąć węzeł.  
  
3. Naciśnij klawisz **strzałkę w dół** można przejść do **czcionki i kolory**.  
  
4. Naciśnij klawisz **kartę** można przejść do **Pokaż ustawienia dla** listy, a następnie naciśnij klawisz **strzałkę w dół** wybrać **CodeLens**.  
  
### <a name="q-can-i-move-the-codelens-heads-up-display"></a>PYT.: Czy mogę przenieść wyświetlacza hud CodeLens  
 **ODP.:** Tak, wybierz ![CodeLens &#45; zadokować okno](../ide/media/codelensdockwindow.png "CodeLensDockWindow") Aby zadokować CodeLens jako okno.  
  
 ![Zadokować okno wskaźnik CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  
  
 ![Okno zadokowane odwołania do wskaźników CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  
  
### <a name="q-how-do-i-refresh-the-indicators"></a>PYT.: Jak odświeżyć wskaźniki?  
 **ODP.:** Zależy to od wskaźnika:  
  
- **Odwołania**: Ten wskaźnik jest aktualizowany automatycznie po wprowadzeniu zmian w kodzie. W przypadku tego wskaźnika zadokowane jako oddzielne okno odświeżania wskaźnika ręcznie w tym miejscu:  
  
     ![Funkcja CodeLens &#45; Zadokuj jako okno](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  
  
- **Zespół**: Odśwież wskaźniki ręcznie w tym miejscu:  
  
     ![Funkcja CodeLens &#45; Odśwież wskaźniki](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  
  
- **Test**: [Znajdź testów jednostkowych dla kodu](#FindRunUnitTests) można odświeżyć tego wskaźnika.  
  
### <a name="LocalVersion"></a> Q: Co to jest "Wersja lokalna"?  
 **ODP.:** **Lokalnej wersji** Strzałka wskazuje na najnowszy zestaw zmian w lokalnej wersji tego pliku. Gdy serwerze znajdują się nowsze zestawy zmian, są one wyświetlane powyżej lub poniżej **lokalnej wersji** strzałka, w zależności od kolejności ich sortowania.  
  
### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>PYT.: Czy mogę zarządzać jak funkcja CodeLens przetwarza kod w celu wyświetlenia historii i połączone elementy?  
 **ODP.:** Tak, jeśli kod jest w programie TFS, użyj [polecenie CodeIndex](../ide/codeindex-command.md) z [polecenia konfiguracji TFS](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).
