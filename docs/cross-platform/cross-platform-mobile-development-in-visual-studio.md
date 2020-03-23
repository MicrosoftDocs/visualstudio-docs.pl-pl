---
title: Wieloplatformowy rozwój mobilny w programie Visual Studio | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: c7f40f656b533949748a7eb2ab88ea3d2b1d5923
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234985"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Tworzenie urządzeń mobilnych na różnych platformach w programie Visual Studio

Aplikacje dla urządzeń z systemem Android, iOS i Windows można tworzyć za pomocą programu Visual Studio.  Podczas projektowania aplikacji użyj narzędzi w programie Visual Studio, aby łatwo dodać połączone usługi, takie jak Office 365, Usługa Azure App Service i Usługa Application Insights.

Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnij kod, ciągi, obrazy, a w niektórych przypadkach nawet interfejs użytkownika.

Jeśli chcesz utworzyć grę lub wciągającą aplikację graficzną, zainstaluj narzędzia programu Visual Studio dla unity i ciesz się wszystkimi zaawansowanymi funkcjami produktywności programu Visual Studio za pomocą unity, popularnego międzyplatformowego silnika gier/grafiki i środowiska programistycznego dla aplikacji uruchamianych w systemach iOS, Android, Windows i innych platformach.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)

![Urządzenia](../cross-platform/media/homedevices.png "Strona głównaUrządzenia")

Za pomocą narzędzia programu Visual Studio Tools for Xamarin można kierować na systemy Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod, a nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie programu Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Dowiedz się więcej o języku Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentacja tworzenia aplikacji mobilnych platformy Xamarin](/xamarin/) |
|[Metodyka DevOps z użyciem platformy Xamarin](/xamarin/tools/ci/devops/) |
|[Dowiedz się więcej o uniwersalnych aplikacjach systemu Windows w programie Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwach między Swift i C#](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Kierowanie na systemy Android, iOS i Windows z jednej bazy kodu

 Aplikacje natywne dla systemów Android, iOS i Windows można tworzyć przy użyciu języka C# lub F# (visual basic nie jest obecnie obsługiwany).  Aby rozpocząć, zainstaluj program Visual Studio, wybierz opcję **Mobile Development z programem .NET** w instalatorze.

 Jeśli masz już zainstalowany program Visual Studio, uruchom ponownie **Instalator programu Visual Studio** i wybierz ten sam program mobile development z opcją **.NET** dla platformy Xamarin (jak wyżej).

 Po zakończeniu szablony projektów są wyświetlane w oknie dialogowym **Nowy projekt.** Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukiwanie na "Xamarin".

 Xamarin udostępnia natywne funkcje systemów Android, iOS i Windows jako klasy i metody .NET. Oznacza to, że aplikacje mają pełny dostęp do natywnych interfejsów API i natywnych formantów i są tak samo responsywne jak aplikacje napisane w językach platformy natywnej.

 Po utworzeniu projektu, można wykorzystać wszystkie funkcje produktywności programu Visual Studio. Na przykład użyjesz projektanta do tworzenia stron i użyj intellisense do eksplorowania natywnych interfejsów API platform mobilnych. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, możesz użyć emulatora SDK systemu Android i uruchomić aplikacje systemu Windows natywnie. Można również używać bezpośrednio na uwięzi urządzeń z systemem Android i Windows. W przypadku projektów systemu iOS połącz się z komputerem Mac w sieci i uruchom emulator systemu iOS w programie Visual Studio lub połącz się z urządzeniem na uwięzi.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jednego zestawu stron renderujących na wszystkich urządzeniach przy użyciu platformy Xamarin.Forms

 W zależności od złożoności projektu aplikacji można rozważyć jego tworzenie przy użyciu szablonów *platformy Xamarin.Forms* w grupie szablonów projektów **aplikacji mobilnych.** Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia utworzenie jednego interfejsu, który można udostępniać w systemach Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin.Forms otrzymasz aplikację dla systemu Android, aplikację dla systemu iOS i aplikację dla systemu Windows. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o rozwoju urządzeń przenośnych za pomocą platformy Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) i [dokumentacji platformy Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Udostępnianie kodu między aplikacjami dla systemów Android, iOS i Windows

 Jeśli nie używasz platformy Xamarin.Forms i wybierz projekt dla każdej platformy indywidualnie, możesz udostępnić większość kodu interfejsu użytkownika między projektami platformy (Android, iOS i Windows). Obejmuje to wszelkie logiki biznesowej, integracji chmury, dostępu do bazy danych lub inny kod, który jest przeznaczony dla programu .NET Framework. Jedynym kodem, który nie można udostępnić jest kod, który jest przeznaczony dla określonej platformy.

 ![Udostępnianie kodu między interfejsami użytkownika systemu Windows, iOS i Android](../cross-platform/media/sharecode.png "Kod akcji")

 Można udostępnić swój kod przy użyciu projektu udostępnionego, projektu biblioteki klas przenośnych lub obu. Może się okazać, że niektóre kod najlepiej pasuje do udostępnionego projektu, a niektóre kod ma większy sens wewnątrz projektu biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Opcje udostępniania kodu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opcje udostępniania kodu za pomocą platformy .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Docelowe urządzenia z systemem Windows 10

 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "Urządzenia z systemem Windows")

 Jeśli chcesz utworzyć pojedynczą aplikację, która jest przeznaczona dla całej szerokości urządzeń z systemem Windows 10, utwórz uniwersalną aplikację systemu Windows. Zaprojektujesz aplikację przy użyciu jednego projektu, a twoje strony będą renderowane poprawnie bez względu na to, które urządzenie jest używane do ich wyświetlania.

 Zacznij od szablonu projektu aplikacji platformy uniwersalnej systemu Windows (UWP). Projektowaniaj stron wizualnie, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak są wyświetlane dla różnych typów urządzeń. Jeśli nie podoba Ci się sposób, w jaki strona jest wyświetlana na urządzeniu, możesz zoptymalizować stronę, aby lepiej dopasować ją do rozmiaru ekranu, rozdzielczości lub różnych orientacji, takich jak tryb poziomy lub pionowy. Wszystko to można zrobić za pomocą intuicyjnych okien narzędzi i łatwo dostępnych opcji menu w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, znajdziesz wszystkie emulatory urządzeń i symulatory dla różnych typów urządzeń razem w jednej liście rozwijanej, która znajduje się na pasku narzędzi **Standard.**

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do uniwersalnej platformy Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migracja aplikacji na platformę uniwersalną systemu Windows](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (HTML/JavaScript)

 ![Urządzenia z systemem Windows, iOS i Android](../cross-platform/media/homedevices.png "Urządzenia z systemem Windows, iOS i Android")

 Jeśli jesteś programistą sieci Web i znasz kod HTML i JavaScript, możesz kierować reklamy na systemy Windows, Android i iOS przy użyciu narzędzi programu Visual Studio tools dla apache Cordova. Te aplikacje mogą kierować się na wszystkie trzy platformy i można je tworzyć przy użyciu umiejętności i procesów, które są najbardziej znane.

 Apache Cordova to struktura, która zawiera model wtyczki. Ten model wtyczki udostępnia jeden interfejs API języka JavaScript, którego można użyć, aby uzyskać dostęp do natywnych funkcji urządzeń wszystkich trzech platform (Android, iOS i Windows).

 Ponieważ te interfejsy API są międzyplatformowe, można udostępnić większość tego, co piszesz między wszystkimi trzema platformami. Zmniejsza to koszty rozwoju i konserwacji. Ponadto, nie ma potrzeby, aby zacząć od zera. Jeśli utworzono inne typy aplikacji internetowych, można udostępnić te pliki aplikacji Cordova bez konieczności modyfikowania lub przeprojektowania ich w jakikolwiek sposób.

 ![Aplikacje hybrydowe dla wielu urządzeń z javascriptem](../cross-platform/media/multidevicehybridapps.png "Aplikacje hybrydowe dla wielu urządzeń z javascriptem")

 Aby rozpocząć, zainstaluj program Visual Studio i wybierz funkcję **Mobile Development z javascript** podczas instalacji. Narzędzia Cordova automatycznie instalują wszystkie oprogramowanie innych firm, które jest wymagane do zbudowania aplikacji wieloplatformowej.

 Po zainstalowaniu rozszerzenia otwórz program Visual Studio i utwórz projekt **pustej aplikacji (Apache Cordova).** Następnie możesz tworzyć aplikację przy użyciu języka JavaScript lub Typescript. Można również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji, a interfejsy API z wtyczek są wyświetlane w intellisense podczas pisania kodu.

 Gdy będziesz gotowy do uruchomienia aplikacji i przejść przez kod, wybierz emulator, taki jak emulator Apache Ripple lub emulator systemu Android, przeglądarka lub urządzenie, które zostało podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli tworzysz aplikację na komputerze z systemem Windows, możesz ją nawet uruchomić. Wszystkie te opcje są wbudowane w programie Visual Studio jako część narzędzia programu Visual Studio dla Apache Cordova.

 Szablony projektów do tworzenia aplikacji platformy uniwersalnej systemu Windows (UWP) są nadal dostępne w programie Visual Studio, więc możesz ich używać, jeśli planujesz kierować reklamy tylko na urządzenia z systemem Windows. Jeśli zdecydujesz się na kierowanie android i iOS później, zawsze można przenieść kod do projektu Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Instalowanie programu Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Wprowadzenie do programu Visual Studio Tools dla apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Dowiedz się więcej o emulatorze programu Visual Studio dla systemu Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (C++)

![Tworzenie aplikacji dla systemów Android, iOS i Windows za pomocą&#43;&#43; C](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio i mobile development z obciążeniem **C++.** Następnie można utworzyć aplikację aktywności natywnej dla systemu Android lub aplikację przeznaczoną dla systemu Windows lub systemu iOS. Możesz kierować reklamy na systemy Android, iOS i Windows w tym samym rozwiązaniu, jeśli chcesz, a następnie udostępnić kod między nimi przy użyciu międzyplatformowej statycznej lub dynamicznej biblioteki udostępnionej.

 Jeśli chcesz utworzyć aplikację dla systemu Android, która wymaga wszelkiego rodzaju zaawansowanej manipulacji grafiką, takiej jak gra, możesz użyć języka C++, aby to zrobić. Rozpocznij od projektu **aplikacji aktywności natywnej (Android).** Ten projekt ma pełne poparcie dla paska narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "Szablon projektu działania natywnego")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, użyj emulatora systemu Android. Jest szybki, niezawodny i łatwy w instalacji i konfiguracji.

 Można również utworzyć aplikację, która jest przeznaczona dla pełnego zakresu urządzeń z systemem Windows 10 przy użyciu języka C++ i szablonu projektu aplikacji platformy uniwersalnej systemu Windows (UWP). Więcej informacji na ten temat można przeczytać w sekcji [Docelowe urządzenia z systemem Windows 10,](#WindowsHTML) która pojawia się wcześniej w tym temacie.

 Kod języka C++ można udostępnić między systemami Android, iOS i Windows, tworząc statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki współdzielone](../cross-platform/media/cross_plat_cpp_libraries.png "Statyczne i dynamiczne biblioteki współdzielone")

 Można korzystać z tej biblioteki w projekcie systemu Windows, iOS lub Android, jak te opisane wcześniej w tej sekcji. Można również używać go w aplikacji, która jest budowana przy użyciu platformy Xamarin, Java, lub dowolnego języka, który pozwala wywołać funkcje w niezarządzanej biblioteki DLL.

 Podczas pisania kodu w tych bibliotekach można użyć intellisense do eksplorowania natywnych interfejsów API platform Android i Windows. Te projekty biblioteki są w pełni zintegrowane z debugerem programu Visual Studio, dzięki czemu można ustawić punkty przerwania, krok po kroku kodu i znaleźć i rozwiązać problemy przy użyciu wszystkich zaawansowanych funkcji debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobieranie programu Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Instalowanie środowiska opracowywania aplikacji mobilnych na wiele platform w języku C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Dowiedz się więcej o używaniu języka C++ do kierowania reklam na wiele platform](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj to, czego potrzebujesz, a następnie utwórz natywną aplikację aktywności języka C++ dla systemu Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Dowiedz się więcej o udostępnianiu kodu W++ za pomocą aplikacji na Androida i Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Międzyplatformowe przykłady rozwoju urządzeń mobilnych dla języka C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Tworzenie gry wieloplatformowej dla systemów Android, iOS i Windows przy użyciu narzędzi programu Visual Studio dla unity

 Visual Studio Tools for Unity to bezpłatne rozszerzenie dla programu Visual Studio, które integruje zaawansowane narzędzia do edycji kodu, produktywności i debugowania programu Visual Studio z *unity*, popularnym międzyplatformowym aparatem gier/grafiki i środowiskiem programistycznym dla wciągających aplikacji przeznaczonych dla systemów Windows, iOS, Android i innych platform, w tym sieci Web.

 ![Środowisko programistyczne VSTU](../cross-platform/media/vstu_overview.png "Omówienie dotyczące narzędzi programu Visual Studio dla aplikacji Unity")

 Za pomocą programu Visual Studio Tools for Unity (VSTU) można używać programu Visual Studio do pisania skryptów gier i edytorów w języku C#, a następnie używać zaawansowanego debugera do znajdowania i naprawiania błędów. Najnowsza wersja programu VSTU zapewnia obsługę unity 2018.1 i zawiera kolorowanie składni dla języka modułu cieniującego ShaderLab unity, lepszą synchronizację z Unity, bogatsze debugowanie i ulepszone generowanie kodu dla kreatora MonoBehavior. VSTU przynosi również pliki projektu Unity, komunikaty konsoli i możliwość uruchomienia gry w programie Visual Studio, dzięki czemu można spędzić mniej czasu przełączania do iz Edytora Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier Unity za pomocą programu Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Dowiedz się więcej o narzędziach programu Visual Studio dla unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Rozpoczynanie korzystania z narzędzi programu Visual Studio dla unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Przeczytaj o najnowszych ulepszeniach narzędzi programu Visual Studio dla unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog programu Visual Studio)|
|[Obejrzyj wprowadzenie do klipu wideo z narzędziami programu Visual Studio dla unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej o Unity](https://unity.com/) (unity stronie)|

## <a name="see-also"></a>Zobacz też

- [Dodawanie interfejsów API usługi Office 365 do projektu programu Visual Studio](/office/developer-program/office-365-developer-program)
- [Usługi azure app services — aplikacje mobilne](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
