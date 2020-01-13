---
title: Programowanie aplikacji mobilnych na wiele platform w programie Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 15c4d31c8cc835884f1093dc78083bbfa9448bc3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916880"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Programowanie aplikacji mobilnych na wiele platform w programie Visual Studio

Można tworzyć aplikacje dla urządzeń z systemem Android, iOS i Windows przy użyciu programu Visual Studio.  Podczas projektowania aplikacji, należy użyć narzędzi w programie Visual Studio, łatwe dodawanie podłączonych usług, takich jak Office 365, Azure App Service i usługi Application Insights.

Tworzenie aplikacji przy użyciu języka C# i .NET Framework, HTML i JavaScript lub C++. Udostępnianie kodu, ciągi, obrazy, a w niektórych przypadkach nawet interfejsu użytkownika.

Do tworzenia gier lub realistycznych aplikacji graficznych, należy zainstalować narzędzia Visual Studio tools for Unity i cieszyć się wszystkimi zaawansowane funkcje produktywności programu Visual Studio przy użyciu aparatu Unity, popularnych Międzyplatformowe gry grafiki aparatu i środowisko programistyczne dla aplikacji, Uruchom na iOS, Android, Windows i innych platform.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (.NET Framework)

![Urządzenia](../cross-platform/media/homedevices.png "HomeDevices")

Za pomocą Visual Studio Tools dla platformy Xamarin można docelowo dla systemów Android, iOS i Windows w tym samym rozwiązaniu, udostępniając kod i nawet interfejs użytkownika.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/community/) (Visual Studio)|
|[Więcej informacji na temat platformy Xamarin w programie Visual Studio](https://visualstudio.microsoft.com/xamarin/) (Visual Studio)|
|[Dokumentacja dotycząca tworzenia aplikacji mobilnych dla oprogramowania Xamarin](/xamarin/) |
|[DevOps z aplikacjami platformy Xamarin](/xamarin/tools/ci/devops/) |
|[Poznaj aplikacje uniwersalne systemu Windows w programie Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Dowiedz się więcej o podobieństwa Swift i C#](https://aka.ms/scposter) (witrynie download.microsoft.com)|

### <a name="AndroidHTML"></a> Docelowe systemów Android, iOS i Windows z pojedynczą bazą kodu

 Możesz tworzyć natywne aplikacje dla systemów Android, iOS i Windows za pomocą C# programu F# lub (Visual Basic nie jest to obsługiwane w tej chwili).  Aby rozpocząć, zainstaluj program Visual Studio, wybierz opcję **Programowanie aplikacji mobilnych przy użyciu platformy .NET** w instalatorze.

 Jeśli masz już zainstalowany program Visual Studio, uruchom ponownie **Instalator programu Visual Studio** i wybierz opcję **Programowanie aplikacji mobilnych za pomocą platformy .NET dla środowiska** Xamarin (jak powyżej).

 Gdy skończysz, szablony projektu są wyświetlane w oknie dialogowym **Nowy projekt** . Najprostszym sposobem znalezienia szablonów platformy Xamarin jest po prostu wyszukać "Xamarin."

 Platforma Xamarin udostępnia natywne funkcje systemu Android, iOS i Windows jako klasy i metody platformy .NET. Oznacza to, że aplikacje mają pełny dostęp do natywnych interfejsów API i natywnych kontrolek i są równie zgodne z aplikacjami zapisanymi w natywnych językach platformy.

 Po utworzeniu projektu będzie można korzystać ze wszystkich funkcji produktywności programu Visual Studio. Na przykład użyjesz projektanta do tworzenia stron i korzystaj z technologii IntelliSense do eksplorowania natywnych interfejsów API platformy mobilnej. Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, możesz użyć emulatora Android SDK i natywnie uruchamiać aplikacje systemu Windows. Umożliwia także powiązane systemami Android i Windows bezpośrednio. W przypadku projektów systemu iOS należy nawiązać połączenie z siecią komputerową Mac i uruchomić emulator systemu iOS z programu Visual Studio lub połączyć się z urządzeniem z tetheringem.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Projektowanie jeden zestaw stron, które są renderowane dla wszystkich urządzeń za pomocą platformy Xamarin.Forms

 W zależności od złożoności projektu aplikacji, można rozważyć wbudowanie jej za pomocą *Xamarin.Forms* szablonów w **Mobile Apps** grupy szablonów projektu. Xamarin.Forms to zestaw narzędzi interfejsu użytkownika, który umożliwia tworzenie jednego interfejsu, którą można współdzielić między systemów Android, iOS i Windows.  Podczas kompilowania rozwiązania Xamarin. Forms uzyskasz aplikację dla systemu Android, aplikację dla systemu iOS i aplikację systemu Windows. Aby uzyskać więcej informacji, zobacz informacje [o tworzeniu aplikacji mobilnych za pomocą platformy Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) i [dokumentacji platformy Xamarin. Forms](/xamarin/xamarin-forms/).

#### <a name="ShareHTML"></a> Współdziel kod między systemami Android, iOS i aplikacji Windows

 Jeśli nie korzystasz z programu Xamarin. Forms i chcesz projektować dla każdej platformy osobno, możesz udostępnić większość kodu innego niż interfejs użytkownika między projektami platformy (Android, iOS i Windows). W tym wszelka logika biznesowa, integracja z chmurą, dostęp do bazy danych lub inny kod, który jest przeznaczony dla .NET Framework. Jedyny kod, którego nie można udostępnić, to kod, który jest przeznaczony dla konkretnej platformy.

 ![Udostępnianie kodu między systemami Windows, iOs i Android](../cross-platform/media/sharecode.png "ShareCode")

 Możesz udostępnić swój kod za pomocą udostępnionego projektu i/lub projekt przenośnej biblioteki klas. Może się okazać, że niektóre kodu mieści się najlepiej w projekcie udostępnionym i jakiś kod sprawia, że więcej sens w projekcie biblioteki klas przenośnych.

|**Dowiedz się więcej**|
|--------------------|
|[Udostępnianie kodu opcje](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Opcje udostępniania kodu w programie .NET](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a> Docelowe urządzenia z systemem Windows 10

 ![Urządzenia z systemem Windows](../cross-platform/media/windowsdevices.png "Urządzenia z systemem Windows")

 Jeśli chcesz utworzyć pojedynczą aplikacją, który jest przeznaczony dla rozmaitych urządzeniach z systemem Windows 10, należy utworzyć uniwersalnej aplikacji Windows. Aplikacja zostanie zaprojektowana przy użyciu pojedynczego projektu, a strony będą renderowane prawidłowo, niezależnie od tego, jakie urządzenie jest używane do ich wyświetlania.

 Zacznij od szablonu projektu aplikacji platforma uniwersalna systemu Windows (platformy UWP). Projektowanie wizualnie strony, a następnie otwórz je w oknie podglądu, aby zobaczyć, jak pojawiają się dla różnych typów urządzeń. Jeśli nie chcesz, aby strona została wyświetlona na urządzeniu, możesz zoptymalizować ją, aby lepiej odpowiadała rozmiarowi ekranu, rozdzielczości lub różnym orientacjom, takim jak orientacja pozioma lub pionowa. Możesz tworzyć wszystko to za pomocą intuicyjnego narzędzia systemu windows i opcje menu łatwo dostępne w programie Visual Studio. Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, znajdziesz wszystkie emulatory urządzeń i symulatory dla różnych typów urządzeń razem w jednej liście rozwijanej, która znajduje się na pasku narzędzi **Standardowy** .

|**Dowiedz się więcej**|
|--------------------|
|[Wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app)|
|[Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrowanie aplikacji na platformie Universal Windows (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a> Tworzenie aplikacji dla systemu Android, iOS i Windows (HTML/JavaScript)

 ![Urządzenia z systemami Windows, iOS i Android](../cross-platform/media/homedevices.png "Urządzenia z systemami Windows, iOS i Android")

 Jeśli jesteś deweloperem sieci Web i znasz język HTML i JavaScript, możesz użyć systemu Windows, Android i iOS za pomocą Visual Studio Tools Apache Cordova. Te aplikacje mogą być przeznaczone dla wszystkich trzech platform i można je kompilować przy użyciu umiejętności i procesów, które są najbardziej znane.

 Apache Cordova to struktura, która obejmuje model dodatku plug-in. Ten model wtyczek zawiera pojedynczy interfejs API języka JavaScript, która umożliwia dostęp do natywnych możliwości urządzenia dla wszystkich trzech platformach (Android, iOS i Windows).

 Ponieważ te interfejsy API dla wielu platform, możesz udostępniać większość zapisu od wszystkich trzech platformach. Zmniejsza koszty tworzenia i konserwacji. Nie trzeba również zaczynać od zera. Jeśli zostały utworzone inne typy aplikacji sieci Web, możesz udostępnić te pliki w aplikacji Cordova bez konieczności modyfikowania lub zmiany ich projektu w dowolny sposób.

 ![Aplikacje hybrydowe dla urządzeń z obsługą języka JavaScript](../cross-platform/media/multidevicehybridapps.png "Aplikacje hybrydowe dla urządzeń z obsługą języka JavaScript")

 Aby rozpocząć, zainstaluj program Visual Studio i wybierz funkcję **Programowanie aplikacji mobilnych za pomocą języka JavaScript** podczas instalacji. Narzędzia oprogramowania Cordova automatycznie instalują całe oprogramowanie innych firm wymagane do tworzenia aplikacji dla wielu platform.

 Po zainstalowaniu rozszerzenia Otwórz program Visual Studio i Utwórz **pusty projekt aplikacji (Apache Cordova)** . Następnie możesz opracować aplikację przy użyciu języka JavaScript i Typescript. Możesz również dodać wtyczki, aby rozszerzyć funkcjonalność aplikacji i interfejsów API z dodatków plug-in są wyświetlane w IntelliSense podczas pisania kodu.

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i przechodzenia przez kod, wybierz emulator, taki jak emulator Apache Ripple lub Emulator systemu Android, przeglądarka lub urządzenie podłączone bezpośrednio do komputera. Następnie uruchom aplikację. Jeśli tworzysz aplikację na komputerze z systemem Windows, możesz nawet uruchomić ją na tym urządzeniu. Wszystkie te opcje są tworzone w programie Visual Studio jako część programu Visual Studio Tools for Apache Cordova.

 Szablony projektów służące do tworzenia aplikacji platforma uniwersalna systemu Windows (platformy UWP) są nadal dostępne w programie Visual Studio, dzięki czemu mogą być używane w przypadku planowania tylko urządzeń z systemem Windows. Jeśli zdecydujesz się pod kątem systemów Android i iOS, a później, należy zawsze portu kodu z projektem Cordova.

|**Dowiedz się więcej**|
|--------------------|
|[Zainstaluj program Visual Studio](https://visualstudio.microsoft.com/vs/community/) (Visual Studio)|
|[Wprowadzenie do Visual Studio Tools dla Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Dowiedz się więcej o Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (Visual Studio)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Tworzenie aplikacji dla systemów Android, iOS i Windows (C++)

![Używanie języka&#43; &#43; C do kompilowania dla systemów Android, iOS i Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Najpierw zainstaluj program Visual Studio i **Programowanie aplikacji mobilnych za C++ pomocą** obciążenia. Następnie można utworzyć natywną aplikację działania dla systemu Android lub aplikację, która jest przeznaczona dla systemu Windows lub iOS. W razie potrzeby możesz wybrać systemy Android, iOS i Windows w tym samym rozwiązaniu, a następnie udostępnić kod między nimi przy użyciu statycznej lub dynamicznej biblioteki udostępnionej dla wielu platform.

 Jeśli potrzebujesz do tworzenia aplikacji dla systemu Android, która wymaga dowolny rodzaj manipulowanie grafiki zaawansowane, takie jak gry, można użyć C++, aby to zrobić. Zacznij od projektu **natywnej aplikacji działania (Android)** . W tym projekcie są pełna obsługa łańcucha narzędzi Clang.

 ![Szablon projektu działania natywnego](../cross-platform/media/cross-plat_cpp_native.png "Szablon projektu działania natywnego")

 Gdy wszystko będzie gotowe do uruchomienia aplikacji i zobacz, jak wygląda, użyj Emulator systemu Android. Jest to szybkie, niezawodne i łatwe do zainstalowania i skonfigurowania.

 Możesz również utworzyć aplikację, która jest przeznaczona dla pełnej szerokości urządzeń z systemem Windows 10 przy C++ użyciu szablonu projektu aplikacji platforma uniwersalna systemu Windows (platformy UWP). Dowiedz się więcej w [urządzenia docelowego systemu Windows 10](#WindowsHTML) sekcji, która występuje wcześniej w tym temacie.

 Aby udostępnić C++ kod między systemami Android, iOS i Windows, można utworzyć statyczną lub dynamiczną bibliotekę udostępnioną.

 ![Statyczne i dynamiczne biblioteki udostępnione](../cross-platform/media/cross_plat_cpp_libraries.png "Statyczne i dynamiczne biblioteki udostępnione")

 Tej biblioteki można użyć w projekcie systemu Windows, iOS lub Android, jak opisano wcześniej w tej sekcji. Można również korzystać go w aplikacji, gdy kompilujesz przy użyciu platformy Xamarin, Java lub dowolnego języka, który pozwala wywoływać funkcje w niezarządzaną biblioteką DLL.

 Podczas pisania kodu w tych bibliotek, można użyć IntelliSense, aby zapoznać się z natywnymi interfejsami API platform dla systemów Android i Windows. Te projekty biblioteki są całkowicie zintegrowane z debugera programu Visual Studio, aby można było ustawić punkty przerwania, Przechodź przez kod i znajdowanie i rozwiązywanie problemów przy użyciu wszystkie zaawansowane funkcje debugera.

|**Dowiedz się więcej**|
|--------------------|
|[Pobierz program Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Instalowanie aplikacji mobilnych dla wielu platform za pomocą programuC++](install-visual-cpp-for-cross-platform-mobile-development.md)|
|[Dowiedz się więcej C++ o korzystaniu z programu w celu użycia na wielu platformach](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Zainstaluj to, czego potrzebujesz, a następnie utwórz natywną aplikację działania dla systemu Android](create-an-android-native-activity-app.md)|
|[Dowiedz się więcej na temat udostępniania kodu w języku C++ w aplikacjach dla systemów Android i Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (Visual Studio)|
|[Przykłady tworzenia aplikacji mobilnych dla wielu platform dla programuC++](cross-platform-mobile-development-examples.md)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Tworzenie wieloplatformowej gry dla systemów Android, iOS i Windows przy użyciu narzędzi Visual Studio Tools for Unity

 Visual Studio Tools for Unity to bezpłatne rozszerzenie programu Visual Studio, które integruje zaawansowane narzędzia do edycji kodu, produktywności i debugowania w programie Visual Studio za pomocą *aparatu Unity*, popularne aparaty do gier/grafiki dla wielu platform oraz środowisko programistyczne dla aplikacji w sieci Web przeznaczonych dla systemu Windows, iOS, Android i innych platform, w tym dla Internetu.

 ![Środowisko deweloperskie rozszerzenia VSTU](../cross-platform/media/vstu_overview.png "Przegląd Visual Studio Tools for Unity")

 Program Visual Studio Tools for Unity (VSTU) można użyć programu Visual Studio tworzyć gry i Edytor skrypty w języku C#, a następnie użyć jej zaawansowany debuger, można znaleźć i naprawić błędy. Najnowsza wersja programu rozszerzenia VSTU obsługuje środowisko Unity 2018,1 i oferuje kolorowanie składni dla języka modułu cieniującego ShaderLab w środowisku Unity, lepszą synchronizację z technologią Unity, bogatsze debugowanie i ulepszone generowanie kodu dla Kreatora działania. Narzędzia VSTU także niesie plików projektu środowiska Unity, komunikaty konsoli i możliwości, aby rozpocząć tworzenie gry w programie Visual Studio, dzięki czemu spędzisz mniej czasu przełączanie z edytora środowiska Unity podczas pisania kodu.

|**Dowiedz się więcej**|
|--------------------|
|[Dowiedz się więcej o tworzeniu gier za pomocą programu Visual Studio Unity](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Przeczytaj więcej na temat Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Zacznij korzystać z Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Przeczytaj najnowsze ulepszenia do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog Visual Studio)|
|[Obejrzyj wprowadzenie wideo do programu Visual Studio Tools for Unity 2.0 w wersji zapoznawczej](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (wideo)|
|[Dowiedz się więcej o Unity](https://unity.com/) (Unity witryny sieci Web)|

## <a name="see-also"></a>Zobacz także

- [Dodawanie interfejsów API pakietu Office 365 do projektu programu Visual Studio](/office/developer-program/office-365-developer-program)
- [App Services platformy Azure — Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
