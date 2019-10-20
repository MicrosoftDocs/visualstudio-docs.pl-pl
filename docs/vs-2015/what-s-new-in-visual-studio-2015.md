---
title: Co nowego w programie Visual Studio 2015 | Microsoft Docs
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
ms.openlocfilehash: 469405515b7cc0ebe615dc821ebfa5ddb7258468
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672084"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Co&#39;nowego w programie Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Witamy w programie Visual Studio 2015, zintegrowany pakiet narzędzi do tworzenia produktywności dla deweloperów, usług w chmurze i rozszerzenia, które pozwalają Ci i Twojemu zespołowi tworzyć wspaniałe aplikacje i gry dla sieci Web, dla Sklepu Windows, dla systemów Android i iOS.

Ta strona zawiera najważniejsze funkcje, które są nowe od wersji Visual Studio 2013 RTM, w tym funkcje, które zostały po raz pierwszy wprowadzone w jednej z aktualizacji Visual Studio 2013. Aby zapoznać się z pełną listą nowości w programie Visual Studio 2015, zobacz [Informacje o wersji](https://www.visualstudio.com/news/vs2015-vs).

Aby dowiedzieć się więcej na temat wielu ulepszeń i nowych funkcji w programie Visual Studio ALM, zobacz [co nowego w programie TFS 2015](/tfs/server/whats-new?view=vsts#tfs-2015-rtm).

## <a name="a-new-setup-experience"></a>Nowe środowisko instalacji
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Środowisko instalacyjne programu Visual Studio 2015 zostało zgłoszone w celu zainstalowania tylko potrzebnych części. Dzięki temu instalacja jest szybsza dla wielu typowych scenariuszy obejmujących platformę .NET lub programowanie w sieci Web. W przypadku innych typów programowania, takich jak programowanie aplikacji mobilnych na wiele platform lub w programie C++ F#, wybierz opcję Instalacja **niestandardowa** , a następnie wybierz składniki i opcjonalne wymagane zestawy SDK innych firm. Możesz również zainstalować dowolny składnik niestandardowy później. Jeśli na przykład zostanie wybrana opcja instalacja podstawowa, a następnie zostanie podjęta próba utworzenia C++ nowego projektu, zostanie wyświetlony monit o pobranie narzędzi C++ programistycznych.

 ![Okno dialogowe Instalatora programu Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Logowanie się na wielu kontach
 Dzięki programowi Visual Studio 2015 nowe usprawnione środowisko logowania ma znacznie uprościć dostęp do zasobów online nawet wtedy, gdy masz wiele kont programu Visual Studio. Po zalogowaniu się do programu Visual Studio użytkownik jest automatycznie zalogowany do wszystkich wystąpień programu Visual Studio 2015 i Blend na komputerze. Logowanie jest automatycznie uruchamiane w roamingu ustawień. W programie Visual Studio 2015 Twoje konto jest udostępniane w różnych funkcjach, tak długo, jak masz dobry token, możesz uzyskać dostęp do kont Visual Studio Team Services z **Team Explorer**, a także zasobów i witryn sieci Web z subskrypcji Microsoft Azure na serwerze Programie. Zobaczysz również zasoby platformy Azure w oknie dialogowym Nowy projekt dla Application Insights projektów, a zobaczysz konta [deweloperów](https://developer.salesforce.com/) Azure Mobile, Azure Storage, [Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) i Saleforce.com w nowym obszarze **Dodaj podłączoną usługę** okno dialogowe.

 Możesz współpracować z wieloma kontami użytkowników w programie Visual Studio, dodając je w taki sam sposób lub za pomocą nowego menedżera kont. Następnie można przełączać się między tymi kontami na bieżąco podczas nawiązywania połączenia z usługami lub uzyskiwania dostępu do zasobów online. Program Visual Studio zapamiętuje dodane konta, aby można było używać ich z dowolnego wystąpienia programu Visual Studio lub Blend. Program Visual Studio przeprowadzi również przechodzenie do listy kont (chociaż nie będziemy mieć swoich cennych poświadczeń) przy użyciu konta personalizacji, dzięki czemu możesz szybko rozpocząć pracę z jednym z tych kont na innym urządzeniu. Oczywiście można w dowolnym momencie usunąć konta z okna dialogowego Ustawienia konta. Aby rozpocząć, zobacz [pracę z wieloma kontami użytkowników](./ide/work-with-multiple-user-accounts.md).

 ![Menedżer kont](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Wybierz Platformy docelowe
 Program Visual Studio 2015 obsługuje Międzyplatformowe programowanie urządzeń przenośnych. Możesz pisać aplikacje i gry przeznaczone dla systemów iOS, Android i Windows oraz współużytkować wspólną bazę kodu z poziomu środowiska IDE programu Visual Studio. Wszystkie te nowe typy projektów zostaną wyświetlone w oknie dialogowym plik, nowy projekt.

 I — oczywiście — Obsługa klasycznych aplikacji komputerowych jest lepsza niż kiedykolwiek, z wieloma ulepszeniami dotyczącymi języków, bibliotek i narzędzi.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Aplikacje mobilne dla wielu platform w C# programie Xamarin dla programu Visual Studio
 Xamarin to platforma przenośna, która umożliwia pisanie kodu w programie C# , który jest powiązany natywnie z interfejsami API systemów iOS i Android. Firma Microsoft ściśle współpracuje z platformą Xamarin w wersji platformy Xamarin dla programu Visual Studio, która umożliwia tworzenie aplikacji dla systemów Android, iOS i Windows Phone w jednym rozwiązaniu z kodem współdzielonym. Za pomocą platformy Xamarin będziesz używać jednego języka i jednej bazy kodu z minimalnymi różnicami między platformami.  Program Xamarin for Visual Studio jest obsługiwany w programie Visual Studio 2010 i nowszych. Wersja Starter programu Xamarin jest dołączona do programu Visual Studio 2015. Aby rozpocząć, zobacz [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Aplikacje mobilne dla wielu platform w języku HTML/JavaScript z Apache Cordova
 Visual Studio Tools dla Apache Cordova jest wynikiem ścisłej współpracy między firmą Microsoft a społecznością typu open source Apache Cordova. Narzędzia umożliwiają Programowanie aplikacji mobilnych na wiele platform przy użyciu języków HTML, CSS i JavaScript (lub TypeScript). Dla systemów Android, iOS i Windows można dowolnie korzystać z jednej bazy kodu i uzyskać bogate możliwości środowiska IDE programu Visual Studio, w tym JavaScript IntelliSense, DOM Explorer, konsolę JavaScript, punkty przerwania, zegarki, lokalne, Tylko mój kod itd.  Dzięki Visual Studio Tools dla Apache Cordova aplikacje mają dostęp do natywnych możliwości urządzenia na wszystkich platformach za pomocą wtyczek, które udostępniają wspólny interfejs API języka JavaScript. Aby rozpocząć, zobacz Wprowadzenie do [Visual Studio Tools dla Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Gry mobilne dla wielu platform w C# systemie Unity
 Unity to szeroko wykorzystywana platforma do tworzenia gier wieloplatformowych 2D i 3W. Możesz napisać grę C# i uruchamiać ją natywnie w systemach Android, iOS, Windows Phone i wielu innych platformach. Visual Studio Tools for Unity to rozszerzenie, które integruje środowisko Unity z programem Visual Studio IDE. Dzięki temu rozszerzeniu można uzyskać wszystkie funkcje środowiska IDE i debugera programu Visual Studio, a także funkcje produktywności, które są przeznaczone dla deweloperów aparatu Unity. Visual Studio Tools for Unity 2,0 wersja zapoznawcza 2 dodaje obsługę programu Visual Studio 2015, a także szereg nowych funkcji, takich jak lepsza Wizualizacja obiektów w lokalnych i Zegarkowych oknach. Firma Microsoft niedawno uzyskała element SyntaxTree, twórców Visual Studio Tools for Unity. Aby pobrać Visual Studio Tools for Unity 2,0 w wersji zapoznawczej 2 i uzyskać więcej informacji na temat Visual Studio Tools for Unity, zobacz [Visual Studio Tools for Unity 2,0](https://aka.ms/vstu).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Aplikacje i biblioteki dla wielu platform dla natywnychC++
 C++to język dostępny natywnie na większości urządzeń przenośnych. Za jego pomocą można napisać udostępnione biblioteki kodu dla wielu platform, które mogą być skompilowane dla kilku celów platformy mobilnej. Możesz nawet utworzyć w programie C++wszystkie aplikacje mobilne. Wizualizacja C++ udostępnia narzędzia do edytowania, kompilowania, wdrażania i debugowania kodu międzyplatformowego. Oprócz szablonów aplikacji systemu Windows, można tworzyć projekty z szablonów dla natywnych aplikacji dla systemu Android, aplikacji systemu iOS lub udostępnionych projektów bibliotek kodu dla wielu platform, które zawierają aplikacje hybrydowe platformy Xamarin. Technologia IntelliSense specyficzna dla platformy umożliwia Eksplorowanie interfejsów API i generowanie poprawnego kodu dla obiektów docelowych systemu Android, iOS lub Windows. Możesz skonfigurować kompilację dla platform macierzystych x86 lub ARM i wdrożyć kod w symulatorze systemu iOS lub na urządzeniach z systemem iOS na komputerze Mac podłączonym do sieci, bezpośrednio podłączonym urządzeniom z systemem Android lub użyć Microsoft Visual Studio Emulator for Android wykonujących testy. Możesz ustawiać punkty przerwania, oglądać zmienne, wyświetlać stos i przechodzić przez C++ kod w debugerze programu Visual Studio. Wszystkie z wyjątkiem kodu specyficznego dla platformy można udostępniać na wielu platformach aplikacji i kompilować dla nich wszystkie przy użyciu jednego rozwiązania w programie Visual Studio.

 Aby rozpocząć pracę na wielu platformach C++, zobacz [Tworzenie aplikacji mobilnych dla wielu platform za pomocą wizualizacji C++ ](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Aplikacje uniwersalne systemu Windows dla dowolnego urządzenia z systemem Windows 10
 Dzięki platforma uniwersalna systemu Windows i naszym jednemu rdzeńowi systemu Windows można uruchomić tę samą aplikację na dowolnym urządzeniu z systemem Windows 10 z telefonów na komputerach stacjonarnych. Twórz te aplikacje uniwersalne systemu Windows za pomocą programu Visual Studio 2015 i narzędzi do tworzenia aplikacji uniwersalnych systemu Windows.

 ![platforma uniwersalna systemu Windows](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uruchom aplikację na telefonie z systemem Windows 10, Windows 10 Desktop lub Xbox. Jest to ten sam pakiet aplikacji. Wraz z wprowadzeniem pojedynczego, ujednoliconego rdzeń systemu Windows 10 jeden pakiet aplikacji może być uruchamiany na wszystkich platformach. Kilka platform zawiera zestawy SDK rozszerzeń, które można dodać do aplikacji, aby korzystać z zachowań specyficznych dla platformy. Na przykład zestaw SDK rozszerzenia dla urządzeń przenośnych obsługuje naciśnięcie przycisku Wstecz w systemie Windows Phone. Jeśli odwołujesz się do zestawu SDK rozszerzenia w projekcie, po prostu Dodaj testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. Oznacza to, że możesz mieć ten sam pakiet aplikacji dla każdej platformy.

 Użyj C#, Visual Basic lub C++ JavaScript, aby utworzyć te [aplikacje uniwersalne systemu Windows](https://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>sieć Web
 ASP.NET 5 to ważna aktualizacja do MVC, WebAPI i sygnalizująca, która działa w systemach Windows, Mac i Linux.  Program ASP.NET 5 został zaprojektowany od podstaw w celu zapewnienia do tworzenia nowoczesnych aplikacji opartych na chmurze, które tworzą stosy architektury .NET. Narzędzia programu Visual Studio 2015 są ściśle zintegrowane z popularnymi narzędziami deweloperskimi dla sieci Web, takimi jak Bower i grunt. Aby rozpocząć, zapoznaj się z artykułem dotyczącym wielu wpisów w blogu w [blogu programowanie i projektowanie w sieci Web](http://blogs.msdn.com/b/webdev/).

### <a name="classic-desktop-and-windows-store"></a>Klasyczny pulpit i Sklep Windows
 Program Visual Studio 2015 nadal obsługuje klasyczny pulpit i programowanie dla Sklepu Windows. Wraz z rozwojem systemu Windows program Visual Studio rozwiąże się z nim.  W programie Visual Studio 2015 biblioteki i języki dla programu .NET, a także C++ wprowadzono znaczące postępy, które mają zastosowanie do wszystkich wersji systemu Windows.

#### <a name="the-net-framework"></a>.NET Framework
 @No__t_0 firmy Microsoft oferuje informacje o 150 nowych interfejsów API i zaktualizowanych interfejsach API 50, aby umożliwić obsługę większej liczby scenariuszy. Na przykład więcej kolekcji implementuje teraz <xref:System.Collections.Generic.IReadOnlyCollection%601> ułatwiające korzystanie z nich. Ponadto program ASP.NET 5, wymieniony wcześniej, oferuje platformę .NET Leaning do tworzenia nowoczesnych aplikacji opartych na chmurze.

 Aplikacje ze sklepu Windows utworzone C# w tym miejscu docelowym .NET Framework mogą teraz korzystać z .NET Native, która kompiluje aplikacje do kodu natywnego, a nie IL, a [!INCLUDE[net_v46](./includes/net-v46-md.md)] dodaje również RyuJIT, 64-bitowy kompilator just-in-Time (JIT).

 Nowe C# i kompilatory vb ("Roslyn") znacząco przyspieszają czas kompilowania i zapewniają kompleksowe interfejsy API analizy kodu. Program Visual Studio 2015 wykorzystuje Roslyn, aby zapewnić więcej refaktoryzacji, takich jak wbudowane nazwy, analizatory i szybkie poprawki.

 Języki C# i Visual Basic zawierają wiele ulepszeń smallish w języku podstawowym i w obsłudze środowiska IDE. Wszystkie te ulepszenia są dodawane, aby środowisko kodowania .NET było bardziej intuicyjne, wygodne i wydajne.

 Aby uzyskać więcej informacji, zobacz [co nowego](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) i [blog platformy .NET](http://blogs.msdn.com/b/dotnet/).

#### <a name="c"></a>C++
 Wizualizacja C++ zawiera znaczne postępy w zakresie zgodności z językiem c++ 11/14, obsługa tworzenia międzyplatformowych urządzeń przenośnych, obsługa funkcji możliwością wznowienia i oczekiwanych (obecnie zaplanowanych do normalizacji w języku c++ 17), ulepszeń i poprawek błędów w programie implementacje biblioteki środowiska uruchomieniowego języka C C++ (CRT) i biblioteki standardowej (STL), okna dialogowe z możliwością zmiany rozmiaru w MFC, nowe optymalizacje kompilatora, lepsza wydajność kompilacji, nowe możliwości diagnostyki oraz nowe narzędzia produktywności w edytorze kodu.

 Aby uzyskać więcej informacji, zobacz [co nowego w C++ wizualizacji](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) i [ C++ blogu](http://blogs.msdn.com/b/vcblog/)dla wizualizacji.

## <a name="device-preview-menu-bar"></a>Pasek menu podglądu urządzenia
 W projektach platforma uniwersalna systemu Windows pasek menu podglądu urządzenia pozwala zobaczyć, jak interfejs użytkownika oparty na języku XAML będzie renderowany na różnych rozmiarach ekranu.

 ![Menu Podgląd urządzenia](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki w programie Visual Studio
 Ze względu na to, Visual Studio 2013 że program Visual Studio Diagnostyka grafiki dodał wiele nowych funkcji, takich jak analiza ramek, obsługa Windows Phone, & cieniowania i narzędzia do przechwytywania wiersza polecenia. Dodano również obsługę debugowania aplikacji DirectX12. Aby uzyskać więcej informacji, zobacz [Visual Studio Diagnostyka grafiki](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Łączenie z usługami
 Program Visual Studio 2015 ułatwia łączenie aplikacji z usługami.  Nowy Kreator dodawania połączonej usługi konfiguruje projekt, dodaje wymaganą obsługę uwierzytelniania i pobiera niezbędne pakiety NuGet, aby szybko i bezproblemowe rozpoczęcie rozpocząć kodowanie usługi. Kreator dodawania połączonej usługi integruje się również z nowym menedżerem kont w celu ułatwienia pracy z wieloma kontami użytkowników i subskrypcjami. W programie Visual Studio 2015 Pomoc techniczna dla następujących usług jest świadczona z pola (przy założeniu, że masz konto):

1. Mobile Services platformy Azure

2. Azure Storage

3. Office 365 (poczta, kontakty, kalendarze, pliki, użytkownicy & grupy)

4. Usługi

   Nowe usługi będą stale dodawane i można je wykryć, klikając link "Znajdź nowe usługi" w kreatorze.

   ![Okno dialogowe Dodawanie usług połączonych](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Projektowanie interfejsu użytkownika
 Środowisko mieszania do projektowania interfejsów użytkownika XAML zostało znacznie rozszerzone. Program Blend został całkowicie przeprojektowany w celu zapewnienia bardziej intuicyjnego interfejsu użytkownika, bardziej zaawansowanych możliwości edytowania kodu XAML, w tym technologii IntelliSense i lepszego integracji z programem Visual Studio. Aby uzyskać więcej informacji, zobacz [Designing XAML in Visual Studio i Blend for Visual Studio](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Obsługa debugowania dla wielu platform
 Możesz użyć programu Visual Studio do tworzenia i debugowania natywnych aplikacji mobilnych, które działają na urządzeniach z systemami Windows, iOS i Android. Używaj [emulatora programu Visual Studio dla systemu Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx)lub podłącz urządzenie i Debuguj kod bezpośrednio w programie Visual Studio.

- **JavaScript/Cordova**. Użyj Visual Studio Tools, aby [Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) do kompilowania natywnych aplikacji dla systemów Windows, iOS i Android przy użyciu języka JavaScript.

     [Debugowanie aplikacji](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) w bibliotece MSDN jest szczegółowym opisem obsługi debugowania programu Visual Studio dla oprogramowania Cordova.

- **C# /Xamarin**. Za pomocą platformy [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) Twórz natywne aplikacje dla systemów Windows, iOS i Android w programie C#Visual Studio za pomocą programu.

     [Debugowanie](http://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/) (iOS) i [debugowanie na urządzeniu](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debugging_with_xamarin_android/) w [przewodniku dewelopera platformy Xamarin](http://developer.xamarin.com/guides) opisuje środowisko debugowania.

- **C++ /Android**. Użyj [wizualizacji C++ dla międzyplatformowych szablonów programistycznych dla deweloperów](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) oraz narzędzi innych firm, takich jak zestaw [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) , aby tworzyć natywne aplikacje dla systemów Windows i Android.

## <a name="debugging-and-diagnostics"></a>Debugowanie i diagnostyka

Aby uzyskać informacje na temat Nowości w diagnostyce, zobacz [co nowego w programie narzędzia profilowania](./profiling/what-s-new-in-profiling-tools.md).

Poniżej przedstawiono nowe lub udoskonalone narzędzia, które wykonują różne typy diagnostyki i analizy kodu:

### <a name="perftips"></a>Wskazówki dotyczące wydajności
 Funkcja PerfTip Wyświetlaj czas wykonywania metod podczas debugowania, co pozwala na szybkie wykrywanie wąskich gardeł bez konieczności wywoływania profilera. Aby rozpocząć, zobacz [Funkcja PerfTip: informacje o wydajności w skrócie, podczas debugowania w programie Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)

### <a name="error-list"></a>Lista błędów
 Lista błędów obsługuje teraz filtrowanie dla dowolnej kolumny. Przedstawia on również dynamiczny widok błędów, ostrzeżeń i analizy kodu w całym C# rozwiązaniu lub Visual Basic podczas pisania, nawet jeśli zmiana kodu powoduje tysiące ostrzeżeń. Nowy Lista błędów jest ponownie zgodny z istniejącym użyciem. Aby uzyskać więcej informacji, zobacz [okno Lista błędów](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>Narzędzie użycie procesora GPU
 Narzędzie użycie procesora GPU ułatwia zbieranie i analizowanie danych użycia procesora GPU w aplikacjach i grach DirectX oraz Rozwiązywanie problemów związanych z wąskimi gardłami wydajności w PROCESORAch lub procesorach GPU. Aby rozpocząć pracę z narzędziem, zobacz wpis w [blogu C++ zespołu wizualnego](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx).

## <a name="live-code-analysis-light-bulbs"></a>Analiza kodu na żywo (żarówki)
 Nowy kompilator Roslyn dla C# i Visual Basic nie tylko zapewnia szybszy czas kompilowania — umożliwia również korzystanie z całkowicie nowych scenariuszy, takich jak analiza kodu na żywo, które umożliwiają rozbudowane i dostosowywalne opinie oraz sugestie bezpośrednio w edytorze kodu. Wprowadź. W programie Visual Studio 2015 żarówki są wyświetlane na lewym marginesie (w przypadku korzystania z klawiatury) lub etykietki narzędzia (gdy wskaźnik myszy znajduje się nad błędem z myszą). Żarówka informuje w czasie rzeczywistym, że kompilator (prawdopodobnie korzystający z niestandardowego zestawu reguł) wykrył problem w kodzie i ma także sugestię dotyczącą sposobu rozwiązania problemu. Gdy zobaczysz żarówkę, kliknij ją w celu uzyskania sugestii do wykonania.

 ![Żarówki w edytorze Visual Studio Code](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Korzystaj z tych dodatkowych ulepszeń środowiska IDE

### <a name="synchronized-settings-roaming-settings"></a>Ustawienia zsynchronizowane (ustawienia roamingu)
 W Visual Studio 2013 wprowadzono zsynchronizowane ustawienia dla niektórych najczęściej skonfigurowanych ustawień, takich jak edytor tekstu, powiązania klawiszy, kompozycje & czcionki & kolorów, uruchamiania i aliasów środowiskowych.  Program Visual Studio 2015 usprawnia korzystanie z tego środowiska przez zsynchronizowanie większej liczby ustawień i synchronizowanie ustawień w ramach aplikacji rodziny Visual Studio, takich jak Professional, Enterprise, Express SKU i Blend. Po pierwszym zalogowaniu się do programu Visual Studio 2015 przy użyciu tego samego konta, które zostało użyte w Visual Studio 2013, zostaną wyświetlone zsynchronizowane ustawienia zastosowane z Visual Studio 2013. Możesz uzyskać dostęp do ustawień, wpisując "Synchronize" w **szybkim uruchomieniu**lub przechodząc do **narzędzi > opcje > środowisku > Ustawienia zsynchronizowane**.

### <a name="automatic-extension-updates"></a>Automatyczne aktualizacje rozszerzeń
 Zainstalowane rozszerzenia programu Visual Studio będą teraz automatycznie aktualizowane, gdy nowa wersja będzie dostępna w galerii programu Visual Studio. Zobacz [Znajdowanie i używanie rozszerzeń programu Visual Studio,](./ide/finding-and-using-visual-studio-extensions.md) Aby uzyskać szczegółowe informacje na temat sposobu dostosowywania automatycznych aktualizacji rozszerzeń.

### <a name="title-case-menus"></a>Menu wielkości liter tytułu
 Ty nasłuchuje. Menu programu Visual Studio domyślnie ponownie rozróżniają wielkość liter. Jeśli jednak tak samo, jak styl WERSALIKi, można ustawić go przy uruchamianiu lub na stronie **narzędzia > opcje > Właściwości ogólne** :

 ![Polecenia menu głównego przypadku tytułu programu Visual Studio 2015](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Obrazy o wysokiej rozdzielczości i obsługa dotyku
 Środowisko IDE programu Visual Studio ma teraz rzeczywiste obrazy o wysokiej rozdzielczości na ponad gęstym wyświetlaczu (w takich obszarach jak menu, menu kontekstowe, paski poleceń okna narzędzi i w niektórych projektach w Eksplorator rozwiązań). Na ekranie dotykowym w oknie Edytor kodu programu Visual Studio można teraz używać gestów, takich jak Touch i HOLD, szczypania, naciśnij i tak dalej, aby powiększać, przewijać, wybierać tekst i wywoływać menu kontekstowe.

 ![Obsługa dotykowa w edytorze](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Układy niestandardowe
 Możesz tworzyć i przechować niestandardowe układy okien. Na przykład można zdefiniować jeden preferowany układ do użycia na komputerze stacjonarnym i inny układ do użycia na laptopie lub małym ekranie. Lub można preferować jeden układ dla projektu interfejsu użytkownika i drugi dla projektu bazy danych. Kluczowe powiązania pozwalają szybko przełączać się między układami. Te układy są dostępne w dowolnym wystąpieniu programu Visual Studio, gdy użytkownik jest zalogowany. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych układów okien](./misc/create-custom-window-layouts.md).

 ![Element menu układu niestandardowego programu Visual Studio](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Centrum powiadomień
 Interfejs użytkownika centrum powiadomień został ulepszony, aby ułatwić szybkie skanowanie. Dodano dodatkowe rodzaje powiadomień, w tym problemy z wydajnością, problemy z renderowaniem i awarie, a teraz możesz powiedzieć, że program Visual Studio ma przestać wyświetlać powiadomienie. Aby uzyskać więcej informacji, zobacz [powiadomienia programu Visual Studio](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Znajdź, co się stało z kodem (tylko wersja Enterprise i Professional)
 Możesz skupić się na pracy, gdy znajdziesz informacje o kodzie — bez opuszczania edytora. Możesz przejrzeć zmiany i inne historia elementów roboczych, usterek, przeglądów kodu i tak dalej dla kodu, który jest przechowywany w Visual Studio Team Services (VSTS) lub w Team Foundation Server (TFS).

 W Visual Studio Enterprise i Visual Studio Professional możesz teraz:

- Pobierz historię całego pliku kodu w edytorze programu Visual Studio.

   ![CodeLens: Pobierz szczegóły pliku kodu](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Zobacz wykres, który pokazuje osoby, które zmieniły swój kod. Może to pomóc znaleźć wzorce w zmianach zespołu i ocenić ich wpływ.

   ![CodeLens: Zobacz historię zmian kodu jako Graf](./ide/media/codelens.png "CodeLens")

- Łatwo Sprawdź, kiedy kod został ostatnio zmieniony.

- Znajdź zmiany w innych gałęziach, które mają wpływ na Twój kod.

  Zobacz [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Narzędzia projektowania i modelowania (tylko wersja Enterprise Edition)
 **Mapy kodu i wykresy zależności**

 W Visual Studio Enterprise, gdy chcesz zrozumieć konkretne zależności w kodzie, wizualizuj je przez tworzenie map kodu. Następnie można przejść do tych relacji przy użyciu mapy, która pojawia się obok kodu. Mapy kodu mogą również pomóc w śledzeniu miejsca w kodzie podczas pracy lub debugowania kodu, dzięki czemu można czytać mniej kodu, a dowiedzieć się więcej o projekcie kodu.

 W tej wersji wprowadziliśmy menu skrótów dla elementów kodu i linków znacznie łatwiejsze do użycia przez grupowanie poleceń w sekcje związane z zaznaczaniem, edytowaniem i zarządzaniem grupami oraz zmiana układu zawartości grupy. Zwróć również uwagę, że projekty testowe są wyświetlane w innym stylu niż inne projekty i że zaktualizowaliśmy ikony dla elementów na mapie, aby uzyskać bardziej odpowiednie wersje.

 ![Pokaż zaznaczone elementy na nowej mapie kodu](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Inne ulepszenia obejmują:

- **Udoskonalone diagramy górne**. W przypadku średnich i dużych rozwiązań programu Visual Studio możesz teraz użyć uproszczonego menu architektura, aby uzyskać bardziej przydatne mapy kodu dla rozwiązania. Zestawy rozwiązań są pogrupowane według folderów rozwiązania, dzięki czemu można je zobaczyć w kontekście i wykorzystać nakład pracy, który został umieszczony w tworzeniu struktury rozwiązania. Natychmiast zobaczysz odwołania projektu i zestawu, a następnie pojawią się typy łączy. Ponadto zestawy zewnętrzne są pogrupowane w bardziej zwarty sposób.

- **Projekty testowe mają różne style i można je filtrować**. Teraz można łatwiej i szybko identyfikować projekty testowe na mapie, ponieważ różnią się one stylami. Można je również odfiltrować, aby skoncentrować się na kodzie roboczym aplikacji.

- **Uproszczone zewnętrzne linki zależności**. Linki zależności nie przedstawiają już dziedziczenia z elementów System. Object, system. ValueType, system. Enum i system. Delegate, co ułatwia przeglądanie zewnętrznych zależności na mapie kodu.

- **"Przechodzenie do szczegółów w łączach zależności" obejmuje filtry**. Uzyskujesz przydatny, przejrzysty diagram podczas jego rozszerzania, aby zrozumieć wkłady do linku zależności. Diagram jest mniej czytelny i uwzględnia wybrane opcje filtrowania linków.

- **Elementy kodu są dodawane do mapy kodu z ich kontekstami**. Ponieważ diagramy są teraz wyświetlane wraz z ich kontekstami (do zestawu i folderu rozwiązania, które można odfiltrować w razie potrzeby), są dostępne bardziej użyteczne diagramy podczas przeciągania i upuszczania elementów kodu z Eksplorator rozwiązań, Widok klasy, Przeglądarka obiektów; lub po wybraniu elementów w Eksplorator rozwiązań i wybraniu pozycji Pokaż na mapie kodu.

- Szybsze **pobieranie map kodu**. Operacje przeciągania i upuszczania dają bezpośredni wynik, a linki między węzłami są tworzone znacznie szybciej, bez wywierania wpływu na kolejne operacje inicjowane przez użytkownika, takie jak rozszerzanie węzła lub żądanie większej liczby węzłów. Po utworzeniu map kodu bez kompilowania rozwiązania wszystkie przypadki narożne — takie jak zestawy nie są kompilowane — są teraz przetwarzane.

- **Pomiń ponowne kompilowanie rozwiązania.** Zapewnia lepszą wydajność podczas tworzenia i edytowania diagramów.

- **Filtrowanie węzłów i grup elementów kodu**. Mapy można szybko odkodować, pokazując lub ukrywając elementy kodu na podstawie ich kategorii, a także Grupując elementy kodu według folderów rozwiązania, zestawów, przestrzeni nazw, folderów projektu i typów.

- **Odfiltruj relacje, aby ułatwić odczytywanie diagramów**. Filtrowanie linków teraz dotyczy również linków między grupami, dzięki czemu praca z oknem filtru jest mniej niepożądane niż w poprzednich wersjach.

- **Utwórz diagramy na podstawie widok klasy i Przeglądarka obiektów**. Przeciągnij i upuść pliki i zestawy do nowej lub istniejącej mapy z Widok klasy i Przeglądarka obiektów Windows.

  Zobacz [zależności mapy w ramach rozwiązań](./modeling/map-dependencies-across-your-solutions.md).

  **Inne zmiany dotyczące projektowania i modelowania w tej wersji:**

- **Diagramy warstwowe**. Zaktualizuj te diagramy przy użyciu Widok klasy i Przeglądarka obiektów. Aby spełnić wymagania dotyczące projektu oprogramowania, należy użyć diagramów warstw do opisania żądanych zależności oprogramowania. Zachowaj spójność kodu z tym projektem, wyszukując kod, który nie spełnia tych ograniczeń, i sprawdzając przyszły kod w tym punkcie odniesienia.

- **Diagramy UML**. Nie można już tworzyć diagramów klas UML i diagramów sekwencyjnych na podstawie kodu. Jednak nadal można tworzyć te diagramy za pomocą nowych elementów UML.

- **Eksplorator architektury**. Nie można już korzystać z Eksploratora architektury do tworzenia diagramów. Można jednak nadal używać Eksplorator rozwiązań.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio Extensibility Tools
 Nie było łatwiejsze Instalowanie Visual Studio Extensibility Tools (VS SDK i szablonów), ponieważ są one teraz dołączane jako składnik opcjonalny podczas instalacji.  Narzędzia rozszerzalności umożliwiają deweloperom pisanie rozszerzeń w celu dostosowywania i dodawania funkcji do programu Visual Studio. Aby uzyskać więcej informacji o rozszerzalności programu Visual Studio, zobacz [Visual Studio SDK](./extensibility/visual-studio-sdk.md)

 Jeśli chcesz dołączyć narzędzia rozszerzalności do instalacji niestandardowej, możesz je znaleźć w obszarze **funkcje/typowe narzędzia/Visual Studio Extensibility Tools**.  Narzędzia rozszerzalności można także zainstalować w późniejszym czasie, otwierając okno dialogowe **Nowy projekt** i wybierając pozycję **Zainstaluj Visual Studio Extensibility Tools** w obszarze **Wizualizacja C# /rozszerzalność**.

## <a name="please-give-feedback"></a>Przekaż opinię
 Dlaczego warto wysłać opinię do zespołu programu Visual Studio? Ze względu na to, że potraktujemy Opinie klientów. W rzeczywistości przeglądamy każdą opinię, która jest dostępna w naszym systemie opinii. Twoje opinie są bardzo duże.

### <a name="send-a-smile"></a>Wyślij uśmiech
 Poinformuj nas, co pomoże nam zrozumieć, gdy spełnimy lub przekroczę oczekiwania. Gdy opracowujemy i wdrażamy nowe funkcje, używamy danych o funkcjach, które chcesz pomóc w naszych decyzjach projektowych. Tak więc, jeśli lubisz funkcję w programie Visual Studio, zrób nam więcej informacji. Jest to łatwe i można to zrobić bezpośrednio z poziomu środowiska IDE.

 Po prostu kliknij żółtą uśmiechniętą buźka na pasku tytułu, powiedz nam, co Ci się podoba, a następnie kliknij przycisk **Wyślij uśmiech** .

 To wszystko! Będziemy kierować swoją opinię do poprawnego zespołu, w którym będzie ona się oddzwonić, a następnie szybko zacząć zastanawiać się, jak jeszcze bardziej poprowadzisz.

### <a name="send-a-frown"></a>Wyślij niezadowolenie
 Wysłuchaj, gdzie musimy udoskonalać produkt, pomaga nam zarządzać naszym zaległościami, koncentrując się na najważniejszych kwestiach, które są najważniejsze dla naszych klientów. Jeśli istnieje coś, co jest debugowane, powiedz nam o nim, używając funkcji **Wyślij niezadowolenie** bezpośrednio w środowisku IDE. Ten proces jest zbyt prosty:

 Kliknij żółtą uśmiechniętą buźka na pasku tytułu, a następnie kliknij pozycję **Wyślij niezadowolenie**. Powiedz nam, co Ci się nie podoba, a następnie kliknij przycisk Wyślij niezadowolenie. Aby uzyskać więcej informacji, zobacz [rozmowa z nami](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Zgłaszaj awarie, zawieszenia i problemy z wydajnością
 Czasami szybka Uwaga w nieznanym niewoli jest zbyt mała, aby przekazać pełen wpływ niepotrzebnego elementu. Gdy występuje problem z zawieszaniem, awarią lub wydajnością, można łatwo udostępniać Odtwórz kroki, Zrzuty awaryjne i pliki śledzenia za pomocą okna dialogowego, które jest wyświetlane po wysłaniu niezadowolenia.

 Najpierw Wyślij niezadowolenie, jak opisano powyżej. W oknie dialogowym, które się pojawi, możesz oznaczyć swoją opinię za pomocą jednego z domyślnych tagów lub utworzyć własny tag. Tagi pomagają nam kierować swoją opinię do odpowiedniego zespołu funkcji. Z listy rozwijanej **Wybierz kategorię** wybierz opcję reprezentującą raportowany problem, a następnie postępuj zgodnie z instrukcjami, aby odtworzyć problem. Szczegółowe instrukcje dotyczące sposobu korzystania z programu Visual Studio do zgłaszania opinii są również dostępne. Aby uzyskać więcej informacji, zobacz [Visual Studio — instrukcje dotyczące wysyłania uśmiechów](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Zobacz też

* [Twórz aplikacje dla wielu platform za pomocą Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Twórz aplikacje mobilne dla wielu platform za pomocą wizualizacjiC++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Generowanie testów jednostkowych dla kodu za pomocą funkcji IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Praca z wieloma kontami użytkowników](./ide/work-with-multiple-user-accounts.md)
* [Tworzenie niestandardowych układów okien](./misc/create-custom-window-layouts.md)
* [Szybkie wykonywanie akcji dzięki żarówkom](./ide/perform-quick-actions-with-light-bulbs.md)
* [Co nowego w programie Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)