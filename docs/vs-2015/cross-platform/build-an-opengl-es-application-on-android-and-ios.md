---
title: Tworzenie aplikacji OpenGL ES w systemach Android i iOS | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b9f5db4ccd70136b711f5bd221244418cf843485
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151169"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Tworzenie aplikacji OpenGL ES w systemach Android i iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zainstalowaniu Visual C++ for Cross-Platform Mobile Development opcji, można utworzyć rozwiązania programu Visual Studio i projektów dla aplikacji systemu iOS i aplikacje dla systemu Android, które współużytkują wspólny kod. Ten temat przeprowadzi Cię przez szablon rozwiązania, która tworzy zarówno w przypadku aplikacji systemu iOS proste, jak i aplikacji Android Native Activity. Aplikacje wspólnym kodu w języku C++, których używa OpenGL ES do wyświetlenia tego samego modułu rotacji animowany na każdej platformie. OpenGL ES (OpenGL dla systemów osadzone lub GLES) jest grafiki 2D i 3D interfejsu API, który jest obsługiwany na wiele urządzeń przenośnych.  
  
 [Wymagania](#req)   
 [Utwórz nowy projekt aplikacja OpenGLES](#Create)   
 [Kompilowanie i uruchamianie aplikacji systemu Android](#BuildAndroid)   
 [Kompilowanie i uruchamianie aplikacji dla systemu iOS](#BuildIOS)   
 [Dostosowywanie aplikacji](#Customize)  
  
## <a name="req"></a> Wymagania  
 Przed utworzeniem aplikacji OpenGL ES dla systemów iOS i Android, upewnij się, że zostały spełnione wszystkie wymagania systemowe. Należy zainstalować Visual C++ for Cross-Platform Mobile Development opcji w programie Visual Studio 2015. Upewnij się, że wymagane narzędzia innych firm i zestawy SDK są uwzględniane w instalacji programu i czy jest zainstalowany program Visual Studio Emulator for Android. Aby uzyskać więcej informacji oraz szczegółowe instrukcje, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Do tworzenia i testowania aplikacji dla systemu iOS, będzie potrzebny jest komputer Mac komputer, skonfigurowany zgodnie z instrukcjami instalacji. Aby uzyskać więcej informacji o tym, jak skonfigurować do tworzenia aplikacji dla systemu iOS, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
## <a name="Create"></a> Utwórz nowy projekt aplikacja OpenGLES  
 W tym samouczku najpierw utwórz nowy projekt aplikacji OpenGL ES i następnie skompilować i uruchomić aplikację domyślnej w Visual Studio Emulator dla systemu Android. Następnie utwórz aplikację dla systemu iOS i uruchomić aplikację w symulatorze systemu iOS.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1. Otwórz program Visual Studio. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. W **nowy projekt** dialogowego **szablony**, wybierz **Visual C++** , **Międzyplatformowe**, a następnie wybierz  **Aplikacja OpenGLES (Android, iOS)** szablonu.  
  
3. Nadaj aplikacji nazwę, takich jak `MyOpenGLESApp`, a następnie wybierz **OK**.  
  
    ![Nowy projekt aplikacji OpenGLES](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio tworzy nowego rozwiązania i otwiera w Eksploratorze rozwiązań.  
  
    ![MyOpenGLESApp w Eksploratorze rozwiązań](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Nowe rozwiązanie aplikacji OpenGL ES obejmuje trzy projekty biblioteki i dwa projekty aplikacji. Folder biblioteki zawiera projekt współużytkowanego kodu i dwa projekty specyficzne dla platformy, odwołujące się do udostępnionego kodu:  
  
- **MyOpenGLESApp.Android.NativeActivity** zawiera odwołania i kod sklejający, który implementuje aplikację jako działania natywnego w systemie Android. Implementacja punkty wejścia z kodu pośredniczącego znajdują się w main.cpp, która obejmuje wspólny kod udostępniony w MyOpenGLESApp.Shared. Prekompilowane nagłówki są w pliku pch.h. Ten projekt aplikacji Native Activity jest kompilowany do pliku biblioteki udostępnionej (SO), który zostaje pobrana przez projekt MyOpenGLESApp.Android.Packaging.  
  
- **MyOpenGLESApp.iOS.StaticLibrary** tworzy plik biblioteka statyczna (.a) dla systemu iOS, która zawiera kod udostępniony w MyOpenGLESApp.Shared. Aplikację utworzoną przez projekt MyOpenGLESApp.iOS.Application jest połączony.  
  
- **MyOpenGLESApp.Shared** zawiera kod udostępniony, który działa na wielu platformach. Makra preprocesora używa dla kompilacji warunkowej kodu specyficznego dla platformy. Kod udostępniony zostaje pobrana przez odwołanie do projektu w MyOpenGLESApp.Android.NativeActivity i MyOpenGLESApp.iOS.StaticLibrary.  
  
  Rozwiązanie zawiera dwa projekty do tworzenia aplikacji dla platformy Android i iOS:  
  
- **MyOpenGLESApp.Android.Packaging** tworzy plik apk do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera zasoby i pliku AndroidManifest.xml, można ustawić właściwości manifestu. Zawiera ona także build.xml pliku, który kontroluje proces kompilacji narzędzia Ant. Ustawiana jest jako projekt startowy domyślnie, tak że można wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
- **MyOpenGLESApp.iOS.Application** zawiera zasoby i kodu pośredniczącego języka Objective-C, aby utworzyć aplikację dla systemu iOS prowadzący do kodu C++ w bibliotece statycznej w MyOpenGLESApp.iOS.StaticLibrary. Ten projekt tworzy pakiet kompilacji, który jest przekazywany do komputera Mac, program Visual Studio i zdalnego agenta. Podczas tworzenia tego projektu programu Visual Studio wysyła pliki i polecenia do tworzenia i wdrażania aplikacji na komputerach Mac.  
  
## <a name="BuildAndroid"></a> Kompilowanie i uruchamianie aplikacji systemu Android  
 Rozwiązanie utworzone przez szablon ustawia aplikacji dla systemu Android jako domyślny projekt.  Można skompilować i uruchomić tę aplikację, aby zweryfikować instalacji i konfiguracji. Dla testu wstępnego, uruchom aplikację na jeden z profilów urządzeń instalowane przez Visual Studio Emulator for Android. Jeśli chcesz testować swoją aplikację na innym elementem docelowym można ładować emulatora docelowego, lub podłącz urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Aby skompilować i uruchomić aplikację systemu Android działania natywnego  
  
1. Jeśli nie została jeszcze wybrana, wybierz opcję **x86** z **platformy rozwiązania** listy rozwijanej.  
  
    ![Ustaw platforma rozwiązania x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Użyj x86 pod kątem emulatora systemu Android do Windows. Jeśli są przeznaczone dla urządzenia, wybierz platformę rozwiązania oparte na procesorze urządzenia. Jeśli **platformy rozwiązania** lista nie jest wyświetlona, wybierz polecenie **platformy rozwiązania** z **Dodaj lub usuń przyciski** , a następnie wybierz platformy.  
  
2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu MyOpenGLESApp.Android.Packaging, a następnie wybierz **kompilacji**.  
  
    ![Kompiluj projekt pakowania dla systemu Android](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji dla programu Android udostępnionych, biblioteki i aplikacji dla systemu Android.  
  
    ![Dane wyjściowe kompilacji dla projektów systemu Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Wybierz jedną z emulatora VS profile telefon z systemem Android (x86) jako urządzenie docelowe wdrożenia.  
  
    ![Wybierz cel wdrożenia](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Jeśli masz zainstalowany innych emulatorów lub podłączone urządzenie z systemem Android, można je na liście rozwijanej cel wdrożenia. Aby uruchomić aplikację, wbudowanego platforma rozwiązania muszą być zgodne platforma urządzenia docelowego.  
  
4. Naciśnij klawisz F5, aby rozpocząć debugowanie lub Shift + F5, aby uruchomić bez debugowania.  
  
    Program Visual Studio uruchamia emulatora, który zajmuje kilka sekund, aby załadować i wdrożyć swój kod. Oto, jak aplikacja jest wyświetlana w emulatora programu Visual Studio dla systemu Android.  
  
    ![Aplikacja uruchomiona w emulatorze systemu Android](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i użyć debugera, aby przejść przez kod, Sprawdź zmienne lokalne i obejrzyj wartości.  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
    Emulator jest oddzielny proces, który będzie nadal działać. Można edytować, skompiluj i wdróż swój kod wielokrotnie do tego samego emulatora. Aplikacja pojawia się w kolekcji aplikacji w emulatorze, i może być uruchamiany z tego miejsca bezpośrednio.  
  
   Wygenerowany Android Native Activity aplikacji i bibliotekę projektów C++ kodu udostępnionego w Biblioteka dynamiczna, która zawiera kod "skleić" interfejs za pomocą platformy systemu Android. Oznacza to większość kodu aplikacji znajduje się w bibliotece, i manifestu, zasoby i instrukcje kompilacji podczas pakowania projektu. Kod udostępniony jest wywoływana z main.cpp w projekcie klasy NativeActivity. Aby uzyskać więcej informacji na temat sposobu programowania dla systemu Android Native Activity Zobacz zestawu Android NDK Developer [pojęcia](https://developer.android.com/ndk/guides/concepts.html) strony.  
  
   Program Visual Studio tworzy Android Native Activity projektów przy użyciu zestawu Android NDK, który używa zestawu narzędzi platformy Clang. Program Visual Studio mapuje właściwości w projekcie klasy NativeActivity przełączniki wiersza polecenia i opcje, które są używane do kompilowania, link i debugowanie na platformie docelowej. Aby uzyskać szczegółowe informacje, otwórz **stron właściwości** okno dialogowe dla projektu MyOpenGLESApp.Android.NativeActivity. Aby uzyskać więcej informacji na temat przełączników wiersza polecenia, zobacz [Clang kompilatora obsługi](http://clang.llvm.org/docs/UsersManual.html).  
  
## <a name="BuildIOS"></a> Kompilowanie i uruchamianie aplikacji dla systemu iOS  
 Projekt aplikacji systemu iOS jest tworzony i edytować w programie Visual Studio, ale z powodu ograniczeń licencyjnych, musi być utworzone i wdrożone z komputerów Mac. Program Visual Studio komunikuje się z agenta zdalnego uruchomiona na komputerze Mac do przesyłania plików projektu i wykonania kompilacji, wdrażania i debugowania poleceń. Musisz skonfigurować i konfigurowanie systemów Mac i Visual Studio, do komunikowania się przed utworzeniem aplikacji dla systemu iOS. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Gdy zdalny agent jest uruchomiony i programu Visual Studio jest powiązany z Twoim komputerem Mac, można tworzyć i uruchom aplikację dla systemu iOS, aby zweryfikować instalacji i konfiguracji.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Aby skompilować i uruchomić aplikację systemu iOS  
  
1. Sprawdź, czy zdalny agent jest uruchomiony na komputerze Mac, i że program Visual Studio jest sparowana z agentem zdalnym. Aby uruchomić agenta zdalnego, Otwórz okno terminalu aplikacji, a następnie wprowadź `vcremote`. Aby uzyskać więcej informacji, zobacz [skonfigurować agenta zdalnego w programie Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Okno terminala na komputerze Mac vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Jeśli nie została jeszcze wybrana, wybierz opcję **x86** z **platformy rozwiązania** listy rozwijanej.  
  
    ![Ustaw platforma rozwiązania x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Użyj x86 pod kątem symulatora systemu iOS. Jeśli urządzenie z systemem iOS, wybierz platformę rozwiązania oparte na procesorze urządzenia (zazwyczaj z procesorem ARM). Jeśli **platformy rozwiązania** lista nie jest wyświetlona, wybierz polecenie **platformy rozwiązania** z **Dodaj lub usuń przyciski** , a następnie wybierz platformy.  
  
3. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu MyOpenGLESApp.iOS.Application, a następnie wybierz **kompilacji**.  
  
    ![Tworzenie projektu aplikacji systemu iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji dla biblioteki statycznej dla systemu iOS oraz aplikacji dla systemu iOS. Na komputerze Mac, uruchamianie zdalnego agenta Pokazuje okno terminalu polecenia i transferu plików działania.  
  
    Na komputerze Mac, może pojawić się prośba o akceptować żądania do podpisywania kodu. Wybierz pozycję Zezwalaj, aby kontynuować.  
  
4. Wybierz **symulatora systemu iOS** na pasku narzędzi, aby uruchomić aplikację w symulatorze systemu iOS na komputerze Mac. Może upłynąć kilka minut, aby uruchomić symulator. Może być konieczne przenieść symulatorze na pierwszy plan na komputerze Mac, aby wyświetlić jego dane wyjściowe.  
  
    ![Aplikacja działająca w systemie iOS Simulator](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i za pomocą debugera programu Visual Studio do badania zmiennych lokalnych, zobaczyć stos wywołań i obejrzyj wartości.  
  
    ![Debuger w punkcie przerwania w aplikacji dla systemu iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
    IOS Simulator jest oddzielny proces, który będzie działać na komputerze Mac. Można edytować, skompiluj i wdróż swój kod wielokrotnie do tego samego wystąpienia symulatora systemu iOS. Po jej wdrożeniu, można uruchomić kod bezpośrednio w symulatorze.  
  
   Projekty aplikacji i biblioteki wygenerowany dla systemu iOS umieść kod C++ w bibliotece statycznej, która implementuje udostępnionego kodu. Większość kodu aplikacji znajduje się w projekcie aplikacji. Wywołania do biblioteki udostępnionej kodu w tym projekcie szablonu są wprowadzane w pliku GameViewController.m. Tworzenie aplikacji dla systemu iOS, Visual Studio korzysta z narzędzia Xcode zestaw narzędzi platformy, która wymaga komunikacji z klientem zdalnym, który działa na komputerach Mac.  
  
   Visual Studio przesyła pliki projektu i wysyła polecenia do zdalnego klienta, aby skompilować aplikację za pomocą środowiska Xcode. Klient zdalny wysyła kompilacji informacje o stanie do programu Visual Studio. Gdy aplikacja została pomyślnie skompilowane, można użyć programu Visual Studio do wysyłania poleceń do uruchamiania i debugowania aplikacji. W debugerze programu Visual Studio steruje aplikacji uruchomionej w uruchamiania symulatora systemu iOS, na komputerze Mac lub urządzenia z systemem iOS dołączone. Program Visual Studio mapuje właściwości w projekcie StaticLibrary przełączniki wiersza polecenia i opcje, które są używane do tworzenia, link i debugowanie na platformę docelową dla systemu iOS. Dla opcji wiersza polecenia kompilatora uzyskać więcej informacji, otwórz **stron właściwości** okno dialogowe dla projektu MyOpenGLESApp.iOS.StaticLibrary.  
  
## <a name="Customize"></a> Dostosowywanie aplikacji  
 Można zmodyfikować współdzielonym kodem C++, aby dodać lub zmienić typowych funkcji. Należy zmienić wywołania do udostępnionego kodu w projektach MyOpenGLESApp.Android.NativeActivity i MyOpenGLESApp.iOS.Application do dopasowania. Makra preprocesora służy do określania sekcje specyficzne dla platformy w kodzie wspólnej. Makro preprocesora `__ANDROID__` jest wstępnie zdefiniowane podczas kompilowania dla systemu Android. Makro preprocesora `__APPLE__` jest wstępnie zdefiniowane podczas kompilowania dla systemu iOS.  
  
 Aby wyświetlić funkcję IntelliSense dla platform konkretnego projektu, wybierz projekt w menu rozwijanym przełącznik kontekstu na pasku nawigacyjnym, w górnej części okna edytora.  
  
 ![Projekt z listy rozwijanej przełącznik kontekst, w edytorze](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Czerwona linia falista są oznaczone problemów IntelliSense w bieżącym projekcie. Purpurowa linia falista są oznaczone problemów w innych projektach. Domyślnie program Visual Studio nie obsługuje kod kolorowania i technologii IntelliSense dla plików języka Java lub języka Objective-C. Można nadal zmodyfikować pliki źródłowe i zmienić zasoby, aby ustawić nazwę swojej aplikacji, ikony i inne szczegóły implementacji.
