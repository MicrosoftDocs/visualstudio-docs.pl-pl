---
title: Programowanie aplikacji mobilnych na wiele platform w programie Visual Studio | Microsoft Docs
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
ms.openlocfilehash: eea38f8109069f6d6526b2ccb920565f09b98043
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535674"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Programowanie aplikacji mobilnych na wiele platform w programie Visual Studio

Możesz tworzyć aplikacje dla urządzeń z systemami Android, iOS i Windows za pomocą programu Visual Studio.  Podczas projektowania aplikacji użyj narzędzi w programie Visual Studio, aby łatwo dodawać połączone usługi, takie jak Office 365, Azure App Service i Application Insights.

Twórz aplikacje, korzystając C# z .NET Framework, HTML i JavaScript lub. C++ Udostępniaj kod, ciągi, obrazy i w niektórych przypadkach nawet w interfejsie użytkownika.

Jeśli chcesz skompilować grę lub aplikację, możesz zainstalować narzędzia Visual Studio Tools for Unity i korzystać ze wszystkich zaawansowanych funkcji produktywności programu Visual Studio z systemem Unity, popularnego aparatu gier/grafiki dla wielu platform i środowiska programistycznego dla aplikacji, które działa w systemach iOS, Android, Windows i innych platformach.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)

![Urządzeniem](../cross-platform/media/homedevices.png "HomeDevices")

Za pomocą Visual Studio Tools dla platformy Xamarin można docelowo dla systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod i nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Informacje o programie Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentacja dotycząca tworzenia aplikacji mobilnych dla oprogramowania Xamarin](/xamarin/) |
|[DevOps z aplikacjami platformy Xamarin](/xamarin/tools/ci/devops/) |
|[Poznaj aplikacje uniwersalne systemu Windows w programie Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwach SWIFT C# i](https://aka.ms/scposter) (Download.Microsoft.com)|

### <a name="AndroidHTML"></a>Docelowa wersja systemu Android, iOS i Windows z pojedynczej bazy kodu

 Możesz tworzyć natywne aplikacje dla systemów Android, iOS i Windows za pomocą C# programu F# lub (Visual Basic nie jest to obsługiwane w tej chwili).  Aby rozpocząć, zainstaluj program Visual Studio 2017, wybierz opcję **Programowanie aplikacji mobilnych przy użyciu platformy .NET** w instalatorze.

 Jeśli masz już zainstalowany program Visual Studio 2017, uruchom ponownie **Instalator programu Visual Studio** i wybierz opcję **Programowanie aplikacji mobilnych przy użyciu opcji .NET dla platformy** Xamarin (jak powyżej).

 Gdy skończysz, szablony projektu są wyświetlane w oknie dialogowym **Nowy projekt** . Najprostszym sposobem znalezienia szablonów platformy Xamarin jest przeszukanie "Xamarin".

 Platforma Xamarin udostępnia natywne funkcje systemu Android, iOS i Windows jako klasy i metody platformy .NET. Oznacza to, że aplikacje mają pełny dostęp do natywnych interfejsów API i natywnych kontrolek i są równie zgodne z aplikacjami zapisanymi w natywnych językach platformy.

 Po utworzeniu projektu będzie można korzystać ze wszystkich funkcji produktywności programu Visual Studio. Na przykład użyjesz projektanta do tworzenia stron i korzystaj z technologii IntelliSense do eksplorowania natywnych interfejsów API platformy mobilnej. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, możesz użyć emulatora Android SDK i natywnie uruchamiać aplikacje systemu Windows. Można również bezpośrednio korzystać z urządzeń z systemem Android i Windows. W przypadku projektów systemu iOS należy nawiązać połączenie z siecią komputerową Mac i uruchomić emulator systemu iOS z programu Visual Studio lub połączyć się z urządzeniem z tetheringem.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jednego zestawu stron, który jest renderowany na wszystkich urządzeniach przy użyciu platformy Xamarin. Forms

 W zależności od złożoności projektu aplikacji można rozważyć skompilowanie go przy użyciu szablonów *Xamarin. Forms* w grupie **Mobile Apps** szablonów projektu. Xamarin. Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, który można udostępnić w systemach Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin. Forms uzyskasz aplikację dla systemu Android, aplikację dla systemu iOS i aplikację systemu Windows. Aby uzyskać więcej informacji, zobacz informacje [o tworzeniu aplikacji mobilnych za pomocą platformy Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) i [dokumentacji platformy Xamarin. Forms](/xamarin/xamarin-forms/).

#### <a name="ShareHTML"></a>Udostępnianie kodu między aplikacjami dla systemów Android, iOS i Windows

 Jeśli nie korzystasz z programu Xamarin. Forms i chcesz projektować dla każdej platformy osobno, możesz udostępnić większość kodu innego niż interfejs użytkownika między projektami platformy (Android, iOS i Windows). Obejmuje to każdą logikę biznesową, integrację z chmurą, dostęp do bazy danych lub inny kod, który jest przeznaczony dla .NET Framework. Jedyny kod, którego nie można udostępnić, to kod, który jest przeznaczony dla konkretnej platformy.

 ![Udostępnianie kodu między systemami Windows, iOs i Android](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępnić kod przy użyciu projektu udostępnionego, projektu biblioteki klas przenośnych lub obu tych metod. Może się okazać, że jakiś kod pasuje do najlepszego w projekcie udostępnionym, a jakiś kod staje się bardziej zrozumiały w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Udostępnianie opcji kodu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opcje udostępniania kodu w programie .NET](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a>Docelowe urządzenia z systemem Windows 10

 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "Urządzenia z systemem Windows")

 Jeśli chcesz utworzyć pojedynczą aplikację, która jest przeznaczona dla wszystkich urządzeń z systemem Windows 10, Utwórz aplikację uniwersalną systemu Windows. Aplikacja zostanie zaprojektowana przy użyciu pojedynczego projektu, a strony będą renderowane prawidłowo, niezależnie od tego, jakie urządzenie jest używane do ich wyświetlania.

 Zacznij od szablonu projektu aplikacji platforma uniwersalna systemu Windows (platformy UWP). Zaprojektuj strony wizualnie, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie chcesz, aby strona została wyświetlona na urządzeniu, możesz zoptymalizować ją, aby lepiej odpowiadała rozmiarowi ekranu, rozdzielczości lub różnym orientacjom, takim jak orientacja pozioma lub pionowa. Wszystkie te możliwości można wykonać za pomocą intuicyjnych okien narzędzi i łatwo dostępnych opcji menu w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, znajdziesz wszystkie emulatory urządzeń i symulatory dla różnych typów urządzeń razem w jednej liście rozwijanej, która znajduje się na pasku narzędzi **Standardowy** .

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji do platforma uniwersalna systemu Windows (platformy UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)

 ![Urządzenia z systemami Windows, iOS i Android](../cross-platform/media/homedevices.png "Urządzenia z systemami Windows, iOS i Android")

 Jeśli jesteś deweloperem sieci Web i znasz język HTML i JavaScript, możesz użyć systemu Windows, Android i iOS za pomocą Visual Studio Tools Apache Cordova. Te aplikacje mogą być przeznaczone dla wszystkich trzech platform i można je kompilować przy użyciu umiejętności i procesów, które są najbardziej znane.

 Apache Cordova to struktura, która zawiera model wtyczki. Ten model wtyczek udostępnia jeden interfejs API języka JavaScript, za pomocą którego można uzyskać dostęp do natywnych możliwości urządzenia wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są Międzyplatformowe, można udostępnić większość operacji zapisu między wszystkimi trzema platformami. Zmniejsza to koszty związane z programowaniem i konserwacją. Nie trzeba również zaczynać od zera. Jeśli zostały utworzone inne typy aplikacji sieci Web, możesz udostępnić te pliki w aplikacji Cordova bez konieczności modyfikowania lub zmiany ich projektu w dowolny sposób.

 ![Aplikacje hybrydowe dla urządzeń z obsługą języka JavaScript](../cross-platform/media/multidevicehybridapps.png "Aplikacje hybrydowe dla urządzeń z obsługą języka JavaScript")

 Aby rozpocząć, zainstaluj program Visual Studio i wybierz funkcję **Programowanie aplikacji mobilnych za pomocą języka JavaScript** podczas instalacji. Narzędzia oprogramowania Cordova automatycznie instalują całe oprogramowanie innych firm wymagane do tworzenia aplikacji dla wielu platform.

 Po zainstalowaniu rozszerzenia Otwórz program Visual Studio i Utwórz **pusty projekt aplikacji (Apache Cordova)** . Następnie możesz opracowywać aplikację przy użyciu języka JavaScript lub TypeScript. Możesz również dodać wtyczki, aby zwiększyć funkcjonalność aplikacji, a interfejsy API z wtyczek pojawiają się w IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, wybierz emulator, taki jak emulator Apache Ripple lub Emulator systemu Android, przeglądarka lub urządzenie podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli tworzysz aplikację na komputerze z systemem Windows, możesz nawet uruchomić ją na tym urządzeniu. Wszystkie te opcje są wbudowane w program Visual Studio jako część Visual Studio Tools Apache Cordova.

 Szablony projektów służące do tworzenia aplikacji platforma uniwersalna systemu Windows (platformy UWP) są nadal dostępne w programie Visual Studio, dzięki czemu mogą być używane w przypadku planowania tylko urządzeń z systemem Windows. Jeśli zdecydujesz się na późniejsze ukierunkowanie urządzeń z systemem Android i iOS, zawsze możesz przenieść kod do projektu Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Wprowadzenie do Visual Studio Tools dla Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Dowiedz się więcej o programie Visual Studio Emulator for Android](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-and-windows-c"></a>Tworzenie aplikacji dla systemów Android i Windows (C++)
 ![Używanie języka&#43; &#43; C do kompilowania dla systemów Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio 2017 i **Programowanie aplikacji mobilnych za C++ pomocą** obciążenia. Następnie można utworzyć natywną aplikację działania dla systemu Android lub aplikację, która jest przeznaczona dla systemu Windows. C++Szablony przeznaczone dla systemu iOS nie są jeszcze dostępne. W razie potrzeby możesz wybrać systemy Android i Windows w tym samym rozwiązaniu, a następnie udostępnić kod między nimi przy użyciu statycznej lub dynamicznej biblioteki udostępnionej dla wielu platform.

 Jeśli konieczne jest skompilowanie aplikacji dla systemu Android, która wymaga dowolnego rodzaju zaawansowanego manipulowania grafiki, takiego jak gra, można użyć C++ w tym celu. Zacznij od projektu **aplikacji native-activity (Android)** . Ten projekt ma pełną obsługę Clang łańcucha narzędzi.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "Szablon projektu działania natywnego")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, użyj Emulator systemu Android. Jest to szybkie, niezawodne i łatwe do zainstalowania i skonfigurowania.

 Możesz również utworzyć aplikację, która jest przeznaczona dla pełnej szerokości urządzeń z systemem Windows 10 przy C++ użyciu szablonu projektu aplikacji platforma uniwersalna systemu Windows (platformy UWP). Więcej informacji na ten temat znajduje się w sekcji [docelowe urządzenia z systemem Windows 10](#WindowsHTML) , która występuje wcześniej w tym temacie.

 Aby udostępnić C++ kod między systemami Android i Windows, można utworzyć statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki udostępnione](../cross-platform/media/cross_plat_cpp_libraries.png "Statyczne i dynamiczne biblioteki udostępnione")

 Tej biblioteki można użyć w projekcie systemu Windows lub Android, jak opisano wcześniej w tej sekcji. Można go również użyć w aplikacji, którą tworzysz przy użyciu platformy Xamarin, Java lub dowolnego języka, który umożliwia wywoływanie funkcji w niezarządzanej bibliotece DLL.

 Podczas pisania kodu w tych bibliotekach można użyć funkcji IntelliSense do eksplorowania natywnych interfejsów API platformy Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debugerem programu Visual Studio, dzięki czemu można ustawiać punkty przerwania, przechodzić przez kod i znajdować i rozwiązywać problemy przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Zainstaluj wizualizację C++ dla wieloplatformowych narzędzi programistycznych dla aplikacji mobilnych.](https://msdn.microsoft.com/library/dn707591.aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej C++ o używaniu programu w celu kierowania wielu platform.](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj to, czego potrzebujesz, a następnie utwórz natywną aplikację działania dla systemu Android](https://msdn.microsoft.com/library/dn707595.aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej C++ o udostępnianiu kodu w aplikacjach dla systemów Android i Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Przykłady tworzenia aplikacji mobilnych dla wielu platform C++ dla programu](https://msdn.microsoft.com/library/dn707596.aspx) (Biblioteka MSDN)|
|[Dodatkowe przykłady tworzenia aplikacji mobilnych dla wielu platform C++ dla programu](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code. MSDN)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Tworzenie wieloplatformowej gry dla systemów Android, iOS i Windows przy użyciu narzędzi Visual Studio Tools for Unity

 Visual Studio Tools for Unity to bezpłatne rozszerzenie programu Visual Studio, które integruje zaawansowane narzędzia do edycji kodu, produktywności i debugowania w programie Visual Studio za pomocą *aparatu Unity*, popularne aparaty gier/grafiki dla wielu platform oraz środowisko programistyczne dla aplikacji immersyjny przeznaczonych dla systemu Windows, iOS, Android i innych platform, w tym sieci Web.

 ![Środowisko deweloperskie rozszerzenia VSTU](../cross-platform/media/vstu_overview.png "Przegląd Visual Studio Tools for Unity")

 Za pomocą Visual Studio Tools for Unity (rozszerzenia VSTU) można używać programu Visual Studio do zapisywania skryptów gier i edytorów C# w programie, a następnie używać swojego zaawansowanego debugera do znajdowania i naprawiania błędów. Najnowsza wersja programu rozszerzenia VSTU obsługuje środowisko Unity 2018,1 i oferuje kolorowanie składni dla języka modułu cieniującego ShaderLab w środowisku Unity, lepszą synchronizację z technologią Unity, bogatsze debugowanie i ulepszone generowanie kodu dla Kreatora działania. ROZSZERZENIA VSTU również udostępnia pliki projektu Unity, komunikaty konsoli i możliwość uruchamiania gry w programie Visual Studio, dzięki czemu można poświęcać mniej czasu na przełączanie do i z edytora Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier Unity w programie Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Przeczytaj więcej na temat Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Zacznij korzystać z Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|Zapoznaj się z [najnowszymi ulepszeniami w wersji Zapoznawczej Visual Studio Tools for Unity 2,0](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog programu Visual Studio)|
|[Obejrzyj film wideo z wprowadzeniem do wersji Zapoznawczej Visual Studio Tools for Unity 2,0](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej na temat aparatu Unity](http://unity3d.com/) (witryna sieci Web Unity)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie interfejsów API pakietu Office 365 do projektu programu Visual Studio](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [App Services platformy Azure — Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)
