---
title: Program Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 76e1d9c4a7cbfdfc2a7011668eb58a5ea9741d3d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54780682"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 jest zestaw narzędzi do tworzenia oprogramowania, na podstawie za pośrednictwem projektu interfejsu użytkownika w fazie planowania, kodowania, testowanie, debugowanie, analizowanie jakości kodu i wydajność, wdrażanie klientów w celu gromadzenia telemetrii użycia. Te narzędzia są przeznaczone do współpracują ze sobą tak jak to możliwe i czy wszystkie narażonych za pomocą zintegrowanego rozwoju środowiska (IDE) Visual Studio.

Visual Studio umożliwia tworzenie wiele rodzajów aplikacji, od prostych sklepu i gier dla klientów mobilnych do dużych, złożonych systemów, które centra power przedsiębiorstwa i danych. Można utworzyć:

- Aplikacje i gry, które nie tylko systemem Windows, ale także systemy Android i iOS.

- Usługi sieci web i witryn sieci Web na podstawie programu ASP.NET, JQuery, AngularJS i innych popularnych platform.

- Aplikacje dla platform i urządzeń, np platformy Azure, Office, Sharepoint, Hololens, Kinect i Internet of Things nazwy tylko kilka przykładów.

- Gier i aplikacji intensywnie korzystających z grafiki dla różnych urządzeń Windows, w tym Xbox, za pomocą programu DirectX.

Program Visual Studio domyślnie udostępnia obsługę C#, C i C++, JavaScript, F#i Visual Basic. Program Visual Studio działa i dobrze integruje się z aplikacji innych firm, takich jak Unity za pośrednictwem [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) rozszerzenie i Apache Cordova za pośrednictwem [Visual Studio Tools for Apache Cordova](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Można rozszerzyć Visual Studio samodzielnie, tworząc niestandardowe narzędzia, które wykonywały wyspecjalizowane zadania.

Jeśli nie znasz programu Visual Studio przed, w opanowaniu podstaw za pomocą naszych [Rozpoczynanie pracy opracowywanie zawartości przy użyciu programu Visual Studio](../ide/get-started-developing-with-visual-studio.md) wskazówki i samouczki.

Jeśli chcesz dowiedzieć się o nowych funkcjach w programie Visual Studio 2015, zobacz [What's New in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio
 Możesz dowiedzieć się, którą wersję programu Visual Studio jest odpowiedni dla Ciebie na [wersje programu Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Visual Studio 2015 można zainstalować, pobierając go z [pobieranie Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Jeśli potrzebujesz dowiedzieć się więcej na temat procesu instalacji, zobacz [instalowania programu Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Podstawowe informacje o środowisku IDE
 Na poniższej ilustracji przedstawiono program Visual Studio IDE z otwartym projekcie, a w oknie Eksploratora rozwiązań do nawigowania w plikach projektu i okna programu Team Explorer do nawigowania między źródło kontroli i śledzenie elementów roboczych. Funkcje na pasku tytułu, które są wywoływane są omówione bardziej szczegółowo poniżej.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Logowanie
 Po uruchomieniu programu Visual Studio po raz pierwszy, możesz zalogować się przy użyciu konta Microsoft lub pracy lub konta służbowego. Trwa logowanie umożliwia synchronizację ustawień, takich jak układy okna, na wielu urządzeniach i łączyć się automatycznie z usług, który może być konieczne, takie jak subskrypcje platformy Azure i programu Visual Studio Team Services. Jeśli masz licencję subskrypcji, musisz zalogować się do programu Visual Studio na bieżąco Aby zachować token licencji od nowa. Jeśli masz licencję klucza produktu, nie musisz się zalogować, ale spowoduje to więc wygodniej łączyć się z Visual Studio Team Services i swoje konta za pomocą platformy Azure, usług Office 365 i Salesforce.com. Aby uzyskać więcej informacji, zobacz [logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md).

 Jeśli masz wiele kont usługi Visual Studio Team Services, konta platformy Azure lub subskrypcje MSDN można łączyć je i uzyskiwać dostęp do zasobów i usług na wszystkie swoje konta za pomocą logowania jednokrotnego. Aby uzyskać więcej informacji, zobacz [Praca z wieloma kontami użytkownika](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Dokonywanie aktualizacji na bieżąco
 Ikonę powiadomienia w prawym górnym rogu paska tytułu informujący o tym, kiedy aktualizacje są dostępne dla programu Visual Studio lub wszystkie powiązane składniki, które zostały zainstalowane. Możesz wybrać, czy odrzucić, czy działają na tych powiadomieniach. Aby uzyskać więcej informacji, zobacz [powiadomienia usługi Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Znajdowanie rzeczy oraz uzyskiwanie pomocy
 [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md) okna poniżej to szybko znaleźć poleceń programu Visual Studio, narzędzia, funkcje i tak dalej, jeśli nie znasz lokalizacji lub w menu skrótów klawiatury. Po prostu wpisać, czego potrzebujesz, i szybkie uruchamianie prześle Ci link do niego.

 ![Szybkie uruchamianie wyniki "nowy projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN to zasób witrynie internetowej firmy Microsoft, dokumentacja techniczna; podczas odczytu tę stronę w witrynie MSDN teraz! W programie Visual Studio, możesz nacisnąć przycisk **F1** aby przejść do strony pomocy MSDN dla aktywnego okna. Można również nacisnąć klawisz **F1** w edytorze kodu, aby przejść do strony pomocy MSDN dla interfejsu API lub słowa kluczowego w bieżącym położeniu karetki. Na przykład w pliku C#, umieść karetki gdzieś w lub tylko na końcu `System.String` deklaracji, a następnie naciśnij klawisz **F1** przejść na stronę pomocy MSDN <xref:System.String>.

### <a name="giving-feedback"></a>Wyrażanie opinii
 To proste przesłać nam swoją opinię w programie Visual Studio zawsze wtedy, gdy chcesz. Kliknij ikony opinii na pasku tytułu **szybkiego uruchamiania** a następnie kliknij polecenie **Zgłoś Problem** lub **sugestię**. Przed wydaniem wersji programu Visual Studio mają również **Oceń ten produkt** opcji. Możemy przyjrzeć się te komentarze i ich używać w ulepszaniu produktu. Aby uzyskać więcej informacji, zobacz [Porozmawiaj z nami](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalizowanie środowiska IDE
 Można dostosować układ okna, aby dopasować własnego stylu programowania. Można zadokować, float lub ukryć wszystkie okna w dowolnym momencie, a także można uruchomić edytora w trybie pełnoekranowym. Można utworzyć i zapisać wiele niestandardowe układy okna, które pokazują tylko systemu windows, czego potrzebujesz do określonych kontekstach. Na przykład można utworzyć układ pełnego ekranu, tak, aby wszystko, co zostanie wyświetlony Edytor kodu. I tworzyć różne układy operacji zespołu i debugowania. Aby uzyskać więcej informacji, zobacz [dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

 Dostosuj program Visual Studio w inny sposób i ustawienia roamingu, jeśli pracujesz na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md).

 Istnieją skróty klawiaturowe dla prawie wszystko, co i można je również dostosować. Aby utworzyć nowe skróty, wpisz "Klawiatury" szybkiego uruchamiania, aby otworzyć okno dialogowe klawiatury. Z tego miejsca można nacisnąć klawisz F1, aby przejść do strony pomocy MSDN, jeśli potrzebujesz więcej informacji na temat opcji. Aby uzyskać więcej informacji, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Nawiązywanie połączenia z programu Visual Studio Team Services i serwera Team Foundation Server
 Visual Studio Team Services (VSTS) jest oparta na chmurze Usługa hostingu projektach oprogramowania i umożliwianie współpracy w zespołach. Usługa VSTS wspiera systemu Git i kontrolą źródła Team Foundation, a także Scrum i CMMI Agile metodologii programowania. Team Foundation Version Control (TFVC) używa serwera pojedynczego, scentralizowane repozytorium do śledzenia i wersji plików. Lokalne zmiany są zawsze ewidencjonowane na centralnym serwerze, gdzie inni deweloperzy mogą pobrać najnowsze zmiany. Team Foundation Server (TFS) 2015 to Centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Dzięki temu wszyscy pracownicy z procesem rozwoju uczestnictwa, używając jednego rozwiązania. TFS jest przydatne w celu zarządzania heterogenicznych zespołów i projektów, zbyt.

 Jeśli masz konto usługi Visual Studio Team Services lub serwera Team Foundation Server w sieci, nawiążesz z nim za pośrednictwem okna programu Team Explorer. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzania elementami roboczymi, kompilacji i rozpoczęcia pokoje zespołów dostępu oraz obszarów roboczych. Możesz otworzyć Team Explorer z **Szybkie uruchamianie** lub w menu głównym z **widoku &#124; Team Explorer** lub **zespołu &#124; Zarządzaj połączeniami**.  Aby uzyskać więcej informacji na temat programu Visual Studio Team Services, zobacz [www.visualstudio.com](https://www.visualstudio.com/). Aby uzyskać więcej informacji na temat serwera Team Foundation Server, zobacz [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Na poniższej ilustracji przedstawiono okienka programu Team Explorer dla rozwiązania, który znajduje się w usłudze VSTS:

 ![Program Visual Studio Team Explorer](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Tworzenie rozwiązań i projektów
 Chociaż można używać programu Visual Studio do przeglądania kodu poszczególnych plików, częściej będziesz pracować *projektu*. Projekt programu Visual Studio to zbiór plików i zasobów, które są kompilowane do pojedynczego pliku binarnego pliku wykonywalnego dla aplikacji (na przykład .exe, biblioteki DLL lub appx). Dla witryn sieci Web — ASP.NET jest generowany nie pliku wykonywalnego, a projekt zawiera tylko kod HTML, plików JavaScript i obrazy. Visual Studio, ponieważ czasami może być konieczne do utworzenia wielu plików binarnych lub witryn sieci Web, które są ściśle powiązane, ma koncepcji rozwiązania, które mogą zawierać wiele projektów lub witryn sieci Web. Podczas tworzenia projektu rzeczywistości tworzysz projekt w a rozwiązania, a następnie można dodać więcej projektów do tego rozwiązania później Jeśli potrzebujesz. Na przykład jeśli masz projekt DLL, można dodać projektu .exe do rozwiązania, który ładuje i korzysta z biblioteki DLL.

 A *szablonu projektu* to zbiór plików kodu wstępnie wypełniony i ustawienia konfiguracji, które Ci szybko skonfigurować do utworzenia określonego rodzaju aplikacji. Program Visual Studio jest dostarczany z wielu szablonów projektu do wyboru, a jeśli żadna z domyślnych szablonów działa, możesz utworzyć własne. Po utworzeniu projektu z szablonem, można uruchomić pisania własnego kodu w nim, w dostarczone pliki lub w nowych plików, które można dodać. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md). Poniższa ilustracja przedstawia okno dialogowe Nowy projekt z szablonami projektu, które są dostępne dla aplikacji ASP.NET.

 ![Okno dialogowe nowego projektu programu Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Projektowanie interfejsu użytkownika
 Projektant jest intuicyjne narzędzia, która pozwala na tworzenie interfejsu użytkownika bez konieczności pisania kodu. Można przeciągać formanty interfejsu użytkownika, takie jak pola listy, kalendarze i przyciski z [przybornika](../ide/reference/toolbox.md) okna na powierzchni projektowej, który reprezentuje okno lub okno dialogowe. Można zmienić rozmiar i rozmieszczanie elementów bez pisania żadnego kodu. Projektanci są uwzględniane dla dowolnego typu projektu, która ma interfejs użytkownika.

 Jeżeli projekt zawiera interfejs użytkownika oparty na XAML, projektancie domyślny jest program Blend for Visual Studio, narzędzie złożone grafiki, które bezproblemowo współdziała z programem Visual Studio.

 ![Obszar roboczy](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Widok projektu** Wyświetla projektowania wizualnego dokumentu. W tym widoku można narysować lub modyfikować obiekty na powierzchni projektowej.|
|![](../designers/media/b1-2.png "B1_2")|**Łącza do stron nadrzędnych** szybko poruszać się między edycję szablonu tryb edycji stylu tryb i edytowania obiektów zakres dla wybranego obiektu.|
|![](../designers/media/b1-3.png "B1_3")|**Powiększenie** umożliwia powiększenia powierzchni projektowej lub obiekty na powierzchni projektowej.|
|![](../designers/media/b1-4.png "B1_4")|**Projektowanie kontrolek powierzchni** Użyj tych kontrolek (**Pokaż siatkę przyciągania**, **przyciąganie do linii siatki** i **włączyć lub wyłączyć przyciąganie do linii wyrównania**) można ustawić opcje przyciągania. Przyciągania jest na obiekty do siebie lub mają równe odstępy wierszy na powierzchni projektowej.|
|![](../designers/media/b1-5.png "B1_5")|**Edytor kodu** edycji kodu XAML, C#, C++ lub Visual Basic ręcznie w edytorze kodu.|

 Aby uzyskać więcej informacji, zobacz [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Pisania, nawigowania i rozumienie kodu
 Jeśli jesteś deweloperem, okno edytora jest będzie prawdopodobnie spędzisz tutaj większość czasu. Program Visual Studio obejmuje edytory dla C#, C++, Visual Basic, JavaScript, XML, HTML, CSS i F#, i innych firm stanowią wtyczek edytorów (i kompilatory) dla innych języków.

 Można edytować poszczególne pliki w edytorze tekstów, klikając **pliku &#124; Otwórz &#124; pliku.** Aby edytować pliki w otwartym projekcie, należy kliknąć nazwę pliku w Eksploratorze rozwiązań. Jest w trybie kolorowym kod i schemat kolorów można spersonalizować, wpisując "Kolory" Szybkie uruchamianie. Może mieć wiele systemu windows z kartami edytora tekstu Otwórz naraz. Każde okno podzielić się niezależnie. Edytor tekstu można również uruchomić w trybie pełnoekranowym.

 ![GreetingsConsoleApp.cpp w edytorze kodu](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn C ++")

 Edytor tekstu jest wysoce interakcyjny (jeśli ma to być) produktywne wiele funkcji, które ułatwiają lepsze szybsze pisanie kodu. Różne funkcje za pomocą języka, a nie masz żadnego z nich (typu "Editor" na szybkie uruchamianie) umożliwia włączanie i wyłączanie funkcji: Typowe funkcje produktywności, należą:

1. [Refaktoryzacja](../ide/refactoring-in-visual-studio.md) obejmuje operacje, takie jak inteligentne zmiana nazwy zmiennych, przenosząc zaznaczone wiersze kodu w to oddzielna funkcja przenoszenia kodu do innych lokalizacji, redordering parametrów funkcji i nie tylko.

2. *Funkcja IntelliSense* to ogólny termin dla zestawu popularne funkcje, które wyświetlania informacji o typie o kodzie bezpośrednio w edytorze, a w niektórych przypadkach zapisu małe fragmenty kodu dla Ciebie. To, jak podstawowa dokumentacja wbudowanego w edytorze, co pozwala uniknąć konieczności wyszukiwania informacji o typie w oknie Pomoc. Funkcje IntelliSense, zależy od języka. Aby uzyskać więcej informacji, zobacz [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [IntelliSense specyficzne dla języka Visual Basic ](../ide/visual-basic-specific-intellisense.md). Poniższa ilustracja przedstawia niektóre funkcje IntelliSense w miejscu pracy:

    ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Zygzaki** alertów dotyczących błędów lub potencjalnych problemów w kodzie w czasie rzeczywistym podczas wpisywania, co umożliwia naprawić natychmiast bez oczekiwania na błąd, które mają zostać odnalezione w czasie kompilacji lub wykonywania. Po umieszczeniu wskaźnika myszy nad wężyk, zobaczysz dodatkowe informacje o tym błędzie. Żarówka może również wystąpić na lewym marginesie z sugestii dotyczących sposobu naprawić błąd. Aby uzyskać więcej informacji, zobacz [szybkie wykonywanie akcji dzięki żarówkom](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Ikona żarówki z kursor](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Zakładki](../ide/setting-bookmarks-in-code.md) umożliwiają szybko przechodzić do określonych wierszy w plikach, które aktywnie pracuje.

5. [Hierarchię wywołań](../ide/reference/call-hierarchy.md) okno może być wywoływany w menu kontekstowym edytora tekstu, aby pokazać metody, które wywołanie i są wywoływane przez, metoda pod karetką.

6. **Code Lens** umożliwia znajdowanie odwołań i zmian kodu, połączone usterki, elementy robocze, przeglądy kodu i testów jednostkowych, wszystko to bez zamykania edytora. Aby uzyskać więcej informacji, zobacz [znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md).

7. **Wgląd do definicji** okno pokazuje tekście definicji metody lub typu, bez przechodzenia poza bieżący kontekst. To okno teraz działa dla XAML, zbyt.

8. **Przejdź do definicji** menu kontekstowego spowoduje przejście bezpośrednio do miejsca, w którym definiowany jest funkcji lub obiektu. Inne polecenia nawigacji są także dostępne przez kliknięcie prawym przyciskiem myszy w edytorze.

9. Pokrewne narzędzia [przeglądarki obiektów](http://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470)zawierają umożliwia umożliwia sprawdzanie zestawów .NET lub środowiska wykonawczego Windows w systemie, aby zobaczyć ich typy i jakie metody i właściwości zawierają te typy.

     ![Obiekt System.Timer w przeglądarce](../ide/media/objectbrowser.png "ObjectBrowser")

   Większość elementów menu Edycja i menu Widok odnoszą się do edytora kodu, które w jakiś sposób. Aby uzyskać więcej informacji na temat edytora, zobacz [pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md) i [edycji kodu](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilowanie i tworzenie kodu

Do utworzenia projektu oznacza, że skompilować kod źródłowy i wykonać dowolne kroki są niezbędne do utworzenia pliku wykonywalnego. Różne języki są różne kompilacje i witryn sieci Web w regularnych nie twórz na wszystkich. Niezależnie od typu projektu kompilacji jest standardowa lokalizacji dla tych poleceń. Aby skompilować i uruchomić kod, jednym naciśnięciem klawisza, naciśnij klawisz F5. Każdego kompilatora jest całkowicie można konfigurować za pośrednictwem środowiska IDE. Na pasku narzędzi kompilacji umożliwia określenie, czy chcesz utworzyć wersję debugowania programu przy użyciu symboli i błąd dodatkowe sprawdzanie włączone na potrzeby obsługi punktów przerwania i pojedynczy krok w debugerze lub kompilację wydania, czyli co zostanie ostatecznie zapewni klientom. Na stronie właściwości projektu, można skonfigurować więcej ustawień kompilacji i wielu innych ustawień. Kliknij prawym przyciskiem myszy węzeł projektu w Eksploratorze rozwiązań i wybierz polecenie Właściwości. Można także uruchamiać kompilacje z wiersza polecenia.

Dane wyjściowe z kompilacji, takie jak komunikaty powodzenia lub błędu są wyświetlane w **dane wyjściowe** okna. **Lista błędów** przedstawia szczegółowe informacje na temat błędów kompilacji.

## <a name="debugging-your-code"></a>Debugowanie kodu
 Debuger stanu grafiki programu Visual Studio umożliwia debugowanie kodu uruchamianego w projekcie lokalnym, na zdalnym urządzeniu lub w emulatorze, takie jak te dla systemu Android lub Windows Phone. Można przejść przez kod w jednej instrukcji w danym momencie i sprawdzanie zmiennych, jak możesz przejść, możesz przejrzeć aplikacji wielowątkowych i można ustawić punkty przerwania, które są osiągane tylko wtedy, gdy określony warunek ma wartość true. Wszystkie te można skonfigurować w edytorze kodu, dzięki czemu nie trzeba pozostawić kontekstem Twojego kodu.

 ![Okno podglądu ustawienia punktu przerwania](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Sam debuger ma wiele okien, które umożliwiają wyświetlanie i manipulowanie zmienne lokalne, stos wywołań i innych aspektów środowiska wykonawczego. Możesz znaleźć tych okien na **debugowania** menu.

 [Bezpośrednim](../ide/reference/immediate-window.md) pozwala na typ w wyrażeniu i natychmiastowe wyświetlenie jego wyniku.

 [IntelliTrace](http://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) okna rejestruje każde wywołanie metody i innych zdarzeń z uruchomiony .NET program i może ułatwić odnajdywanie, gdy problem pochodzi.

 Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testowanie kodu
 Program Visual Studio obejmuje środowiska testów jednostkowych dla kodu zarządzanego (.NET) i jeden dla natywnych języka C++. Aby utworzyć jednostkę testów, po prostu Dodaj projekt testu do rozwiązania, pisania testów, a następnie uruchom je z okna Eksploratora testów. Aby uzyskać więcej informacji, zobacz [swój kod testu jednostkowego](../test/unit-test-your-code.md).

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analizowanie jakości kodu i wydajności
 Visual Studio zawiera zaawansowane narzędzia do analizy statycznej i środowiska uruchomieniowego. Narzędzia do analizy statycznej pomóc w zidentyfikowaniu potencjalnych błędów projektowania, globalizacji, współpracy, wydajności, zabezpieczeń i innych kategorii. Testowanie wydajności lub profilowania, polega na mierzenie sposób działania Twojego programu. Dostęp tych narzędzi z **analizy** menu. Aby uzyskać więcej informacji, zobacz [poprawa jakości za pomocą programu Visual Studio, narzędzia diagnostyczne](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Łączenie z usługami w chmurze i baz danych
 [Eksploratora serwera](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) zasoby zostaną wyświetlone w oknie programu Visual Studio w ramach kont zarządzanych w ramach konta personalizacji (po jednym zalogowaniu przy użyciu), łącznie z wystąpienia programu SQL Server, Azure, usługami Salesforce.com, Office 365 i witryny sieci Web.

 ![Eksplorator serwera](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Program Visual Studio obejmuje [programu Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), które umożliwiają tworzenie, debugowanie, obsługa i Refaktoryzuj baz danych. Możesz pracować z projektem bazy danych lub bezpośrednio z bazy danych połączone wystąpienie na — lub poza siedzibą firmy.

 Eksplorator obiektów SQL Server w programie Visual Studio oferuje widok obiektów bazy danych podobny do programu SQL Server Management Studio. Eksplorator obiektów SQL Server pozwala realizować administracji i projektowania lekkich bazy danych, w tym edytowanie danych w tabelach, porównywanie schematów i wykonywanie zapytań za pomocą menu kontekstowych bezpośrednio w Eksploratorze obiektów SQL Server. Narzędzia SSDT obejmują również typy projektu i narzędzia do programowania programu SQL Server 2012 Analysis Services, usługi Reporting Services i rozwiązań integracji usług Business Intelligence (BI) (wcześniej znane jako Business Intelligence Development Studio).

 ![Eksplorator obiektów SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Wdrażanie gotowych aplikacji
 Gdy aplikacja jest gotowa do wdrożenia dla klientów, Visual Studio udostępnia narzędzia, aby to zrobić, czy wdrażasz Windows Store, w witrynie programu SharePoint lub przy użyciu technologii InstallShield lub Instalatora Windows. Jest ona dostępna za pośrednictwem środowiska IDE. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Architektura i modelowanie narzędzi (tylko wersja Enterprise)
 Architektura i modelowanie narzędzi programu Visual Studio umożliwia projektowanie i modelowanie aplikacji. Te narzędzia ułatwiają wizualizować strukturę kodu, zachowanie i relacje. Możesz tworzyć modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji, jako część procesu opracowywania. Możesz śledzić wymagania, zadania, przypadki testowe, błędy i inne prace związane ze swoimi modelami, łącząc elementy modelu do elementów roboczych serwera Team Foundation Server i plan rozwoju. Aby uzyskać więcej informacji, zobacz [projektowanie i modelowanie aplikacji](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Rozszerzanie programu Visual Studio za pomocą programu Visual Studio SDK
 Program Visual Studio jest rozszerzalna platforma. Rozszerzenia programu Visual Studio to narzędzie niestandardowe, która integruje się z IDE. Można dodać rozszerzenia innych firm lub tworzyć własne. Aby uzyskać więcej informacji, zobacz [programowanie rozszerzenia programu Visual Studio](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Dotyczące środowiska użytkownika w usłudze Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) są niezbędne odwołania dla każdego, kto pisanie rozszerzenia dla programu Visual Studio. Te wytyczne specyficzne dla platformy obejmują informacji na temat projektu okna dialogowego, czcionki, kolory, ikony, typowe formanty oraz inne wzorce interakcji, składające się z nowej funkcji bezproblemowo integrują się z programem Visual Studio.

## <a name="in-this-guide"></a>W tym przewodniku

|||
|-|-|
|[Konta użytkowników i aktualizacje](../ide/user-accounts-and-updates.md)|[Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[Instrukcje: Poruszanie się w środowisku IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Wprowadzenie do programowania w programie Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Znajdowanie rozszerzeń programu Visual Studio i korzystanie z nich](../ide/finding-and-using-visual-studio-extensions.md)|[Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)|
|[Pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md)|[Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Narzędzia profilowania](../profiling/profiling-tools.md)|[Podnoszenie jakości kodu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Projektowanie interfejsów użytkownika](../designers/designing-user-interfaces.md)|[Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)|
|[Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)|[Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)|
|[Obsługa 64-bitowego środowiska IDE programu Visual Studio](../ide/visual-studio-ide-64-bit-support.md)|[Zabezpieczenia](../ide/security-in-visual-studio.md)|
|[Przykłady w Visual Studio](../ide/visual-studio-samples.md)|[Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)|
|[Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)|[Informacje o interfejsie użytkownika](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Edytowanie kodu](https://www.visualstudio.com/features/ide-vs)
- [Co nowego w programie Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Porozmawiaj z nami](../ide/talk-to-us.md)