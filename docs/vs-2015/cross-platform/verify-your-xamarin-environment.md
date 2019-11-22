---
title: Weryfikowanie środowiska Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: 134ed47d26fb7afb50bb50ac18418b436a563eb6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297582"
---
# <a name="verify-your-xamarin-environment"></a>Sprawdzanie środowiska Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zakończeniu instalacji (zobacz [Instalacja i instalacja](../cross-platform/setup-and-install.md)) Poświęć kilka minut, aby upewnić się, że wszystko jest gotowe do tworzenia aplikacji dla platformy Xamarin.  
  
 Po zakończeniu tych weryfikacji można wykonać jedną lub obie następujące czynności:  
  
- [Poznaj podstawowe informacje dotyczące tworzenia aplikacji za pomocą platformy Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
- [Tworzenie aplikacji za pomocą natywnego interfejsu użytkownika przy użyciu platformy Xamarin w programie Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Najpierw wybierz pozycję **narzędzia > opcje**, rozwiń węzeł **Xamarin > inne**, a następnie kliknij link **Sprawdź teraz, czy** są dostępne aktualizacje. Musisz używać platformy Xamarin 4.0.3.214 lub nowszej, aby uniknąć wcześniejszych problemów z licencjonowaniem.  
  
 Następnie utwórz nowe rozwiązanie Xamarin w programie Visual Studio przy użyciu **pliku > nowy projekt**, a następnie w oknie dialogowym rozwiń **szablon > inne języki C# > Visual > na wielu platformach**, wybierz pozycję **pusta aplikacja (natywna przenośna)** , a następnie kliknij przycisk OK. Dzięki temu można utworzyć rozwiązanie ze współdzielonym projektem biblioteki klas przenośnych i indywidualnymi projektami dla systemów Android, iOS i Windows:  
  
 ![Wyniki tworzenia nowego projektu na podstawie pustego szablonu przenośnego &#40;&#41; natywnej aplikacji](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin — Weryfikuj 1")  
  
> [!NOTE]
> Jeśli nie ma tam szablonów, zobacz [czy brakuje szablonów projektu Xamarin? Wypróbuj tę](#missing) stronę w dolnej części tej strony.  
  
## <a name="android"></a>Android  
  
1. Zapoznaj się z najnowszymi narzędziami Android SDK zainstalowanych za pomocą **narzędzi > Android > Android SDK Manager** i zainstalowania najnowszej wersji Android SDK Tools, Android SDK platformy i narzędzi do tworzenia i Android SDK składników. Należy pamiętać, że nie jest konieczne zawsze zainstalowanie najnowszego poziomu interfejsu API systemu Android; Wymagany interfejs API zależy od poziomu platformy, który ma być docelowy. Ogólnie rzecz biorąc zainstalowanie środowiska Xamarin zainstaluje wymagany poziom platformy.  

2. Weryfikowanie projektanta systemu Android: w projekcie systemu Android w Eksplorator rozwiązań Otwórz **> układu zasobów > głównym** pliku. axml. (Jeśli ten plik nie jest wyświetlany bezpośrednio, spróbuj wyszukać go w Eksplorator rozwiązań; istnieje tylko w projekcie systemu Android, a nie w projekcie systemu iOS).  
  
    - Jeśli zostanie wyświetlony komunikat o błędzie informujący, że zainstalowana Android SDK jest zbyt stara, kliknij pozycję **otwórz Android SDK** w tym komunikacie, aby wybrać i zainstalować najnowsze narzędzia wersji zestawu SDK dostępne w kroku 1 powyżej. 
  
3. Sprawdź poprawność kompilowania i debugowania w emulatorze (lub urządzeniu):  
  
    - Kliknij prawym przyciskiem myszy projekt systemu Android w Eksplorator rozwiązań i wybierz pozycję **Ustaw jako projekt startowy**.  
  
         ![Program Visual Studio ustawiony jako opcja projektu startowego](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin — weryfikacja 2")  
  
    - Wybierz odpowiedni emulator w oparciu o docelową wersję systemu Android. Jeśli masz dołączone do komputera urządzenie deweloperskie z systemem Android, zobaczysz je również w tym miejscu obok emulatorów:  
  
        - Windows 8 +: Wybierz element docelowy **emulatora vs** na liście rozwijanej Debuguj programu Visual Studio, jak pokazano poniżej, i uruchom debuger, naciskając klawisz **F5**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do emulatora programu Visual Studio dla systemu Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (blog programu Visual Studio ALM). Jeśli wystąpią problemy z rozpoczęciem działania emulatora, zobacz [Rozwiązywanie problemów z programem Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Możesz również utworzyć nowe profile urządzeń dla emulatora, wybierając pozycję **narzędzia > Emulator programu Visual Studio dla systemu Android...** .  
  
             ![Wybieranie emulatora programu Visual Studio dla systemu Android jako elementu docelowego debugowania](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin — Sprawdź 3")  
  
             Uwaga: Jeśli nie widzisz opcji **narzędzia > Visual Studio Emulator for Android...** — menu, może nie być zainstalowany sam emulator. Przejdź do **Panelu sterowania, > programy i funkcje**, wybierz pozycję **Microsoft Visual Studio**, a następnie kliknij przycisk **Zmień** , aby ponownie uruchomić Instalatora. Kliknij przycisk **Modyfikuj** w instalatorze, zaznacz pole wyboru **Międzyplatformowe programowanie aplikacji mobilnych > Microsoft Visual Studio Emulator for Android**, a następnie kliknij przycisk **Aktualizuj**.  
  
        - W przypadku systemu Windows 7 i starszych wersji: zamiast tego wybierz z listy rozwijanej pozycję Xamarin Player dla systemu Android i naciśnij klawisz F5, aby uruchomić. Aby uzyskać szczegółowe informacje na temat programu Xamarin Player, jego Menedżera urządzeń i porad dotyczących rozwiązywania problemów, Przeczytaj [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
> [!NOTE]
> W programie Visual Studio można zauważyć, że na pasku narzędzi zostanie wyświetlony przycisk Emulator systemu Android Manager (AVD) (Pokaż poniżej), w którym zostanie otwarty Menedżer urządzeń używany do konfigurowania emulatora systemu Google Android.  Nie ma to wpływu na emulator programu Visual Studio dla systemu Android lub Xamarin Player, z których każdy ma własny Menedżer urządzeń do konfigurowania profilów.  Aby uzyskać szczegółowe informacje, zobacz [wprowadzenie do emulatora programu Visual Studio dla systemu Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (blog Visual Studio ALM) i [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
> ![CrossPlat Xamarin — Weryfikuj 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin — Weryfikuj 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1. Sprawdź poprawność projektanta Windows Phone: w projekcie Windows Phone w Eksplorator rozwiązań otwórz plik **MainPage. XAML** .  
  
2. Sprawdź poprawność kompilowania i debugowania w emulatorze lub na urządzeniu (Uwaga: konieczne będzie zainstalowanie emulatora Windows Phone za pomocą Instalatora programu Visual Studio dla tego kroku lub urządzenia z tetheringem):  
  
    - Kliknij prawym przyciskiem myszy projekt Windows Phone w Eksplorator rozwiązań i wybierz pozycję **Ustaw jako projekt startowy**.  
  
    - Wybierz element docelowy **emulatora 8,1** lub dołączonego urządzenia na liście rozwijanej Debuguj programu Visual Studio, jak pokazano poniżej, i uruchom debuger, naciskając klawisz F5.  
  
         ![Wybieranie emulatora Windows Phone jako elementu docelowego debugowania](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin — Sprawdź 4")  
  
    - Jeśli wystąpią problemy z rozpoczęciem działania emulatora, Przeczytaj [temat Rozwiązywanie problemów z emulatorem Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1. Upewnij się, że komputer Mac jest dostępny w sieci i sparowany z programem Visual Studio, zgodnie z opisem w artykule [nawiązywanie połączenia z komputerem Mac](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com).  
  
2. Sprawdź poprawność projektanta scenorysu: w projekcie systemu iOS w Eksplorator rozwiązań Otwórz **główny plik scenorysu** . W tym miejscu program Visual Studio obsługuje projektanta, który jest uruchomiony zdalnie na komputerze Mac.  
  
3. Weryfikuj Kompilowanie i debugowanie:  
  
    1. Kliknij prawym przyciskiem myszy projekt iOS w Eksplorator rozwiązań i wybierz pozycję **Ustaw jako projekt startowy**.  
  
    2. Wybierz element docelowy **iPhoneSimulator** z listy rozwijanej kompilacja programu Visual Studio, jak pokazano poniżej, lub miejsce docelowe **telefonu iPhone** , jeśli masz urządzenie z systemem tetheringu. Jeśli na liście nie ma żadnych symulatorów, uruchom Xcode na komputerze Mac, wybierz pozycję **Preferencje Xcode->** i kliknij pozycję **Pobierz**. W obszarze **składniki** powinny być widoczne wersje symulatora, które są dostępne do pobrania. Dodatkowe instrukcje dotyczące debugowania można znaleźć na stronie [debugowania](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) platformy Xamarin (Xamarin.com).  
  
         ![Wybieranie elementu docelowego kompilacji iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin — Weryfikowanie 5")  
  
    3. Wybierz element docelowy telefonu iPhone z listy rozwijanej Debuguj programu Visual Studio, jak pokazano poniżej, i uruchom debuger, naciskając klawisz F5. Spowoduje to uruchomienie symulatora na komputerze Mac, na którym będziesz korzystać z aplikacji, podczas gdy debugowanie odbywa się w programie Visual Studio. Jeśli masz fizyczny iPhone lub tablet iPad podłączony do komputera Mac, pojawi się on tutaj i możesz go wybrać zamiast tego. Jeśli nie widzisz żadnych urządzeń lub symulatorów, sprawdź połączenie z komputerem Mac, przeglądając temat połączony w kroku 1 powyżej lub przechodząc do **narzędzi** >**iOS** >**Xamarin Mac Agent**  
  
         ![Wybieranie elementu docelowego debugowania telefonu iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin — Weryfikuj 6")  
  
    4. Jeśli wystąpią problemy z nawiązywaniem połączenia z komputerem Mac, należy przeczytać [temat Rozwiązywanie problemów z połączeniem](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting) (Xamarin.com).  
  
    5. Jeśli zostanie wyświetlony komunikat o błędzie informujący, że nie zainstalowano profilów aprowizacji pasujących do zainstalowanych kluczy podpisywania systemu iOS, wykonaj następujące czynności:  
  
        - Sprawdź, czy konto Apple ID zostało dodane do Xcode na komputerze Mac, zgodnie z opisem w temacie [Dodawanie konta do usługi Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com).  Po dodaniu konta Pamiętaj o ponownym uruchomieniu zarówno programu Visual Studio, jak i Xcode.  
  
             ![CrossPlat Xamarin — Sprawdź 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin — Sprawdź 8")  
  
        - Sprawdź, czy we właściwościach projektu systemu iOS na karcie podpisywanie pakietu systemu iOS pole niestandardowe uprawnienie jest puste dla aktywnej konfiguracji debugowania.  Uwaga: należy wypróbować tylko usunięcie tego ustawienia, Jeśli napotkasz powyższy komunikat o błędzie.  
  
## <a name="missing"></a>Czy brakuje szablonów projektu Xamarin? Wypróbuj ten  
 Szablony mogą być niedostępne, Jeśli instalujesz program Xamarin bezpośrednio z witryny Xamarin w sieci Web i masz zainstalowane Visual Studio 2013 i Visual Studio 2015 obok siebie. Można to łatwo naprawić, chociaż: wystarczy włączyć funkcję **Xamarin for Visual Studio 2015** w programie instalacyjnym Xamarin.  
  
1. W panelu sterowania otwórz aplet **programy i funkcje**, wybierz element **Xamarin** , a następnie kliknij przycisk **Zmień**.  
  
2. W Kreatorze instalacji programu Xamarin, który zostanie wyświetlony, kliknij przycisk **dalej** , a następnie **Zmień**.  
  
3. Na liście opcjonalnych funkcji do zainstalowania rozwiń węzeł **Xamarin dla programu Visual Studio 2015**, wybierz **zostanie zainstalowany na dysku lokalnym**, a następnie kliknij przycisk **dalej** , aby kontynuować dodawanie funkcji.
