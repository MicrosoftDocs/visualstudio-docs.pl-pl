---
title: Co nowego w programie Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 758e2bbf69c7b48a1027819377839cbdce9204fe
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919257"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Co&#39;s Nowość w programie Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Witamy w programie Visual Studio 2015, zintegrowany pakiet narzędzi zwiększających produktywność dla deweloperów, cloud services i rozszerzeń umożliwiających Tobie i Twojemu zespołowi tworzyć dobre aplikacje i gry dla sieci web, for Windows Store, za pomocą pulpitu, dla systemu Android i dla systemu iOS.

Ta strona opisano niektóre najważniejsze funkcje, które są nowy od czasu Visual Studio 2013 RTM, łącznie z funkcjami, które zostały najpierw wprowadzone w jednej z aktualizacji programu Visual Studio 2013. Aby uzyskać pełną listę what's new in Visual Studio 2015, zobacz [wersji](https://www.visualstudio.com/news/vs2015-vs).

Aby dowiedzieć się więcej na temat wiele ulepszeń oraz nowe funkcje w programie Visual Studio ALM, zobacz [What's new for TFS 2015](/azure/devops/server/whats-new#tfs-2015).

## <a name="a-new-setup-experience"></a>Nowe środowisko instalacji
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Środowisko instalacji programu Visual Studio 2015 zawiera zostały składającej tak, że musisz zainstalować części, które są potrzebne. Dzięki temu instalacja szybciej w przypadku wielu typowych scenariuszy obejmujących programowanie .NET lub sieci Web. Czy są inne typy programowania, takich jak tworzenie aplikacji mobilnych dla wielu platform, pracujesz w języku C++ lub F#, wybierz **niestandardowe** instalacji i następnie wybierz składniki i opcjonalne zestawy SDK innych firm, których potrzebujesz. Można także zainstalować dowolne niestandardowe składniki później. Na przykład jeśli wybranie instalacji podstawowe, a następnie ponów próbę utworzenia nowego projektu w języku C++, możesz zostanie wyświetlony monit Pobierz narzędzia programistyczne języka C++.

 ![Okno dialogowe Instalatora programu Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Zaloguj się na wielu kontach
 Za pomocą programu Visual Studio 2015 nowe usprawnione środowisko logowania zaprojektowano do znacznego uproszczenia dostępu do zasobów online, nawet wtedy, gdy masz wiele kont programu Visual Studio. Po użytkownik logowania do programu Visual Studio, automatycznie zalogowano Cię do wszystkich wystąpień programu Visual Studio 2015 i Blend na swojej maszynie. Logowanie się automatycznie uruchamia roaming ustawień dla Ciebie. W programie Visual Studio 2015, Twoje konto jest współużytkowany przez funkcje tak, tak długo, jak masz dobre tokenu, można uzyskać dostęp kont usługi Visual Studio Team Services z **Team Explorer**i zasobów, jak i witryny sieci Web z usługi Microsoft Azure Subskrypcja, w Eksploratorze serwera. Zobaczysz również Twoich zasobów platformy Azure, w oknie dialogowym Nowy projekt dla projektów usługi Application Insights i aplikacji mobilnych platformy Azure, usługi Azure Storage, zostanie wyświetlony [Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) i [Saleforce.com developer](https://developer.salesforce.com/) konta w nowym **Dodaj podłączoną usługę** okna dialogowego.

 Można pracować z wieloma kontami użytkowników w programie Visual Studio, dodając je zgodnie z rzeczywistym lub za pośrednictwem nowego Menedżera konta. Następnie można przełączać się między tymi kontami na bieżąco podczas nawiązywania połączenia z usługi lub uzyskiwaniem dostępu do zasobów online. Visual Studio zapamiętuje konta, które możesz dodać, aby można było używać ich z dowolnego wystąpienia programu Visual Studio lub Blend. Program Visual Studio są także przenoszone listy kont (Chociaż firma Microsoft nie zostaną odzwierciedlone cenne poświadczenia) przy użyciu konta personalizacji, dzięki czemu możesz szybko rozpocząć pracę przy użyciu jednego z tych kont na innym urządzeniu. Oczywiście można usunąć konta z poziomu okna dialogowego Ustawienia konta w dowolnym momencie. Aby rozpocząć pracę, zobacz [Praca z wieloma kontami użytkownika](./ide/work-with-multiple-user-accounts.md).

 ![Menedżer kont](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Wybieranie odpowiednich platform docelowych
 Program Visual Studio 2015 obsługuje programowanie dla wielu platform urządzeń przenośnych. Można pisać aplikacje i gry, które docelowy z systemem iOS, Android i Windows i udostępnić wspólny kod podstawowy wszystko z poziomu środowiska IDE programu Visual Studio. Zostaną wyświetlone wszystkie te nowe typy projektów w pliku, okno dialogowe Nowy projekt.

 I — oczywiście — Obsługa klasycznych aplikacji pulpitu jest lepsze niż kiedykolwiek wcześniej z dużą liczbą ulepszenia języków, biblioteki i narzędzia.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Aplikacje mobilne dla wielu platform w języku C# za pomocą platformy Xamarin dla programu Visual Studio
 Xamarin to przenośnych strukturę, która umożliwia pisanie kodu w języku C#, który wiąże natywnie w systemach IOS i interfejsy API systemu Android. Firma Microsoft nawiązała współpracę ściśle zintegrowana za pomocą platformy Xamarin w swojej wersji programu Xamarin dla programu Visual Studio rozszerzenia, które pozwala na tworzenie oprogramowania dla systemów Android, iOS i Windows Phone za pomocą jednego rozwiązania, ze współdzielonym kodem. Za pomocą platformy Xamarin korzystając z jednego języka i jednego kodu bazowego, z minimalnym różnic między platformami.  Platforma Xamarin dla programu Visual Studio jest obsługiwana w programie Visual Studio 2010 i nowszych. Program Xamarin w wersji starter znajduje się w programie Visual Studio 2015. Aby rozpocząć pracę, zobacz [Kompilowanie aplikacji z natywnym interfejsem użytkownika przy użyciu platformy Xamarin w programie Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Aplikacje mobilne dla wielu platform w języku HTML/JavaScript przy użyciu Apache Cordova
 Visual Studio Tools for Apache Cordova jest wyniku bliskiej współpracy między firmami Microsoft i typu open source społeczności Apache Cordova. Narzędzia te umożliwiają za pomocą kodu HTML, CSS i JavaScript (lub języka Typescript) opracowywania aplikacji mobilnych dla wielu platform. Możesz docelowych systemów Android, iOS i Windows przy użyciu jednej bazy kodu i bogactwa programu Visual Studio IDE, w tym JavaScript IntelliSense, narzędzia DOM Explorer, konsoli języka JavaScript, punkty przerwania, zegarki, zmiennych lokalnych, tylko mój kod i inne.  Program Visual Studio Tools for Apache Cordova aplikacje mają dostęp do natywnych możliwości urządzenia na wszystkich platformach za pomocą wtyczki, które zapewniają wspólny interfejs API języka JavaScript. Aby rozpocząć pracę, zobacz [Rozpoczynanie pracy z usługą Visual Studio Tools for Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Gry na urządzenia przenośne dla wielu platform w języku C# za pomocą aparatu Unity
 Unity to platforma powszechnie używane dla wielu platform tworzeniu gier 2D i 3D. Można napisać swoją grę w języku C# i uruchom go natywnie na systemów Android, iOS, Windows Phone i wielu innych platform. Visual Studio Tools for Unity to rozszerzenie, które integruje Unity za pomocą programu Visual Studio IDE. To rozszerzenie zapewnia wszystkie funkcje programu Visual Studio IDE i debugera, oprócz wydajności funkcji, które są przeznaczone dla deweloperów Unity. Visual Studio Tools for Unity 2.0 w wersji Preview 2 dodaje obsługę programu Visual Studio 2015, dodatkowo na szereg nowych funkcji, takich jak lepszą wizualizację obiektów w zmiennych lokalnych i obejrzyj systemu windows. Firma Microsoft niedawno pozyskała SyntaxTree, twórców programu Visual Studio Tools for Unity. Aby pobrać program Visual Studio Tools for Unity 2.0 w wersji 2, a aby uzyskać więcej informacji na temat programu Visual Studio Tools for Unity, zobacz [Visual Studio Tools for Unity 2.0](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Aplikacje dla wielu platform i bibliotek natywnych języka C++
 Język C++ jest dostępna natywnie na większości urządzeń przenośnych. Służy on do zapisu dla wielu platform udostępnionych bibliotek kodu, które mogą być wbudowane w wiele obiektów docelowych platform przenośnych. Możesz nawet utworzyć zupełnie mobilnych w języku C++. Visual C++ zapewnia narzędzia umożliwiające edytowanie, tworzenie, wdrażanie i debugowanie kodu dla wielu platform. Oprócz szablonów dla aplikacji Windows mogą tworzyć projekty na podstawie szablonów dla aplikacji Android Native Activity, aplikacje dla systemu iOS lub projekty biblioteki udostępnionego kodu dla wielu platform, które obejmują aplikacje hybrydowe platformy Xamarin. Specyficzne dla platformy funkcje IntelliSense pozwala eksplorować interfejsy API i generować poprawny kod dla systemu Android, iOS lub Windows. Można skonfigurować kompilację dla x86 lub natywnych platform ARM i wdrożyć kod symulatora systemu iOS lub urządzeń z systemem iOS dołączone do sieci komputera Mac, na bezpośrednio podłączonych urządzeń z systemem Android lub wydajne Microsoft Visual Studio Emulator for Android używać do testowania. Możesz ustawić punkty przerwania, obserwuj zmienne, wyświetlanie stosu i przejść przez kod języka C++ w debugerze programu Visual Studio. Możesz udostępniać wszystkie regiony z wyjątkiem kodu najbardziej specyficznego dla platformy między wieloma platformami aplikacji i kompilacji dla nich wszystko w jednym rozwiązaniu w programie Visual Studio.

 Aby rozpocząć pracę na wiele platform w języku C++, zobacz [tworzenie aplikacji mobilnych dla wielu platform w języku Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Uniwersalne aplikacje Windows na urządzeniach z systemem Windows 10
 Uniwersalnej platformy Windows i naszych jednego rdzenia Windows umożliwia uruchamianie tę samą aplikację na dowolnym urządzeniu z systemem Windows 10 z telefonów do komputerów stacjonarnych. Tworzenie aplikacji Windows Universal za pomocą programu Visual Studio 2015 i narzędzi Universal Windows App Development.

 ![Platforma uniwersalna systemu Windows](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uruchom aplikację na telefonie z systemem Windows 10, system Windows 10 desktop lub konsoli Xbox. To ten sam pakiet aplikacji! Wraz z wprowadzeniem core systemu Windows 10 w pojedynczą, jednolitą jednego pakietu aplikacji można uruchamiać na wszystkich platformach. Różnych platform mają zestawów SDK rozszerzeń, które można dodać do aplikacji, aby skorzystać z zachowań określonych platform. Na przykład zestawu SDK rozszerzenia dla urządzeń przenośnych obsługuje przycisku Wstecz naciśniętym na urządzeniu z systemem Windows phone. Jeśli odwołujesz rozszerzenie SDK w projekcie, wystarczy dodać testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. To, jak może mieć ten sam pakiet aplikacji dla każdej platformy.

 Umożliwia utworzenie tych językach C#, Visual Basic, C++ lub JavaScript [Universal Windows apps](https://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>sieć Web
 Program ASP.NET 5 jest ważna aktualizacja MVC, WebAPI i SignalR i uruchamiana na Windows, Mac i Linux.  Program ASP.NET 5 ma został zaprojektowany od podstaw zapewnienie, że stosu z odchudzona i konfigurowalna platformy .NET do tworzenia nowoczesnych aplikacji w chmurze. Narzędzi programu Visual Studio 2015 jest ściślej zintegrowane z popularnych narzędzi do programowania, takich jak rozwiązania Bower i Grunt. Aby rozpocząć pracę, zobacz wiele wpisów w blogu na [Blog narzędzi i programowania dla sieci Web NET](https://devblogs.microsoft.com/aspnet/).

### <a name="classic-desktop-and-windows-store"></a>Klasyczny pulpit a Windows Store
 Program Visual Studio 2015 w dalszym ciągu obsługuje klasyczny pulpit i rozwoju Windows Store. Miarę rozwoju Windows, programu Visual Studio ewoluuje wraz z jej.  W programie Visual Studio 2015 biblioteki i języków .NET, a także C++ dokonano znaczących postępu, które mają zastosowanie do wszystkich wersji systemu Windows.

#### <a name="the-net-framework"></a>.NET Framework
 Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] oferuje około 150 nowych interfejsów API i 50 zaktualizowane interfejsy API umożliwiające dalszych scenariuszach. Na przykład teraz wdrożyć więcej kolekcji <xref:System.Collections.Generic.IReadOnlyCollection%601> ułatwianie korzystania. Ponadto platform ASP.NET 5 i wspomniano wcześniej, oferuje zwarte platformy .NET do tworzenia nowoczesnych aplikacji w chmurze.

 Aplikacje Windows Store napisanych w języku C#, przeznaczonych dla platformy .NET Framework mogą korzystać z zalet platformy .NET Native, który kompiluje aplikacje do kodu natywnego, a nie IL, i [!INCLUDE[net_v46](./includes/net-v46-md.md)] dodaje również elementach RyuJIT, 64-bitowy kompilator just in Time (JIT).

 Nowe kompilatory C# i VB ("Roslyn") znacznie przyspieszyć czasy kompilacji i podaj kod kompleksowe interfejsy API do analizy. Program Visual Studio 2015 korzysta z zalet platformy Roslyn, aby zapewnić więcej operacji refaktoryzacji, zawierające wbudowaną zmiany nazwy, analizatory i szybkich poprawek.

 Języki C# i Visual Basic zawierają wiele ulepszeń smallish w języku podstawowym i obsługa środowiska IDE. Te ulepszenia wszystkich jest dodanie do wprowadzić środowiska jeszcze bardziej intuicyjnego, wygodne i wydajnego pisania kodu platformy .NET.

 Aby uzyskać więcej informacji, zobacz [What's New](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) i [bloga platformy .NET](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 Visual C++ zapewnia znaczne postępy w C ++ 11/14 języka zgodność, wsparcie dla programowania i platform urządzeń przenośnych, obsługę funkcji wznawialnych i await (obecnie planowane normalizacji w języku C ++ 17), poprawki ulepszenia i usterki w języku C Biblioteki środowiska uruchomieniowego (CRT) i C++ standardowej biblioteki (STL) implementacji resizeable okien dialogowych w MFC, nowe optymalizacje kompilatora, twórz lepiej wydajności, nowe funkcje diagnostyki i nowych narzędzi zwiększających produktywność w edytorze kodu.

 Aby uzyskać więcej informacji, zobacz [What's New for Visual C++](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) i [blogu Visual C++](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Pasek menu podglądu urządzeń
 W projektach platformy uniwersalnej Windows pasek menu urządzenia (wersja zapoznawcza) można zobaczyć, jak Twój interfejs użytkownika na podstawie XAML będą renderowane w różnych rozmiarów ekranu.

 ![Menu Podgląd urządzenia](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
 Od programu Visual Studio 2013 grafiki programu Visual Studio diagnostyki dodano wiele nowych funkcji, w tym analizy ramek, Windows Phone, pomocy technicznej, Edycja programu do cieniowania i Zastosuj i wiersza polecenia przechwytywania narzędzia. Dodano również obsługę debugowania aplikacji DirectX12. Aby uzyskać więcej informacji, zobacz [Visual Studio diagnostyki grafiki](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Łączenie się z usługami
 Program Visual Studio 2015 sprawia, że łatwiej niż kiedykolwiek do łączenie aplikacji z usług.  Nowy Kreator Dodaj podłączoną usługę skonfiguruje projekt, dodaje obsługę uwierzytelniania niezbędne i pobierze niezbędne pakiety NuGet umożliwiające szybkie i bezproblemowe rozpoczęcie kodowania dla usługi. Kreator Dodaj podłączoną usługę integruje się również za pomocą nowego Menedżera konta ułatwia pracę z wieloma kontami użytkowników i subskrypcji. W programie Visual Studio 2015 pomoc techniczna dla następujących usług znajduje się poza pole (przy założeniu, że masz konto):

1. Usług Azure Mobile Services

2. Azure Storage

3. Usługi Office 365 (wiadomości e-mail, kontakty, kalendarze, plików, użytkowników i grup)

4. Salesforce

   Nowe usługi, które zostaną dodane w sposób ciągły, a można wykryć te, klikając przycisk "Znajdź nowych usług link" w kreatorze.

   ![Okno dialogowe Dodawanie usług połączonych](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Interfejs użytkownika projektuje się
 Program Blend umożliwiający projektowanie interfejsów użytkownika XAML zostały znacznie rozszerzone. Program Blend został całkowicie przeprojektowany w celu zapewnienia bardziej intuicyjnego interfejsu użytkownika, bardziej zaawansowane funkcje edycji XAML, takich jak technologia IntelliSense i lepszą integrację z programem Visual Studio. Aby uzyskać więcej informacji, zobacz [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Obsługa debugowania dla wielu platform
 Za pomocą programu Visual Studio do tworzenia i debugowania natywnych aplikacji mobilnych przeznaczone dla systemów Windows, iOS i urządzenia z systemem Android. Użyj [Visual Studio Emulator for Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/), lub podłącz urządzenie i debugowania kodu bezpośrednio w programie Visual Studio.

- **JavaScript / Cordova**. Użyj [Visual Studio Tools for Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) do tworzenia aplikacji natywnych dla Windows, iOS i Android za pomocą języka JavaScript.

     [Debugowanie aplikacji](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) w bibliotece MSDN przedstawiono szczegółowe obsługę Cordova debugowania programu Visual Studio.

- **C# / Xamarin**. Użyj [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) do tworzenia aplikacji natywnych dla Windows, iOS i Android w programie Visual Studio w języku C#.

     [Debugowanie](/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) (iOS) i [debugowania na urządzeniu](/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) w [przewodników dla deweloperów platformy Xamarin](/xamarin/) opisano środowisko debugowania.

- **C++ / Android**. Użyj [Visual C++ for Cross-Platform Mobile Development](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) szablony wraz z narzędziami innych firm, takich jak [zestawu Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) może tworzyć aplikacje natywne dla Windows i Android.

## <a name="debugging-and-diagnostics"></a>Debugowanie i diagnostyka

Aby uzyskać informacje o nowościach w diagnostyce, zobacz [What's New in Profiling Tools](./profiling/what-s-new-in-profiling-tools.md).

Następujące elementy są nowe lub udoskonalone narzędzia, które wykonują różne rodzaje diagnostykę i analizę w kodzie:

### <a name="perftips"></a>Wskazówki dotyczące wydajności
 Perftip wyświetlić czas wykonywania metody podczas debugowania, dzięki któremu można szybko wykrywaj wąskie gardła, bez konieczności wywoływania profilera. Aby rozpocząć pracę, zobacz [Perftip: informacje dotyczące wydajności w skrócie podczas debugowania za pomocą programu Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Lista błędów
 Lista błędów obsługuje teraz filtrowanie według dowolnej kolumny. Pokazuje także widok na żywo, błędy, ostrzeżenia i analizy kodu dla całego rozwiązania języka C# lub Visual Basic podczas wpisywania, nawet jeśli zmiany w kodzie tworzy tysiące ostrzeżenia. Nowa lista błędów jest zgodny z powrotem z użyciem istniejących. Aby uzyskać więcej informacji, zobacz [okno listy błędów](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>Narzędzie użycie procesora GPU
 Narzędzie użycie procesora GPU ułatwia zbieranie oraz analizowanie danych użycia procesora GPU w aplikacjach DirectX i gry i rozwiązywanie problemów z pochodzące wąskich gardeł wydajności procesora CPU lub GPU. Aby rozpocząć pracę przy użyciu narzędzia, zobacz [wpis w blogu zespołu Visual C++](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/).

## <a name="live-code-analysis-light-bulbs"></a>Analizy kodu na żywo (żarówki)
 Nowy kompilator Roslyn w języku C# i Visual Basic nie tylko zapewnia krótszy czas kompilacji — umożliwia również całkowicie nowych scenariuszy, takich jak analizy kodu na żywo, które zapewniają bogate i możliwe do dostosowania opinii i sugestii bezpośrednio w edytorze kodu podczas wpisywania. W programie Visual Studio 2015 żarówki wyświetlane w lewy margines (w przypadku używania klawiatury) lub etykietki narzędzia (podczas przesuwania wskaźnika w obrębie błąd za pomocą myszy). Żarówki informuje w czasie rzeczywistym, że kompilator (prawdopodobnie przy użyciu niestandardowego zestawu reguł) wykrył problem w kodzie i ma również sugestię dotyczącą sposobu rozwiązania problemu. Gdy pojawi się żarówka, kliknij ją uzyskać sugestie informacje z możliwością działania.

 ![Żarówki w edytorze Visual Studio Code](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Ciesz się te dodatkowe ulepszenia środowiska IDE

### <a name="synchronized-settings-roaming-settings"></a>Zsynchronizowane ustawienia (ustawienia roamingu)
 Visual Studio 2013 wprowadzono zsynchronizowane ustawienia dla niektórych najczęściej skonfigurowanych ustawień, takich jak edytor tekstu, powiązania klawiszy, motyw & czcionki i kolory, uruchamiania i aliasy środowiska.  Program Visual Studio 2015 usprawnieniem to środowisko więcej ustawień synchronizacji i synchronizowanie ustawień między aplikacjami, takimi jak Professional, Enterprise, Express SKU i Blend rodziny Visual Studio. Po zalogowaniu do programu Visual Studio 2015 po raz pierwszy przy użyciu tego samego konta używane w programie Visual Studio 2013, zobaczysz zsynchronizowane ustawienia w programie Visual Studio 2013. Możesz uzyskać dostęp ustawienia, wpisując "sync" w **Szybkie uruchamianie**, lub przejdź do sekcji **Narzędzia > Opcje > środowisko > zsynchronizowane ustawienia**.

### <a name="automatic-extension-updates"></a>Aktualizacje automatyczne rozszerzenia
 Zainstalowane rozszerzenia programu Visual Studio będzie teraz automatycznie aktualizowane podczas galerii Visual Studio dostępna jest nowa wersja. Zobacz [Znajdowanie i przy użyciu rozszerzenia programu Visual Studio](./ide/finding-and-using-visual-studio-extensions.md) Aby uzyskać szczegółowe informacje, w jaki sposób dostosować aktualizacje automatyczne rozszerzenia.

### <a name="title-case-menus"></a>Tytuł przypadku menu
 Możesz szprychy, zwróciliśmy uwagę. Visual Studio menu są ponownie wielkimi literami domyślnie. Jednak jeśli występuje w całości wielkimi literami, np. Możesz skonfigurować go w menu start lub w **Narzędzia > Opcje > Ogólne** strona właściwości:

 ![Polecenia menu głównego przypadku tytułu programu Visual Studio 2015](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Obrazy o wysokiej rozdzielczości i obsługi wprowadzania dotykowego
 Środowiska IDE programu Visual Studio ma teraz wartość true, wysokiej rozdzielczości na zagęszczenie Wyświetla (w obszarach, takich jak menu, menu kontekstowe, pasków poleceń okna narzędzi i w niektórych projektów w Eksploratorze rozwiązań). A-ekranie dotykowym w oknie Edytor kodu programu Visual Studio, możesz teraz Użyj gestów takich jak Dotyk i przytrzymaj, ściśnięcie, naciśnij i tak dalej, aby Powiększenie, przewiń, zaznacz tekst i wywołać menu kontekstowe.

 ![Obsługa dotykowa w edytorze](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Układy niestandardowe
 Można utworzyć magazynu i są przekazywane niestandardowe układy okien. Na przykład można zdefiniować jeden układ preferowany do użytku na komputerze stacjonarnym, a inny układ do użycia na laptopie lub urządzenie na małym ekranie. Lub możesz jeden układ dla projektu interfejsu użytkownika i inny wpis dla projektu bazy danych. Powiązania klawiszy umożliwiają szybko przełączać się między układów. Tych układów są dostępne na dowolnego wystąpienia programu Visual Studio, gdy użytkownik jest zalogowany. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych układów okien](./misc/create-custom-window-layouts.md).

 ![Element menu układu niestandardowego programu Visual Studio](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Centrum powiadomień
 W interfejsie użytkownika dla Centrum powiadomień został ulepszony, aby ułatwić szybkie skanowanie. Dodano dodatkowych typów powiadomień, w tym problemów z wydajnością, problemy z renderowaniem i awarie i można teraz Przekaż programowi Visual Studio przestanie być wyświetlana powiadomienia. Aby uzyskać więcej informacji, zobacz [powiadomienia usługi Visual Studio](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Dowiedz się, co się stało z kodu (tylko wersje Enterprise i Professional)
 Skoncentrowanie się na pracy, podczas gdy można znaleźć informacje o swoim kodzie — bez opuszczania edytora. Możesz przejrzeć zmiany i innych elementów historii dla elementów roboczych, usterek, przeglądy kodu, i tak dalej dla kodu, który jest przechowywany w Visual Studio Team Services (VSTS) lub w Team Foundation Server (TFS).

 W programie Visual Studio Enterprise i Visual Studio Professional możesz teraz:

- Pobieranie historii dla całego pliku z kodem w edytorze programu Visual Studio.

   ![CodeLens: Pobierz szczegóły pliku kodu](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Zobacz wykres pokazujący osoby, która zmieniła swój kod. Może to pomóc Ci znaleźć wzorce w zmiany swojego zespołu i ocena ich skutków.

   ![CodeLens: Zobacz historię zmian kodu jako Graf](./ide/media/codelens.png "CodeLens")

- Łatwo zobaczyć, kiedy ostatniej zmiany kodu.

- Znajdź zmian w innych gałęzi, które wpływają na kodzie.

  Zobacz [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Projektowanie i modelowanie narzędzi (tylko wersja Enterprise)
 **Mapy kodu i wykresy zależności**

 W programie Visual Studio Enterprise Jeśli chcesz poznać konkretne zależności w kodzie, utwórz ich wizualizację przez utworzenie map kodów. Następnie można przejść te relacje za pomocą mapy wyświetlanej obok kodu. Mapy kodu może również ułatwić śledzenie bieżącego miejsca w kodzie podczas pracy nad nim lub debugowania, dzięki czemu przeczytasz mniej kodu podczas Dowiedz się więcej na temat projektu kodu.

 W tej wersji wprowadziliśmy menu skrótów dla elementów kodu i linki znacznie łatwiejsze do użycia przez zgrupowanie poleceń w sekcje dotyczące wybierania, edycji, Zarządzanie grupami i zmieniania układu zawartości grupy. Zwróć uwagę, że projekty testu są wyświetlane przy użyciu innego stylu z innych projektów i zaktualizowane bardziej odpowiednie ikony elementów w mapie.

 ![Pokaż zaznaczone elementy na nowej mapie kodu](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Inne ulepszenia obejmują:

- **Ulepszone diagramy widoku z góry na dół**. Dla średnich lub dużych rozwiązań programu Visual Studio można teraz używać uproszczonego menu architektura, można uzyskać kod bardziej przydatne mapy rozwiązania. Zestawy rozwiązania są grupowane według folderów rozwiązania, dzięki czemu można zobaczyć je w kontekście i wykorzystać nakład pracy, umieszczoną w tworzenie struktury rozwiązania. Natychmiast zauważysz projektu i odwołania do zestawu, a następnie zostaną wyświetlone typy linków. Dodatkowo zestawy zewnętrzne w stosunku do rozwiązania są pogrupowane w bardziej zwarty sposób.

- **Projekty testowe mają różne style i można je filtrować**. Teraz możesz łatwiej i szybciej zidentyfikować projekty testowe na mapie, ponieważ mają odrębny styl. One może je także odfiltrować, dzięki czemu możesz skupić się na działającym kodzie aplikacji.

- **Uproszczone linki zależności zewnętrznych**. Linki zależności nie przedstawiają już dziedziczenia z System.Object, System.ValueType, System.Enum i System.Delegate, co ułatwia dostrzeżenie zewnętrznych zależności na mapie kodu.

- **"Testowania odzyskiwania po awarii w linków zależności" uwzględnia filtry**. Otrzymujesz przydatny, przejrzysty diagram, który umożliwia poznanie elementów składowych linku zależności. Diagram jest mniej "zatłoczony" i uwzględnia zostało wybrane opcje filtrowania linków.

- **Elementy kodu są umieszczone na mapie razem z ich kontekstami**. Ponieważ teraz diagramy są wyświetlane razem ze swoimi kontekstami (aż do poziomu zestawu i folderu rozwiązania, które można odfiltrować w razie potrzeby), uzyskujesz bardziej użyteczne diagramy podczas przeciągania i upuszczania elementów kodu z Eksploratora rozwiązań, widoku klas i przeglądarki obiektów; lub podczas zaznaczania elementów w Eksploratorze rozwiązań i wybierając polecenie Pokaż na mapie kodu.

- **Uzyskaj szybciej aktywne mapy kodu szybciej**. Operacja przeciągnięcia i upuszczenia daje natychmiastowy efekt, a linki między węzłami są tworzone dużo szybciej i bez wpływania na kolejne operacje użytkownika, takie jak rozwinięcie węzła lub zażądanie kolejnych węzłów. Po utworzeniu map kodu bez kompilowania rozwiązania, wszystkie przypadki brzegowe — takie jak brak skompilowanych zestawów — są obecnie przetwarzane.

- **Pomiń ponowną kompilację rozwiązania.** Zapewnia lepszą wydajność, podczas tworzenia i edytowania diagramów.

- **Filtrowanie węzłów elementów kodu i grupy**. Możesz szybko zwiększyć przejrzystość map, pokazując lub ukrywając elementy kodu według ich kategorii, a także grupować elementy kodu według folderów rozwiązania, zestawów, przestrzeni nazw, folderów projektu i typów.

- **Filtruj relacje, aby ułatwić interpretowanie diagramów**. Filtrowanie linku dotyczy teraz także linków między grupami, co sprawia, że praca z oknem filtru jest płynniejsza niż w poprzednich wersjach.

- **Tworzenie diagramów z widoku klas i przeglądarki obiektów**. Przeciągnij i upuść pliki oraz zestawy na nową lub istniejącą mapę w oknach widoku klas i przeglądarki obiektów.

  Zobacz [mapowanie zależności w ramach rozwiązań](./modeling/map-dependencies-across-your-solutions.md).

  **Inne zmiany projektu i modelowania w tej wersji:**

- **Diagramy warstw**. Aktualizuj te diagramy za pomocą widoku klas i przeglądarki obiektów. Aby spełnić wymagania dotyczące projektowania oprogramowania, należy użyć diagramów warstw do opisania oczekiwanych zależności oprogramowania. Utrzymuj spójność kodu z tego projektu możliwości znalezienia kodu niespełniającego tych ograniczeń i weryfikowaniu przyszłego kodu względem tej linii bazowej.

- **Diagramy UML**. Użytkownik nie można już tworzyć diagramów klas UML i diagramy sekwencji z kodu. Ale wciąż można jednak tworzyć te diagramy z użyciem nowych elementów UML.

- **Eksplorator architektury**. Do tworzenia diagramów nie jest już służy Eksploratora architektury. Ale nadal można korzystać z Eksploratora rozwiązań.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio Extensibility Tools
 Nigdy nie było łatwiejsze do zainstalowania programu Visual Studio Extensibility Tools (zestaw SDK programu VS i szablonów), ponieważ są one teraz dołączone jako składnik opcjonalny podczas instalacji.  Narzędzia rozszerzalności umożliwić programistom pisanie rozszerzeń w celu dostosowania i Dodaj funkcje do programu Visual Studio. Aby uzyskać więcej informacji o możliwościach rozszerzania programu Visual Studio, zobacz [programu Visual Studio SDK](./extensibility/visual-studio-sdk.md)

 Jeśli chcesz dołączyć narzędzia rozszerzalności przy użyciu instalacji niestandardowej, możesz znaleźć je w obszarze **funkcji / popularnych narzędzi / Visual Studio Extensibility Tools**.  Można także zainstalować narzędzia rozszerzalności w późniejszym czasie, otwierając **nowy projekt** okna dialogowego i wybierając polecenie **zainstalować program Visual Studio Extensibility Tools** w obszarze **Visual C# / Rozszerzalność**.

## <a name="please-give-feedback"></a>Przekaż swoją opinię
 Dlaczego warto wysłać opinię do zespołu usługi Visual Studio? Ponieważ traktujemy opinie naszych użytkowników bardzo poważnie. W rzeczywistości omówimy każdego z nich opinie, które wchodzi w naszym systemie opinii. Twoja opinia dysków mnóstwo co możemy zrobić.

### <a name="send-a-smile"></a>Wyślij uśmiech
 Informuje NAS, co można, jak pomaga nam zrozumieć, kiedy możemy spełnia lub przekracza oczekiwania. Gdy firma Microsoft projektowania i implementowania nowych funkcji, używamy danych dotyczących funkcji, z których chcesz pomóc naszym decyzji projektowych. Tak Jeśli chcesz, aby funkcja w programie Visual Studio, Opowiedz nam o nim. To proste i możesz to zrobić bezpośrednio z poziomu środowiska IDE.

 Po prostu kliknij żółtą ikonę uśmiechniętej buźki na pasku tytułu, powiedz nam, co Ci się podoba kliknięcie **Wyślij uśmiech** przycisku.

 To wszystko! Firma Microsoft będzie kierować swoją opinię do właściwego zespołu, w którym będzie osobisty token dostępu się na tylnej następnie szybko zacząć myśleć sposobów, aby zapewnić obsługę można jeszcze bardziej.

### <a name="send-a-frown"></a>Wyślij grymas niezadowolenia
 Przerwy, w którym należy wprowadzić ulepszenia w produkcie pomaga nam zarządzać naszej liście prac w pierwszej kolejności koncentrować się na rzeczy, które są najważniejsze dla naszych klientów. Jeśli jest coś, co jest bugging możesz, Opowiedz nam o nim za pomocą **Wyślij grymas niezadowolenia** funkcji z bezpośrednio z poziomu środowiska IDE. Wprowadziliśmy to bardzo prosty proces za:

 Kliknij żółtą ikonę uśmiechniętej buźki na pasku tytułu, a następnie kliknij przycisk **Wyślij grymas niezadowolenia**. Daj nam znać, co użytkownik nie podoba następnie kliknij przycisk Wyślij niezadowolenie przycisku. Aby uzyskać więcej informacji, zobacz [Porozmawiaj z nami](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Raport ulegnie awarii, zawieszenia i problemów z wydajnością
 Czasami szybką notatkę w niezadowolenie po prostu nie jest wystarczająca do przekazania pełnego wpływu coś, co nie chcesz. Do sytuacji, w przypadku zawieszenia, awarii lub problemie z wydajnością mogą łatwo udostępniać za pomocą okna dialogowego wyświetlanego po Wyślij grymas niezadowolenia Odtwórz kroki i zrzuty awaryjne plików śledzenia.

 Po pierwsze Wyślij niezadowolenie, zgodnie z powyższym opisem. W oknie dialogowym, które się pojawi można oznaczyć swoją opinię za pomocą jednego ze znaczników domyślnych lub utworzyć własnego tagu. Tagi pomagają nam kierować swoją opinię do zespołu odpowiednich funkcji. W **wybrać kategorię** listę rozwijaną, wybierz opcję, która reprezentuje problem w przypadku raportowania, należy wykonać kroki prowadzące do odtworzenia problemu. Dostępne są także uzyskać szczegółowe instrukcje dotyczące sposobu używania programu Visual Studio na opinie raportu. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Wyślij uśmiech instrukcje](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Zobacz też

* [Twórz aplikacje dla wielu platform przy użyciu Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Tworzenie aplikacji mobilnych dla wielu platform w języku Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Praca z wieloma kontami użytkowników](./ide/work-with-multiple-user-accounts.md)
* [Tworzenie niestandardowych układów okien](./misc/create-custom-window-layouts.md)
* [Szybkie wykonywanie akcji dzięki żarówkom](./ide/perform-quick-actions-with-light-bulbs.md)
* [Co nowego w programie Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
