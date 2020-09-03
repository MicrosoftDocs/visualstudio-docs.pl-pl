---
title: Dowiedz się więcej na temat tworzenia aplikacji mobilnych za pomocą platformy Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: a362bd4eef2a48667c67c03e940e213fc960418b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919005"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Informacje dotyczące programowania mobilnego za pomocą platformy Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie przedstawiono informacje o materiałach, które ułatwiają zrozumienie tworzenia międzyplatformowych aplikacji mobilnych za pomocą platformy Xamarin. Jeśli nie masz jeszcze zainstalowanego programu Visual Studio i platformy Xamarin, najpierw Rozpocznij [instalację i proces instalacji](../cross-platform/setup-and-install.md) , a następnie wróć tutaj, aby pracować z tymi zasobami podczas działania Instalatora.  
  
> [!NOTE]
> O ile nie zaznaczono inaczej, zalecamy wstępne odczytywanie tylko tych stron, które są połączone bezpośrednio w tym miejscu, a nie na stronach oddziałów. Jeśli proces instalacji nadal działa po zakończeniu tej listy, możesz skorzystać z bezpłatnej, aby zapoznać się z dodatkowymi tematami.  
>   
> Możesz również bezpłatnie przejrzeć Tematy oznaczone jako "Essentials" i wrócić do tematów "bardziej dokładniejszych szczegółowe".  
  
## <a name="essentials-introduction-to-xamarin"></a>Podstawowe informacje: wprowadzenie do platformy Xamarin  
 *10-20 minut*  
  
1. [Mobile Apps w programie Visual Studio z](https://www.visualstudio.com/explore/xamarin-vs) platformą xamarin (VisualStudio.com) zapewnia bardzo krótkie uwalnianie podstawowych charakterystyk platformy Xamarin.  
  
2. [Tworzenie Międzyplatformowych Mobile Apps przy użyciu języka C# i programu Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (channel9, 15m16s) przy użyciu platformy Xamarin propagator, Kuba Montemagno. Pierwsze trzy minuty to omówienie platformy Xamarin, a następnie demonstracje kodu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Podstawowe informacje: przegląd środowiska Visual Studio i Xamarin  
 *5-15 minut*  
  
- Komputer z systemem Windows z programem Visual Studio i Xamarin to miejsce, w którym można wykonywać większość zadań. Na tym komputerze można bezpośrednio budować aplikacje dla systemu Windows i Android oraz uruchamiać i debugować je na urządzeniu lub w emulatorze. Możesz również zdalnie kompilować, uruchamiać i debugować aplikacje dla systemu iOS za pośrednictwem komputera Mac. Program Visual Studio na komputerze z systemem Windows może również nawiązać połączenie z projektantem systemu iOS i symulatorem systemu iOS.  
  
- Komputery Mac z Xcode i Xamarin pełnią rolę hosta kompilowania/podpisywania oraz środowiska uruchomieniowego dla aplikacji systemu iOS. Kompilacje dla systemu iOS z programu Visual Studio na komputerze z systemem Windows są delegowane do tego komputera Mac. podczas debugowania aplikacji dla systemu iOS z poziomu programu Visual Studio działa ona w symulatorze systemu iOS na komputerze Mac lub bezpośrednio na urządzeniu powiązanym z komputerem Mac. W takim przypadku będziesz w stanie korzystać z aplikacji na komputerze Mac lub w jego sąsiedztwie oraz korzystać z funkcji debugowania w programie Visual Studio.  
  
  Te relacje przedstawiono poniżej i można zapoznać się z informacjami na temat pracy z aplikacjami dla systemu iOS na platformie [Xamarin. iOS dla programu Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (Xamarin.com).  
  
  ![Relacja między komputerami deweloperskimi systemu Windows i Mac w środowisku Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin — informacje 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Podstawowe informacje: jak są strukturalne projekty  
 *10-30 minut*  
  
1. [Udostępnianie opcji kodu](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com). Zalecamy korzystanie z opcji biblioteki klas przenośnych, ponieważ najlepiej obsługuje ona Używanie tylko tych interfejsów API platformy .NET, które są obsługiwane na wszystkich platformach docelowych. Większość kodów logiki biznesowej będzie znajdować się w PCL, włącznie z dostępem do baz danych, wywołaniami interfejsów API REST i wywołaniami [przenośnych składników Xamarin](#components) Wspólny kod interfejsu użytkownika zapisany w środowisku Xamarin. Forms może również znajdować się w PCL.  
  
2. Obowiązkowe [Analiza przypadku: Tasks](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (Xamarin.com), opisuje niektóre najlepsze rozwiązania związane z projektowaniem i strukturą w pełni funkcjonalnej aplikacji, takiej jak tworzenie struktury projektu przy użyciu PCL dla udostępnionego kodu, który oddziela dane, dostęp do danych i warstwy biznesowe.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Podstawowe: warstwy interfejsu użytkownika Native i Xamarin. Forms  
 *10-40 minut*  
  
 Platforma Xamarin oferuje dwa sposoby tworzenia doskonałych aplikacji natywnych: platformy Xamarin Native i interfejsu Xamarin. Forms.  
  
 Za pomocą platformy Xamarin Native napiszesz osobny kod interfejsu użytkownika dla poszczególnych platform docelowych: iOS, Android i Windows.  Dzięki temu masz bezpośredni dostęp do interfejsów API specyficznych dla platformy, co pozwala na dostosowanie środowiska interfejsu użytkownika na platformę.  Ponadto masz pełny dostęp do macierzystego projektanta i formantów dla każdej platformy, aby pomóc w tworzeniu odpowiedniego interfejsu użytkownika.  
  
 Środowisko Xamarin. Forms zawiera uogólniony zestaw interfejsów API, które umożliwiają pisanie udostępnionej warstwy interfejsu użytkownika dla wszystkich platform w przenośnej bibliotece klas.  Program Xamarin. Forms renderuje natywne kontrolki na każdej platformie docelowej w celu zapewnienia natywnego wyglądu i działania.  Zamiast korzystać z projektanta, za pomocą interfejsu Xamarin. Forms tworzysz interfejs użytkownika przy użyciu języka C# i języka XAML.  
  
 Nie musisz podejmować decyzji o tym, które podejście należy podjąć; Aplikacje można zaimplementować przy użyciu kombinacji programów Xamarin Native i Xamarin. Forms:  
  
- Za pomocą platformy Xamarin. Forms można tworzyć ekrany ogólnego przeznaczenia, które zapewniają podobny interfejs użytkownika i możliwości na wielu platformach, takich jak logowania, formularze kontaktowe i wyniki wyszukiwania.  
  
- Użyj różnych możliwości dostosowywania w programie Xamarin. Forms, aby dostosować interfejs użytkownika dla poszczególnych platform. Obejmują one interfejs API onplatform, który może być używany zarówno z kodu, jak i XAML, Tworzenie widoku niestandardowego, rozszerzanie istniejącego modułu renderowania i tworzenie niestandardowego modułu renderowania.  
  
- W razie potrzeby użyj interfejsu Xamarin native do tworzenia ekranów, które używają unikatowych funkcji interfejsu użytkownika dla każdej platformy, na przykład ekranu, który używa natywnego przechwytywania aparatu i manipulowania obrazami.  
  
  Zalecamy zawsze Rozpoczynanie pracy z rozwiązaniem Xamarin. Forms, aby skonfigurować udostępnianie kodu interfejsu użytkownika między platformami oraz korzystać z możliwości dostosowywania w celu wprowadzenia korekt specyficznych dla platformy. Jeśli i w przypadku korzystania z całkowicie ekranów specyficznych dla platformy, można je dodać pojedynczo przy użyciu interfejsu Xamarin Native.  
  
  Dodatkowe informacje:  
  
1. [Xamarin. Forms](/xamarin/xamarin-forms/) (Xamarin.com) zawiera krótkie omówienie oraz zalety i wady narzędzi Xamarin. Forms i natywnych warstw interfejsu użytkownika (czyli platformy Xamarin. iOS i Xamarin. Android).  
  
2. Pierwsze trzy minuty Montemagno wideo [Xamarin. Forms: Native iOS, Android & aplikacje systemu Windows przy użyciu języka C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (channel9, 13m3s) udostępniają inne omówienie i można nadal oglądać pokazy.  
  
3. Obowiązkowe [Wprowadzenie do platformy Xamarin. Forms](/xamarin/get-started/quickstarts/deepdive?pivots=windows) (Xamarin.com)  
  
4. Obowiązkowe Zobacz przykłady użycia funkcji onplatform do dostosowywania w dokumentacji [klasy urządzeń](/xamarin/xamarin-forms/platform/device) (Xamarin.com)  
  
5. Obowiązkowe [Międzyplatformowy kod interfejsu użytkownika w ramach platformy mobilnej z interfejsem Xamarin. Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) przez Jason Smith (MSDN Magazine) przedstawia różne opcje dostosowywania w programie Xamarin. Forms, dla których szczegóły są objęte [dostosowywaniem formantów na każdej platformie](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (Xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Dokładniejsze szczegółowe: debugowanie przy użyciu emulatorów  
 *10–15 minut*  
  
 Aby debugować aplikacje dla wielu platform bez konieczności korzystania z urządzenia fizycznego, należy wykonać następujące czynności:  
  
1. **Emulator systemu Android.** W zależności od używanej wersji systemu Windows zalecamy Emulator programu Visual Studio firmy Microsoft dla systemu Android lub Xamarin Player, z których obie umożliwiają szybką wydajność i obsługę różnych możliwości urządzeń:  
  
    - **Komputery z systemem Windows 8** lub nowszym: Zdecydowanie zalecamy użycie [emulatora Visual Studio firmy Microsoft dla systemu Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx), który jest instalowany z programem Visual Studio.  [Program Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) wideo (channel9, 5m55s) zawiera przegląd i demonstrację.  
  
    - **System Windows 7 lub starszy/Windows działający w Mac OS X**: Użyj [Xamarin Android Player](/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
2. **Symulator systemu iOS firmy Apple.** Aby dowiedzieć się więcej, Przeczytaj [wprowadzenie z symulatorem systemu iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (Apple.com).  
  
3. **Emulator Windows Phone firmy Microsoft.** Aby dowiedzieć się więcej, Przeczytaj [Windows Phone Emulator dla Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
## <a name="deeper-dive-xamarin-components"></a><a name="components"></a> Dokładniejsze szczegółowe: składniki platformy Xamarin  
 *10 minut*  
  
 Wiele rozszerzonych funkcji jest dostępnych dla aplikacji platformy Xamarin za poorednictwem składników platformy Xamarin. Można znaleźć pełny wykaz dostępny do pobrania [http://components.xamarin.com/](/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows) , który obejmuje składniki dla dodatkowych formantów interfejsu użytkownika, uwierzytelnianie, różne usługi w chmurze, takie jak Microsoft Azure i wiele innych.
