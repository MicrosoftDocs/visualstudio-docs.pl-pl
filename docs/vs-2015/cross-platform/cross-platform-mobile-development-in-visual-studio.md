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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302491"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie aplikacji mobilnych na wiele platform w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikacje dla urządzeń z systemem Android, iOS i Windows można tworzyć za pomocą programu Visual Studio.  Podczas projektowania aplikacji użyj narzędzi w programie Visual Studio, aby łatwo dodać połączone usługi, takie jak Office 365, Usługa Azure App Service i Usługa Application Insights.

 Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnij kod, ciągi, obrazy, a w niektórych przypadkach nawet interfejs użytkownika.

 Jeśli chcesz utworzyć grę lub wciągającą aplikację graficzną, zainstaluj narzędzia programu Visual Studio dla unity i ciesz się wszystkimi zaawansowanymi funkcjami produktywności programu Visual Studio za pomocą unity, popularnego międzyplatformowego silnika gier/grafiki i środowiska programistycznego dla aplikacji uruchamianych w systemach iOS, Android, Windows i innych platformach.

 **W tym artykule:**

- [Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)](#NET)

  - [Kierowanie na systemy Android, iOS i Windows z jednej bazy kodu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Docelowe urządzenia z systemem Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)](#HTML)

- [Tworzenie aplikacji dla systemu Android i Windows (C++)](#CPP)

- [Tworzenie gry wieloplatformowej dla systemów Android, iOS i Windows przy użyciu narzędzi programu Visual Studio dla unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)
 ![Urządzenia](../cross-platform/media/homedevices.png "Strona głównaUrządzenia")

 Za pomocą platformy Xamarin możesz kierować reklamy na systemy Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod, a nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie programu Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Dowiedz się więcej o języku Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md) (biblioteka MSDN)|
|[Zarządzanie cyklem życia aplikacji (ALM) z aplikacjami platformy Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (biblioteka MSDN)|
|[Dowiedz się więcej o uniwersalnych aplikacjach systemu Windows w programie Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwach między Swift i C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Dowiedz się więcej o emulatorze programu Visual Studio dla systemu Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Kierowanie na systemy Android, iOS i Windows z jednej bazy kodu
 Aplikacje natywne dla systemów Android, iOS i Windows można tworzyć przy użyciu języka C# lub F# (visual basic nie jest obecnie obsługiwany).  Aby rozpocząć, zainstaluj program Visual Studio 2015, wybierz opcję **Niestandardowa** w instalatorze i zaznacz pole wyboru w obszarze **Cross Platform Mobile Development > C#/.NET (Xamarin)**. Można również rozpocząć od [Instalatora platformy Xamarin](https://www.xamarin.com/download), który jest wymagany do zainstalowania platformy Xamarin dla programu Visual Studio 2013.

 Jeśli masz już zainstalowany program Visual Studio 2015, uruchom instalator z **Panelu sterowania > programy i funkcje** i wybierz tę samą opcję **niestandardową** dla platformy Xamarin, jak powyżej.

 Po zakończeniu szablony projektów są wyświetlane w oknie dialogowym **Nowy projekt.** Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukiwanie na "Xamarin".

 Xamarin udostępnia natywne funkcje android, iOS i Windows jako obiekty .NET. W związku z tym aplikacje mają pełny dostęp do natywnych interfejsów API i natywnych formantów użytkownika i są one tak samo responsywne jak aplikacje napisane w językach platformy natywnej.

 Po utworzeniu projektu, można wykorzystać wszystkie funkcje produktywności programu Visual Studio. Na przykład użyjesz projektanta do tworzenia stron i użyj intellisense do eksplorowania natywnych interfejsów API platform mobilnych. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, możesz użyć emulatora programu Visual Studio dla systemu Android lub emulatora SDK systemu Android, uruchomić aplikacje systemu Windows natywnie lub uruchomić aplikacje systemu Windows na emulatorze systemu Windows Phone. Można również używać bezpośrednio na uwięzi urządzeń z systemem Android i Windows. W przypadku projektów systemu iOS połącz się z komputerem Mac w sieci i uruchom emulator maca w programie Visual Studio lub połącz się z urządzeniem na uwięzi.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jednego zestawu stron renderujących na wszystkich urządzeniach przy użyciu platformy Xamarin.Forms
 W zależności od złożoności projektu aplikacji można rozważyć jego tworzenie przy użyciu szablonów *platformy Xamarin.Forms* w grupie szablonów projektów **aplikacji mobilnych.** Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia utworzenie jednego interfejsu, który można udostępniać w systemach Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin.Forms otrzymasz aplikację dla systemu Android, aplikację dla systemu iOS i aplikację dla systemu Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o rozwoju urządzeń mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Udostępnianie kodu między aplikacjami dla systemów Android, iOS i Windows
 Jeśli nie używasz platformy Xamarin.Forms i wybierz projekt dla każdej platformy indywidualnie, możesz udostępnić większość kodu interfejsu użytkownika między projektami platformy (Android, iOS i Windows). Obejmuje to wszelkie logiki biznesowej, integracji chmury, dostępu do bazy danych lub inny kod, który jest przeznaczony dla programu .NET Framework. Jedynym kodem, który nie można udostępnić jest kod, który jest przeznaczony dla określonej platformy.

 ![Udostępnianie kodu między systemami Windows, iOs i interfejsem użytkownika systemu Android](../cross-platform/media/sharecode.png "Kod akcji")

 Można udostępnić swój kod przy użyciu projektu udostępnionego, projektu biblioteki klas przenośnych lub obu. Może się okazać, że niektóre kod najlepiej pasuje do udostępnionego projektu, a niektóre kod ma większy sens wewnątrz projektu biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|Wybierz, czy kod ma być udostępniany przy użyciu projektów udostępnionych, projektów przenośnej biblioteki klas lub obu tych projektów.<br /><br /> [Udostępnianie kodu na różnych platformach](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog.NET Framework)<br /><br /> [Opcje udostępniania kodu](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Opcje udostępniania kodu za pomocą programu .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (biblioteka MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Docelowe urządzenia z systemem Windows 10
 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "Systemy WindowsDevices")

 Jeśli chcesz utworzyć pojedynczą aplikację, która jest przeznaczona dla całej szerokości urządzeń z systemem Windows 10, utwórz uniwersalną aplikację systemu Windows. Zaprojektujesz aplikację przy użyciu jednego projektu, a twoje strony będą renderowane poprawnie bez względu na to, które urządzenie jest używane do ich wyświetlania.

 Zacznij od uniwersalnego szablonu projektu aplikacji systemu Windows. Projektowaniaj stron wizualnie, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie podoba Ci się sposób, w jaki strona jest wyświetlana na urządzeniu, możesz zoptymalizować stronę, aby lepiej dopasować ją do rozmiaru ekranu, rozdzielczości lub różnych orientacji, takich jak tryb poziomy lub pionowy. Wszystko to można zrobić za pomocą intuicyjnych okien narzędzi i łatwo dostępnych opcji menu w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, znajdziesz wszystkie emulatory urządzeń i symulatory dla różnych typów urządzeń razem w jednej liście rozwijanej, która znajduje się na pasku narzędzi **Standard.**

 Windows 10 jest dość nowy, więc znajdziesz również szablony projektów, które są przeznaczone dla systemu Windows 8.1. Jeśli chcesz, możesz użyć tych szablonów projektów, a aplikacja będzie działać na telefonach, tabletach i komputerach z systemem Windows 10. Jednak wszystkie urządzenia z systemem Windows 8.1 otrzymają automatyczne uaktualnienie do systemu Windows 10, więc jeśli nie masz konkretnych powodów, dla których wolisz kierować system Windows 8.1, zalecamy użycie szablonów projektów kierowanych na system Windows 10.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o uniwersalnych aplikacjach systemu Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Centrum deweloperów systemu Windows)|
|[Zbuduj swój pierwszy](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Centrum deweloperów systemu Windows)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migracja aplikacji na platformę uniwersalną systemu Windows](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)
 ![Urządzenia](../cross-platform/media/homedevices.png "Strona głównaUrządzenia")

 Jeśli jesteś programistą sieci Web i znasz kod HTML i JavaScript, możesz kierować reklamy na systemy Windows, Android i iOS przy użyciu narzędzi programu Visual Studio tools dla apache Cordova. Te aplikacje mogą kierować się na wszystkie trzy platformy i można je tworzyć przy użyciu umiejętności i procesów, które są najbardziej znane.

 Apache Cordova to struktura, która zawiera model wtyczki. Ten model wtyczki udostępnia jeden interfejs API języka JavaScript, którego można użyć, aby uzyskać dostęp do natywnych funkcji urządzeń wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są międzyplatformowe, można udostępnić większość tego, co piszesz między wszystkimi trzema platformami. Zmniejsza to koszty rozwoju i konserwacji. Ponadto, nie ma potrzeby, aby zacząć od zera. Jeśli utworzono inne typy aplikacji internetowych, można udostępnić te pliki aplikacji Cordova bez konieczności modyfikowania lub przeprojektowania ich w jakikolwiek sposób.

 ![Aplikacje hybrydowe wielu urządzeń&#45;](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Aby rozpocząć, zainstaluj program Visual Studio 2015 i wybierz funkcję **HTML/JavaScript (Apache Cordova)** podczas instalacji. Jeśli używasz programu Visual Studio 2013, zainstaluj rozszerzenie Narzędzia programu Visual Studio dla Apache Cordova. Tak czy inaczej, narzędzia Cordova automatycznie instalują wszystkie oprogramowanie innych firm, które jest wymagane do tworzenia aplikacji wieloplatformowej.

 Po zainstalowaniu rozszerzenia otwórz program Visual Studio i utwórz projekt **pustej aplikacji (Apache Cordova).** Następnie możesz tworzyć aplikację przy użyciu języka JavaScript lub Typescript. Można również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji, a interfejsy API z wtyczek są wyświetlane w intellisense podczas pisania kodu.

 Gdy będziesz gotowy do uruchomienia aplikacji i krok po kroku kodu, wybierz emulator, taki jak emulator Apache Ripple lub emulator programu Visual Studio (Android lub Windows Phone), przeglądarka lub urządzenie, które zostały połączone bezpośrednio z komputerem. Następnie uruchom aplikację. Jeśli tworzysz aplikację na komputerze z systemem Windows, możesz ją nawet uruchomić. Wszystkie te opcje są wbudowane w programie Visual Studio jako część narzędzia programu Visual Studio dla Apache Cordova.

 Szablony projektów do tworzenia uniwersalnych aplikacji systemu Windows są nadal dostępne w programie Visual Studio, więc możesz ich używać, jeśli zamierzasz kierować reklamy tylko na urządzenia z systemem Windows. Jeśli zdecydujesz się na kierowanie android i iOS później, zawsze można przenieść kod do projektu Cordova. Istnieją wersje open source interfejsów API WinJS, dzięki czemu można ponownie użyć dowolnego kodu, który zużywa te interfejsy API. Mimo to, jeśli planujesz kierować reklamy na inne platformy w przyszłości, zaleca się rozpoczęcie od narzędzia programu Visual Studio dla Apache Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie programu Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Wprowadzenie do programu Visual Studio Tools for Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Dowiedz się więcej o emulatorze programu Visual Studio dla systemu Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Tworzenie aplikacji dla systemu Android i Windows (C++)
 ![Tworzenie aplikacji dla systemów Android, iOS i Windows za pomocą&#43;&#43; C](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj visual studio 2015 i visual c++ dla wieloplatformowych narzędzi mobilnych programów. Następnie można utworzyć aplikację aktywności natywnej dla systemu Android lub aplikacji przeznaczonej dla systemu Windows. Szablony języka C++ przeznaczone dla systemu iOS nie są jeszcze dostępne. Możesz kierować android i windows w tym samym rozwiązaniu, jeśli chcesz, a następnie udostępnić kod między nimi przy użyciu międzyplatformowej statycznej lub dynamicznej biblioteki udostępnionej.

 Jeśli chcesz utworzyć aplikację dla systemu Android, która wymaga wszelkiego rodzaju zaawansowanej manipulacji grafiką, takiej jak gra, możesz użyć języka C++, aby to zrobić. Rozpocznij od projektu **aplikacji aktywności natywnej (Android).** Ten projekt ma pełne poparcie dla paska narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat-cpp-native.png "Plat_CPP_Native krzyżowe")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, użyj emulatora programu Visual Studio dla systemu Android. Jest szybki, niezawodny i łatwy w instalacji i konfiguracji.

 Można również utworzyć aplikację, która jest przeznaczona dla pełnego zakresu urządzeń z systemem Windows 10 przy użyciu języka C++ i uniwersalnego szablonu projektu aplikacji systemu Windows. Więcej informacji na ten temat można przeczytać w sekcji [Docelowe urządzenia z systemem Windows 10,](#WindowsHTML) która pojawia się wcześniej w tym temacie.

 Kod języka C++ można udostępnić między systemem Android i Windows, tworząc statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki współdzielone](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Można korzystać z tej biblioteki w projekcie systemu Windows lub Android, jak te opisane wcześniej w tej sekcji. Można również używać go w aplikacji, która jest budowana przy użyciu platformy Xamarin, Java, lub dowolnego języka, który pozwala wywołać funkcje w niezarządzanej biblioteki DLL.

 Podczas pisania kodu w tych bibliotekach można użyć intellisense do eksplorowania natywnych interfejsów API platform Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debugerem programu Visual Studio, dzięki czemu można ustawić punkty przerwania, krok po kroku kodu i znaleźć i rozwiązać problemy przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Zainstaluj narzędzia Visual C++ for Cross-Platform Mobile Development.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o używaniu języka C++ do kierowania reklam na wiele platform.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj to, czego potrzebujesz, a następnie utwórz natywną aplikację aktywności dla systemu Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Biblioteka MSDN)|
|[Dowiedz się więcej o emulatorze programu Visual Studio dla systemu Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Dowiedz się więcej o udostępnianiu kodu W++ za pomocą aplikacji na Androida i Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Międzyplatformowe przykłady rozwoju urządzeń mobilnych dla języka C++](https://msdn.microsoft.com/library/dn707596.aspx) (biblioteka MSDN)|
|[Dodatkowe przykłady rozwoju mobilnego na różnych platformach dla języka C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a>Tworzenie gry wieloplatformowej dla systemów Android, iOS i Windows przy użyciu narzędzi programu Visual Studio dla unity
 Visual Studio Tools for Unity to bezpłatne rozszerzenie dla programu Visual Studio, które integruje zaawansowane narzędzia do edycji kodu, produktywności i debugowania programu Visual Studio z *unity*, popularnym międzyplatformowym aparatem gier/grafiki i środowiskiem programistycznym dla wciągających aplikacji przeznaczonych dla systemów Windows, iOS, Android i innych platform, w tym sieci Web.

 ![Środowisko programistyczne VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Za pomocą programu Visual Studio Tools for Unity (VSTU) można używać programu Visual Studio do pisania skryptów gier i edytorów w języku C#, a następnie używać zaawansowanego debugera do znajdowania i naprawiania błędów. Najnowsza wersja vstu zapewnia obsługę Unity 5 i zawiera kolorowanie składni dla języka shaderlab unity, lepszą synchronizację z Unity, bogatsze debugowanie i ulepszone generowanie kodu dla kreatora MonoBehavior. VSTU przynosi również pliki projektu Unity, komunikaty konsoli i możliwość uruchomienia gry w programie Visual Studio, dzięki czemu można spędzić mniej czasu przełączania do iz Edytora Unity podczas pisania kodu.

 Zacznij budować grę za pomocą Unity i Visual Studio Tools for Unity już dziś.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier Unity za pomocą programu Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Dowiedz się więcej o narzędziach programu Visual Studio dla unity](../cross-platform/visual-studio-tools-for-unity.md) (biblioteka MSDN)|
|[Rozpoczynanie korzystania z narzędzi programu Visual Studio tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (biblioteka MSDN)|
|[Przeczytaj o najnowszych ulepszeniach narzędzi programu Visual Studio dla unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog programu Visual Studio)|
|[Obejrzyj wprowadzenie do klipu wideo z narzędziami programu Visual Studio dla unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej o Unity](https://unity.com/) (unity stronie)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie interfejsu API usługi Office 365 do projektu programu Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
