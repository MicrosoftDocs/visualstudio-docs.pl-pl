---
title: Tworzenie aplikacji mobilnych na wiele platform w Visual Studio | Microsoft Docs
description: W tym artykule dowiesz się, jak tworzyć aplikacje dla urządzeń z systemami Android, iOS i Windows przy użyciu Visual Studio.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: f2ce02467a43fc71a0e6e352a9a31a9ccfe810bf
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201770"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie aplikacji mobilnych na wiele platform w Visual Studio

Aplikacje dla urządzeń z systemami Android, iOS i Windows można tworzyć przy użyciu Visual Studio.  Podczas projektowania aplikacji możesz używać narzędzi w programie Visual Studio, aby łatwo dodawać połączone usługi, takie jak Microsoft 365, Azure App Service i Application Szczegółowe informacje.

Twórz aplikacje przy użyciu języka C# i języka .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągów, obrazów, a w niektórych przypadkach nawet interfejsu użytkownika.

Jeśli chcesz utworzyć grę lub immersywną aplikację graficzną, zainstaluj narzędzia platformy Visual Studio dla aparatu Unity i korzystaj ze wszystkich zaawansowanych funkcji zwiększających produktywność platformy Visual Studio za pomocą aparatu Unity, popularnego międzyplatformowego aparatu do gier/grafiki i środowiska programowego dla aplikacji uruchamianych w systemach iOS, Android, Windows i innych platformach.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)

![Urządzenia](../cross-platform/media/homedevices.png "Strona głównaUrządzeń")

Dzięki Visual Studio Tools dla platformy Xamarin można kierować aplikacje do systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod, a nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Dowiedz się więcej o programie Xamarin Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentacja tworzenia aplikacji mobilnych platformy Xamarin](/xamarin/) |
|[Metodyka DevOps z użyciem platformy Xamarin](/xamarin/tools/ci/devops/) |
|[Dowiedz się więcej o Windows uniwersalnych w Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwach między językami Swift](https://aka.ms/scposter) i C# (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Docelowe systemy Android, iOS i Windows z pojedynczej bazy kodu

 Aplikacje natywne dla systemów Android, iOS i Windows można tworzyć przy użyciu języka C# lub F# (Visual Basic obecnie nie jest obsługiwana).  Aby rozpocząć, zainstaluj Visual Studio, wybierz opcję Opracowywanie aplikacji mobilnych za pomocą platformy **.NET** w instalatorze.

 Jeśli masz już zainstalowaną Visual Studio, uruchom ponownie aplikację Instalator programu Visual Studio i wybierz tę samą opcję Tworzenia aplikacji mobilnych **za** pomocą platformy **.NET** dla platformy Xamarin (jak powyżej).

 Gdy wszystko będzie gotowe, szablony projektów zostaną wyświetlone w **oknie dialogowym Project** projektu. Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukanie ciągu "Xamarin".

 Xamarin uwidacznia natywną funkcjonalność systemów Android, iOS i Windows jako klasy i metody platformy .NET. Oznacza to, że aplikacje mają pełny dostęp do natywnych interfejsów API i kontrolek natywnych i są tak samo dynamiczne, jak aplikacje napisane w językach natywnych platformy.

 Po utworzeniu projektu będziesz korzystać ze wszystkich funkcji produktywności Visual Studio. Na przykład użyjesz projektanta do utworzenia stron i użyjesz funkcji IntelliSense, aby eksplorować natywne interfejsy API platform mobilnych. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobaczy, jak wygląda, możesz użyć emulatora Android SDK i natywnie uruchomić Windows aplikacje. Możesz również bezpośrednio używać urządzeń z systemem Android Windows z systemem Android. W przypadku projektów systemu iOS połącz się z sieciowym komputerem Mac i uruchom emulator systemu iOS z Visual Studio lub połącz się z urządzeniem z tetheredem.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jednego zestawu stron renderowanych na wszystkich urządzeniach przy użyciu zestawu Xamarin.Forms

 W zależności od złożoności projektu aplikacji możesz rozważyć jego skucie przy użyciu szablonów *platformy Xamarin.Forms* Mobile Apps **grupy** szablonów projektów. Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, który można udostępniać w systemach Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin.Forms otrzymasz aplikację dla systemu Android, aplikację dla systemu iOS i Windows aplikację. Aby uzyskać więcej informacji, zobacz Learn about mobile development with Xamarin (Informacje na temat tworzenia aplikacji mobilnych za [pomocą platformy Xamarin)](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) i [dokumentację platformy Xamarin.Forms.](/xamarin/xamarin-forms/)

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Udostępnianie kodu między aplikacjami dla systemów Android, iOS Windows aplikacji

 Jeśli nie używasz platformy Xamarin.Forms i chcesz projektować osobno dla każdej platformy, możesz udostępnić większość kodu bez interfejsu użytkownika między projektami platformy (Android, iOS i Windows). Obejmuje to logikę biznesową, integrację z chmurą, dostęp do bazy danych lub dowolny inny kod przeznaczony dla .NET Framework. Jedynym kodem, który nie można udostępnić, jest kod przeznaczony dla określonej platformy.

 ![Udostępnianie kodu między interfejsami użytkownika Windows, iOS i Android](../cross-platform/media/sharecode.png "ShareCode")

 Kod można udostępniać przy użyciu udostępnionego projektu, projektu biblioteki klas przenośnych lub obu tych typów. Może się okazać, że jakiś kod najlepiej pasuje do udostępnionego projektu, a część z nich jest bardziej sensowna w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Udostępnianie opcji kodu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opcje udostępniania kodu za pomocą programu .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Urządzenia Windows 10 docelowe

 ![Windows Urządzeń](../cross-platform/media/windowsdevices.png "Windows Urządzeń")

 Jeśli chcesz utworzyć pojedynczą aplikację, która jest przeznaczony dla pełnego Windows 10 urządzeń, utwórz aplikację uniwersalną Windows aplikację. Zaprojektujemy aplikację przy użyciu jednego projektu, a strony będą renderowane prawidłowo niezależnie od urządzenia używanego do ich wyświetlania.

 Rozpocznij od szablonu projektu Windows platformie uniwersalnej systemu Windows (UWP). Zaprojektuj strony wizualnie, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak wyglądają one dla różnych typów urządzeń. Jeśli nie podoba Ci się sposób, w jaki strona pojawia się na urządzeniu, możesz zoptymalizować stronę, aby lepiej dopasować ją do rozmiaru ekranu, rozdzielczości lub różnych orientacji, takich jak orientacja pozioma lub pionowa. Wszystko to można zrobić przy użyciu intuicyjnych okien narzędzi i łatwo dostępnych opcji menu w Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i krok po kroku kodu, wszystkie emulatory i symulatory urządzeń dla różnych typów urządzeń znajdziesz razem na jednej liście rozwijanej, która znajduje się na pasku **narzędzi Standardowa.**

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do platformy universal Windows Platform](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)

 ![Windows, iOS i Android](../cross-platform/media/homedevices.png "Windows, iOS i Android")

 Jeśli jesteś deweloperem internetowym i znasz kod HTML i JavaScript, możesz wybrać platformę docelową dla systemów Windows, Android i iOS przy użyciu języka Visual Studio Tools for Apache Cordova. Te aplikacje mogą być ukierunkowane na wszystkie trzy platformy i można je tworzyć przy użyciu najbardziej znanych umiejętności i procesów.

 Apache Cordova to framework, który zawiera model wtyczek. Ten model wtyczki udostępnia pojedynczy interfejs API języka JavaScript, który umożliwia dostęp do natywnych możliwości urządzeń na wszystkich trzech platformach (Android, iOS i Windows).

 Ponieważ te interfejsy API są międzyplatformowe, większość pisania można udostępniać między wszystkimi trzema platformami. Zmniejsza to koszty związane z opracowywaniem i konserwacją. Ponadto nie trzeba zaczynać od podstaw. Jeśli utworzono inne typy aplikacji internetowych, możesz udostępnić te pliki aplikacji Cordova bez konieczności ich modyfikowania ani przeprojektowania w jakikolwiek sposób.

 ![Aplikacje hybrydowe dla wielu urządzeń z kodem JavaScript](../cross-platform/media/multidevicehybridapps.png "Aplikacje hybrydowe z wieloma urządzeniami z kodem JavaScript")

 Aby rozpocząć pracę, zainstaluj Visual Studio i wybierz podczas instalacji funkcję Opracowywanie aplikacji mobilnych **za pomocą języka JavaScript.** Narzędzia oprogramowania Cordova automatycznie instalują całe oprogramowanie innych firm, które jest wymagane do skompilowania aplikacji wieloplatformowej.

 Po zainstalowaniu rozszerzenia otwórz program Visual Studio i utwórz projekt **Pusta aplikacja (Apache Cordova).** Następnie możesz opracować aplikację przy użyciu języka JavaScript lub TypeScript. Możesz również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji, a interfejsy API z wtyczek będą wyświetlane w funkcji IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i użycia kodu, wybierz emulator, taki jak emulator Apache Ripple lub system Android Emulator, przeglądarkę lub urządzenie, które zostało podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli opracowujesz aplikację na komputerze Windows, możesz nawet uruchomić ją na tym komputerze. Wszystkie te opcje są wbudowane w Visual Studio w ramach Visual Studio Tools dla Apache Cordova.

 Project szablonów do tworzenia aplikacji platformy uniwersalnej systemu Windows (UWP, Universal Windows Platform) są nadal dostępne w u usługach Visual Studio, więc możesz ich używać, jeśli zamierzasz korzystać tylko z Windows docelowych. Jeśli zdecydujesz się na późniejsze kierowanie kodu do systemów Android i iOS, zawsze możesz przeportować kod do projektu Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Wprowadzenie do Visual Studio Tools for Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[Dowiedz się więcej o Visual Studio Emulator dla systemu Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (C++)

![Używanie języka C&#43;&#43; do kompilowania aplikacji dla systemów Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj pakiet Visual Studio **i tworzenie aplikacji mobilnych w języku C++.** Następnie można utworzyć aplikację działania natywnego dla systemu Android lub aplikację, która jest Windows lub iOS. Jeśli chcesz, możesz wybrać systemy Android, iOS i Windows w tym samym rozwiązaniu, a następnie udostępnić kod między nimi przy użyciu międzyplatformowej statycznej lub dynamicznej biblioteki udostępnionej.

 Jeśli musisz utworzyć aplikację dla systemu Android, która wymaga zaawansowanego manipulowania grafiką, na przykład gry, możesz użyć języka C++. Rozpocznij od projektu **Native Activity Application (Android).** Ten projekt ma pełną obsługę zestawu narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "Szablon projektu działania natywnego")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobaczenia jej wyglądu, użyj aplikacji dla systemu Android Emulator. Jest szybka, niezawodna i łatwa do zainstalowania i skonfigurowania.

 Można również utworzyć aplikację, która jest przeznaczony dla pełnego zakresów urządzeń Windows 10 przy użyciu języka C++ i szablonu projektu aplikacji platformy uniwersalnej systemu Windows (UWP). Przeczytaj więcej na ten temat w sekcji [Target Windows 10 devices (Urządzenia](#WindowsHTML) docelowe), która znajduje się wcześniej w tym temacie.

 Kod C++ można udostępniać między systemami Android, iOS i Windows, tworząc statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki udostępnione](../cross-platform/media/cross_plat_cpp_libraries.png "Statyczne i dynamiczne biblioteki udostępnione")

 Możesz korzystać z tej biblioteki w projekcie Windows, iOS lub Android, jak opisano wcześniej w tej sekcji. Można go również używać w aplikacji, która jest kompilowana przy użyciu platformy Xamarin, języka Java lub dowolnego języka, który umożliwia wywoływanie funkcji w niezamówianej bibliotece DLL.

 Podczas pisania kodu w tych bibliotekach można używać funkcji IntelliSense do eksplorowania natywnych interfejsów API systemu Android Windows platform. Te projekty bibliotek są w pełni zintegrowane z debugerem usługi Visual Studio, dzięki czemu można ustawiać punkty przerwania, przechodzić przez kod oraz odnajdować i naprawiać problemy przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobieranie Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Instalowanie środowiska opracowywania aplikacji mobilnych na wiele platform w języku C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Dowiedz się więcej o używaniu języka C++ do kierowania do wielu platform](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj potrzebne informacje, a następnie utwórz aplikację działania natywnego języka C++ dla systemu Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Dowiedz się więcej o udostępnianiu kodu C++ za](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) pomocą aplikacji Windows Android (VisualStudio.com)|
|[Przykłady tworzenia aplikacji mobilnych dla wielu platform dla języka C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Tworzenie międzyplatformowej gry dla systemów Android, iOS i Windows przy użyciu Visual Studio dla aparatu Unity

 Visual Studio Tools for Unity to bezpłatne rozszerzenie dla platformy Visual Studio, które integruje zaawansowane narzędzia do edytowania, produktywności i debugowania kodu usługi Visual Studio za pomocą aparatu *Unity*, popularnego międzyplatformowego aparatu do gier/grafiki i środowiska programowego dla aplikacji immersywnych przeznaczonych dla platform Windows, iOS, Android i innych platform, w tym internetowych.

 ![Środowisko projektowe VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity omówienie")

 Za Visual Studio Tools for Unity (VSTU) można używać języka Visual Studio do pisania skryptów gier i edytora w języku C#, a następnie używać zaawansowanego debugera do znajdowanie i naprawianie błędów. Najnowsza wersja vstu zapewnia obsługę aparatu Unity 2018.1 i obejmuje kolorowanie składni dla języka cieniowania ShaderLab aparatu Unity, lepszą synchronizację z aparatem Unity, bardziej rozbudowane debugowanie i ulepszone generowanie kodu dla kreatora MonoBehavior. VsTU oferuje również pliki projektu aparatu Unity, komunikaty konsoli i możliwość uruchamiania gry w uściślicie Visual Studio dzięki czemu możesz poświęcać mniej czasu na przełączanie się do edytora aparatu Unity i z edytora aparatu Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o budowania gier Unity za pomocą Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Przeczytaj więcej na temat Visual Studio Tools for Unity](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity) |
|[Rozpoczynanie korzystania z Visual Studio Tools for Unity](/visualstudio/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity) |
|[Przeczytaj o najnowszych ulepszeniach wersji zapoznawczej Visual Studio Tools for Unity 2.0](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio bloga)|
|[Obejrzyj wprowadzenie wideo do wersji Visual Studio Tools for Unity 2.0 (wideo)](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true)|
|[Dowiedz się więcej na temat aparatu Unity](https://unity.com/) (witryna internetowa aparatu Unity)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie Microsoft 365 API do Visual Studio projektu](/office/developer-program/office-365-developer-program)
- [Azure App Services — Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
