---
title: Tworzenie aplikacji Android Native Activity | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115643"
---
# <a name="create-an-android-native-activity-app"></a>Tworzenie aplikacji systemu Android działania natywnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas instalowania Visual C++ for Cross-Platform Mobile Development opcji programu Visual Studio 2015 może służyć do tworzenia w pełni funkcjonalne aplikacje Android Native Activity. Android Kit rozwoju natywnego (NDK) to zestaw narzędzi, która pozwala na implementowanie większość aplikacji systemu Android przy użyciu czystego kodu C/C++. Kodu Java interfejsem JNI działa jako pośredniczącego umożliwia kodu C/C++ do interakcji z systemem Android. Android NDK wprowadzono możliwość tworzenia aplikacji Native Activity z systemem Android 9 poziom interfejsu API. Kod natywny działania jest popularna do tworzenia gier i graficzne intensywnie korzystających z aplikacji, które używają aparatu Unreal Engine lub OpenGL. Ten temat przeprowadzi Cię przez tworzenie prostej aplikacji Native Activity korzystający ze specyfikacji OpenGL. Dodatkowe tematy przeprowadzenie edycji, kompilowania, debugowania i wdrażania działania natywnego kodu cyklu życia dla deweloperów.  
  
 [Wymagania](#req)   
 [Utwórz nowy projekt działania natywnego](#Create)   
 [Kompilowanie i uruchamianie aplikacji Android Native Activity domyślna](#BuildHello)  
  
## <a name="req"></a> Wymagania  
 Przed utworzeniem aplikacji Android Native Activity, upewnij się, że zostały spełnione wszystkie wymagania systemowe i zainstalowane opcji programowania aplikacji mobilnych Visual C++ w programie Visual Studio 2015. Aby uzyskać więcej informacji, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Upewnij się, że wymagane narzędzia innych firm i zestawy SDK są uwzględniane w instalacji programu i czy jest zainstalowany program Microsoft Visual Studio Emulator for Android.  
  
## <a name="Create"></a> Utwórz nowy projekt działania natywnego  
 W tym samouczku zostanie najpierw utwórz nowy projekt dla systemu Android działania natywnego i następnie kompilowanie i uruchamianie aplikacji domyślnej w Visual Studio Emulator dla systemu Android.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1. Otwórz program Visual Studio. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. W **nowy projekt** dialogowego **szablony**, wybierz **Visual C++**, **Międzyplatformowe**, a następnie wybierz  **Aplikacja klasy Nativeactivity (Android)** szablonu.  
  
3. Nadaj aplikacji nazwę, takich jak `MyAndroidApp`, a następnie wybierz **OK**.  
  
    ![Utwórz projekt działania natywnego](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio tworzy nowego rozwiązania i otwiera w Eksploratorze rozwiązań.  
  
    ![Natywny projekt działania w Eksploratorze rozwiązań](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Nowe rozwiązanie aplikacji Android Native Activity obejmuje dwa projekty:  
  
- **MyAndroidApp.NativeActivity** zawiera odwołania i kodu pośredniczącego aplikacji do uruchamiania jako działania natywnego w systemie Android. Implementacja punkty wejścia z kodu pośredniczącego znajdują się w main.cpp. Prekompilowane nagłówki są w pliku pch.h. Ten projekt aplikacji Native Activity jest kompilowany do pliku SO biblioteki udostępnionej, który zostaje pobrana przez projekt pakietu.  
  
- **MyAndroidApp.Packaging** tworzy plik apk do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera zasoby i pliku AndroidManifest.xml, można ustawić właściwości manifestu. Zawiera ona także build.xml pliku, który kontroluje proces kompilacji narzędzia Ant. Ustawiana jest jako projekt startowy domyślnie, tak że można wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
## <a name="BuildHello"></a> Kompilowanie i uruchamianie aplikacji Android Native Activity domyślna  
 Kompilowanie i uruchamianie aplikacji wygenerowanych przez szablon, aby zweryfikować swoje instalacji i konfiguracji. Aby uzyskać ten wstępny test, uruchom aplikację na jeden z profilów urządzeń instalowane przez Visual Studio Emulator for Android. Jeśli chcesz testować swoją aplikację na innym elementem docelowym można ładować emulatora docelowego, lub podłącz urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Aby skompilować i uruchomić aplikację Native Activity domyślne  
  
1. Jeśli nie została jeszcze wybrana, wybierz opcję **x86** z **platformy rozwiązania** listy rozwijanej.  
  
     ![Wybór listy rozwijanej x86 platformy rozwiązania](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Jeśli **platformy rozwiązania** lista nie jest wyświetlany, wybierz polecenie **platformy rozwiązania** z **Dodaj lub usuń przyciski** , a następnie wybierz platformy.  
  
2. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
     W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji na dwa projekty w rozwiązaniu.  
  
3. Wybierz jedną z emulatora VS profile telefon z systemem Android (x86) jako urządzenie docelowe wdrożenia.  
  
     Jeśli masz zainstalowany innych emulatorów lub podłączone urządzenie z systemem Android, można je na liście rozwijanej docelowych wdrożenia.  
  
4. Naciśnij klawisz F5, aby rozpocząć debugowanie lub Shift + F5, aby uruchomić bez debugowania.  
  
     Oto, jak domyślna aplikacja wygląda w emulatora programu Visual Studio dla systemu Android.  
  
     ![Emulator z tą aplikacją](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Program Visual Studio uruchamia emulatora, który zajmuje kilka sekund, aby załadować i wdrażanie kodu. Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i użyć debugera, aby przejść przez kod, Sprawdź zmienne lokalne i obejrzyj wartości.  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
     Emulator jest oddzielny proces, który będzie nadal działać. Można edytować, skompiluj i wdróż swój kod wielokrotnie do tego samego emulatora.
