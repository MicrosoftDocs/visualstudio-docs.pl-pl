---
title: Instalacja i instalacja | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: 430c54527ad0a4647bb750c505942242688aaa17
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297720"
---
# <a name="setup-and-install"></a>Instalator i instalacja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby tworzyć natywne aplikacje dla systemów iOS, Android i Windows ze C#wspólnej bazy kodu/.NET przy użyciu platformy Xamarin, potrzebne są następujące elementy:  
  
- Do pracy z aplikacjami systemu Windows i Android: komputer deweloperski systemu Windows z zainstalowanym programem Visual Studio 2015 i Xamarin 4 (patrz Uwaga poniżej). (Można również użyć Visual Studio 2013, postępując zgodnie z instrukcjami dotyczącymi [bezpośredniego instalowania platformy Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com).   
  
- Do pracy z aplikacjami systemu iOS: system Mac OS X Yosemite (10.10.5) lub nowszy z zainstalowanym programem XCode i Xamarin.  
  
  Komputery z systemem Windows i Mac można skonfigurować w tym samym czasie, a podczas korzystania z tych instalatorów można [zapoznać się z tematem opracowywanie aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) , aby czytać i oglądać niezbędne materiały w tle.  
 
Jeśli masz problemy z używaniem platformy Xamarin po wykonaniu tej instalacji i instalacji, Opublikuj swoje pytanie w witrynie [forums.Xamarin.com](https://forums.xamarin.com/).
  
> [!NOTE]
> Od 31 marca 2016 wszystkie platformy Xamarin są dostępne we wszystkich wersjach programu Visual Studio bez dodatkowych kosztów i nie wymagają oddzielnej licencji. Xamarin Studio społeczność dla komputerów Mac jest również bezpłatna dla studentów, deweloperów OSS i małych zespołów. Należy pamiętać, że w przypadku istniejących instalacji programu Visual Studio, które są skonfigurowane przy użyciu wcześniejszych licencji platformy Xamarin, należy zaktualizować program Xamarin do wersji 4.0.3.214 lub nowszej. W tym celu przejdź do pozycji **narzędzia > opcje > Xamarin > inne**, kliknij link **Sprawdź teraz** i Pobierz aktualizację 4.0.3.214. Po ponownym uruchomieniu programu Visual Studio przejdź do pozycji **narzędzia > konto platformy Xamarin...** i sprawdź, czy Zaktualizowano stan.  
  
 **W tym temacie:**  
  
- [Wymagania wstępne](#prereq)  
  
- [Instalator systemu Windows (Visual Studio i Xamarin)](#windows)  
  
- [Konfiguracja komputerów Mac (Apple ID, Xcode i Xamarin)](#mac)  
  
## <a name="prereq"></a>Wymagania wstępne  
  
1. Dla systemu Windows i Android:  
  
    1. Zalecane: fizyczny komputer z systemem Windows (nie maszyna wirtualna) z systemem Windows 8 lub nowszym, który umożliwia korzystanie z szybkiej, opartej na funkcji Hyper-V emulatora programu Visual Studio dla systemu Android, jeśli nie masz urządzenia z systemem Android. (Czy należy zauważyć, że potrzebujesz fizycznego komputera, a nie maszyny wirtualnej?)  
  
    1. Możesz użyć komputera z systemem Windows 7 lub starszym. w takim przypadku jako emulator będziesz używać odtwarzacza Xamarin dla systemu Android. 
    
    1. Dla każdej konfiguracji można zawsze uruchamiać aplikacje bezpośrednio na podłączonych urządzeniach fizycznych.  
  
1. Dla docelowej platformy iOS:  
  
    1. Sieciowe komputery Mac lub Mac mini z systemem OS X Yosemite działającego w systemie OS X 10.10.5 lub nowszym (wymagane dla Xcode 7,1).  
  
    1. W przypadku korzystania z programu Visual Studio na komputerze z systemem Windows (7 +) jako podstawowego środowiska programistycznego komputer Mac jest niezbędny tylko do kompilowania i debugowania aplikacji systemu iOS, dołączania do symulatora systemu iOS lub urządzeń z tetheringem oraz do korzystania z projektanta scenorysów w programie Visual Studio dla Projektowanie interfejsu użytkownika. Starsze modele adresów MAC są całkowicie wystarczające dla tej roli pomocniczej.  
  
## <a name="windows"></a>Instalator systemu Windows (Visual Studio i Xamarin)  
  
> [!TIP]
> Te instrukcje dotyczą programu Visual Studio 2015. Aby można było używać platformy Xamarin z Visual Studio 2013 (wymagana jest aktualizacja Update 2), postępuj zgodnie z instrukcjami dotyczącymi [bezpośredniego instalowania platformy Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com).  
  
1. [Pobierz i uruchom Instalatora dla dowolnej wersji programu Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional lub Enterprise). Program Visual Studio 2015 Community to wersja bezpłatna. wersje Professional i Enterprise mogą być używane w okresie próbnym przez 30 dni, po których trzeba zakupić licencję.  
  
   1. Jeśli masz już zainstalowany program Visual Studio, Otwórz **Panel sterowania > programy i funkcje**, wybierz element **Visual Studio 2015** , a następnie kliknij przycisk **Zmień**. Po otwarciu Instalatora kliknij przycisk **Modyfikuj** i przejdź do kroku 3 poniżej.  
  
2. (Tylko nowe instalacje) W instalatorze wybierz instalację **niestandardową** :  
  
    ![Wybieranie opcji niestandardowej w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Konfiguracja Xamarin na wielu płytkach 1")  
  
3. Zaznacz następujące pola:  
  
   1. **Międzyplatformowe Programowanie aplikacji mobilnych C#>/.NET (Xamarin)** . Spowoduje to również automatyczne wybranie różnych narzędzi systemu Android w obszarze popularne narzędzia i zestawy SDK. Ta opcja powinna również aktualizować wszystkie istniejące instalacje platformy Xamarin.  
  
        ![Wybierz opcję platformy Xamarin w obszarze&#45;Programowanie aplikacji mobilnych na wiele platform](../cross-platform/media/cross-plat-xamarin-setup-2.png "Dwustronicowy program Xamarin — konfiguracja 2")  
  
   2. Dla systemu Windows 8 +: **Programowanie aplikacji mobilnych na wiele Platform > Microsoft Visual Studio Emulator for Android**. Uwaga: Jeśli używasz komputera z systemem Windows 7 lub starszym lub z systemem Windows na komputerze Mac, upewnij się, że to *pole wyboru*nie jest zaznaczone. Zapoznaj się z tematem "Uwaga dotycząca emulatorów na komputerach z systemem Windows" po kroku 5. Możesz również pozostawić to pole niezaznaczone, jeśli zamierzasz debugować tylko na fizycznych urządzeniach z systemem Android.  
  
   3. Obowiązkowe Jeśli planujesz kierowanie urządzeń z systemem Windows, Sprawdź także **Programowanie dla systemu Windows i sieci Web > narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows** i/lub **Windows 8.1 i Windows Phone 8.0/8.1**. Obejmują one opcje instalowania obrazów emulatorów, które będą trwać dłużej. zawsze możesz wrócić do Instalatora programu Visual Studio, aby dodać je później.  
  
4. Kliknij przycisk Instaluj, aby uruchomić proces. Po wykonaniu tej czynności potrwa to trochę czasu, w tym czasie możesz kontynuować instrukcje konfiguracji dla komputerów Mac i [zapoznać się z tematem opracowywanie aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu konto Microsoft, jeśli zostanie wyświetlony monit (jest to to samo konto, którego używasz w systemie Windows). Następnie sprawdź aktualizacje oprogramowania Xamarin za pomocą **narzędzi > opcje > narzędzia Xamarin** lub **Tools > opcje > Xamarin > Other**, gdzie znajdziesz link **Sprawdź teraz** :  
  
    ![Sprawdzanie aktualizacji platformy Xamarin w opcjach programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Instalator Xamarin na wielu platformach 3")  
  
   > [!NOTE]
   > Jak wspomniano wcześniej, pamiętaj, aby zaktualizować platformę Xamarin do wersji 4.0.3.214 lub nowszej, aby uniknąć problemów z wcześniejszymi licencjami platformy Xamarin.  

   Jeśli nie widzisz opcji dla platformy Xamarin w **narzędziach > opcje**, Sprawdź instalację lub spróbuj ponownie uruchomić program Visual Studio. Możesz również wyszukać Xamarin w oknie dialogowym Opcje.
      
6. W przypadku systemu Windows 7 i starszych wersji lub systemu Windows na komputerze Mac Użyj [emulatora Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) , jeśli nie masz urządzeń fizycznych. Zobacz uwagę poniżej.  
  
   **Uwaga dotycząca emulatorów na komputerach z systemem Windows:** Ponieważ procesory CPU obsługują tylko jedną technologię wirtualizacji jednocześnie, najlepszym rozwiązaniem jest użycie tylko jednego z nich na komputerze deweloperskim. Istnieją trzy główne technologie wirtualizacji to funkcja Hyper-V (używana przez emulator programu Visual Studio dla systemu Android i emulator Windows Phone), pole wirtualne (używane przez Genymotion) oraz procesor Intel HAXM (używany przez Emulator Android SDK). Ze względu na różne problemy między funkcją Hyper-V a usługą Virtual Box najlepiej używać emulatorów tylko jednego typu na dowolnym komputerze, dlatego powyższe zalecenia dotyczące używania funkcji Hyper-V na komputerach z systemem Windows 8 lub nowszym oraz emulatorów Intel HAXM w systemie Windows 7 i starszych, jak również Uruchamianie systemu Windows na komputerze Mac.  
  
## <a name="mac"></a>Konfiguracja komputerów Mac (Apple ID, Xcode i Xamarin)  
  
1. Utwórz bezpłatny identyfikator Apple ID w [https://appleid.apple.com](https://appleid.apple.com/) , jeśli go nie masz. Jest to niezbędne do zainstalowania i zalogowania się do usługi Xcode.  
  
2. Pobierz i zainstaluj Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)i Dodaj identyfikator Apple ID zgodnie z opisem w temacie [Dodawanie konta do usługi Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com).  
  
3. Pobierz i zainstaluj platformę Xamarin, postępując zgodnie z instrukcjami dotyczącymi [instalowania i konfigurowania platformy Xamarin. iOS](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) (Xamarin.com).  
  
4. Po zakończeniu instalowania platformy Xamarin na komputerach z systemem Windows i komputerów Mac postępuj zgodnie z instrukcjami dotyczącymi [łączenia się z komputerem Mac](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com), aby móc korzystać z systemu iOS i Mac z programu Visual Studio na komputerze z systemem Windows.  
  
     Należy pamiętać, że oba komputery muszą znajdować się w tej samej sieci lokalnej.
