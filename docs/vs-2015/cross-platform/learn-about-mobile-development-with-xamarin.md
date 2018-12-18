---
title: Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 329c684dcc09a15ec86f80493d9f084e486b7cfe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733185"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Informacje dotyczące programowania mobilnego za pomocą platformy Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ten temat kieruje do materiału Przegląd, który pomoże Ci zrozumieć, opracowywanie aplikacji mobilnych dla wielu platform za pomocą platformy Xamarin. Jeśli nie zainstalowano jeszcze programu Visual Studio i Xamarin, uruchom [Instalator i instalacja](../cross-platform/setup-and-install.md) procesu po pierwsze, następnie wróć tutaj i pracować za pośrednictwem tych zasobów, gdy instalatory są uruchomione.  
  
> [!NOTE]
>  Jeśli nie określono inaczej, zalecamy początkowo odczytu tylko te strony połączone bezpośrednio w tym miejscu i nie przedstawicielstwach stron. Jeśli proces instalacji jest nadal uruchomione po ukończeniu tej listy, możesz przejść wstecz i Poznaj dodatkowe tematy.  
>   
>  Także swobodnie zapoznaj się z tematami, oznaczone jako "Essentials" i wróć do tematów "Bardziej zgłębić temat" później.  
  
## <a name="essentials-introduction-to-xamarin"></a>Podstawy: Wprowadzenie do platformy Xamarin  
 *10-20 minut*  
  
1.  [Aplikacje mobilne w programie Visual Studio za pomocą platformy Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) zapewnia bardzo krótkie podsumowania podstawowe właściwości platformy Xamarin.  
  
2.  [Tworzenie Cross-Platform Mobile Apps przy użyciu języka C# i Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (— Channel9, 15m16s) za pomocą platformy Xamarin Propagator, James Montemagno. Pierwsze trzy minuty są z omówieniem platformy Xamarin, następuje pokazów kodu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Podstawy: Omówienie programu Visual Studio i środowiska Xamarin  
 *5 – 15 minut*  
  
- Komputer Windows za pomocą programu Visual Studio i Xamarin to, gdzie wykonasz większość swojej pracy. Na tym komputerze bezpośrednio tworzyć aplikacje dla systemu Android i Windows oraz uruchamianie i debugowanie ich na urządzenie lub emulator. Możesz także zdalnie tworzenie, uruchamianie i debugowanie aplikacji dla systemu iOS przy użyciu komputerów Mac. Visual Studio na komputerze Windows też nawiązać połączenie z systemem iOS designer scenorysu i symulatora systemu iOS.  
  
- Mac za pomocą środowiska Xcode i Xamarin służy jako kompilacji/podpisywania hosta i środowiska uruchomieniowego dla aplikacji systemu iOS. Kompilacje dla systemu iOS w programie Visual Studio na komputerze Windows są delegowane ten komputer Mac; podczas debugowania aplikacji systemu iOS w programie Visual Studio, działa w symulatorze systemu iOS na komputerze Mac lub bezpośrednio na urządzenia powiązanego połączone na komputerze Mac. W tym przypadku będzie interakcji z aplikacją na lub w pobliżu komputera Mac, a masz środowisko debugowania w programie Visual Studio.  
  
  Poniżej przedstawiono te relacje i możesz dowiedzieć się więcej o pracy z aplikacjami systemu iOS na [wprowadzenie do rozwiązania Xamarin.iOS dla programu Visual Studio](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) (strony xamarin.com).  
  
  ![Relacja między komputerami deweloperów Windows i Mac w środowisku Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin informacje 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Podstawy: Projekty są struktury  
 *10-30 minut*  
  
1.  [Udostępnianie kodu opcje](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (strony xamarin.com). Zaleca się, że przy użyciu opcji biblioteki klas przenośnych, ponieważ najlepsze obsługuje przy użyciu tylko tych interfejsów API platformy .NET, które są obsługiwane na wszystkich platformach docelowych. Większość kodu logiki biznesowej będą znajdować się w aplikacji PCL, łącznie z dostępem do bazy danych, wywołania interfejsów API REST i wywołania przenośne składników platformy Xamarin (zobacz [bardziej zgłębić temat: składników platformy Xamarin](#components) na końcu tego tematu). Wspólny kod interfejsu użytkownika, napisane przy użyciu zestawu narzędzi Xamarin.Forms również mogą znajdować się w aplikacji PCL.  
  
2.  (Opcjonalnie) [Analiza przypadku: Tasky](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/case_study-tasky/) (strony xamarin.com), w tym artykule opisano najlepsze rozwiązania dotyczące projektowania i struktury aplikacji w pełni funkcjonalne, takie jak tworzenie struktury projektów za pomocą aplikacji PCL dla udostępnionego kodu, który oddziela dane, dostęp do danych i warstwy biznesowej.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: natywne i warstwy interfejsu użytkownika zestawu narzędzi Xamarin.Forms  
 *10-40 minut*  
  
 Środowisko Xamarin zapewnia dwa sposoby tworzenia atrakcyjnych aplikacji natywnych: Native platformy Xamarin i Xamarin.Forms.  
  
 Za pomocą platformy Xamarin Native pisania osobnego kodu interfejsu użytkownika dla każdej z platform docelowych: iOS, Android i Windows.  W przypadku tej metody możesz mieć bezpośredni dostęp do interfejsów API specyficzne dla platformy, dzięki czemu dostosowane środowisko interfejsu użytkownika dla danej platformy.  Możesz również mieć pełny dostęp do natywnych projektanta i kontrolki dla każdej platformy, pomagające w tworzeniu odpowiedniego interfejsu użytkownika.  
  
 Xamarin.Forms zawiera zestaw ogólnych interfejsów API, która umożliwia zapisanie udostępnionej warstwy interfejsu użytkownika dla wszystkich platform w bibliotece klas przenośnych.  Renderuje zestaw narzędzi Xamarin.Forms do natywnych kontrolek na każdej platformie docelowej, aby dać natywnego wyglądu i działania.  Zamiast używania projektanta, za pomocą zestawu narzędzi Xamarin.Forms, możesz utworzyć interfejs użytkownika przy użyciu języka C# i XAML.  
  
 Nie musisz zdecydować, które rozwiązanie do wykonania na początku; aplikacje można zaimplementować przy użyciu kombinacji natywnego środowiska Xamarin i Xamarin.Forms:  
  
- Użyj zestawu narzędzi Xamarin.Forms do tworzenia ekranów ogólnego przeznaczenia, które zapewniają podobne możliwości i interfejsu użytkownika na platformach, takich jak nazwy logowania, skontaktuj się z formularzy i wyniki wyszukiwania.  
  
- Użyj różnych możliwości dostosowywania w interfejsie Xamarin.Forms, aby dopasować interfejsu użytkownika na poszczególnych platform. Obejmują one API OnPlatform, który może być używana zarówno kod i XAML, tworzenie widoku niestandardowego, rozszerzanie istniejących renderowania i tworzenie niestandardowego modułu renderowania.  
  
- Jeśli to konieczne, należy użyć natywnego platformy Xamarin do tworzenia ekranów, korzystających z unikatowych funkcji interfejsu użytkownika dla każdej platformy, na przykład, ekran, który używa natywnego aparatu manipulowania przechwytywania i obrazów.  
  
  Firma Microsoft zaleca, począwszy od zawsze rozwiązanie Xamarin.Forms, aby zdefiniować kod interfejsu użytkownika, udostępnianie na platformach i wprowadzać zmiany specyficzne dla platformy z użyciem możliwości dostosowywania. Jeśli potrzebujesz ekrany całkowicie specyficzne dla platformy, można dodać oddzielnie za pomocą natywnego platformy Xamarin.  
  
  Aby dowiedzieć się więcej:  
  
1.  [Zestaw narzędzi Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/) (strony xamarin.com) zawiera krótkie omówienie i zalet i wad Xamarin.Forms a native warstwy interfejsu użytkownika (czyli Xamarin.iOS i Xamarin.Android).  
  
2.  Pierwsze trzy minuty wideo James Montemagno [Xamarin.Forms: natywnych dla systemów iOS, Android i Windows aplikacje za pomocą języka C# i XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (— Channel9, 13m3s) ogólny innego i będziesz kontynuować, obserwowanie pokazów.  
  
3.  (Opcjonalnie) [Wprowadzenie do zestawu narzędzi Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/introduction-to-xamarin-forms/) (strony xamarin.com)  
  
4.  (Opcjonalnie) Zapoznaj się z przykładami używania OnPlatform do dostosowania w [klasę urządzeń pamięci](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) dokumentacji (strony xamarin.com)  
  
5.  (Opcjonalnie) [Dla wielu Platform — udziału interfejsu użytkownika kodu dla platform urządzeń przenośnych za pomocą zestawu narzędzi Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) przez Jason Smith (MSDN Magazine) przedstawiono opcje dostosowywania różne, w ramach zestawu narzędzi Xamarin.Forms, dla którego szczegółowe informacje znajdują się na [ Dostosowywanie formantów na każdej platformie](http://developer.xamarin.com/guides/xamarin-forms/custom-renderer/) (strony xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Bardziej zgłębić temat: Debugowanie przy użyciu emulatorów  
 *10 – 15 minut*  
  
 Aby debugować aplikacje dla wielu platform bez konieczności używania fizycznego urządzenia, należy użyć następującego polecenia:  
  
1.  **Emulator systemu Android.** Zależności od instalowanej wersji systemu Windows, którego używasz zaleca się albo programu Microsoft Visual Studio Emulator dla systemu Android lub Xamarin Player, które oferują wysoką wydajność i obsługuje szeroką gamę możliwości urządzenia:  
  
    -   **Maszyny z systemem Windows 8 i nowsze:** zdecydowanie zaleca się za pomocą firmy Microsoft [Visual Studio Emulator for Android](https://www.visualstudio.com/en-us/features/msft-android-emulator-vs.aspx), która jest instalowana z programem Visual Studio.  [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) wideo (Channel9, 5m55s) zapewnia przegląd i prezentacja.  
  
    -   **Windows 7 lub wcześniejszej Windows /, systemem Mac OS X**: Użyj [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player) (strony xamarin.com).  
  
2.  **Firmy Apple symulatora systemu iOS.** Aby dowiedzieć się więcej, przeczytaj [wprowadzenie w narzędziu iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3.  **Emulator Windows Phone firmy Microsoft.** Aby dowiedzieć się więcej, przeczytaj [Windows Phone Emulator dla Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
##  <a name="components"></a> Bardziej zgłębić temat: Składników platformy Xamarin  
 *10 minut*  
  
 Wiele rozszerzone możliwości są dostępne dla aplikacji platformy Xamarin przy użyciu składników platformy Xamarin. Możesz znaleźć pełne wykazu, dostępna do pobrania na [ http://components.xamarin.com/ ](http://components.xamarin.com/), która obejmuje składniki dodatkowe formanty interfejsu użytkownika, uwierzytelnianie, szereg usług cloud services, takich jak Microsoft Azure i wiele więcej.

