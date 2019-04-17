---
title: Sprawdź swoje środowisko Xamarin | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: a8be3ad8b102677014aca4b59fed29f11cf3d50a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661051"
---
# <a name="verify-your-xamarin-environment"></a>Sprawdzanie środowiska Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po ukończeniu ma instalatorów (zobacz [Instalator i instalacja](../cross-platform/setup-and-install.md)), Poświęć kilka minut, aby sprawdzić, wszystko jest gotowe do środowisko programowania Xamarin.  
  
 Po zakończeniu tych weryfikacji możesz wykonać jedną lub obie następujące instruktaże:  
  
-   [Poznaj podstawowe informacje dotyczące tworzenia aplikacji za pomocą platformy Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
-   [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Najpierw wybierz **Narzędzia > Opcje**, rozwiń węzeł **Xamarin > inne**i kliknij przycisk **Sprawdź teraz** łącza dla aktualizacji. Należy korzystać z platformy Xamarin 4.0.3.214 lub nowszej, aby uniknąć problemów z poprzednim licencjonowania.  
  
 Następnie utwórz nowe rozwiązanie platformy Xamarin w programie Visual Studio przy użyciu **Plik > Nowy projekt**, następnie w oknie dialogowym Rozwiń **Szablony > inne języki > Visual C# > dla wielu Platform**, wybierz opcję  **Pusta aplikacja (natywny przenośny)** i kliknij przycisk OK. Spowoduje to utworzenie rozwiązania przy użyciu projektu biblioteki klas przenośnych udostępnionych i poszczególnych projektów dla systemu Android, iOS i Windows:  
  
 ![Wyniki tworzenia nowego projektu z pustą aplikację &#40;przenośnego macierzystego&#41; szablonu](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Sprawdź 1")  
  
> [!NOTE]
>  Jeśli szablony nie są tam widoczne [szablonów projektu Xamarin, Brak? Skorzystaj z tej](#missing) u dołu tej strony.  
  
## <a name="android"></a>Android  
  
1. Sprawdź, czy jest zainstalowany, przechodząc do najnowszych narzędzi zestawu SDK systemu Android **Narzędzia > Android > Menedżer zestawów SDK** i zainstalowanie najnowszej wersji Android SDK Tools, narzędzi platformy zestawu Android SDK i narzędzi kompilacji zestawu SDK systemu Android składniki. Należy pamiętać, że nie jest konieczne Zawsze instaluj najnowsze poziom interfejsu API systemu Android; Interfejs API, które są potrzebne zależy od poziomu platformy, która ma pod kątem. Ogólnie rzecz biorąc instalacji Xamarin, zostanie zainstalowany o wymaganym poziomie platformy.  

2.  Sprawdź poprawność narzędzia Android designer: w projekcie dla systemu Android w Eksploratorze rozwiązań Otwórz **zasobów > Układ > Main.axml** pliku. (Jeśli nie widzisz ten plik bezpośrednio, spróbuj wyszukać w Eksploratorze rozwiązań; istnieje w projekcie dla systemu Android tylko i nie w projekcie dla systemu iOS.)  
  
    - Jeśli zostanie wyświetlony błąd informujący o "Zainstalowanego zestawu SDK systemu Android jest zbyt stara", kliknij przycisk **Otwórz zestawu Android SDK** w tej wiadomości, aby wybierać i instalować najnowszych narzędzi zestawu SDK w wersji dostępna jako w kroku 1 powyżej. 
  
3.  Sprawdzanie poprawności, kompilowanie i debugowanie do emulatora (lub urządzenia):  
  
    -   Kliknij prawym przyciskiem myszy projekt systemu Android w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
         ![Visual Studio Ustaw jako projekt startowy — opcja](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin Sprawdź 2")  
  
    -   Wybierz odpowiedni emulator, zależnie od docelowej wersji systemu Android; Jeśli masz urządzenia z systemem Android development podłączone do komputera, pojawi się także w tym miejscu liście wraz z emulatorów:  
  
        -   System Windows 8 i nowsze: Wybierz **emulatora VS** docelowe liście rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchom debuger, naciskając klawisz **F5**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do programu Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blog Visual Studio ALM). Jeśli wystąpią problemy z integracją emulatora do pracy, zobacz [Rozwiązywanie problemów z emulatorem programu Visual Studio dla systemu Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Można również tworzyć nowych profilów urządzeń dla emulatora, wybierając **Narzędzia > Visual Studio Emulator for Android...** .  
  
             ![Wybieranie Visual Studio Emulator for Android jako obiekt docelowy debugowania](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Sprawdź 3")  
  
             Uwaga: Jeśli nie widzisz **Narzędzia > Visual Studio Emulator for Android...**  opcji menu, możesz nie mieć emulatora, sama zainstalowane. Przejdź do **Panel sterowania > programy i funkcje**, wybierz opcję **programu Microsoft Visual Studio**i kliknij przycisk **zmiany** ponownie uruchomić Instalatora. Kliknij przycisk **Modyfikuj** w Instalatorze, zaznacz pole wyboru, aby uzyskać **Cross Platform Mobile Development > program Microsoft Visual Studio Emulator for Android**i kliknij przycisk **aktualizacji**.  
  
        -   Windows 7 i starszych: Wybierz odtwarzacza Xamarin dla systemu Android w menu rozwijanego zamiast tego i naciśnij klawisz F5, aby uruchomić. Szczegółowe informacje dotyczące programu Xamarin Player, jego Menedżera urządzeń i rozwiązywanie problemów z porad, przeczytaj [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (strony xamarin.com).  
  
> [!NOTE]
>  W programie Visual Studio można zauważyć obecność przycisk Menedżera emulatora systemu Android (AVD) na pasku narzędzi (wyświetlane poniżej), co spowoduje otwarcie Menedżera urządzeń, w szczególności służąca do konfigurowania emulator systemu Google Android.  Nie ma to wpływu na albo Visual Studio Emulator dla systemu Android lub Xamarin Player, z których każdy ma swoje własne Menedżera urządzeń dotyczące konfigurowania profilów.  Zobacz [wprowadzenie do programu Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blog Visual Studio ALM) i [Xamarin Android Player](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (strony xamarin.com) Aby uzyskać szczegółowe informacje.  
> ![CrossPlat Xamarin Sprawdź 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin Sprawdź 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1.  Sprawdzanie poprawności projektanta Windows Phone: w projekcie Windows Phone w Eksploratorze rozwiązań Otwórz **MainPage.xaml** pliku.  
  
2.  Sprawdź poprawność kompilowanie i debugowanie w emulatorze lub na urządzeniu (Uwaga: musisz mieć zainstalowane za pomocą Instalatora programu Visual Studio dla tego kroku lub urządzenie powiązane emulator Windows Phone):  
  
    -   Kliknij prawym przyciskiem myszy projekt Windows Phone w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
    -   Wybierz **Emulator 8.1** docelowego lub podłączonego urządzenia w programie Visual Studio debugować listy rozwijanej, jak pokazano poniżej i uruchomić debuger, naciskając klawisz F5.  
  
         ![Wybieranie emulator Windows Phone jako cel debugowania](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin Sprawdź 4")  
  
    -   Jeśli wystąpią problemy z emulatora do pracy, przeczytaj wprowadzenie [Rozwiązywanie problemów z emulatora systemu Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1.  Upewnij się, że komputer Mac jest dostępny w sieci oraz sparowany z programem Visual Studio, zgodnie z opisem na [nawiązywania połączenia z komputerem Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (strony xamarin.com).  
  
2.  Sprawdzanie poprawności projektanta scenorysu: w projekcie dla systemu iOS w Eksploratorze rozwiązań Otwórz **Main.storyboard** pliku. W tym miejscu Visual Studio jest hostem tego projektanta, który jest zdalnie uruchomiony na komputerze Mac.  
  
3.  Sprawdzanie poprawności, kompilowania i debugowania:  
  
    1.  Kliknij prawym przyciskiem myszy projekt iOS, w Eksploratorze rozwiązań i wybierz **Ustaw jako projekt startowy**.  
  
    2.  Wybierz **iPhoneSimulator** element docelowy z rozwijanej kompilacji programu Visual Studio, jak pokazano poniżej, lub **iPhone** docelowy, jeśli masz urządzenie powiązane. Jeśli nie są wyświetlane nie symulatorów, uruchom program Xcode na komputerze Mac, wybierz **Xcode -> Preferencje**i kliknij przycisk **Pobierz**. W obszarze **składniki** powinien zostać wyświetlony wersji symulator, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć na środowisku Xamarin [debugowanie](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) strony (strony xamarin.com).  
  
         ![Wybieranie iPhoneSimulator tworzenia pod kątem](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Sprawdź 5")  
  
    3.  Wybierz obiekt docelowy dla telefonu iPhone z rozwijanej debugowania programu Visual Studio, jak pokazano poniżej, a następnie uruchom debuger, naciskając klawisz F5. Spowoduje to uruchomienie symulator na komputerze Mac, w którym interakcji z aplikacją, podczas gdy profilowanie odbywa się w programie Visual Studio. Jeśli masz fizycznego dla telefonu iPhone lub iPad nawiązanie połączenia z komputerem Mac, pojawi się w tym miejscu i można ją wybrać w zamian. Jeśli nie ma żadnych urządzeń ani symulatorów wymienione, sprawdź połączenie z komputerem Mac, przeglądając tematu w kroku 1 powyżej połączone lub przechodząc do **narzędzia** >**iOS**  > **Xamarin Mac Agent**  
  
         ![Wybieranie obiektu docelowego debugowania dla telefonu iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Sprawdź 6")  
  
    4.  Jeśli wystąpią problemy z połączeniem z komputerem Mac, zapoznaj się z [Rozwiązywanie problemów z połączeniem](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) (strony xamarin.com).  
  
    5.  Jeśli zostanie wyświetlony błąd powiedzenie "żaden z zainstalowanych profilów aprowizacji pasuje do zainstalowanych kluczy podpisywania systemu iOS, wykonaj następujące czynności:  
  
        -   Sprawdź, czy konta Apple Id jest dodany w środowisku Xcode na komputerze Mac, zgodnie z opisem na [dodanie konta do środowiska Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Po dodaniu konta, upewnij się ponownie uruchomić Visual Studio i narzędziu Xcode.  
  
             ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")  
  
        -   Sprawdź w aplikacjach dla systemów iOS właściwości projektu w narzędziu iOS pakietu kartę podpisywania, że pole niestandardowe uprawnienie jest pusta dla konfiguracji debugowania aktywnego.  Uwaga: należy tylko spróbować usuwania tego ustawienia, jeśli wystąpiły powyżej komunikat o błędzie.  
  
##  <a name="missing"></a> Brak szablonów projektu Xamarin? Wypróbuj  
 Szablony może brakować, jeśli Zainstaluj platformę Xamarin bezpośrednio z witryny sieci Web platformy Xamarin i programu Visual Studio 2013 i Visual Studio 2015 zostały zainstalowane side-by-side. Można łatwo rozwiązać, jednak: po prostu włącz **Xamarin dla programu Visual Studio 2015** funkcja w Instalatorze programu Xamarin.  
  
1.  W Panelu sterowania otwórz **programy i funkcje**, wybierz **Xamarin** elementu, a następnie kliknij przycisk **zmiany**.  
  
2.  W Kreatorze instalacji Xamarin, która pojawia się kliknij **dalej** i następnie **zmiany**.  
  
3.  Na liście opcjonalnych funkcji do zainstalowania rozwiń **Xamarin dla programu Visual Studio 2015**, wybierz **zostanie zainstalowana na lokalnym dysku**i kliknij przycisk **dalej** dodawania Funkcja.
