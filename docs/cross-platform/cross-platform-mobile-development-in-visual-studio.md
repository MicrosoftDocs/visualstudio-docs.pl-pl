---
title: Tworzenie aplikacji mobilnych dla wielu Platform w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/24/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: fcf28d844124b7a2ae8a0b380739433261c5a3ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816189"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie aplikacji mobilnych dla wielu platform w programie Visual Studio

Można tworzyć aplikacje dla urządzeń z systemem Android, iOS i Windows przy użyciu programu Visual Studio.  Podczas projektowania aplikacji, należy użyć narzędzi w programie Visual Studio, łatwe dodawanie podłączonych usług, takich jak Office 365, Azure App Service i usługi Application Insights.

Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągi, obrazy, a w niektórych przypadkach nawet interfejsu użytkownika.

Do tworzenia gier lub realistycznych aplikacji graficznych, należy zainstalować narzędzia Visual Studio tools for Unity i cieszyć się wszystkimi zaawansowane funkcje produktywności programu Visual Studio przy użyciu aparatu Unity, popularnych Międzyplatformowe gry grafiki aparatu i środowisko programistyczne dla aplikacji, Uruchom na iOS, Android, Windows i innych platform.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)

![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

Program Visual Studio Tools for Xamarin można wskazać systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniania kodu i nawet interfejsu użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (Visual Studio)|
|[Więcej informacji na temat platformy Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (Visual Studio)|
|[Dokumentacji dla deweloperów aplikacji mobilnych platformy Xamarin](/xamarin/) |
|[DevOps przy użyciu aplikacji Xamarin](/xamarin/tools/ci/devops/) |
|[Dowiedz się więcej o aplikacji Windows Universal apps w programie Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (Visual Studio)|
|[Dowiedz się więcej o podobieństwa Swift i C#](https://aka.ms/scposter) (witrynie download.microsoft.com)|

### <a name="AndroidHTML"></a> Docelowe systemów Android, iOS i Windows z pojedynczą bazą kodu

 Tworzyć natywne aplikacje dla systemów Android, iOS i Windows przy użyciu C# lub F# (Visual Basic nie jest obsługiwane w tej chwili).  Aby rozpocząć pracę, zainstaluj program Visual Studio 2017, wybierz **programowanie aplikacji mobilnych przy użyciu platformy .NET** opcji w Instalatorze.

 Jeśli masz już program Visual Studio 2017, uruchom ponownie **Instalatora programu Visual Studio** i wybierz taki sam **programowanie aplikacji mobilnych przy użyciu platformy .NET** opcji dla platformy Xamarin (powyżej).

 Gdy wszystko będzie gotowe, szablony projektów są wyświetlane w **nowy projekt** okno dialogowe. Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukać "Xamarin."

 Xamarin udostępnia natywnych funkcji systemu Android, iOS i Windows jako metod i klas platformy .NET. To oznacza, że aplikacje mają pełny dostęp do natywnych interfejsów API i natywne kontrolki i są one po prostu jako dynamiczny, jako aplikacje napisane w językach platformy natywnej.

 Po utworzeniu projektu, możesz korzystać tylko niektóre z funkcji produktywności programu Visual Studio. Na przykład będzie tworzenie stron za pomocą projektanta i technologię IntelliSense, aby zapoznać się z natywnych interfejsów API platformy mobilne. Gdy wszystko będzie gotowe uruchomić aplikację i zobacz, jak wygląda na to, można użyć emulatora systemu Android SDK i natywnie uruchamiać aplikacje Windows. Umożliwia także powiązane systemami Android i Windows bezpośrednio. Dla projektów systemu iOS nawiązać połączenie z komputerem Mac w sieci uruchomić emulator dla systemu iOS w programie Visual Studio i nawiązać połączenie z urządzenia powiązanego.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jeden zestaw stron, które są renderowane dla wszystkich urządzeń za pomocą platformy Xamarin.Forms

 W zależności od złożoności projektu aplikacji, można rozważyć wbudowanie jej za pomocą *Xamarin.Forms* szablonów w **Mobile Apps** grupy szablonów projektu. Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, którą można współdzielić między systemów Android, iOS i Windows.  Podczas kompilowania rozwiązania platformy Xamarin.Forms, uzyskasz aplikację systemu Android aplikacji systemu iOS i aplikacji Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) i [dokumentacji zestawu narzędzi Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="ShareHTML"></a> Współdziel kod między systemami Android, iOS i aplikacji Windows

 Jeśli nie będziesz jej używać zestawu narzędzi Xamarin.Forms i projektować pod kątem poszczególnych platform indywidualnie, możesz udostępniać większość kodu między projektami platform (systemów Android, iOS i Windows) bez interfejsu użytkownika. W tym wszelka logika biznesowa, integracja z chmurą, dostęp do bazy danych lub inny kod, który jest przeznaczony dla .NET Framework. Tylko kod, który nie mogą udostępniać jest kod, który jest przeznaczony dla określonej platformy.

 ![Udostępnianie kodu pomiędzy Windows, iOs i Android interfejsu użytkownika](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępnić swój kod za pomocą udostępnionego projektu i/lub projekt przenośnej biblioteki klas. Może się okazać, że niektóre kodu mieści się najlepiej w projekcie udostępnionym i jakiś kod sprawia, że więcej sens w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Udostępnianie kodu opcje](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Kod opcje udostępniania przy użyciu platformy .NET](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a> Docelowe urządzenia z systemem Windows 10

 ![Urządzenia Windows](../cross-platform/media/windowsdevices.png "urządzenia Windows")

 Jeśli chcesz utworzyć pojedynczą aplikacją, który jest przeznaczony dla rozmaitych urządzeniach z systemem Windows 10, należy utworzyć uniwersalnej aplikacji Windows. Będziesz projektowanie aplikacji przy użyciu pojedynczego projektu i stron sieci będą poprawnie renderowane niezależnie od tego, jakiego urządzenia służy do wyświetlania ich.

 Uruchom przy użyciu szablonu projektu aplikacji uniwersalnej platformy Windows (UWP). Projektowanie wizualnie strony, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak pojawiają się dla różnych typów urządzeń. Jeśli nie potrzebujesz, jak zostanie wyświetlona strona, na urządzeniu, można zoptymalizować strony aby lepiej dopasować się do rozmiaru ekranu, rozwiązania lub różnych orientacje, takie jak tryb pozioma lub pionowa. Możesz tworzyć wszystko to za pomocą intuicyjnego narzędzia systemu windows i opcje menu łatwo dostępne w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i kroku przez kod, można znaleźć wszystkie emulatorów urządzeń i symulatorów dla różnych typów urządzeń razem na jednej liście rozwijanej, który znajduje się na **standardowa** paska narzędzi.

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do korzystania z platformy Windows Universal](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji na platformie Universal Windows (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

## <a name="HTML"></a> Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)

 ![Windows, iOS i urządzenia z systemem Android](../cross-platform/media/homedevices.png "Windows, iOS i urządzenia z systemem Android")

 Jeśli jesteś deweloperem internetowym i znasz HTML i JavaScript, można wskazać Windows, Android i iOS przy użyciu programu Visual Studio Tools for Apache Cordova. Te aplikacje mogą są przeznaczone dla wszystkich trzech platformach, a następnie utworzyć je przy użyciu umiejętności i procesy, które znasz najbardziej.

 Apache Cordova to struktura, która obejmuje model dodatku plug-in. Ten model wtyczek zawiera pojedynczy interfejs API języka JavaScript, która umożliwia dostęp do natywnych możliwości urządzenia dla wszystkich trzech platformach (Android, iOS i Windows).

 Ponieważ te interfejsy API dla wielu platform, możesz udostępniać większość zapisu od wszystkich trzech platformach. Zmniejsza koszty tworzenia i konserwacji. Ponadto nie ma potrzeby od samego początku. Jeśli utworzono innych typów aplikacji sieci web, mogą udostępniać te pliki za pomocą aplikacji Cordova, bez konieczności modyfikowania ani projektowane w dowolny sposób.

 ![Aplikacje hybrydowe dla wielu urządzeń przy użyciu języka Javascript](../cross-platform/media/multidevicehybridapps.png "aplikacje hybrydowe dla wielu urządzeń przy użyciu języka Javascript")

 Aby rozpocząć pracę, zainstaluj program Visual Studio, a następnie wybierz **programowanie aplikacji mobilnych za pomocą języka Javascript** funkcji podczas instalacji. Narzędzia Cordova są automatycznie instalować całe oprogramowanie innych firm, które są wymagane do kompilowania aplikacji dla wielu platform.

 Po zainstalowaniu rozszerzenia, Otwórz program Visual Studio i Utwórz **pusta aplikacja (Apache Cordova)** projektu. Następnie możesz opracować aplikację przy użyciu języka JavaScript i Typescript. Możesz również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji i interfejsów API z dodatków plug-in są wyświetlane w IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i kroku przez kod, należy wybrać emulator, takiej jak emulatora Apache Ripple emulatora systemu Android, przeglądarki lub urządzenia, który został podłączony bezpośrednio do komputera. Następnie uruchom aplikację. Jeżeli projektujesz aplikację dla komputera z systemem Windows, możesz nawet uruchamiać go na tym. Wszystkie te opcje są tworzone w programie Visual Studio jako część programu Visual Studio Tools for Apache Cordova.

 Szablony projektu dla tworzenia aplikacji uniwersalnych platformy Windows (UWP) są nadal dostępne w programie Visual Studio więc możesz ich używać, jeśli planujesz tylko urządzenia Windows docelowe. Jeśli zdecydujesz się pod kątem systemów Android i iOS, a później, należy zawsze portu kodu z projektem Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (Visual Studio)|
|[Rozpoczynanie pracy z usługą Visual Studio Tools for Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Dowiedz się więcej o Visual Studio Emulator for Android](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs) (Visual Studio)|

<a name="CPP"></a>

## <a name="build-an-app-for-android-and-windows-c"></a>Tworzenie aplikacji dla systemów Android i Windows (C++)
 ![Użyj C&#43; &#43; kompilacji dla systemów Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio 2017 i **programowanie aplikacji mobilnych w języku C++** obciążenia. Następnie można utworzyć aplikacji działania natywnego dla systemu Android lub aplikacji, który jest przeznaczony dla Windows. Szablonów języka C++, przeznaczonych dla systemu iOS nie są jeszcze dostępne. Dla systemów Android i Windows można wskazać w tym samym rozwiązaniu, jeśli chcesz, a następnie udostępnianie kodu między nimi przy użyciu dla wielu platform statycznej lub dynamicznej biblioteki udostępnionej.

 Jeśli potrzebujesz do tworzenia aplikacji dla systemu Android, która wymaga dowolny rodzaj manipulowanie grafiki zaawansowane, takie jak gry, można użyć C++, aby to zrobić. Rozpoczynać **aplikacja klasy Nativeactivity (Android)** projektu. W tym projekcie są pełna obsługa łańcucha narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "szablonu projektu działania natywnego")

 Gdy wszystko będzie gotowe uruchomić aplikację i zobacz, jak wygląda na to, należy użyć emulatora systemu Android. Jest to szybkie, niezawodne i łatwe do zainstalowania i skonfigurowania.

 Można również utworzyć aplikację, która jest przeznaczony dla rozmaitych urządzeniach z systemem Windows 10 przy użyciu języków C++ i szablon projektu aplikacji uniwersalnej platformy Windows (UWP). Dowiedz się więcej w [urządzenia docelowego systemu Windows 10](#WindowsHTML) sekcji, która występuje wcześniej w tym temacie.

 Możesz udostępniać kodu między systemami Android i Windows w języku C++, tworząc statycznej lub dynamicznej biblioteki udostępnionej.

 ![Biblioteki udostępnione statycznych i dynamicznych](../cross-platform/media/cross_plat_cpp_libraries.png "statycznej i dynamicznej biblioteki udostępnionej")

 Można korzystać z tej biblioteki w Windows lub projekt dla systemu Android, takich jak opisane wcześniej w tej sekcji. Można również korzystać go w aplikacji, gdy kompilujesz przy użyciu platformy Xamarin, Java lub dowolnego języka, który pozwala wywoływać funkcje w niezarządzaną biblioteką DLL.

 Podczas pisania kodu w tych bibliotek, można użyć IntelliSense, aby zapoznać się z natywnymi interfejsami API platform dla systemów Android i Windows. Te projekty biblioteki są całkowicie zintegrowane z debugera programu Visual Studio, aby można było ustawić punkty przerwania, Przechodź przez kod i znajdowanie i rozwiązywanie problemów przy użyciu wszystkie zaawansowane funkcje debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Instalowanie języka Visual C++ for Cross-Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn707591.aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej na temat za pomocą języka C++ na wielu platformach.](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj co użytkownik należy, a następnie utwórz aplikacji działania natywnego dla systemu Android](https://msdn.microsoft.com/library/dn707595.aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej na temat udostępniania kodu w języku C++ w aplikacjach dla systemów Android i Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (Visual Studio)|
|[Przykłady programowania aplikacji mobilnych dla wielu platform w języku C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Przykłady dodatkowe opracowywania aplikacji mobilnych dla wielu platform w języku C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Twórz gry dla wielu platform dla systemów Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity

 Visual Studio Tools for Unity to bezpłatne rozszerzenie programu Visual Studio, która integruje się programu Visual Studio zaawansowane kodu do edycji, wydajności i narzędzia, za pomocą debugowania *Unity*, aparat popularnych Międzyplatformowe gry grafiki i środowisko projektowe dla wciągające aplikacje, których celem, Windows, iOS, Android i innych platform, w tym w sieci web.

 ![Środowisko deweloperskie w narzędziach VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity — omówienie")

 Program Visual Studio Tools for Unity (VSTU) można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy. Najnowsza wersja narzędzi vstu zapewnia obsługę Unity 2018.1 i obejmuje kolorowanie składni języka programu do cieniowania ShaderLab mechanizmu Unity, lepsze synchronizacji za pomocą aparatu Unity, bardziej rozbudowane profilowanie i generowanie kodu ulepszone kreatora MonoBehavior. Narzędzia VSTU także niesie plików projektu środowiska Unity, komunikaty konsoli i możliwości, aby rozpocząć tworzenie gry w programie Visual Studio, dzięki czemu spędzisz mniej czasu przełączanie z edytora środowiska Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier za pomocą programu Visual Studio Unity](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Więcej informacji na temat programu Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Uruchom przy użyciu programu Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Przeczytaj najnowsze ulepszenia do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog Visual Studio)|
|[Obejrzyj wprowadzenie wideo do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej o Unity](http://unity3d.com/) (Unity witryny sieci Web)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie interfejsów API usługi Office 365 do projektu programu Visual Studio](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [Usługa Azure App Services — Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)
