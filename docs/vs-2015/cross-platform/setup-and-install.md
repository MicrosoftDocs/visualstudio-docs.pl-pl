---
title: Konfigurowanie i instalowanie oprogramowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: 26733c576a8bfd260368697ba0791a665afa46ff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781712"
---
# <a name="setup-and-install"></a>Instalator i instalacja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Do tworzenia natywnych dla systemów iOS, Android i Windows aplikacje z poziomu wspólnego języka C# / kodu platformy .NET przy użyciu platformy Xamarin, należy spełnić następujące warunki:  
  
- Do pracy z Windows i aplikacje dla systemu Android: Windows komputerze dewelopera z programem Visual Studio 2015 i Xamarin 4 zainstalowanych (patrz należy zwrócić uwagę poniżej). (Można również użyć programu Visual Studio 2013 postępując zgodnie z instrukcjami dotyczącymi [bezpośredniej instalacji Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (strony xamarin.com).)   
  
- Do pracy z aplikacjami systemu iOS: Mac z systemem OS X Yosemite (10.10.5) lub powyżej, za pomocą środowiska XCode i Xamarin zainstalowane.  
  
  Można skonfigurować komputery Windows i Mac, w tym samym czasie, a podczas wykonywania tych instalatorów można przejść przez [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) do odczytywania i obejrzyj materiał niezbędne tła.  
 
Jeśli masz problemy po wykonaniu tego Instalator i instalacja przy użyciu platformy Xamarin, opublikuj swoje pytanie na [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  31 marca 2016 r. wszystkie platformy Xamarin jest dołączony do wszystkich wersji programu Visual Studio nie wymagają ponoszenia dodatkowych kosztów i nie wymaga osobnej licencji. Program Xamarin Studio Community for Mac jest również dostępny bezpłatnie dla uczniów, deweloperzy OSS i małych zespołów. Należy pamiętać, że w dla istniejącej instalacji programu Visual Studio, które są skonfigurowane przy użyciu starszych licencje środowiska Xamarin, Xamarin należy zaktualizować do wersji 4.0.3.214 lub nowszej. Aby to zrobić, przejdź do **Narzędzia > Opcje > Xamarin > inne**, kliknij przycisk **Sprawdź teraz** łącze i pobierania 4.0.3.214 update. Po ponownym uruchomieniu programu Visual Studio, przejdź do **Narzędzia > konto usługi Xamarin...**  powinien zostać wyświetlony zaktualizowany stan.  
  
 **W tym temacie:**  
  
-   [Wymagania wstępne](#prereq)  
  
-   [Instalator Windows (Visual Studio i Xamarin)](#windows)  
  
-   [Instalator Mac (identyfikator Apple ID, Xcode i Xamarin)](#mac)  
  
##  <a name="prereq"></a> Wymagania wstępne  
  
1.  Aby uzyskać przeznaczonych dla Windows i Android:  
  
    1.  Zalecane: fizycznego komputera Windows (nie maszyna wirtualna) z systemem Windows 8 lub nowszy, co umożliwia użycie szybkie, funkcji Hyper-V na podstawie Visual Studio Emulator dla systemu Android, jeśli nie masz urządzenia z systemem Android. (Czy możemy wymienić należy komputer fizyczny i nie maszyna wirtualna?)  
  
    1.  Można użyć komputera, system Windows 7 lub starszym, w którym to przypadku użyjemy odtwarzacza Xamarin dla systemu Android jako emulator. 
    
    1. Dla obu konfiguracji będzie można uruchamiać aplikacje bezpośrednio na podłączone urządzenia fizycznego.  
  
1.  Aby uzyskać przeznaczonych dla systemu iOS:  
  
    1.  Mac lub komputerów Mac w sieci A mini z systemem OS X 10.10.5 programu OS X Yosemite lub nowszy (wymagane dla środowiska Xcode 7.1).  
  
    1.  Przy użyciu programu Visual Studio na komputerze Windows (7 +), co chroni główne środowisko programistyczne, komputerem Mac jest konieczne tylko Kompiluj i Debuguj aplikacje dla systemu iOS, Dołącz do symulatora systemu iOS lub powiązanego urządzeń, a za pomocą projektanta scenorysu w programie Visual Studio dla Projektowanie interfejsu użytkownika. Starsze modele Mac są całkowicie wystarczający dla tej roli pomocniczej.  
  
##  <a name="windows"></a> Instalator Windows (Visual Studio i Xamarin)  
  
> [!TIP]
>  Te instrukcje dotyczą programu Visual Studio 2015. Aby korzystać z platformy Xamarin w programie Visual Studio 2013 (wymagana jest aktualizacja 2), postępuj zgodnie z instrukcjami dotyczącymi [bezpośredniej instalacji Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (strony xamarin.com).  
  
1. [Pobierz i uruchom Instalatora programu Visual Studio 2015 w każdej wersji](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional lub Enterprise). Visual Studio 2015 Community jest bezpłatną; wersje Professional i Enterprise może służyć do wypróbowania przez 30 dni, po upływie których musisz zakupić licencję.  
  
   1.  Jeśli masz już zainstalowany program Visual Studio, otwórz **Panel sterowania > programy i funkcje**, wybierz **programu Visual Studio 2015** elementu, a następnie kliknij przycisk **zmiany**. Gdy Instalator zostanie otwarta, kliknij przycisk **Modyfikuj** , a następnie przejdź do kroku 3 poniżej.  
  
2. (Tylko w nowych instalacjach) W oknie Instalatora wybierz **niestandardowe** instalacji:  
  
    ![Wybranie opcji Niestandardowa w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "1 instalacji Xamarin Cross-Plat")  
  
3. Sprawdź następujące pola:  
  
   1.  **Tworzenie aplikacji mobilnych dla wielu Platform > C# / .NET (Xamarin)**. To będzie również automatycznie wybierać różne narzędzia dla systemu Android, w obszarze wspólne narzędzia i zestawy Software Development Kit. Tej opcji należy również zaktualizować wszelkich istniejących instalacji Xamarin.  
  
        ![Wybierz opcję Xamarin, w ramach granic&#45;Platform Mobile Development](../cross-platform/media/cross-plat-xamarin-setup-2.png "2 instalacji Xamarin Cross-Plat")  
  
   2.  W systemie Windows 8 +: **Tworzenie aplikacji mobilnych dla wielu Platform > program Microsoft Visual Studio Emulator for Android**. Uwaga: Jeśli jesteś przy użyciu komputerze z systemem Windows 7 lub starszej lub systemem Windows na komputerze Mac, upewnij się, to *unchecked*. Po wykonaniu kroku 5, zobacz "Note o emulatorów na komputerach Windows". Można także pozostawić to unchecked Aby przeprowadzić debugowanie tylko na fizycznych urządzeniach z systemem Android.  
  
   3.  (Opcjonalnie) Jeśli planujesz przeznaczone dla urządzeń Windows również sprawdzić **Windows i aplikacji sieci Web > Narzędzia do programowania aplikacji uniwersalnych Windows** i/lub **Windows 8.1 i Windows Phone 8.0/8.1 narzędzi**. Obejmują one opcje instalacji obrazów emulatorów, które będzie trwać dłużej, aby pobrać; zawsze możesz wrócić do Instalatora programu Visual Studio, aby je dodać później.  
  
4. Kliknij przycisk Instaluj i pozwól procesu, uruchom. Ponownie zajmie trochę czasu, w tym czasie możesz kontynuować instrukcje dotyczące konfigurowania komputerów Mac i przechodzą przez [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu swojego konta Microsoft, jeśli zostanie wyświetlony monit (jest to to samo konto, możesz za pomocą Windows). Następnie sprawdź, czy aktualizacje platformy Xamarin, za pośrednictwem **Narzędzia > Opcje > Xamarin** lub **Narzędzia > Opcje > Xamarin > inne**, gdzie znajdziesz **Sprawdź teraz** łącza:  
  
    ![Sprawdzanie, czy są aktualizacje platformy Xamarin w opcjach programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "3 instalacji Xamarin Cross-Plat")  
  
   > [!NOTE]
   >  Jak wspomniano wcześniej, należy upewnić się, że Xamarin do wersji 4.0.3.214 lub nowszej, aby uniknąć problemów z wcześniejszych licencje środowiska Xamarin.  

   Jeśli nie widzisz opcji dla platformy Xamarin w **Narzędzia > Opcje**, dokładnie sprawdzić instalację lub ponowne uruchomienie programu Visual Studio. Możesz również wyszukać platformy Xamarin w oknie dialogowym Opcje.
      
6. Windows 7 i Windows starszej lub jest uruchomiony na komputerze Mac, należy użyć [emulatora Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) braku urządzeń fizycznych. Zobacz uwagi poniżej.  
  
   **Należy zwrócić uwagę na emulatorach na Windows komputerów:** Ponieważ procesorów obsługują tylko jeden technologii wirtualizacji w danym momencie, najlepiej jest mieć tylko jedną używana na komputerze deweloperskim. Istnieją trzy główne wirtualizacji komputerów PC, technologie są funkcji Hyper-V (używane przez program Visual Studio Emulator dla systemu Android i emulatora Windows Phone), Virtual Box (wykorzystywane przez Genymotion) i Intel HAXM (wykorzystywane przez emulator zestawu SDK systemu Android). Ze względu na różne problemy między funkcją Hyper-V i Virtual Box najlepiej Aby użyć emulatorów tylko jednego typu na dowolnym danym komputerze, dlatego zalecenia powyżej, aby użyć funkcji Hyper-V w systemie Windows 8 i nowszych komputerów i Intel HAXM emulatorów w systemie Windows 7 i wcześniejszych oraz kiedy systemem Windows na komputerach Mac.  
  
##  <a name="mac"></a> Instalator Mac (identyfikator Apple ID, Xcode i Xamarin)  
  
1.  Utwórz bezpłatne identyfikator Apple ID w [ https://appleid.apple.com ](https://appleid.apple.com/) Jeśli nie masz jeszcze takiego. Jest to niezbędne do instalowania i rejestrowania się w środowisku Xcode.  
  
2.  Pobierz i zainstaluj środowisko Xcode ze [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/), i Dodaj swój identyfikator firmy Apple, zgodnie z opisem na [dodanie konta do środowiska XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Pobierz i zainstaluj platformę Xamarin, postępując zgodnie z instrukcjami wyświetlanymi [Instalowanie i konfigurowanie rozszerzenia Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (strony xamarin.com).  
  
4.  Po zakończeniu instalacji Xamarin na komputerach Mac i Windows, postępuj zgodnie z instrukcjami [nawiązywania połączenia z komputerem Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (strony xamarin.com), dzięki czemu można pracować z systemami iOS i Mac w programie Visual Studio na komputerze Windows.  
  
     Należy pamiętać, że oba komputery muszą należeć do tej samej sieci lokalnej.
