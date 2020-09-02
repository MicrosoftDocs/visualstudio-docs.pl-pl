---
title: Tworzenie aplikacji dla systemu Android Native Activity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e554c7b97c2feac031510cfdd0894d29b4ba85eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151038"
---
# <a name="create-an-android-native-activity-app"></a>Tworzenie aplikacji systemu Android działania natywnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zainstalowaniu opcji Visual C++ dla opracowywania aplikacji mobilnych na wiele platform program Visual Studio 2015 może służyć do tworzenia w pełni funkcjonalnej natywnej aplikacji działania systemu Android. Zestaw Android Native Development Kit (NDK) stanowi zestaw narzędzi umożliwiający wdrożenie większości aplikacji systemu Android przy użyciu czystego kodu C/C++. Kod JNI języka Java działa jako Glue, aby umożliwić współdziałanie kodu C/C++ z systemem Android. System Android NDK wprowadził możliwość tworzenia natywnych aplikacji aktywności z użyciem interfejsu API systemu Android Level 9. Natywny kod aktywności jest popularny do tworzenia gier i intensywnie korzystających z grafiki aplikacji wykorzystujących aparat Unreal lub OpenGL. Ten temat przeprowadzi Cię przez proces tworzenia prostej natywnej aplikacji, która korzysta z technologii OpenGL. Dodatkowe tematy przeprowadzą Cię przez cykl życia deweloperów w zakresie edytowania, kompilowania, debugowania i wdrażania natywnego kodu aktywności.  
  
 [Wymagania](#req)   
 [Tworzenie nowego projektu działania natywnego](#Create)   
 [Kompilowanie i uruchamianie domyślnej aplikacji dla systemu Android Native Activity](#BuildHello)  
  
## <a name="requirements"></a><a name="req"></a> Wymagania  
 Aby można było utworzyć aplikację dla działania w trybie macierzystym systemu Android, należy upewnić się, że zostały spełnione wszystkie wymagania systemowe i zainstalowano opcję Visual C++ Mobile Development w programie Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [Install Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Upewnij się, że wymagane narzędzia i zestawy SDK innych firm są zawarte w instalacji oraz że Microsoft Visual Studio Emulator for Android jest zainstalowana.  
  
## <a name="create-a-new-native-activity-project"></a><a name="Create"></a> Tworzenie nowego projektu działania natywnego  
 W tym samouczku najpierw utworzysz nowy projekt aktywności systemu Android Native, a następnie kompilujesz i uruchomisz aplikację domyślną w emulatorze programu Visual Studio dla systemu Android.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1. Otwórz program Visual Studio. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.  
  
2. W oknie dialogowym **Nowy projekt** w obszarze **szablony**wybierz pozycję **Visual C++**, **Międzyplatformowy**, a następnie wybierz szablon **aplikacja native-activity (Android)** .  
  
3. Nadaj aplikacji nazwę, na przykład `MyAndroidApp` , a następnie wybierz **przycisk OK**.  
  
    ![Tworzenie projektu działania natywnego](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.  
  
    ![Natywny projekt aktywności w Eksplorator rozwiązań](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Nowe rozwiązanie aplikacji Android Native Activity obejmuje dwa projekty:  
  
- **MyAndroidApp. Native** zawiera kod odwołań i przyklejania dla aplikacji do uruchomienia jako działanie natywne w systemie Android. Implementacja punktów wejścia z kodu Glue znajduje się w Main. cpp. Wstępnie skompilowane nagłówki znajdują się w pliku PCH. h. Ten projekt aplikacji natywnej aktywności jest kompilowany do biblioteki udostępnionej. plik, który jest wybierany przez projekt pakietu.  
  
- **MyAndroidApp. pakowanie** tworzy plik. apk do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera ona zasoby i AndroidManifest.xml plik, w którym są ustawiane właściwości manifestu. Zawiera również plik build.xml, który kontroluje proces kompilacji ANT. Domyślnie jest ustawiony jako projekt startowy, aby można go było wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
## <a name="build-and-run-the-default-android-native-activity-app"></a><a name="BuildHello"></a> Kompilowanie i uruchamianie domyślnej aplikacji dla systemu Android Native Activity  
 Skompiluj i uruchom aplikację wygenerowaną przez szablon w celu zweryfikowania instalacji i konfiguracji. Na potrzeby tego testu wstępnego Uruchom aplikację na jednym z profili urządzeń zainstalowanych przez emulator programu Visual Studio dla systemu Android. Jeśli wolisz przetestować aplikację w innym miejscu docelowym, możesz załadować emulator docelowy lub podłączyć urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Aby skompilować i uruchomić domyślną aplikację natywnego działania  
  
1. Jeśli nie została jeszcze wybrana, wybierz pozycję **x86** z listy rozwijanej **platformy rozwiązań** .  
  
     ![Lista rozwijana platformy rozwiązań x86 — wybór](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Jeśli lista **platform rozwiązań** nie jest wyświetlana, wybierz pozycję **platformy rozwiązań** z listy **Dodaj/Usuń przyciski** , a następnie wybierz swoją platformę.  
  
2. Na pasku menu wybierz **kompilacja**, **Kompiluj rozwiązanie**.  
  
     W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji dla dwóch projektów w rozwiązaniu.  
  
3. Wybierz jeden z profilów systemu Android (x86) dla programu VS jako cel wdrożenia.  
  
     Jeśli zainstalowano Inne emulatory lub podłączone urządzenie z systemem Android, można je wybrać z listy rozwijanej cel wdrożenia.  
  
4. Naciśnij klawisz F5, aby rozpocząć debugowanie, lub klawisze Shift + F5, aby rozpocząć bez debugowania.  
  
     Oto, jak wygląda aplikacja domyślna w emulatorze programu Visual Studio dla systemu Android.  
  
     ![Emulator z uruchomioną aplikacją](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Program Visual Studio uruchamia emulator, który zajmuje kilka sekund, aby załadować i wdrożyć kod. Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera do przechodzenia przez kod, badania wartości lokalnych i obserwacji.  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Emulator to oddzielny proces, który jest nadal uruchamiany. Można edytować, kompilować i wdrażać kod wielokrotnie w tym samym emulatorze.
