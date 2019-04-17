---
title: Tworzenie aplikacji mobilnych dla wielu Platform
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: d82776b72b1634e3645749c8a1fb8eaecbedf17c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657301"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie aplikacji mobilnych na wiele platform w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć aplikacje dla urządzeń z systemem Android, iOS i Windows przy użyciu programu Visual Studio.  Podczas projektowania aplikacji, należy użyć narzędzi w programie Visual Studio, łatwe dodawanie podłączonych usług, takich jak Office 365, Azure App Service i usługi Application Insights.

 Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągi, obrazy, a w niektórych przypadkach nawet interfejsu użytkownika.

 Do tworzenia gier lub realistycznych aplikacji graficznych, należy zainstalować narzędzia Visual Studio tools for Unity i cieszyć się wszystkimi zaawansowane funkcje produktywności programu Visual Studio przy użyciu aparatu Unity, popularnych Międzyplatformowe gry grafiki aparatu i środowisko programistyczne dla aplikacji, Uruchom na iOS, Android, Windows i innych platform.

 **W tym artykule:**

-   [Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)](#NET)

    -   [Docelowe systemów Android, iOS i Windows z pojedynczą bazą kodu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

    -   [Docelowe urządzenia z systemem Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

-   [Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)](#HTML)

-   [Tworzenie aplikacji dla systemów Android i Windows (C++)](#CPP)

-   [Twórz gry dla wielu platform dla systemów Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity](#Unity)

##  <a name="NET"></a> Tworzenie aplikacji dla systemu Android, iOS i Windows (.NET Framework)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Za pomocą platformy Xamarin można wskazać systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniania kodu i nawet interfejsu użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (Visual Studio)|
|[Więcej informacji na temat platformy Xamarin w programie Visual Studio](http://www.visualstudio.com/explore/xamarin-vs) (Visual Studio)|
|[Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Biblioteka MSDN)|
|[Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Biblioteka MSDN)|
|[Dowiedz się więcej o uniwersalnych aplikacji dla Windows w programie Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (Visual Studio)|
|[Dowiedz się więcej o podobieństwa Swift i C#](https://aka.ms/scposter) (witrynie download.microsoft.com)|
|[Dowiedz się więcej o Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (Visual Studio)|

###  <a name="AndroidHTML"></a> Docelowe systemów Android, iOS i Windows z pojedynczą bazą kodu
 Tworzyć natywne aplikacje dla systemów Android, iOS i Windows przy użyciu C# lub F# (Visual Basic nie jest obsługiwane w tej chwili).  Aby rozpocząć pracę, należy zainstalować program Visual Studio 2015, wybierz **niestandardowe** opcji w oknie Instalatora, a następnie zaznacz pole w obszarze **Cross Platform Mobile Development > C# / .NET (Xamarin)**. Można także uruchomić z [Instalatora platformy Xamarin](https://www.xamarin.com/download), co jest wymagane do instalacji Xamarin dla programu Visual Studio 2013.

 Jeśli masz już program Visual Studio 2015, uruchom Instalatora z **Panel sterowania > programy i funkcje** i wybierz taki sam **niestandardowe** opcji dla programu Xamarin opisanych powyżej.

 Gdy wszystko będzie gotowe, szablony projektów są wyświetlane w **nowy projekt** okno dialogowe. Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukać "Xamarin."

 Xamarin udostępnia natywnych funkcji systemu Android, iOS i Windows jako obiektów platformy .NET. Dlatego aplikacje mają pełny dostęp do natywnych interfejsów API i kontrolki użytkownika natywnych i są one po prostu jako dynamiczny, jako aplikacje napisane w językach platformy natywnej.

 Po utworzeniu projektu, możesz korzystać tylko niektóre z funkcji produktywności programu Visual Studio. Na przykład będzie tworzenie stron za pomocą projektanta i technologię IntelliSense, aby zapoznać się z natywnych interfejsów API platformy mobilne. Gdy wszystko będzie gotowe uruchomić aplikację i zobaczyć, jak wygląda, można użyć Visual Studio Emulator for Android lub w emulatorze systemu Android SDK, natywnie uruchamiać aplikacje Windows lub uruchamiać aplikacje Windows na emulator Windows Phone. Umożliwia także powiązane systemami Android i Windows bezpośrednio. Dla projektów systemu iOS nawiązać połączenie z komputerem Mac w sieci uruchomić Mac emulator w programie Visual Studio i nawiązać połączenie z urządzenia powiązanego.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jeden zestaw stron, które są renderowane dla wszystkich urządzeń za pomocą platformy Xamarin.Forms
 W zależności od złożoności projektu aplikacji, można rozważyć wbudowanie jej za pomocą *Xamarin.Forms* szablonów w **Mobile Apps** grupy szablonów projektu. Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, którą można współdzielić między systemów Android, iOS i Windows.  Podczas kompilowania rozwiązania platformy Xamarin.Forms, uzyskasz aplikację systemu Android aplikacji systemu iOS i aplikacji Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

####  <a name="ShareHTML"></a> Współdziel kod między systemami Android, iOS i aplikacji Windows
 Jeśli nie będziesz jej używać zestawu narzędzi Xamarin.Forms i projektować pod kątem poszczególnych platform indywidualnie, możesz udostępniać większość kodu między projektami platform (systemów Android, iOS i Windows) bez interfejsu użytkownika. W tym wszelka logika biznesowa, integracja z chmurą, dostęp do bazy danych lub inny kod, który jest przeznaczony dla .NET Framework. Tylko kod, który nie mogą udostępniać jest kod, który jest przeznaczony dla określonej platformy.

 ![Udostępnianie kodu pomiędzy Windows, iOs i Android interfejsu użytkownika](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępnić swój kod za pomocą udostępnionego projektu i/lub projekt przenośnej biblioteki klas. Może się okazać, że niektóre kodu mieści się najlepiej w projekcie udostępnionym i jakiś kod sprawia, że więcej sens w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|Wybierz, czy można udostępnić swój kod za pomocą udostępnionych projektów i/lub projektów biblioteki klas przenośnych.<br /><br /> [Współdzielenie kodu między platformami](http://blogs.msdn.com/b/dotnet/archive/2014/04/21/sharing-code-across-platforms.aspx) (blog .NET Framework)<br /><br /> [Udostępnianie kodu opcje](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (Xamarin)<br /><br /> [Opcje udostępniania przy użyciu programu .NET Framework kodu](http://msdn.microsoft.com/library/dn720832.aspx) (Biblioteka MSDN)|

###  <a name="WindowsHTML"></a> Docelowe urządzenia z systemem Windows 10
 ![Urządzenia Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Jeśli chcesz utworzyć pojedynczą aplikacją, który jest przeznaczony dla rozmaitych urządzeniach z systemem Windows 10, należy utworzyć uniwersalnej aplikacji Windows. Będziesz projektowanie aplikacji przy użyciu pojedynczego projektu i stron sieci będą poprawnie renderowane niezależnie od tego, jakiego urządzenia służy do wyświetlania ich.

 Uruchom przy użyciu szablonu projektu aplikacji Windows universal. Projektowanie wizualnie strony, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak pojawiają się dla różnych typów urządzeń. Jeśli nie potrzebujesz, jak zostanie wyświetlona strona, na urządzeniu, można zoptymalizować strony aby lepiej dopasować się do rozmiaru ekranu, rozwiązania lub różnych orientacje, takie jak tryb pozioma lub pionowa. Możesz tworzyć wszystko to za pomocą intuicyjnego narzędzia systemu windows i opcje menu łatwo dostępne w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i kroku przez kod, można znaleźć wszystkie emulatorów urządzeń i symulatorów dla różnych typów urządzeń razem na jednej liście rozwijanej, który znajduje się na **standardowa** paska narzędzi.

 Windows 10 jest stosunkowo nowym, więc tam również szablony projektów przeznaczonych dla Windows 8.1. Jeśli chcesz, a aplikacja zostanie uruchomiona na telefony, tablety i komputerów z systemem Windows 10, możesz użyć tych szablonów projektu. Jednak wszystkie urządzenia z systemem Windows 8.1 będą otrzymywać automatyczne uaktualnienia do systemu Windows 10, więc chyba, że określone przyczyny, dlaczego czy raczej platformą docelową jest program Windows 8.1, firma Microsoft zaleca użycie szablonów projektu, przeznaczonych dla systemu Windows 10.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o uniwersalnych aplikacji dla Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Tworzenie swojej pierwszej](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji na platformie Universal Windows (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

##  <a name="HTML"></a> Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Jeśli jesteś deweloperem internetowym i znasz HTML i JavaScript, można wskazać Windows, Android i iOS przy użyciu programu Visual Studio Tools for Apache Cordova. Te aplikacje mogą są przeznaczone dla wszystkich trzech platformach, a następnie utworzyć je przy użyciu umiejętności i procesy, które znasz najbardziej.

 Apache Cordova to struktura, która obejmuje model dodatku plug-in. Ten model wtyczek zawiera pojedynczy interfejs API języka JavaScript, która umożliwia dostęp do natywnych możliwości urządzenia dla wszystkich trzech platformach (Android, iOS i Windows).

 Ponieważ te interfejsy API dla wielu platform, możesz udostępniać większość zapisu od wszystkich trzech platformach. Zmniejsza koszty tworzenia i konserwacji. Ponadto nie ma potrzeby od samego początku. Jeśli utworzono innych typów aplikacji sieci web, mogą udostępniać te pliki za pomocą aplikacji Cordova, bez konieczności modyfikowania ani projektowane w dowolny sposób.

 ![Obsługa wielu&#45;aplikacje hybrydowe dla urządzeń](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Aby rozpocząć pracę, zainstaluj program Visual Studio 2015, a następnie wybierz **HTML/JavaScript (Apache Cordova)** funkcji podczas instalacji. Jeśli używasz programu Visual Studio 2013, należy zainstalować Visual Studio Tools for Apache Cordova rozszerzenia. W obu przypadkach narzędzia Cordova automatycznie instalować całe oprogramowanie innych firm, które są wymagane do kompilowania aplikacji dla wielu platform.

 Po zainstalowaniu rozszerzenia, Otwórz program Visual Studio i Utwórz **pusta aplikacja (Apache Cordova)** projektu. Następnie możesz opracować aplikację przy użyciu języka JavaScript i Typescript. Możesz również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji i interfejsów API z dodatków plug-in są wyświetlane w IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i kroku przez kod, należy wybrać emulator, takie jak emulatora Apache Ripple lub Visual Studio Emulator (system Android lub Windows Phone), przeglądarki lub urządzenia, który został podłączony bezpośrednio do komputera. Następnie uruchom aplikację. Jeżeli projektujesz aplikację dla komputera z systemem Windows, możesz nawet uruchamiać go na tym. Wszystkie te opcje są tworzone w programie Visual Studio jako część programu Visual Studio Tools for Apache Cordova.

 Szablony projektów dla tworzenia uniwersalnych aplikacji dla Windows są nadal dostępne w programie Visual Studio więc możesz ich używać, jeśli planujesz tylko urządzenia Windows docelowe. Jeśli zdecydujesz się pod kątem systemów Android i iOS, a później, należy zawsze portu kodu z projektem Cordova. Istnieją wersji typu open-source WinJS interfejsów API, dzięki czemu można ponownie użyć wszelki kod, który korzysta z tych interfejsów API. Inaczej mówiąc, jeśli planowane jest na innych platformach w przyszłości, zaleca się po uruchomieniu program Visual Studio Tools for Apache Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://www.visualstudio.com/products/visual-studio-community-vs) (Visual Studio)|
|[Rozpoczynanie pracy z usługą Visual Studio Tools for Apache Cordova](http://taco.visualstudio.com/docs/get-started-vs-tools-apache-cordova/) (taco.visualstudio.com)|
|[Dowiedz się więcej o Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (Visual Studio)|

##  <a name="CPP"></a> Tworzenie aplikacji dla systemów Android i Windows (C++)
 ![Użyj C&#43; &#43; kompilacji dla systemów Android, iOS i Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio 2015 i Visual C++ for Cross Platform Mobile Development tools. Następnie można utworzyć aplikacji działania natywnego dla systemu Android lub aplikacji, który jest przeznaczony dla Windows. Szablonów języka C++, przeznaczonych dla systemu iOS nie są jeszcze dostępne. Dla systemów Android i Windows można wskazać w tym samym rozwiązaniu, jeśli chcesz, a następnie udostępnianie kodu między nimi przy użyciu dla wielu platform statycznej lub dynamicznej biblioteki udostępnionej.

 Jeśli potrzebujesz do tworzenia aplikacji dla systemu Android, która wymaga dowolny rodzaj manipulowanie grafiki zaawansowane, takie jak gry, można użyć C++, aby to zrobić. Rozpoczynać **aplikacja klasy Nativeactivity (Android)** projektu. W tym projekcie są pełna obsługa łańcucha narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat-cpp-native.png "Cross Plat_CPP_Native")

 Gdy wszystko będzie gotowe uruchomić aplikację i zobacz, jak wygląda na to, należy użyć programu Visual Studio Emulator dla systemu Android. Jest to szybkie, niezawodne i łatwe do zainstalowania i skonfigurowania.

 Można również utworzyć aplikację, która jest przeznaczony dla rozmaitych urządzeniach z systemem Windows 10 przy użyciu języków C++ i uniwersalnej szablon projektu aplikacji Windows. Dowiedz się więcej w [urządzenia docelowego systemu Windows 10](#WindowsHTML) sekcji, która występuje wcześniej w tym temacie.

 Możesz udostępniać kodu między systemami Android i Windows w języku C++, tworząc statycznej lub dynamicznej biblioteki udostępnionej.

 ![Biblioteki udostępnione statycznych i dynamicznych](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Można korzystać z tej biblioteki w Windows lub projekt dla systemu Android, takich jak opisane wcześniej w tej sekcji. Można również korzystać go w aplikacji, gdy kompilujesz przy użyciu platformy Xamarin, Java lub dowolnego języka, który pozwala wywoływać funkcje w niezarządzaną biblioteką DLL.

 Podczas pisania kodu w tych bibliotek, można użyć IntelliSense, aby zapoznać się z natywnymi interfejsami API platform dla systemów Android i Windows. Te projekty biblioteki są całkowicie zintegrowane z debugera programu Visual Studio, aby można było ustawić punkty przerwania, Przechodź przez kod i znajdowanie i rozwiązywanie problemów przy użyciu wszystkie zaawansowane funkcje debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](http://www.visualstudio.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Instalowanie języka Visual C++ for Cross-Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej na temat za pomocą języka C++ na wielu platformach.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj co użytkownik należy, a następnie utwórz aplikacji działania natywnego dla systemu Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o Visual Studio Emulator for Android](http://www.visualstudio.com/explore/msft-android-emulator-vs) (Visual Studio)|
|[Dowiedz się więcej na temat udostępniania kodu w języku C++ w aplikacjach dla systemów Android i Windows](http://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx) (Visual Studio)|
|[Przykłady programowania aplikacji mobilnych dla wielu platform w języku C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Przykłady dodatkowe opracowywania aplikacji mobilnych dla wielu platform w języku C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

##  <a name="Unity"></a> Twórz gry dla wielu platform dla systemów Android, iOS i Windows za pomocą narzędzi Visual Studio tools for Unity
 Visual Studio Tools for Unity to bezpłatne rozszerzenie programu Visual Studio, która integruje się programu Visual Studio zaawansowane kodu do edycji, wydajności i narzędzia, za pomocą debugowania *Unity*, aparat popularnych Międzyplatformowe gry grafiki i środowisko projektowe dla wciągające aplikacje, których celem, Windows, iOS, Android i innych platform, w tym w sieci web.

 ![Środowisko deweloperskie w narzędziach VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Program Visual Studio Tools for Unity (VSTU) można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy. Najnowsza wersja narzędzi vstu zapewniają obsługę dla aparatu Unity 5 i obejmuje kolorowanie składni języka programu do cieniowania ShaderLab mechanizmu Unity, lepsze synchronizacji za pomocą aparatu Unity, bardziej rozbudowane profilowanie i generowanie kodu ulepszone kreatora MonoBehavior. Narzędzia VSTU także niesie plików projektu środowiska Unity, komunikaty konsoli i możliwości, aby rozpocząć tworzenie gry w programie Visual Studio, dzięki czemu spędzisz mniej czasu przełączanie z edytora środowiska Unity podczas pisania kodu.

 Zacznij tworzyć gry przy użyciu aparatu Unity i programu Visual Studio Tools for Unity już dziś.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier za pomocą programu Visual Studio Unity](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Dowiedz się więcej o programie Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|[Uruchom przy użyciu programu Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|[Przeczytaj najnowsze ulepszenia do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](http://blogs.msdn.com/b/visualstudio/archive/2014/12/03/visual-studio-tools-for-unity-2-0-preview.aspx) (blog Visual Studio)|
|[Obejrzyj wprowadzenie wideo do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej o Unity](http://unity3d.com/) (Unity witryny sieci Web)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie pakietu Office 365 API do projektu programu Visual Studio](http://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](http://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)