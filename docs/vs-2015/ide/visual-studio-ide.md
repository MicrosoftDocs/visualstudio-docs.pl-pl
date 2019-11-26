---
title: Program Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3780e0ee5cf6bffb1a749b17d868445fbda38b13
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296912"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 jest zestaw narzędzi do tworzenia oprogramowania, na podstawie za pośrednictwem projektu interfejsu użytkownika w fazie planowania, kodowania, testowanie, debugowanie, analizowanie jakości kodu i wydajność, wdrażanie klientów w celu gromadzenia telemetrii użycia. Te narzędzia są przeznaczone do współpracują ze sobą tak jak to możliwe i czy wszystkie narażonych za pomocą zintegrowanego rozwoju środowiska (IDE) Visual Studio.

Visual Studio umożliwia tworzenie wiele rodzajów aplikacji, od prostych sklepu i gier dla klientów mobilnych do dużych, złożonych systemów, które centra power przedsiębiorstwa i danych. Można utworzyć:

- Aplikacje i gry, które nie tylko systemem Windows, ale także systemy Android i iOS.

- Usługi sieci web i witryn sieci Web na podstawie programu ASP.NET, JQuery, AngularJS i innych popularnych platform.

- Aplikacje dla platform i urządzeń, np platformy Azure, Office, Sharepoint, Hololens, Kinect i Internet of Things nazwy tylko kilka przykładów.

- Gier i aplikacji intensywnie korzystających z grafiki dla różnych urządzeń Windows, w tym Xbox, za pomocą programu DirectX.

Program Visual Studio domyślnie udostępnia obsługę C#, C i C++, JavaScript, F#i Visual Basic. Program Visual Studio działa i integruje się z aplikacjami innych firm, takimi jak Unity, za pomocą rozszerzenia [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) i Apache Cordova przez [Visual Studio Tools Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Można rozszerzyć Visual Studio samodzielnie, tworząc niestandardowe narzędzia, które wykonywały wyspecjalizowane zadania.

Jeśli jeszcze nie korzystasz z programu Visual Studio, zapoznaj się z tematami dotyczącymi programowania, korzystając z samouczków i przewodników dotyczących [programu Visual Studio](../ide/get-started-developing-with-visual-studio.md) .

Jeśli chcesz dowiedzieć się więcej o nowych funkcjach w programie Visual Studio 2015, zobacz [co nowego w programie Visual studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio
 Możesz sprawdzić, która wersja programu Visual Studio jest odpowiednia dla Ciebie w [wersjach programu Visual Studio](https://visualstudio.microsoft.com/vs/).

 Program Visual Studio 2015 można zainstalować, pobierając go z [plików do pobrania w programie Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Aby dowiedzieć się więcej o procesie instalacji, zobacz [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Podstawowe informacje o środowisku IDE
 Na poniższej ilustracji przedstawiono program Visual Studio IDE z otwartym projekcie, a w oknie Eksploratora rozwiązań do nawigowania w plikach projektu i okna programu Team Explorer do nawigowania między źródło kontroli i śledzenie elementów roboczych. Funkcje na pasku tytułu, które są wywoływane są omówione bardziej szczegółowo poniżej.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Logowanie się
 Po uruchomieniu programu Visual Studio po raz pierwszy, możesz zalogować się przy użyciu konta Microsoft lub pracy lub konta służbowego. Trwa logowanie umożliwia synchronizację ustawień, takich jak układy okna, na wielu urządzeniach i łączyć się automatycznie z usług, który może być konieczne, takie jak subskrypcje platformy Azure i programu Visual Studio Team Services. Jeśli masz licencję subskrypcji, musisz zalogować się do programu Visual Studio na bieżąco Aby zachować token licencji od nowa. Jeśli masz licencję klucza produktu, nie musisz się zalogować, ale spowoduje to więc wygodniej łączyć się z Visual Studio Team Services i swoje konta za pomocą platformy Azure, usług Office 365 i Salesforce.com. Aby uzyskać więcej informacji, zobacz [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md).

 Jeśli masz wiele kont usługi Visual Studio Team Services, konta platformy Azure lub subskrypcje MSDN można łączyć je i uzyskiwać dostęp do zasobów i usług na wszystkie swoje konta za pomocą logowania jednokrotnego. Aby uzyskać więcej informacji, zobacz [pracy z wieloma kontami użytkowników](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Dokonywanie aktualizacji na bieżąco
 Ikonę powiadomienia w prawym górnym rogu paska tytułu informujący o tym, kiedy aktualizacje są dostępne dla programu Visual Studio lub wszystkie powiązane składniki, które zostały zainstalowane. Możesz wybrać, czy odrzucić, czy działają na tych powiadomieniach. Aby uzyskać więcej informacji, zobacz [powiadomienia programu Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Znajdowanie rzeczy oraz uzyskiwanie pomocy
 Okno [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md) wyświetlone poniżej umożliwia szybkie znajdowanie poleceń programu Visual Studio, narzędzi, funkcji i tak dalej, gdy nie znasz skrótu klawiaturowego lub położenia menu. Po prostu wpisać, czego potrzebujesz, i szybkie uruchamianie prześle Ci link do niego.

 ![Wyniki szybkiego uruchamiania dla "nowy projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN to zasób witrynie internetowej firmy Microsoft, dokumentacja techniczna; podczas odczytu tę stronę w witrynie MSDN teraz! W programie Visual Studio możesz nacisnąć klawisz **F1** , aby przejść do strony pomocy MSDN dla aktywnego okna. Możesz również nacisnąć klawisz **F1** w edytorze kodu, aby przejść do strony pomocy MSDN dla interfejsu API lub słowa kluczowego w bieżącym położeniu karetki. Na przykład w C# pliku Umieść karetkę w miejscu lub tuż na końcu deklaracji `System.String` i naciśnij klawisz **F1** , aby przejść do strony pomocy MSDN dla <xref:System.String>.

### <a name="giving-feedback"></a>Wyrażanie opinii
 To proste przesłać nam swoją opinię w programie Visual Studio zawsze wtedy, gdy chcesz. Kliknij ikonę opinii na pasku tytułu obok pozycji **Szybkie uruchamianie** , a następnie kliknij pozycję **Zgłoś problem** lub **Podaj sugestię**. W wersjach wstępnych programu Visual Studio jest również dostępna opcja **Oceń ten produkt** . Możemy przyjrzeć się te komentarze i ich używać w ulepszaniu produktu. Aby uzyskać więcej informacji, zobacz [rozmowa z nami](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalizowanie środowiska IDE
 Można dostosować układ okna, aby dopasować własnego stylu programowania. Można zadokować, float lub ukryć wszystkie okna w dowolnym momencie, a także można uruchomić edytora w trybie pełnoekranowym. Można utworzyć i zapisać wiele niestandardowe układy okna, które pokazują tylko systemu windows, czego potrzebujesz do określonych kontekstach. Na przykład można utworzyć układ pełnego ekranu, tak, aby wszystko, co zostanie wyświetlony Edytor kodu. I tworzyć różne układy operacji zespołu i debugowania. Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

 Dostosuj program Visual Studio w inny sposób i ustawienia roamingu, jeśli pracujesz na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md).

 Istnieją skróty klawiaturowe dla prawie wszystko, co i można je również dostosować. Aby utworzyć nowe skróty, wpisz "Klawiatury" szybkiego uruchamiania, aby otworzyć okno dialogowe klawiatury. Z tego miejsca można nacisnąć klawisz F1, aby przejść do strony pomocy MSDN, jeśli potrzebujesz więcej informacji na temat opcji. Aby uzyskać więcej informacji, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Nawiązywanie połączenia z programu Visual Studio Team Services i serwera Team Foundation Server
 Visual Studio Team Services (VSTS) jest oparta na chmurze Usługa hostingu projektach oprogramowania i umożliwianie współpracy w zespołach. Usługa VSTS wspiera systemu Git i kontrolą źródła Team Foundation, a także Scrum i CMMI Agile metodologii programowania. Team Foundation Version Control (TFVC) używa serwera pojedynczego, scentralizowane repozytorium do śledzenia i wersji plików. Lokalne zmiany są zawsze ewidencjonowane na centralnym serwerze, gdzie inni deweloperzy mogą pobrać najnowsze zmiany. Team Foundation Server (TFS) 2015 to Centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Dzięki temu wszyscy pracownicy z procesem rozwoju uczestnictwa, używając jednego rozwiązania. TFS jest przydatne w celu zarządzania heterogenicznych zespołów i projektów, zbyt.

 Jeśli masz konto usługi Visual Studio Team Services lub serwera Team Foundation Server w sieci, nawiążesz z nim za pośrednictwem okna programu Team Explorer. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzania elementami roboczymi, kompilacji i rozpoczęcia pokoje zespołów dostępu oraz obszarów roboczych. Team Explorer można otworzyć z poziomu **paska Szybkie uruchamianie** lub z poziomu menu głównego **z &#124; widoku Team Explorer** lub **z &#124; zespołu zarządzanie połączeniami**.  Aby uzyskać więcej informacji na temat Visual Studio Team Services, zobacz [www.VisualStudio.com](https://www.visualstudio.com/). Aby uzyskać więcej informacji na temat Team Foundation Server, zobacz [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Na poniższej ilustracji przedstawiono okienka programu Team Explorer dla rozwiązania, który znajduje się w usłudze VSTS:

 ![Team Explorer programu Visual Studio](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Tworzenie rozwiązań i projektów
 Chociaż możesz użyć programu Visual Studio do przeglądania pojedynczych plików kodu, często będziesz pracować w *projekcie*. Projekt programu Visual Studio to zbiór plików i zasobów, które są kompilowane do pojedynczego pliku binarnego pliku wykonywalnego dla aplikacji (na przykład .exe, biblioteki DLL lub appx). Dla witryn sieci Web — ASP.NET jest generowany nie pliku wykonywalnego, a projekt zawiera tylko kod HTML, plików JavaScript i obrazy. Visual Studio, ponieważ czasami może być konieczne do utworzenia wielu plików binarnych lub witryn sieci Web, które są ściśle powiązane, ma koncepcji rozwiązania, które mogą zawierać wiele projektów lub witryn sieci Web. Podczas tworzenia projektu rzeczywistości tworzysz projekt w a rozwiązania, a następnie można dodać więcej projektów do tego rozwiązania później Jeśli potrzebujesz. Na przykład jeśli masz projekt DLL, można dodać projektu .exe do rozwiązania, który ładuje i korzysta z biblioteki DLL.

 *Szablon projektu* to zbiór wstępnie wypełnionych plików kodu i ustawień konfiguracji, które pozwalają szybko skonfigurować tworzenie określonego rodzaju aplikacji. Program Visual Studio jest dostarczany z wielu szablonów projektu do wyboru, a jeśli żadna z domyślnych szablonów działa, możesz utworzyć własne. Po utworzeniu projektu z szablonem, można uruchomić pisania własnego kodu w nim, w dostarczone pliki lub w nowych plików, które można dodać. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md). Poniższa ilustracja przedstawia okno dialogowe Nowy projekt z szablonami projektu, które są dostępne dla aplikacji ASP.NET.

 ![Okno dialogowe nowego projektu programu Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Projektowanie interfejsu użytkownika
 Projektant jest intuicyjne narzędzia, która pozwala na tworzenie interfejsu użytkownika bez konieczności pisania kodu. Możesz przeciągnąć kontrolki interfejsu użytkownika, takie jak pola listy, kalendarze i przyciski z okna [przybornika](../ide/reference/toolbox.md) na powierzchnię projektu reprezentującą okno lub okno dialogowe. Można zmienić rozmiar i rozmieszczanie elementów bez pisania żadnego kodu. Projektanci są uwzględniane dla dowolnego typu projektu, która ma interfejs użytkownika.

 Jeżeli projekt zawiera interfejs użytkownika oparty na XAML, projektancie domyślny jest program Blend for Visual Studio, narzędzie złożone grafiki, które bezproblemowo współdziała z programem Visual Studio.

 ![Robocze](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Widok Projekt** Wyświetla projekt wizualizacji dokumentu. W tym widoku można narysować lub modyfikować obiekty na powierzchni projektowej.|
|![](../designers/media/b1-2.png "B1_2")|Pasek **nawigacyjny** Szybko Przechodź między trybem edycji szablonu, trybem edycji stylu i zakresem edycji obiektów dla zaznaczonego obiektu.|
|![](../designers/media/b1-3.png "B1_3")|**Powiększenie** Służy do powiększania powierzchni projektowej lub obiektów na powierzchni projektowej.|
|![](../designers/media/b1-4.png "B1_4")|**Projektowanie kontrolek powierzchni** Użyj tych kontrolek (**Pokaż siatkę**przyciągania, **Przyciągaj do linii siatki** i **Włącz lub Wyłącz przyciąganie do linii wyrównania**), aby ustawić opcje przyciągania. Przyciągania jest na obiekty do siebie lub mają równe odstępy wierszy na powierzchni projektowej.|
|![](../designers/media/b1-5.png "B1_5")|**Edytor kodu** Edytuj kod XAML C# C++ lub Visual Basic ręcznie w edytorze kodu.|

 Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Pisania, nawigowania i rozumienie kodu
 Jeśli jesteś deweloperem, okno edytora jest będzie prawdopodobnie spędzisz tutaj większość czasu. Program Visual Studio obejmuje edytory dla C#, C++, Visual Basic, JavaScript, XML, HTML, CSS i F#, i innych firm stanowią wtyczek edytorów (i kompilatory) dla innych języków.

 Poszczególne pliki można edytować w edytorze tekstów, klikając pozycję **plik &#124; &#124; Otwórz plik.** Aby edytować pliki w otwartym projekcie, należy kliknąć nazwę pliku w Eksploratorze rozwiązań. Jest w trybie kolorowym kod i schemat kolorów można spersonalizować, wpisując "Kolory" Szybkie uruchamianie. Może mieć wiele systemu windows z kartami edytora tekstu Otwórz naraz. Każde okno podzielić się niezależnie. Edytor tekstu można również uruchomić w trybie pełnoekranowym.

 ![GreetingsConsoleApp. cpp w edytorze kodu](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn języka c++")

 Edytor tekstu jest wysoce interakcyjny (jeśli ma to być) produktywne wiele funkcji, które ułatwiają lepsze szybsze pisanie kodu. Różne funkcje za pomocą języka, a nie masz żadnego z nich (typu "Editor" na szybkie uruchamianie) umożliwia włączanie i wyłączanie funkcji: niektóre typowe funkcje produktywności są:

1. [Refaktoryzacja](../ide/refactoring-in-visual-studio.md) obejmuje operacje, takie jak inteligentne Zmienianie nazw zmiennych, przeniesienie wybranych wierszy kodu do oddzielnej funkcji, przeniesienie kodu do innych lokalizacji, redordering parametrów funkcji i innych.

2. *IntelliSense* to długoterminowy termin dla zestawu popularnych funkcji, które wyświetlają informacje o typie kodu bezpośrednio w edytorze i, w niektórych przypadkach, zapisują małe bity kodu. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w oknie Pomoc. Funkcje IntelliSense, zależy od języka. Aby uzyskać więcej informacji, [Zobacz C# Visual IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic funkcji IntelliSense](../ide/visual-basic-specific-intellisense.md). Poniższa ilustracja przedstawia niektóre funkcje IntelliSense w miejscu pracy:

    ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Zygzaky ostrzegają** o błędach lub potencjalnych problemach w kodzie w czasie rzeczywistym, co pozwala na ich natychmiastowe rozwiązanie, bez czekania na odnalezienie błędu podczas kompilacji lub czasu wykonywania. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z sugestii dotyczących sposobu naprawić błąd. Aby uzyskać więcej informacji, zobacz [wykonywanie szybkich akcji z żarówkami](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Żarówka z przesuwaniem myszy](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Zakładki](../ide/setting-bookmarks-in-code.md) pozwalają szybko przechodzić do określonych wierszy w plikach, nad którymi pracujesz.

5. Okno [Hierarchia wywołań](../ide/reference/call-hierarchy.md) może być wywoływane w menu kontekstowym edytora tekstu, aby wyświetlić metody wywołujące i wywoływane przez metodę pod karetką.

6. **Soczewka kodu** umożliwia znajdowanie odwołań i zmian w kodzie, połączonych błędach, elementach roboczych, przeglądach kodu i testów jednostkowych, bez opuszczania edytora. Aby uzyskać więcej informacji, zobacz [Znajdowanie zmian w kodzie i innych historii](../ide/find-code-changes-and-other-history-with-codelens.md).

7. Okno **wgląd do definicji** przedstawia metodę lub definicję typu w tekście, bez przechodzenia z bieżącego kontekstu. To okno teraz działa dla XAML, zbyt.

8. Opcja menu kontekstowego **Przejdź do definicji** prowadzi bezpośrednio do miejsca, w którym zdefiniowano funkcję lub obiekt. Inne polecenia nawigacji są także dostępne przez kliknięcie prawym przyciskiem myszy w edytorze.

9. Powiązane narzędzie, [Przeglądarka obiektów](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), umożliwia sprawdzenie zestawów .net lub środowisko wykonawcze systemu Windows w systemie, aby zobaczyć, jakie typy zawierają i jakie metody i właściwości zawierają.

     ![Przeglądarka Obect przedstawiająca system. Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   Większość elementów menu Edycja i menu Widok odnoszą się do edytora kodu, które w jakiś sposób. Aby uzyskać więcej informacji na temat edytora, zobacz [pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md) i [Edytowanie kodu](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilowanie i tworzenie kodu

Do utworzenia projektu oznacza, że skompilować kod źródłowy i wykonać dowolne kroki są niezbędne do utworzenia pliku wykonywalnego. Różne języki są różne kompilacje i witryn sieci Web w regularnych nie twórz na wszystkich. Niezależnie od typu projektu kompilacji jest standardowa lokalizacji dla tych poleceń. Aby skompilować i uruchomić kod, jednym naciśnięciem klawisza, naciśnij klawisz F5. Każdego kompilatora jest całkowicie można konfigurować za pośrednictwem środowiska IDE. Na pasku narzędzi kompilacji umożliwia określenie, czy chcesz utworzyć wersję debugowania programu przy użyciu symboli i błąd dodatkowe sprawdzanie włączone na potrzeby obsługi punktów przerwania i pojedynczy krok w debugerze lub kompilację wydania, czyli co zostanie ostatecznie zapewni klientom. Na stronie właściwości projektu, można skonfigurować więcej ustawień kompilacji i wielu innych ustawień. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie Właściwości. Można także uruchamiać kompilacje z wiersza polecenia.

Dane wyjściowe kompilacji, w tym błąd lub komunikat o powodzeniu, pojawiają się w oknie **danych wyjściowych** . W **Lista błędów** przedstawiono szczegółowe informacje o błędach kompilacji.

## <a name="debugging-your-code"></a>Debugowanie kodu
 Debuger stanu grafiki programu Visual Studio umożliwia debugowanie kodu uruchamianego w projekcie lokalnym, na zdalnym urządzeniu lub w emulatorze, takie jak te dla systemu Android lub Windows Phone. Można przejść przez kod w jednej instrukcji w danym momencie i sprawdzanie zmiennych, jak możesz przejść, możesz przejrzeć aplikacji wielowątkowych i można ustawić punkty przerwania, które są osiągane tylko wtedy, gdy określony warunek ma wartość true. Wszystkie te można skonfigurować w edytorze kodu, dzięki czemu nie trzeba pozostawić kontekstem Twojego kodu.

 ![Okno wglądu w ustawienia punktu przerwania](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Sam debuger ma wiele okien, które umożliwiają wyświetlanie i manipulowanie zmienne lokalne, stos wywołań i innych aspektów środowiska wykonawczego. Te okna można znaleźć w menu **debugowanie** .

 [Okno bezpośrednie](../ide/reference/immediate-window.md) umożliwia wpisywanie wyrażenia i natychmiastowe wyświetlanie jego wyniku.

 Okno [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) rejestruje każde wywołanie metody i inne zdarzenia w uruchomionym programie .NET i może pomóc w szybkim wyszukiwaniu miejsca, z którego pochodzi problem.

 Aby uzyskać więcej informacji, zobacz [debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testowanie kodu
 Program Visual Studio obejmuje środowiska testów jednostkowych dla kodu zarządzanego (.NET) i jeden dla natywnych języka C++. Aby utworzyć jednostkę testów, po prostu Dodaj projekt testu do rozwiązania, pisania testów, a następnie uruchom je z okna Eksploratora testów. Aby uzyskać więcej informacji, zobacz [Unit Testing Code](../test/unit-test-your-code.md).

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analizowanie jakości kodu i wydajności
 Visual Studio zawiera zaawansowane narzędzia do analizy statycznej i środowiska uruchomieniowego. Narzędzia do analizy statycznej pomóc w zidentyfikowaniu potencjalnych błędów projektowania, globalizacji, współpracy, wydajności, zabezpieczeń i innych kategorii. Testowanie wydajności lub profilowania, polega na mierzenie sposób działania Twojego programu. Dostęp do tych narzędzi można uzyskać z menu **Analizuj** . Aby uzyskać więcej informacji, zobacz [poprawianie jakości za pomocą programu Visual Studio narzędzia diagnostyczne](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Łączenie z usługami w chmurze i baz danych
 W oknie [Eksplorator serwera](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) w programie Visual Studio są wyświetlane zasoby ze wszystkich kont zarządzanych przy użyciu konta personalizacji (tego, kto jest zalogowany), w tym SQL Server wystąpienia, Azure, Salesforce.com, Office 365 i websites.

 ![Eksplorator serwera](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Program Visual Studio zawiera [narzędzia Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), które umożliwiają kompilowanie, debugowanie, konserwację i refaktoryzację baz danych. Możesz pracować z projektem bazy danych lub bezpośrednio z bazy danych połączone wystąpienie na — lub poza siedzibą firmy.

 Eksplorator obiektów SQL Server w programie Visual Studio oferuje widok obiektów bazy danych podobny do programu SQL Server Management Studio. Eksplorator obiektów SQL Server pozwala realizować administracji i projektowania lekkich bazy danych, w tym edytowanie danych w tabelach, porównywanie schematów i wykonywanie zapytań za pomocą menu kontekstowych bezpośrednio w Eksploratorze obiektów SQL Server. Narzędzia SSDT obejmują również typy projektu i narzędzia do programowania programu SQL Server 2012 Analysis Services, usługi Reporting Services i rozwiązań integracji usług Business Intelligence (BI) (wcześniej znane jako Business Intelligence Development Studio).

 ![Eksplorator obiektów SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Wdrażanie gotowych aplikacji
 Gdy aplikacja jest gotowa do wdrożenia dla klientów, Visual Studio udostępnia narzędzia, aby to zrobić, czy wdrażasz Windows Store, w witrynie programu SharePoint lub przy użyciu technologii InstallShield lub Instalatora Windows. Jest ona dostępna za pośrednictwem środowiska IDE. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Architektura i modelowanie narzędzi (tylko wersja Enterprise)
 Architektura i modelowanie narzędzi programu Visual Studio umożliwia projektowanie i modelowanie aplikacji. Te narzędzia ułatwiają wizualizować strukturę kodu, zachowanie i relacje. Możesz tworzyć modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji, jako część procesu opracowywania. Możesz śledzić wymagania, zadania, przypadki testowe, błędy i inne prace związane ze swoimi modelami, łącząc elementy modelu do elementów roboczych serwera Team Foundation Server i plan rozwoju. Aby uzyskać więcej informacji, zobacz [projektowanie i modelowanie aplikacji](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Rozszerzanie programu Visual Studio za pomocą programu Visual Studio SDK
 Program Visual Studio jest rozszerzalna platforma. Rozszerzenia programu Visual Studio to narzędzie niestandardowe, która integruje się z IDE. Można dodać rozszerzenia innych firm lub tworzyć własne. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzeń programu Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Wskazówki dotyczące środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) są istotnym odwołaniem dla każdego zapisu rozszerzeń dla programu Visual Studio. Te wytyczne specyficzne dla platformy obejmują informacji na temat projektu okna dialogowego, czcionki, kolory, ikony, typowe formanty oraz inne wzorce interakcji, składające się z nowej funkcji bezproblemowo integrują się z programem Visual Studio.

## <a name="in-this-guide"></a>W tym przewodniku

|||
|-|-|
|[Konta użytkowników i aktualizacje](../ide/user-accounts-and-updates.md)|[Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[Instrukcje: poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)|[Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)|
|[Pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md)|[Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Narzędzia profilowania](../profiling/profiling-tools.md)|[Podnoszenie jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Projektowanie interfejsów użytkownika](../designers/designing-user-interfaces.md)|[Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)|
|[Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)|[Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)|
|[Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)|[Security](../ide/security-in-visual-studio.md)|
|[Przykłady programu Visual Studio](../ide/visual-studio-samples.md)|[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)|
|[Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)|[Dokumentacja interfejsu użytkownika](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Edytowanie kodu](https://www.visualstudio.com/features/ide-vs)
- [Co nowego w programie Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Porozmawiaj z nami](../ide/talk-to-us.md)