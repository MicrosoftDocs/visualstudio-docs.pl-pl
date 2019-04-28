---
title: Tworzenie aplikacji Android Native Activity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: ac2f040addb4c387afe0b325fe53b6a9c289f33a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62819630"
---
# <a name="create-an-android-native-activity-app"></a>Tworzenie aplikacji systemu Android działania natywnego

Podczas instalowania Visual C++ for Cross-Platform Mobile Development opcji programu Visual Studio 2015 może służyć do tworzenia w pełni funkcjonalne aplikacje Android Native Activity. Android Kit rozwoju natywnego (NDK) to zestaw narzędzi, która pozwala na implementowanie większość aplikacji systemu Android przy użyciu czystego kodu C/C++. Kodu Java interfejsem JNI działa jako pośredniczącego umożliwia kodu C/C++ do interakcji z systemem Android. Android NDK wprowadzono możliwość tworzenia aplikacji Native Activity z systemem Android 9 poziom interfejsu API. Kod natywny działania jest popularna do tworzenia gier i graficzne intensywnie korzystających z aplikacji, które używają aparatu Unreal Engine lub OpenGL. Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji Native Activity korzystający ze specyfikacji OpenGL. Dodatkowe tematy przeprowadzenie edycji, kompilowania, debugowania i wdrażania działania natywnego kodu cyklu życia dla deweloperów.

## <a name="requirements"></a>Wymagania

Przed utworzeniem aplikacji Android Native Activity, upewnij się, że zostały spełnione wszystkie wymagania systemowe i zainstalowane opcji programowania aplikacji mobilnych Visual C++ w programie Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Upewnij się, że wymagane narzędzia innych firm i zestawy SDK są uwzględniane w instalacji programu i czy jest zainstalowany program Microsoft Visual Studio Emulator for Android.

## <a name="create-a-new-native-activity-project"></a>Utwórz nowy projekt działania natywnego

W tym samouczku zostanie najpierw utwórz nowy projekt dla systemu Android działania natywnego i następnie kompilowanie i uruchamianie aplikacji domyślnej w Visual Studio Emulator dla systemu Android.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okno dialogowe, w obszarze **szablony**, wybierz **Visual C++** > **Międzyplatformowe**, a następnie wybierz pozycję **Aplikacja klasy Nativeactivity (Android)** szablonu.

3. Nadaj aplikacji nazwę, takich jak `MyAndroidApp`, a następnie wybierz **OK**.

    ![Utwórz projekt działania natywnego](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

    Visual Studio tworzy nowego rozwiązania i otwiera w Eksploratorze rozwiązań.

    ![Natywny projekt działania w Eksploratorze rozwiązań](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

   Nowe rozwiązanie aplikacji Android Native Activity obejmuje dwa projekty:

- `MyAndroidApp.NativeActivity` zawiera odwołania i kodu pośredniczącego aplikacji do uruchamiania jako działania natywnego w systemie Android. Implementacja punkty wejścia z kodu pośredniczącego znajdują się w *main.cpp*. Prekompilowane nagłówki znajdują się w *pch.h*. Ten projekt aplikacji Native Activity jest skompilowany w bibliotece udostępnionej *SO* pliku, który zostaje pobrana przez projekt pakietu.

- `MyAndroidApp.Packaging` Tworzy *.apk* plik dla wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera zasoby i *AndroidManifest.xml* pliku można ustawić właściwości manifestu. Zawiera ona także *build.xml* pliku, który kontroluje Ant procesu kompilacji. Ustawiana jest jako projekt startowy domyślnie, tak że można wdrożyć i uruchomić bezpośrednio z programu Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Kompilowanie i uruchamianie aplikacji Android Native Activity domyślna

Kompilowanie i uruchamianie aplikacji wygenerowanych przez szablon, aby zweryfikować swoje instalacji i konfiguracji. Aby uzyskać ten wstępny test, uruchom aplikację na jeden z profilów urządzeń instalowane przez Visual Studio Emulator for Android. Jeśli chcesz testować swoją aplikację na innym elementem docelowym można ładować emulatora docelowego, lub podłącz urządzenie do komputera.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Aby skompilować i uruchomić aplikację Native Activity domyślne

1. Jeśli nie została jeszcze wybrana, wybierz opcję **x86** z **platformy rozwiązania** listy rozwijanej.

     ![Wybór listy rozwijanej x86 platformy rozwiązania](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Jeśli **platformy rozwiązania** lista nie jest wyświetlany, wybierz polecenie **platformy rozwiązania** z **Dodaj lub usuń przyciski** , a następnie wybierz platformy.

2. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.

     W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji na dwa projekty w rozwiązaniu.

3. Wybierz jedną z emulatora VS profile telefon z systemem Android (x86) jako urządzenie docelowe wdrożenia.

     Jeśli masz zainstalowany innych emulatorów lub podłączone urządzenie z systemem Android, można je na liście rozwijanej docelowych wdrożenia.

4. Naciśnij klawisz **F5** rozpoczęcia debugowania lub Shift + F5, aby uruchomić bez debugowania.

     Oto, jak domyślna aplikacja wygląda w emulatora programu Visual Studio dla systemu Android.

     ![Emulator z tą aplikacją](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

     Program Visual Studio uruchamia emulatora, który zajmuje kilka sekund, aby załadować i wdrażanie kodu. Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i użyć debugera, aby przejść przez kod, Sprawdź zmienne lokalne i obejrzyj wartości.

5. Naciśnij klawisz **Shift**+**F5** Aby zatrzymać debugowanie.

     Emulator jest oddzielny proces, który będzie nadal działać. Można edytować, skompiluj i wdróż swój kod wielokrotnie do tego samego emulatora.