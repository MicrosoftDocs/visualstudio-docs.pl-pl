---
title: Tworzenie aplikacji dla systemu Android Native Activity | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b8fbc8d651536c35ee2dae985876f38336c9061
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588909"
---
# <a name="create-an-android-native-activity-app"></a>Tworzenie aplikacji systemu Android działania natywnego

W przypadku instalowania międzyplatformowego **opracowywania aplikacji mobilnych C++ przy użyciu** obciążenia programu Program Visual Studio może służyć do tworzenia w pełni funkcjonalnego środowiska z natywnymi działaniami systemu Android. Zestaw Android Native Development Kit (NDK) stanowi zestaw narzędzi umożliwiający wdrożenie większości aplikacji systemu Android przy użyciu czystego kodu C/C++ . Kod JNI języka Java działa jako Glue, aby umożliwić współdziałanie kodu C/C++ z systemem Android. System Android NDK wprowadził możliwość tworzenia natywnych aplikacji aktywności z użyciem interfejsu API systemu Android Level 9. Natywny kod aktywności jest popularny do tworzenia gier i intensywnie korzystających z grafiki aplikacji wykorzystujących aparat Unreal lub OpenGL. Ten temat przeprowadzi Cię przez proces tworzenia prostej natywnej aplikacji, która korzysta z technologii OpenGL. Dodatkowe tematy przeprowadzą Cię przez cykl życia deweloperów w zakresie edytowania, kompilowania, debugowania i wdrażania natywnego kodu aktywności.

## <a name="requirements"></a>Wymagania

Aby można było utworzyć aplikację dla działania w trybie macierzystym systemu Android, należy upewnić się, że zostały spełnione wszystkie wymagania systemowe oraz że zainstalowano **Tworzenie aplikacji mobilnych przy użyciu C++**  obciążenia w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie aplikacji mobilnych dla wielu platform C++za pomocą programu ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Upewnij się, że wymagane narzędzia i zestawy SDK innych firm są zawarte w instalacji oraz że zainstalowano emulator systemu Android.

## <a name="create-a-new-native-activity-project"></a>Tworzenie nowego projektu działania natywnego

W tym samouczku utworzysz nowy projekt aktywności systemu Android Native, a następnie kompilujesz i uruchomisz aplikację domyślną w emulatorze systemu Android.

::: moniker range="vs-2017"

1. W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w obszarze **Szablony**wybierz pozycję **Visual C++**  > **cross platform**, a następnie wybierz szablon **aplikacja native-activity (Android)** .

1. Nadaj aplikacji nazwę, na przykład *MyAndroidApp*, a następnie wybierz przycisk **OK**.

   ![Tworzenie projektu działania natywnego](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

   Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.

   ![Natywny projekt aktywności w Eksplorator rozwiązań](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Utwórz nowy projekt** wybierz szablon **aplikacja natywna działania (Android)** , a następnie wybierz przycisk **dalej**.

1. W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź nazwę, taką jak *MyAndroidApp* w polu **Nazwa projektu**, a następnie wybierz pozycję **Utwórz**.

   Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.

::: moniker-end

Nowe rozwiązanie aplikacji Android Native Activity obejmuje dwa projekty:

- `MyAndroidApp.NativeActivity` zawiera odwołania i kod przyklejania dla aplikacji do uruchamiania jako działanie natywne w systemie Android. Implementacja punktów wejścia z kodu Glue znajduje się w *Main. cpp*. Wstępnie skompilowane nagłówki znajdują się w pliku *PCH. h*. Ten projekt aplikacji natywnej aktywności jest kompilowany do biblioteki udostępnionej *. plik,* który jest wybierany przez projekt pakietu.

- `MyAndroidApp.Packaging` tworzy plik *. apk* do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera ona plik resources i *pliku AndroidManifest. XML* , w którym są ustawiane właściwości manifestu. Zawiera również plik *Build. XML* , który kontroluje proces kompilacji ANT. Domyślnie jest ustawiony jako projekt startowy, aby można go było wdrożyć i uruchomić bezpośrednio z programu Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Kompilowanie i uruchamianie domyślnej aplikacji dla systemu Android Native Activity

Skompiluj i uruchom aplikację wygenerowaną przez szablon w celu zweryfikowania instalacji i konfiguracji. Na potrzeby tego testu wstępnego Uruchom aplikację na jednym z profili urządzeń zainstalowanych przez emulator systemu Android. Jeśli wolisz przetestować aplikację w innym miejscu docelowym, możesz załadować emulator docelowy lub podłączyć urządzenie do komputera.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Aby skompilować i uruchomić domyślną aplikację natywnego działania

1. Jeśli nie została jeszcze wybrana, wybierz pozycję **x86** z listy rozwijanej **platformy rozwiązań** .

     ![Lista rozwijana platformy rozwiązań x86 — wybór](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Jeśli lista **platform rozwiązań** nie jest wyświetlana, wybierz pozycję **platformy rozwiązań** z listy **Dodaj/Usuń przyciski** , a następnie wybierz swoją platformę.

1. Na pasku menu wybierz **kompiluj**  > **Kompiluj rozwiązanie**.

     W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji dla dwóch projektów w rozwiązaniu.

1. Wybierz jeden z profilów emulatora systemu Android jako cel wdrożenia.

     Jeśli zainstalowano Inne emulatory lub podłączone urządzenie z systemem Android, można je wybrać z listy rozwijanej cel wdrożenia.

1. Naciśnij klawisz **F5** , aby rozpocząć debugowanie, lub **przesuń** +**F5** , aby rozpocząć bez debugowania.

   Oto jak wygląda aplikacja domyślna w emulatorze systemu Android.

   ![Emulator z uruchomioną aplikacją](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

   Program Visual Studio uruchamia emulator, który zajmuje kilka sekund, aby załadować i wdrożyć kod. Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera do przechodzenia przez kod, badania wartości lokalnych i obserwacji.

1. Naciśnij klawisz **Shift** +**F5** , aby zatrzymać debugowanie.

   Emulator to oddzielny proces, który jest nadal uruchamiany. Można edytować, kompilować i wdrażać kod wielokrotnie w tym samym emulatorze.
