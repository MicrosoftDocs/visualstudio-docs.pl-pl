---
title: Instalacja, instalacja i weryfikacja dla użytkowników komputerów Mac | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 703ee752a9f16f0abc5e4813707890a6d17947af
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538940"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat jest przeznaczony dla deweloperów pracujących głównie na komputerze Mac, którzy Opcjonalnie korzystają z programu Visual Studio na maszynie wirtualnej z systemem Windows na komputerach Mac. Jeśli jesteś deweloperem pracującym głównie na komputerze z systemem Windows i musisz skonfigurować dodatkowy adres MAC dla systemu iOS, zobacz temat główna [Instalacja i instalacja](../cross-platform/setup-and-install.md) .  
  
 Aby można było korzystać z platformy Xamarin na komputerze Mac, potrzebne są następujące elementy:  
  
- Konto platformy Xamarin. Przejdź do [https://www.xamarin.com/](https://www.xamarin.com/) i kliknij przycisk **Zaloguj się** w prawym górnym rogu strony, a następnie kliknij pozycję **Utwórz nowe konto** na wyświetlonej stronie. Wybierz adres e-mail i hasło do konta platformy Xamarin.  
  
- Komputer Mac z OSX Yosemite (10,10) lub nowszym z zainstalowanym programem Xcode 7 i Xamarin 4.  
  
- Jedna z następujących konfiguracji:  
  
  - **Do uruchamiania Xamarin Studio bezpośrednio na komputerze Mac:** Xamarin Studio to środowisko programistyczne Xamarin, które obsługuje tworzenie aplikacji dla systemów Android, iOS i C#Windows przy użyciu programu.  Aby zapoznać się z krótkim omówieniem Xamarin Studio, zapoznaj się z tematem [Xamarin Studio Overview](https://xamarin.com/studio) (Xamarin.com).  
  
  - **Jeśli na komputerze Mac już skonfigurowano Parallels lub VMware, możesz** uruchamiać system Windows z programem Visual Studio 2015 i Xamarin 4 wewnątrz równolegle lub VMware.  W przypadku tej konfiguracji platforma Xamarin jest rozszerzeniem instalowanym z programem Visual Studio, które zapewnia możliwość korzystania z programu Visual Studio jako środowiska deweloperskiego do tworzenia aplikacji dla systemów Android, iOS i C#WinPhone przy użyciu usługi.  Należy pamiętać, że można uzyskać bezpłatną 3-miesięczną subskrypcję równoległą w ramach programu Visual Studio Developer Essentials. Zobacz [Microsoft Visual Studio Dev Essentials obejmuje równolegle dostęp do oprogramowania Desktop Pro i Parallels](https://www.parallels.com/blogs/) (na Blog Parallels).  
  
  Ten temat zawiera instrukcje dotyczące tych wymagań.  Gdy proces instalacji jest uruchomiony, możesz zapoznać się z tematem [Omówienie opracowywania aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) w celu odczytywania i oglądania niezbędnego materiału w tle.  
  
  **W tym temacie:**  
  
- [Konfiguracja komputerów Mac (Apple ID, Xcode i Xamarin)](#mac)  
  
- [Instalacja systemu Windows wewnątrz równoległych (Visual Studio i Xamarin)](#windows)  
  
- [Weryfikowanie środowiska](#verify)  
  
## <a name="mac"></a>Konfiguracja komputerów Mac (Apple ID, Xcode i Xamarin)  
  
1. Jeśli jeszcze tego nie zrobiono, Utwórz bezpłatny identyfikator Apple ID pod [identyfikatorem Apple ID](https://appleid.apple.com/) . Jest to niezbędne do zainstalowania i zalogowania się do usługi Xcode.  
  
2. Pobierz i zainstaluj Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).  
  
3. Pobierz i zainstaluj platformę Xamarin, postępując zgodnie z instrukcjami dotyczącymi [instalowania i konfigurowania platformy Xamarin. iOS](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) (Xamarin.com).  
  
4. Po zakończeniu instalowania platformy Xamarin na komputerach z systemem Windows i komputerów Mac postępuj zgodnie z instrukcjami dotyczącymi [łączenia się z komputerem Mac przy użyciu usługi XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com), aby móc korzystać z systemu iOS i Mac z programu Visual Studio na komputerze z systemem Windows.  
  
## <a name="windows"></a>Instalacja systemu Windows wewnątrz równoległych (Visual Studio i Xamarin)  
  
1. Korzystając z pulpitu systemu Windows, który został skonfigurowany w ramach równoległych/VMWare, [Pobierz i uruchom Instalatora dla dowolnej wersji programu Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional lub Enterprise). Program Visual Studio 2015 Community to wersja bezpłatna. wersje Professional i Enterprise mogą być używane w okresie próbnym przez 30 dni.  
  
2. W instalatorze wybierz instalację **niestandardową** :  
  
     ![Wybieranie opcji niestandardowej w instalacji programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Konfiguracja Xamarin na wielu płytkach 1")  
  
3. Zaznacz/Wyczyść następujące pola:  
  
    1. Sprawdź **Międzyplatformowe Programowanie aplikacji mobilnych C#>/.NET (Xamarin)** . Spowoduje to również automatyczne wybranie różnych narzędzi systemu Android w obszarze popularne narzędzia i zestawy SDK.  
  
         ![Wybierz opcję platformy Xamarin w obszarze&#45;Programowanie aplikacji mobilnych na wiele platform](../cross-platform/media/cross-plat-xamarin-setup-2.png "Dwustronicowy program Xamarin — konfiguracja 2")  
  
    2. Wyczyść **Microsoft Visual Studio Emulator for Android > tworzenia aplikacji mobilnych dla wielu platform**.  
  
4. Kliknij przycisk Instaluj, aby uruchomić proces. Po wykonaniu tej czynności potrwa to trochę czasu, w tym czasie możesz kontynuować pracę z tym tematem i [zapoznać się z tematem opracowywanie aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po zakończeniu instalacji uruchom program Visual Studio i zaloguj się przy użyciu konto Microsoft, jeśli zostanie wyświetlony monit (jest to to samo konto, którego używasz w systemie Windows). Następnie sprawdź aktualizacje oprogramowania Xamarin za pomocą **narzędzi > opcje > narzędzia Xamarin** lub **Tools > opcje > Xamarin > Other**, gdzie znajdziesz link **Sprawdź teraz** :  
  
     ![Sprawdzanie aktualizacji platformy Xamarin w opcjach programu Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Instalator Xamarin na wielu platformach 3")  
  
    > [!NOTE]
    > Pamiętaj, aby zaktualizować platformę Xamarin do wersji 4.0.3.214 lub nowszej, aby uniknąć problemów z wcześniejszymi licencjami platformy Xamarin.  Jeśli podjęto próbę sprawdzenia dostępności aktualizacji i wyświetlenia błędu dotyczącego narzędzi Microsoft Build Tools, zobacz wątek na [forach platformy Xamarin](https://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6. Po zakończeniu instalowania platformy Xamarin na komputerach z systemem Windows i komputerów Mac postępuj zgodnie z instrukcjami dotyczącymi [nawiązywania połączenia z komputerem Mac przy użyciu usługi XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com), aby móc korzystać z systemu iOS w programie Visual Studio.  
  
## <a name="verify"></a>Weryfikowanie środowiska  
 Po zakończeniu instalacji Poświęć kilka minut, aby upewnić się, że wszystko jest gotowe do tworzenia aplikacji dla platformy Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 Najpierw upewnij się, że po przejściu do podanych linków **Xamarin Studio** zaznaczone w prawym górnym rogu, aby zobaczyć poprawną wersję dokumentacji platformy Xamarin:  
  
 ![Wybór Xamarin Studio, aby wyświetlić poprawną dokumentację w witrynie Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Sprawdź poprawność tworzenia projektu systemu Android, postępując zgodnie z instrukcjami dotyczącymi [tworzenia projektu systemu Android](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com).  
  
2. Sprawdź poprawność debugowania w odtwarzaczu systemu Android za pomocą programu [Android player > integrację z dokumentacją Xamarin Studio](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (Xamarin.com).  
  
   **iOS**  
  
3. Sprawdź poprawność tworzenia projektu dla systemu iOS, postępując zgodnie z instrukcjami dotyczącymi [tworzenia systemu iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com).  
  
4. Sprawdź poprawność debugowania w symulatorze systemu iOS za pomocą [debugowania w dokumentacji symulatora](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (Xamarin.com).  
  
### <a name="visual-studio"></a>{1&gt;Visual Studio&lt;1}  
 Po pierwsze upewnij się, że po przejściu do podanych linków zostanie wybrany **program Visual Studio** w prawym górnym rogu, aby zobaczyć poprawną wersję dokumentacji platformy Xamarin:  
  
 ![Wybieranie programu Visual Studio w celu wyświetlenia odpowiedniej dokumentacji w witrynie Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Zaloguj się również do konta platformy Xamarin za poorednictwem **narzędzi > konto platformy Xamarin..** ..  
  
 **Android**  
  
1. Sprawdź poprawność tworzenia projektu systemu Android, postępując zgodnie z instrukcjami dotyczącymi [tworzenia projektu systemu Android](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com).  
  
2. Weryfikowanie projektanta systemu Android: w projekcie systemu Android w Eksplorator rozwiązań Otwórz **> układu zasobów > głównym** pliku. axml.  
  
   - Jeśli zostanie wyświetlony komunikat o błędzie informujący, że zainstalowana Android SDK jest zbyt stara, "kliknij pozycję **otwórz Android SDK** w tym komunikacie i wybierz najnowszą wersję zestawu SDK. Należy pamiętać, że program Visual Studio musi być uruchomiony jako administrator, aby zaktualizować zestaw SDK.  
  
3. Sprawdź, czy możesz nawiązać połączenie z programu Visual Studio do emulatora zainstalowanego na komputerze Mac.  Wynikiem tego jest to, że program Xamarin Player zostanie wyświetlony na liście emulatorów, które można wybrać w programie Visual Studio na potrzeby debugowania.  Aby to zrobić, postępuj zgodnie z instrukcjami dotyczącymi [łączenia programu Visual Studio z Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
   **iOS**  
  
4. Upewnij się, że komputer Mac jest dostępny w sieci i sparowany z programem Visual Studio, zgodnie z opisem w artykule [nawiązywanie połączenia z komputerem Mac przy użyciu usługi XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com).  
  
5. Sprawdź poprawność tworzenia projektu dla systemu iOS, postępując zgodnie z instrukcjami dotyczącymi [tworzenia systemu iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com).  
  
6. Sprawdź poprawność projektanta scenorysu: w projekcie systemu iOS w Eksplorator rozwiązań otwórz plik **MainStoryboard. scenorys** . W tym miejscu program Visual Studio obsługuje projektanta, który jest uruchomiony zdalnie na komputerze Mac.  
  
7. Weryfikuj Kompilowanie i debugowanie:  
  
   1. Kliknij prawym przyciskiem myszy projekt iOS w Eksplorator rozwiązań i wybierz pozycję **Ustaw jako projekt startowy**.  
  
   2. Wybierz element docelowy **iPhoneSimulator** z listy rozwijanej kompilacja programu Visual Studio, jak pokazano poniżej. Jeśli na liście nie ma żadnych symulatorów, uruchom Xcode na komputerze Mac, wybierz pozycję **Preferencje Xcode->** i kliknij pozycję **Pobierz**. W obszarze **składniki** powinny być widoczne wersje symulatora, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć na stronie [debugowania](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) platformy Xamarin (Xamarin.com).  
  
        ![Wybieranie elementu docelowego kompilacji iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin — Weryfikowanie 5")  
  
   3. Wybierz element docelowy telefonu iPhone z listy rozwijanej Debuguj programu Visual Studio, jak pokazano poniżej, i uruchom debuger, naciskając klawisz F5. Spowoduje to uruchomienie symulatora na komputerze Mac, na którym będziesz korzystać z aplikacji, podczas gdy debugowanie odbywa się w programie Visual Studio.  
  
        ![Wybieranie elementu docelowego debugowania telefonu iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin — Weryfikuj 6")
