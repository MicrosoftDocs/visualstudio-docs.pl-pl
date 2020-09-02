---
title: Programowanie mobilnych aplikacji międzyplatformowych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312759"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie aplikacji mobilnych na wiele platform w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz tworzyć aplikacje dla urządzeń z systemami Android, iOS i Windows za pomocą programu Visual Studio.  Podczas projektowania aplikacji użyj narzędzi w programie Visual Studio, aby łatwo dodawać połączone usługi, takie jak Office 365, Azure App Service i Application Insights.

 Twórz aplikacje przy użyciu języka C# oraz .NET Framework, HTML i JavaScript lub C++. Udostępniaj kod, ciągi, obrazy i w niektórych przypadkach nawet w interfejsie użytkownika.

 Jeśli chcesz skompilować grę lub aplikację, możesz zainstalować narzędzia Visual Studio Tools for Unity i korzystać ze wszystkich zaawansowanych funkcji produktywności programu Visual Studio z systemem Unity, popularnego aparatu gier/grafiki dla wielu platform i środowiska programistycznego dla aplikacji działających w systemach iOS, Android, Windows i innych platformach.

 **W tym artykule:**

- [Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)](#NET)

  - [Docelowa wersja systemu Android, iOS i Windows z pojedynczej bazy kodu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Docelowe urządzenia z systemem Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)](#HTML)

- [Tworzenie aplikacji dla systemów Android i Windows (C++)](#CPP)

- [Tworzenie wieloplatformowej gry dla systemów Android, iOS i Windows przy użyciu narzędzi Visual Studio Tools for Unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Za pomocą platformy Xamarin można docelowo dla systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod i nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Informacje o programie Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Biblioteka MSDN)|
|[Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji platformy Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Biblioteka MSDN)|
|[Poznaj aplikacje uniwersalne systemu Windows w programie Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwach SWIFT i C#](https://aka.ms/scposter) (Download.Microsoft.com)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Docelowa wersja systemu Android, iOS i Windows z pojedynczej bazy kodu
 Możesz tworzyć natywne aplikacje dla systemów Android, iOS i Windows przy użyciu języka C# lub F # (Visual Basic nie jest to obsługiwane w tej chwili).  Aby rozpocząć, zainstaluj program Visual Studio 2015, wybierz opcję **niestandardowa** w instalatorze, a następnie zaznacz pole wyboru w obszarze **Programowanie aplikacji mobilnych na wiele platform > C#/.NET (Xamarin)**. Możesz również rozpocząć od [Instalatora Xamarin](https://www.xamarin.com/download), który jest wymagany do zainstalowania programu xamarin dla Visual Studio 2013.

 Jeśli masz już zainstalowany program Visual Studio 2015, uruchom Instalatora z **Panelu sterowania > programy i funkcje** , a następnie wybierz tę samą opcję **niestandardową** dla platformy Xamarin, tak jak powyżej.

 Gdy skończysz, szablony projektu są wyświetlane w oknie dialogowym **Nowy projekt** . Najprostszym sposobem znalezienia szablonów platformy Xamarin jest przeszukanie "Xamarin".

 Platforma Xamarin udostępnia natywne funkcje systemu Android, iOS i Windows jako obiekty .NET. W ten sposób aplikacje mają pełny dostęp do natywnych interfejsów API i natywnych kontrolek użytkownika, a także są tak samo, jak aplikacje utworzone w natywnych językach platformy.

 Po utworzeniu projektu będzie można korzystać ze wszystkich funkcji produktywności programu Visual Studio. Na przykład użyjesz projektanta do tworzenia stron i korzystaj z technologii IntelliSense do eksplorowania natywnych interfejsów API platformy mobilnej. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, możesz użyć emulatora programu Visual Studio dla systemu Android lub emulatora Android SDK, uruchamiać aplikacje systemu Windows w sposób natywny lub uruchamiać aplikacje systemu Windows na emulatorze Windows Phone. Można również bezpośrednio korzystać z urządzeń z systemem Android i Windows. W przypadku projektów systemu iOS należy nawiązać połączenie z siecią komputerową Mac i uruchomić emulator Mac z programu Visual Studio lub połączyć się z urządzeniem z tetheringem.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jednego zestawu stron, który jest renderowany na wszystkich urządzeniach przy użyciu platformy Xamarin. Forms
 W zależności od złożoności projektu aplikacji można rozważyć skompilowanie go przy użyciu szablonów *Xamarin. Forms* w grupie **Mobile Apps** szablonów projektu. Xamarin. Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, który można udostępnić w systemach Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin. Forms uzyskasz aplikację dla systemu Android, aplikację dla systemu iOS i aplikację systemu Windows. Aby uzyskać więcej informacji, zobacz [Informacje o tworzeniu aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Udostępnianie kodu między aplikacjami dla systemów Android, iOS i Windows
 Jeśli nie korzystasz z programu Xamarin. Forms i chcesz projektować dla każdej platformy osobno, możesz udostępnić większość kodu innego niż interfejs użytkownika między projektami platformy (Android, iOS i Windows). Obejmuje to każdą logikę biznesową, integrację z chmurą, dostęp do bazy danych lub inny kod, który jest przeznaczony dla .NET Framework. Jedyny kod, którego nie można udostępnić, to kod, który jest przeznaczony dla konkretnej platformy.

 ![Udostępnianie kodu między systemami Windows, iOs i Android](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępnić kod przy użyciu projektu udostępnionego, projektu biblioteki klas przenośnych lub obu tych metod. Może się okazać, że jakiś kod pasuje do najlepszego w projekcie udostępnionym, a jakiś kod staje się bardziej zrozumiały w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|Zdecyduj, czy kod ma być współużytkowany przy użyciu projektów udostępnionych, projektów biblioteki klas przenośnych lub obu.<br /><br /> [Udostępnianie kodu na wielu platformach](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog .NET Framework)<br /><br /> [Udostępnianie opcji kodu](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Opcje udostępniania kodu z .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (Biblioteka MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Docelowe urządzenia z systemem Windows 10
 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Jeśli chcesz utworzyć pojedynczą aplikację, która jest przeznaczona dla wszystkich urządzeń z systemem Windows 10, Utwórz aplikację uniwersalną systemu Windows. Aplikacja zostanie zaprojektowana przy użyciu pojedynczego projektu, a strony będą renderowane prawidłowo, niezależnie od tego, jakie urządzenie jest używane do ich wyświetlania.

 Zacznij od szablonu projektu uniwersalnej aplikacji systemu Windows. Zaprojektuj strony wizualnie, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie chcesz, aby strona została wyświetlona na urządzeniu, możesz zoptymalizować ją, aby lepiej odpowiadała rozmiarowi ekranu, rozdzielczości lub różnym orientacjom, takim jak orientacja pozioma lub pionowa. Wszystkie te możliwości można wykonać za pomocą intuicyjnych okien narzędzi i łatwo dostępnych opcji menu w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, znajdziesz wszystkie emulatory urządzeń i symulatory dla różnych typów urządzeń razem w jednej liście rozwijanej, która znajduje się na pasku narzędzi **Standardowy** .

 System Windows 10 jest dość nowy, więc znajdziesz również szablony projektu, które są przeznaczone Windows 8.1. Możesz użyć tych szablonów projektu, jeśli chcesz, a aplikacja będzie działać na telefonach, tabletach i komputerach z systemem Windows 10. Jednak wszystkie urządzenia, na których działa Windows 8.1, otrzymają automatyczne uaktualnienie do systemu Windows 10, dlatego jeśli Windows 8.1 nie masz określonych powodów, dla których wolisz, należy korzystać z szablonów projektu przeznaczonych dla systemu Windows 10.

|**Dowiedz się więcej**|
|--------------------|
|[Poznaj aplikacje uniwersalne systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Centrum deweloperów systemu Windows)|
|[Kompiluj swój pierwszy](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Centrum deweloperów systemu Windows)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migracja aplikacji na platformę uniwersalną systemu Windows](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)
 ![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

 Jeśli jesteś deweloperem sieci Web i znasz język HTML i JavaScript, możesz użyć systemu Windows, Android i iOS za pomocą Visual Studio Tools Apache Cordova. Te aplikacje mogą być przeznaczone dla wszystkich trzech platform i można je kompilować przy użyciu umiejętności i procesów, które są najbardziej znane.

 Apache Cordova to struktura, która zawiera model wtyczki. Ten model wtyczek udostępnia jeden interfejs API języka JavaScript, za pomocą którego można uzyskać dostęp do natywnych możliwości urządzenia wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są Międzyplatformowe, można udostępnić większość operacji zapisu między wszystkimi trzema platformami. Zmniejsza to koszty związane z programowaniem i konserwacją. Nie trzeba również zaczynać od zera. Jeśli zostały utworzone inne typy aplikacji sieci Web, możesz udostępnić te pliki w aplikacji Cordova bez konieczności modyfikowania lub zmiany ich projektu w dowolny sposób.

 ![Aplikacje hybrydowe dla wiele&#45;urządzeń](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Aby rozpocząć, zainstaluj program Visual Studio 2015 i wybierz funkcję **HTML/JavaScript (Apache Cordova)** podczas instalacji. Jeśli używasz Visual Studio 2013, zainstaluj Visual Studio Tools rozszerzenia Apache Cordova. W obu przypadkach narzędzia oprogramowania Cordova automatycznie instalują całe oprogramowanie innych firm wymagane do utworzenia aplikacji wieloplatformowej.

 Po zainstalowaniu rozszerzenia Otwórz program Visual Studio i Utwórz **pusty projekt aplikacji (Apache Cordova)** . Następnie możesz opracowywać aplikację przy użyciu języka JavaScript lub TypeScript. Możesz również dodać wtyczki, aby zwiększyć funkcjonalność aplikacji, a interfejsy API z wtyczek pojawiają się w IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, wybierz emulator, taki jak emulator Apache Ripple lub Emulator programu Visual Studio (Android lub Windows Phone), przeglądarka lub urządzenie podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli tworzysz aplikację na komputerze z systemem Windows, możesz nawet uruchomić ją na tym urządzeniu. Wszystkie te opcje są wbudowane w program Visual Studio jako część Visual Studio Tools Apache Cordova.

 Szablony projektów służące do tworzenia aplikacji uniwersalnych systemu Windows są nadal dostępne w programie Visual Studio, dzięki czemu mogą być używane w przypadku planowania tylko urządzeń z systemem Windows. Jeśli zdecydujesz się na późniejsze ukierunkowanie urządzeń z systemem Android i iOS, zawsze możesz przenieść kod do projektu Cordova. Istnieją wersje interfejsów API WinJS typu open source, dzięki czemu można ponownie użyć dowolnego kodu, który korzysta z tych interfejsów API. Że jeśli planujesz kierowanie innych platform w przyszłości, zalecamy rozpoczęcie od Visual Studio Tools Apache Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Wprowadzenie do Visual Studio Tools dla Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (Taco.VisualStudio.com)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a> Tworzenie aplikacji dla systemów Android i Windows (C++)
 ![Używanie języka C&#43;&#43; do kompilowania dla systemów Android, iOS i Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio 2015 i Visual C++ dla wieloplatformowych narzędzi programistycznych dla aplikacji mobilnych. Następnie można utworzyć natywną aplikację działania dla systemu Android lub aplikację, która jest przeznaczona dla systemu Windows. Szablony języka C++, które są przeznaczone dla systemu iOS, nie są jeszcze dostępne. W razie potrzeby możesz wybrać systemy Android i Windows w tym samym rozwiązaniu, a następnie udostępnić kod między nimi przy użyciu statycznej lub dynamicznej biblioteki udostępnionej dla wielu platform.

 Jeśli musisz utworzyć aplikację dla systemu Android, która wymaga dowolnego sortowania zaawansowanego manipulowania grafiki, takiego jak gra, możesz to zrobić przy użyciu języka C++. Zacznij od projektu **aplikacji native-activity (Android)** . Ten projekt ma pełną obsługę Clang łańcucha narzędzi.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat-cpp-native.png "Plat_CPP_Native krzyżowe")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, użyj programu Visual Studio Emulator for Android. Jest to szybkie, niezawodne i łatwe do zainstalowania i skonfigurowania.

 Możesz również utworzyć aplikację, która jest przeznaczona dla wszystkich urządzeń z systemem Windows 10 przy użyciu języka C++ i szablonu projektu uniwersalnej aplikacji systemu Windows. Więcej informacji na ten temat znajduje się w sekcji [docelowe urządzenia z systemem Windows 10](#WindowsHTML) , która występuje wcześniej w tym temacie.

 Kod C++ można udostępnić między systemami Android i Windows, tworząc statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki udostępnione](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Tej biblioteki można użyć w projekcie systemu Windows lub Android, jak opisano wcześniej w tej sekcji. Można go również użyć w aplikacji, którą tworzysz przy użyciu platformy Xamarin, Java lub dowolnego języka, który umożliwia wywoływanie funkcji w niezarządzanej bibliotece DLL.

 Podczas pisania kodu w tych bibliotekach można użyć funkcji IntelliSense do eksplorowania natywnych interfejsów API platformy Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debugerem programu Visual Studio, dzięki czemu można ustawiać punkty przerwania, przechodzić przez kod i znajdować i rozwiązywać problemy przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Zainstaluj narzędzia Visual C++ dla opracowywania aplikacji mobilnych na wiele platform.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o używaniu języka C++ w celu kierowania wielu platform.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj to, czego potrzebujesz, a następnie utwórz natywną aplikację działania dla systemu Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Dowiedz się więcej o udostępnianiu kodu C++ za pomocą aplikacji dla systemów Android i Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Przykłady tworzenia aplikacji mobilnych dla wielu platform w języku C++](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Dodatkowe przykłady tworzenia aplikacji mobilnych dla wielu platform w języku C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code. MSDN)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a> Tworzenie wieloplatformowej gry dla systemów Android, iOS i Windows przy użyciu narzędzi Visual Studio Tools for Unity
 Visual Studio Tools for Unity to bezpłatne rozszerzenie programu Visual Studio, które integruje zaawansowane narzędzia do edycji kodu, produktywności i debugowania w programie Visual Studio za pomocą *aparatu Unity*, popularne aparaty do gier/grafiki dla wielu platform oraz środowisko programistyczne dla aplikacji w sieci Web przeznaczonych dla systemu Windows, iOS, Android i innych platform, w tym dla Internetu.

 ![Środowisko deweloperskie rozszerzenia VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Za pomocą Visual Studio Tools for Unity (rozszerzenia VSTU) można używać programu Visual Studio do zapisywania skryptów gier i edytorów w języku C#, a następnie używać swojego zaawansowanego debugera do znajdowania i naprawiania błędów. Najnowsza wersja programu rozszerzenia VSTU obsługuje środowisko Unity 5 i zawiera kolorowanie składni dla języka modułu cieniującego ShaderLab w środowisku Unity, lepszą synchronizację z technologią Unity, bogatsze debugowanie i ulepszone generowanie kodu dla Kreatora działania. ROZSZERZENIA VSTU również udostępnia pliki projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, dzięki czemu można poświęcać mniej czasu na przełączanie do i z edytora Unity podczas pisania kodu.

 Zacznij tworzyć grę z użyciem aparatu Unity i Visual Studio Tools for Unity już dzisiaj.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier Unity w programie Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Przeczytaj więcej na temat Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|[Zacznij korzystać z Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (Biblioteka MSDN)|
|Zapoznaj się z [najnowszymi ulepszeniami w wersji Zapoznawczej Visual Studio Tools for Unity 2,0](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog programu Visual Studio)|
|[Obejrzyj film wideo z wprowadzeniem do wersji Zapoznawczej Visual Studio Tools for Unity 2,0](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej na temat aparatu Unity](https://unity.com/) (witryna sieci Web Unity)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie interfejsu API pakietu Office 365 do projektu programu Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
