---
title: Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52e0b8f87774b11b1750700d5bef19c5423824c4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667141"
---
# <a name="visual-studio-ide"></a>Visual Studio IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 to pakiet narzędzi do tworzenia oprogramowania, od fazy planowania poprzez projektowanie interfejsu użytkownika, kodowanie, testowanie, debugowanie, analizowanie jakości kodu i wydajności, wdrażanie w klientach oraz zbieranie danych telemetrycznych dotyczących użycia. Te narzędzia są przeznaczone do bezproblemowego współdziałania i są udostępniane za pomocą zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.

Za pomocą programu Visual Studio można tworzyć wiele rodzajów aplikacji, od prostych aplikacji ze sklepu i gier dla klientów mobilnych, w dużych, złożonych systemach, które są przedsiębiorstwami i centrami danych. Możesz utworzyć:

- Aplikacje i gry, które działają nie tylko w systemie Windows, ale również w systemach Android i iOS.

- Witryny internetowe i usługi sieci Web oparte na ASP.NET, JQuery, AngularJS i innych popularnych strukturach.

- Aplikacje dla platform i urządzeń, tak jak platformy Azure, Office, SharePoint, Hololens, urządzenia Kinect i Internet rzeczy, do nazywania zaledwie kilku przykładów.

- Gry i aplikacje intensywnie korzystające z grafiki dla różnych urządzeń z systemem Windows, w tym z konsoli Xbox, za pomocą technologii DirectX.

Program Visual Studio domyślnie zapewnia obsługę języków C#, C i C++, JavaScript, F#i Visual Basic. Program Visual Studio działa i integruje się z aplikacjami innych firm, takimi jak Unity, za pomocą rozszerzenia [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) i Apache Cordova przez [Visual Studio Tools Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Możesz samodzielnie rozciągnąć program Visual Studio, tworząc niestandardowe narzędzia wykonujące wyspecjalizowane zadania.

Jeśli jeszcze nie korzystasz z programu Visual Studio, zapoznaj się z tematami dotyczącymi programowania, korzystając z samouczków i przewodników dotyczących [programu Visual Studio](../ide/get-started-developing-with-visual-studio.md) .

Jeśli chcesz dowiedzieć się więcej o nowych funkcjach w programie Visual Studio 2015, zobacz [co nowego w programie Visual studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Instalator programu Visual Studio
 Możesz sprawdzić, która wersja programu Visual Studio jest odpowiednia dla Ciebie w [wersjach programu Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Program Visual Studio 2015 można zainstalować, pobierając go z [plików do pobrania w programie Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Aby dowiedzieć się więcej o procesie instalacji, zobacz [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Podstawy środowiska IDE
 Na poniższej ilustracji przedstawiono środowisko IDE programu Visual Studio z otwartym projektem oraz okno Eksplorator rozwiązań dla nawigowania w plikach projektu oraz okno Team Explorer do nawigowania po kontroli źródła i śledzenia elementów roboczych. Funkcje na pasku tytułu, które zostały wywołane, zostały opisane poniżej bardziej szczegółowo.

 ![Visual Studio IDE](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Logowanie
 Po uruchomieniu programu Visual Studio po raz pierwszy możesz zalogować się przy użyciu konto Microsoft lub konta służbowego. Użytkownik jest zalogowany, umożliwia synchronizowanie ustawień, takich jak układy okien, na wielu urządzeniach i automatyczne nawiązywanie połączenia z usługami, które mogą być potrzebne, takich jak subskrypcje platformy Azure i Visual Studio Team Services. Jeśli masz licencję opartą na subskrypcji, musisz najpierw zalogować się do programu Visual Studio, aby uzyskać aktualność tokenu licencji. Jeśli masz licencję klucza produktu, nie musisz się zalogować, ale dzięki temu będzie wygodniejsze łączenie się z Visual Studio Team Services i kontami przy użyciu platformy Azure, pakietu Office 365, Salesforce.com. Aby uzyskać więcej informacji, zobacz [Logowanie do programu Visual Studio](../ide/signing-in-to-visual-studio.md).

 Jeśli masz wiele kont Visual Studio Team Services, kont platformy Azure lub subskrypcji MSDN, możesz połączyć je i uzyskać dostęp do zasobów i usług we wszystkich kontach przy użyciu logowania jednokrotnego. Aby uzyskać więcej informacji, zobacz [pracy z wieloma kontami użytkowników](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Aktualność
 Ikona powiadomienia w prawym górnym rogu paska tytułu informuje o dostępności aktualizacji dla programu Visual Studio lub wszelkich powiązanych składników, które zostały zainstalowane. Możesz zdecydować, czy te powiadomienia mają zostać odrzucone. Aby uzyskać więcej informacji, zobacz [powiadomienia programu Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Znajdowanie rzeczy i uzyskiwanie pomocy
 Okno [Szybkie uruchamianie](../ide/reference/quick-launch-environment-options-dialog-box.md) wyświetlone poniżej umożliwia szybkie znajdowanie poleceń programu Visual Studio, narzędzi, funkcji i tak dalej, gdy nie znasz skrótu klawiaturowego lub położenia menu. Wystarczy wpisać to, czego szukasz, i szybkie uruchomienie spowoduje nadanie linku do niego.

 ![Wyniki szybkiego uruchamiania dla "nowy projekt"](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN to witryna sieci Web firmy Microsoft dla dokumentacji technicznej; czytasz tę stronę w witrynie MSDN już teraz! W programie Visual Studio możesz nacisnąć klawisz **F1** , aby przejść do strony pomocy MSDN dla aktywnego okna. Możesz również nacisnąć klawisz **F1** w edytorze kodu, aby przejść do strony pomocy MSDN dla interfejsu API lub słowa kluczowego w bieżącym położeniu karetki. Na przykład w C# pliku Umieść karetkę w miejscu lub tuż na końcu deklaracji `System.String` i naciśnij klawisz **F1** , aby przejść do strony pomocy MSDN dla <xref:System.String>.

### <a name="giving-feedback"></a>Przekazywanie opinii
 W dowolnym momencie możesz łatwo przekazać nam swoją opinię na temat programu Visual Studio. Kliknij ikonę opinii na pasku tytułu obok pozycji **Szybkie uruchamianie** , a następnie kliknij pozycję **Zgłoś problem** lub **Podaj sugestię**. W wersjach wstępnych programu Visual Studio jest również dostępna opcja **Oceń ten produkt** . Sprawdzamy wszystkie te komentarze i używają ich do ulepszania produktu. Aby uzyskać więcej informacji, zobacz [rozmowa z nami](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalizowanie środowiska IDE
 Układ okna można dostosować tak, aby pasował do stylu programowania. W dowolnym momencie można zadokować, przestawić lub ukryć dowolne okno, a także uruchomić Edytor w trybie pełnoekranowym. Możesz tworzyć i zapisywać wiele niestandardowych układów okien, które pokazują tylko te okna, które są potrzebne dla określonych kontekstów. Na przykład można utworzyć układ pełnoekranowy, aby cały widoczny jest Edytor kodu. Można też tworzyć różne układy do debugowania i dla operacji zespołu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md).

 Możesz dostosować program Visual Studio na wiele innych sposobów i przeroamingować ustawienia, jeśli pracujesz na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md).

 Istnieją skróty klawiaturowe dla niemal wszystkich elementów i można je również dostosować. Aby utworzyć nowe skróty, wpisz "klawiatura" w obszarze szybkiego uruchamiania, aby otworzyć okno dialogowe klawiatura. W tym miejscu możesz nacisnąć klawisz F1, aby przejść do strony pomocy MSDN, jeśli potrzebujesz więcej informacji na temat opcji. Aby uzyskać więcej informacji, zobacz [domyślne skróty klawiaturowe w programie Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Nawiązywanie połączenia z Visual Studio Team Services i Team Foundation Server
 Visual Studio Team Services (VSTS) to oparta na chmurze usługa do hostowania projektów oprogramowania i umożliwiająca współpracę w zespołach. VSTS obsługuje zarówno systemy kontroli źródła git, jak i Team Foundation, a także metody programowania Scrum, CMMI i Agile. Kontrola wersji serwera Team Foundation (TFVC) używa jednego scentralizowanego repozytorium serwera do śledzenia i wersji plików. Lokalne zmiany są zawsze sprawdzane na serwerze centralnym, w którym inni deweloperzy mogą uzyskać najnowsze zmiany. Team Foundation Server (TFS) 2015 to centrum zarządzania cyklem życia aplikacji dla programu Visual Studio. Umożliwia ona wszystkim uczestnikom procesu opracowywania korzystanie z jednego rozwiązania. TFS jest również przydatny do zarządzania niejednorodnymi zespołami i projektami.

 Jeśli masz konto Visual Studio Team Services lub Team Foundation Server w sieci, Połącz się z nim za pomocą okna Team Explorer. Z tego okna można sprawdzić kod do lub z kontroli źródła, zarządzać elementami roboczymi, uruchamiać kompilacje i uzyskiwać dostęp do pokojów zespołu i obszarów roboczych. Team Explorer można otworzyć z poziomu **paska Szybkie uruchamianie** lub z poziomu menu głównego **z &#124; widoku Team Explorer** lub **z &#124; zespołu zarządzanie połączeniami**.  Aby uzyskać więcej informacji na temat Visual Studio Team Services, zobacz [www.VisualStudio.com](https://www.visualstudio.com/). Aby uzyskać więcej informacji na temat Team Foundation Server, zobacz [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Na poniższej ilustracji przedstawiono okienko Team Explorer dla rozwiązania, które jest hostowane w VSTS:

 ![Team Explorer programu Visual Studio](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Tworzenie rozwiązań i projektów
 Chociaż możesz użyć programu Visual Studio do przeglądania pojedynczych plików kodu, często będziesz pracować w *projekcie*. Projekt programu Visual Studio to zbiór plików i zasobów, które są kompilowane do pojedynczego binarnego pliku wykonywalnego dla aplikacji (na przykład exe, DLL lub APPX). W przypadku witryn sieci Web non-ASP.NET nie jest tworzony plik wykonywalny, a projekt zawiera tylko pliki HTML, JavaScript i obrazy. Ponieważ czasami może być konieczne utworzenie wielu plików binarnych lub witryn sieci Web, które są ściśle powiązane, program Visual Studio ma koncepcję rozwiązania, które może zawierać wiele projektów lub witryn sieci Web. Podczas tworzenia projektu, w rzeczywistości tworzysz projekt-w-a-rozwiązanie, a później możesz dodać kolejne projekty do tego rozwiązania. Na przykład jeśli masz projekt DLL, możesz dodać projekt. exe do rozwiązania, które ładuje i zużywa bibliotekę DLL.

 *Szablon projektu* to zbiór wstępnie wypełnionych plików kodu i ustawień konfiguracji, które pozwalają szybko skonfigurować tworzenie określonego rodzaju aplikacji. Program Visual Studio jest dostarczany z wieloma szablonami projektu do wyboru, a jeśli żaden z szablonów domyślnych nie będzie działać, możesz utworzyć własne. Po utworzeniu projektu przy użyciu szablonu można zacząć pisać własny kod w pliku lub w nowo dodawanych plikach. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md). Na poniższej ilustracji przedstawiono okno dialogowe Nowy projekt z szablonami projektu, które są dostępne dla aplikacji ASP.NET.

 ![Okno dialogowe nowego projektu programu Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Projektowanie interfejsu użytkownika
 Projektant jest intuicyjnym narzędziem umożliwiającym tworzenie interfejsu użytkownika bez pisania kodu. Możesz przeciągnąć kontrolki interfejsu użytkownika, takie jak pola listy, kalendarze i przyciski z okna [przybornika](../ide/reference/toolbox.md) na powierzchnię projektu reprezentującą okno lub okno dialogowe. Można zmienić rozmiar i rozmieścić elementy bez pisania kodu. Projektanci są uwzględnieni dla dowolnego typu projektu, który ma interfejs użytkownika.

 Jeśli projekt ma interfejs użytkownika oparty na języku XAML, domyślnym projektantem jest Blend for Visual Studio, zaawansowane narzędzie graficzne, które bezproblemowo współpracuje z programem Visual Studio.

 ![Robocze](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Widok Projekt** Wyświetla projekt wizualizacji dokumentu. W tym widoku można rysować lub modyfikować obiekty na powierzchni projektowej.|
|![](../designers/media/b1-2.png "B1_2")|Pasek **nawigacyjny** Szybko Przechodź między trybem edycji szablonu, trybem edycji stylu i zakresem edycji obiektów dla zaznaczonego obiektu.|
|![](../designers/media/b1-3.png "B1_3")|**Powiększenie** Służy do powiększania powierzchni projektowej lub obiektów na powierzchni projektowej.|
|![](../designers/media/b1-4.png "B1_4")|**Projektowanie kontrolek powierzchni** Użyj tych kontrolek (**Pokaż siatkę**przyciągania, **Przyciągaj do linii siatki** i **Włącz lub Wyłącz przyciąganie do linii wyrównania**), aby ustawić opcje przyciągania. Przyciąganie jest przydatne do nakreślania obiektów do siebie lub do równomiernie rozłożonych linii na powierzchni projektowej.|
|![](../designers/media/b1-5.png "B1_5")|**Edytor kodu** Edytuj kod XAML C# C++ lub Visual Basic ręcznie w edytorze kodu.|

 Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Pisanie, nawigowanie i zrozumienie kodu
 Jeśli jesteś deweloperem, okno edytora jest miejscem, w którym najprawdopodobniej spędzasz najwięcej czasu. Program Visual Studio zawiera C#edytory C++dla,, Visual Basic, JavaScript, XML, HTML, CSS F#i i innych firm oferują edytory wtyczek (i kompilatory) dla wielu innych języków.

 Poszczególne pliki można edytować w edytorze tekstów, klikając pozycję **plik &#124; &#124; Otwórz plik.** Aby edytować pliki w otwartym projekcie, kliknij nazwę pliku w Eksplorator rozwiązań. Kod jest kolorowy i można spersonalizować schemat kolorów, wpisując "kolory" w szybkim uruchamianiu. Możesz mieć wiele okien z kartami edytora tekstu otwartych jednocześnie. Każde okno można podzielić niezależnie. Edytor tekstu można również uruchomić w trybie pełnoekranowym.

 ![GreetingsConsoleApp. cpp w edytorze kodu](../ide/media/c-ide-editorlinenumberswordwrapon.png "C + + IDE_EditorLineNumbersWordWrapOn")

 Edytor tekstu jest wysoce interaktywny (Jeśli chcesz) z wieloma funkcjami produktywności, które ułatwiają szybsze pisanie lepszego kodu. Funkcje te różnią się w zależności od języka i nie trzeba używać żadnego z nich ("Edytor" w szybkim uruchomieniu) do włączania lub wyłączania funkcji: niektóre typowe funkcje produktywności są następujące:

1. [Refaktoryzacja](../ide/refactoring-in-visual-studio.md) obejmuje operacje, takie jak inteligentne Zmienianie nazw zmiennych, przeniesienie wybranych wierszy kodu do oddzielnej funkcji, przeniesienie kodu do innych lokalizacji, redordering parametrów funkcji i innych.

2. *IntelliSense* to długoterminowy termin dla zestawu popularnych funkcji, które wyświetlają informacje o typie kodu bezpośrednio w edytorze i, w niektórych przypadkach, zapisują małe bity kodu. Jest tak jak w przypadku, gdy podstawowa dokumentacja jest wbudowana w edytorze, co umożliwia wyszukiwanie informacji o typie w osobnym oknie Pomoc. Funkcje IntelliSense różnią się w zależności od języka. Aby uzyskać więcej informacji, [Zobacz C# Visual IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic funkcji IntelliSense](../ide/visual-basic-specific-intellisense.md). Na poniższej ilustracji przedstawiono niektóre funkcje IntelliSense w pracy:

    ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3. **Zygzaky ostrzegają** o błędach lub potencjalnych problemach w kodzie w czasie rzeczywistym, co pozwala na ich natychmiastowe rozwiązanie, bez czekania na odnalezienie błędu podczas kompilacji lub czasu wykonywania. Po umieszczeniu wskaźnika myszy na zygzaku pojawią się dodatkowe informacje o błędzie. Żarówka może również pojawić się na lewym marginesie z sugestiami dotyczącymi sposobu usuwania błędu. Aby uzyskać więcej informacji, zobacz [wykonywanie szybkich akcji z żarówkami](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Żarówka z przesuwaniem myszy](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4. [Zakładki](../ide/setting-bookmarks-in-code.md) pozwalają szybko przechodzić do określonych wierszy w plikach, nad którymi pracujesz.

5. Okno [Hierarchia wywołań](../ide/reference/call-hierarchy.md) może być wywoływane w menu kontekstowym edytora tekstu, aby wyświetlić metody wywołujące i wywoływane przez metodę pod karetką.

6. **Soczewka kodu** umożliwia znajdowanie odwołań i zmian w kodzie, połączonych błędach, elementach roboczych, przeglądach kodu i testów jednostkowych, bez opuszczania edytora. Aby uzyskać więcej informacji, zobacz [Znajdowanie zmian w kodzie i innych historii](../ide/find-code-changes-and-other-history-with-codelens.md).

7. Okno **wgląd do definicji** przedstawia metodę lub definicję typu w tekście, bez przechodzenia z bieżącego kontekstu. To okno teraz działa również w przypadku języka XAML.

8. Opcja menu kontekstowego **Przejdź do definicji** prowadzi bezpośrednio do miejsca, w którym zdefiniowano funkcję lub obiekt. Inne polecenia nawigacji są również dostępne po kliknięciu prawym przyciskiem myszy w edytorze.

9. Powiązane narzędzie, [Przeglądarka obiektów](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), umożliwia sprawdzenie zestawów .net lub środowisko wykonawcze systemu Windows w systemie, aby zobaczyć, jakie typy zawierają i jakie metody i właściwości zawierają.

     ![Przeglądarka Obect przedstawiająca system. Timer](../ide/media/objectbrowser.png "ObjectBrowser")

   Większość elementów z menu Edytuj i menu Widok odnosi się do edytora kodu w jakiś sposób. Aby uzyskać więcej informacji na temat edytora, zobacz [pisanie kodu](../ide/writing-code-in-the-code-and-text-editor.md) i [Edytowanie kodu](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilowanie i kompilowanie kodu

Aby skompilować projekt, należy skompilować kod źródłowy i wykonać wszelkie kroki niezbędne do utworzenia pliku wykonywalnego. Różne języki mają różne operacje kompilacji, a regularne witryny sieci Web nie kompilują się wcale. Niezależnie od typu projektu menu Kompilacja jest standardową lokalizacją tych poleceń. Aby skompilować i uruchomić kod przy użyciu pojedynczego klawisza, naciśnij klawisz F5. Każdy kompilator jest całkowicie konfigurowalny za pomocą IDE. Na pasku narzędzi kompilacja można określić, czy ma zostać utworzona wersja debugowania programu, z symbolami i dodatkowym sprawdzaniem błędów, które obsługują punkty przerwania i pojedynczą czynność w debugerze, lub kompilację wydania, która będzie ostatecznie dostępna dla klientów. Można skonfigurować więcej ustawień kompilacji i wiele innych ustawień na stronie właściwości projektu. Kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań i wybierz polecenie Właściwości. Możesz również uruchamiać kompilacje z poziomu wiersza polecenia.

Dane wyjściowe kompilacji, w tym błąd lub komunikat o powodzeniu, pojawiają się w oknie **danych wyjściowych** . W **Lista błędów** przedstawiono szczegółowe informacje o błędach kompilacji.

## <a name="debugging-your-code"></a>Debugowanie kodu
 Wizualny debuger programu Visual Studio umożliwia debugowanie kodu działającego w projekcie lokalnym, na urządzeniu zdalnym lub na emulatorze, takim jak te dla systemu Android lub Windows Phone. Można przechodzić przez kod po jednej instrukcji w czasie i sprawdzać zmienne w miarę ich wykonywania, można przechodzić przez aplikacje wielowątkowe i można ustawić punkty przerwania, które są osiągane tylko wtedy, gdy określony warunek ma wartość true. Wszystkie te możliwości można skonfigurować w edytorze kodu, tak aby nie trzeba było zostawiać kontekstu kodu.

 ![Okno wglądu w ustawienia punktu przerwania](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Debuger ma wiele okien, które umożliwiają wyświetlanie zmiennych lokalnych, stos wywołań i innych aspektów środowiska uruchomieniowego oraz manipulowanie nimi. Te okna można znaleźć w menu **debugowanie** .

 [Okno bezpośrednie](../ide/reference/immediate-window.md) umożliwia wpisywanie wyrażenia i natychmiastowe wyświetlanie jego wyniku.

 Okno [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) rejestruje każde wywołanie metody i inne zdarzenia w uruchomionym programie .NET i może pomóc w szybkim wyszukiwaniu miejsca, z którego pochodzi problem.

 Aby uzyskać więcej informacji, zobacz [debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testowanie kodu
 Program Visual Studio zawiera platformę testów jednostkowych dla kodu zarządzanego (.NET) i jeden C++dla języka natywnego. Aby utworzyć testy jednostkowe, wystarczy dodać projekt testowy do rozwiązania, napisać testy, a następnie uruchomić je w oknie Eksplorator testów. Aby uzyskać więcej informacji, zobacz [Unit Testing Code](../test/unit-test-your-code.md).

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analizowanie jakości i wydajności kodu
 Program Visual Studio zawiera zaawansowane narzędzia do analizy statycznej i środowiska uruchomieniowego. Narzędzia do analizy statycznej pomagają identyfikować potencjalne błędy podczas projektowania, globalizacji, współdziałania, wydajności, zabezpieczeń i innych kategorii. Testowanie wydajności lub profilowanie obejmuje mierzenie sposobu działania programu. Dostęp do tych narzędzi można uzyskać z menu **Analizuj** . Aby uzyskać więcej informacji, zobacz [poprawianie jakości za pomocą programu Visual Studio narzędzia diagnostyczne](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Łączenie z usługami i bazami danych w chmurze
 W oknie [Eksplorator serwera](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) w programie Visual Studio są wyświetlane zasoby ze wszystkich kont zarządzanych przy użyciu konta personalizacji (tego, kto jest zalogowany), w tym SQL Server wystąpienia, Azure, Salesforce.com, Office 365 i websites.

 ![Eksplorator serwera](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Program Visual Studio zawiera [narzędzia Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), które umożliwiają kompilowanie, debugowanie, konserwację i refaktoryzację baz danych. Można korzystać z projektu bazy danych lub bezpośrednio z połączonym wystąpieniem bazy danych lub w środowisku lokalnym.

 Eksplorator obiektów SQL Server w programie Visual Studio oferuje widok obiektów bazy danych podobny do SQL Server Management Studio. Eksplorator obiektów SQL Server umożliwia administrowanie i Projektowanie bazy danych z lekkim cłem, w tym edytowanie danych tabeli, porównywanie schematów i wykonywanie zapytań za pomocą menu kontekstowego bezpośrednio z Eksplorator obiektów SQL Server. SSDT obejmuje również specjalne typy projektów i narzędzia do opracowywania rozwiązań SQL Server 2012 Analysis Services, Reporting Services i Integration Services (BI) (znanych wcześniej jako Business Intelligence Development Studio).

 ![Eksplorator obiektów SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Wdrażanie ukończonej aplikacji
 Gdy aplikacja jest gotowa do wdrożenia klientom, program Visual Studio udostępnia narzędzia do tego celu, niezależnie od tego, czy wdrażasz w Sklepie Windows, w witrynie programu SharePoint, czy za pomocą technologii InstallShield czy Instalator Windows. Jest ona dostępna za pośrednictwem IDE. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Architektura i narzędzia modelowania (tylko dla przedsiębiorstw)
 Możesz użyć architektury programu Visual Studio i narzędzi do modelowania, aby zaprojektować i modelować aplikację. Te narzędzia ułatwiają wizualizację struktury kodu, zachowania i relacji. Możesz tworzyć modele na różnych poziomach szczegółowości w całym cyklu życia aplikacji w ramach procesu tworzenia oprogramowania. Można śledzić wymagania, zadania, przypadki testowe, błędy i inne prace skojarzone z modelami, łącząc elementy modelu z Team Foundation Server elementami roboczymi i planem rozwoju. Aby uzyskać więcej informacji, zobacz [projektowanie i modelowanie aplikacji](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Rozszerzanie programu Visual Studio za pomocą zestawu Visual Studio SDK
 Program Visual Studio jest rozszerzalną platformą. Rozszerzenie programu Visual Studio to niestandardowe narzędzie, które integruje się z IDE. Możesz dodać rozszerzenia innych firm lub utworzyć własne. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzeń programu Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 [Wskazówki dotyczące środowiska użytkownika programu Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) są istotnym odwołaniem dla każdego zapisu rozszerzeń dla programu Visual Studio. Te wytyczne dotyczące platformy obejmują informacje dotyczące projektowania okna dialogowego, czcionek, kolorów, ikon, wspólnych kontrolek i innych wzorców interakcji, dzięki którym Nowa funkcja zostanie bezproblemowo zintegrowana z programem Visual Studio.

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