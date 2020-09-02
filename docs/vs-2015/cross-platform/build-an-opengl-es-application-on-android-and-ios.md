---
title: Tworzenie aplikacji OpenGL ES w systemach Android i iOS | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151169"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Tworzenie aplikacji OpenGL ES w systemach Android i iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po zainstalowaniu opcji Visual C++ dla opracowywania aplikacji mobilnych na wiele platform można tworzyć rozwiązania i projekty programu Visual Studio dla aplikacji systemu iOS i aplikacji systemu Android, które współużytkują wspólny kod. Ten temat przeprowadzi Cię przez szablon rozwiązania, który tworzy prostą aplikację systemu iOS i aplikację z natywnym działaniem systemu Android. Aplikacje mają wspólny kod języka C++, który używa technologii OpenGL ES do wyświetlania tego samego animowanego sześcianu obracającego na każdej platformie. Oprogramowanie OpenGL ES (OpenGL for Embedded Systems lub GLES) jest interfejsem API grafiki 2D i 3D, który jest obsługiwany na wielu urządzeniach przenośnych.  
  
 [Wymagania](#req)   
 [Utwórz nowy projekt aplikacji OpenGL](#Create)   
 [Kompilowanie i uruchamianie aplikacji systemu Android](#BuildAndroid)   
 [Kompilowanie i uruchamianie aplikacji systemu iOS](#BuildIOS)   
 [Dostosowywanie aplikacji](#Customize)  
  
## <a name="requirements"></a><a name="req"></a> Wymagania  
 Aby można było utworzyć aplikację OpenGL ES dla systemów iOS i Android, należy upewnić się, że zostały spełnione wszystkie wymagania systemowe. Należy zainstalować opcję Visual C++ dla opracowywania aplikacji mobilnych na wiele platform w programie Visual Studio 2015. Upewnij się, że wymagane narzędzia i zestawy SDK innych firm są zawarte w instalacji oraz że zainstalowano Emulator programu Visual Studio dla systemu Android. Aby uzyskać więcej informacji i uzyskać szczegółowe instrukcje, zobacz [Install Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Aby skompilować i przetestować aplikację dla systemu iOS, musisz mieć komputer Mac, a następnie skonfigurować go zgodnie z instrukcjami instalacji. Aby uzyskać więcej informacji na temat sposobu konfigurowania programu do tworzenia aplikacji dla systemu iOS, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
## <a name="create-a-new-opengles-application-project"></a><a name="Create"></a> Utwórz nowy projekt aplikacji OpenGL  
 W tym samouczku należy najpierw utworzyć nowy projekt aplikacji OpenGL ES, a następnie skompilować i uruchomić aplikację domyślną w emulatorze programu Visual Studio dla systemu Android. Następnie można skompilować aplikację dla systemu iOS i uruchomić aplikację w symulatorze systemu iOS.  
  
#### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1. Otwórz program Visual Studio. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.  
  
2. W oknie dialogowym **Nowy projekt** w obszarze **szablony**wybierz pozycję **Visual C++**, **Międzyplatformowy**, a następnie wybierz szablon **aplikacja opengls (Android, iOS)** .  
  
3. Nadaj aplikacji nazwę, na przykład `MyOpenGLESApp` , a następnie wybierz **przycisk OK**.  
  
    ![Nowy projekt aplikacji OpenGL](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.  
  
    ![MyOpenGLESApp w Eksplorator rozwiązań](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Nowe rozwiązanie aplikacji OpenGL ES zawiera trzy projekty biblioteki i dwa projekty aplikacji. Folder biblioteki zawiera współużytkowany projekt kodu i dwa projekty specyficzne dla platformy, które odwołują się do udostępnionego kodu:  
  
- **MyOpenGLESApp. Android. Native** zawiera odwołania i kod przyklejania, który implementuje aplikację jako natywną aktywność w systemie Android. Implementacja punktów wejścia z kodu przyklejania znajduje się w Main. cpp, który obejmuje wspólny kod współużytkowany w MyOpenGLESApp. Shared. Wstępnie skompilowane nagłówki znajdują się w pliku PCH. h. Ten projekt aplikacji natywnej aktywności jest kompilowany do pliku biblioteki udostępnionej (. so), który jest wybierany przez projekt MyOpenGLESApp. Android. opakowanie.  
  
- **MyOpenGLESApp. iOS. StaticLibrary** tworzy plik statycznej biblioteki systemu iOS (. a), który zawiera kod współużytkowany w MyOpenGLESApp. Shared. Jest on połączony z aplikacją utworzoną przez projekt MyOpenGLESApp. iOS. Application.  
  
- **MyOpenGLESApp. Shared** zawiera kod współużytkowany, który działa na różnych platformach. Używa makr preprocesora do kompilacji warunkowej kodu specyficznego dla platformy. Kod współużytkowany jest wybierany przez odwołanie do projektu zarówno w MyOpenGLESApp. Android. Native, jak i MyOpenGLESApp. iOS. StaticLibrary.  
  
  Rozwiązanie ma dwa projekty do kompilowania aplikacji dla platform Android i iOS:  
  
- **MyOpenGLESApp. Android. pakowanie** tworzy plik. apk do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Zawiera ona zasoby i AndroidManifest.xml plik, w którym są ustawiane właściwości manifestu. Zawiera również plik build.xml, który kontroluje proces kompilacji ANT. Domyślnie jest ustawiony jako projekt startowy, aby można go było wdrożyć i uruchomić bezpośrednio z programu Visual Studio.  
  
- **MyOpenGLESApp. iOS. Application** zawiera kod przyklejania zasobów i celu utworzenia aplikacji dla systemu iOS, który łączy się z kodem biblioteki statycznej C++ w MyOpenGLESApp. iOS. StaticLibrary. Ten projekt tworzy pakiet kompilacji, który jest przesyłany do komputera Mac przez program Visual Studio i agenta zdalnego. Podczas kompilowania projektu program Visual Studio wysyła pliki i polecenia, aby kompilować i wdrażać aplikację na komputerze Mac.  
  
## <a name="build-and-run-the-android-app"></a><a name="BuildAndroid"></a> Kompilowanie i uruchamianie aplikacji systemu Android  
 Rozwiązanie utworzone przez szablon ustawia aplikację dla systemu Android jako projekt domyślny.  Możesz skompilować i uruchomić tę aplikację, aby zweryfikować instalację i konfigurację. W przypadku testu wstępnego Uruchom aplikację na jednym z profili urządzeń zainstalowanych przez emulator programu Visual Studio dla systemu Android. Jeśli wolisz przetestować aplikację w innym miejscu docelowym, możesz załadować emulator docelowy lub podłączyć urządzenie do komputera.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Aby skompilować i uruchomić aplikację natywnego działania systemu Android  
  
1. Jeśli nie została jeszcze wybrana, wybierz pozycję **x86** z listy rozwijanej **platformy rozwiązań** .  
  
    ![Ustaw platformę rozwiązania na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Użyj procesora x86, aby określić Emulator systemu Android dla systemu Windows. W przypadku określania docelowej urządzenia wybierz platformę rozwiązania opartą na procesorze urządzeń. Jeśli lista **platform rozwiązania** nie zostanie wyświetlona, wybierz pozycję **platformy rozwiązań** z listy **Dodaj/Usuń przyciski** , a następnie wybierz swoją platformę.  
  
2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu MyOpenGLESApp. Android. pakowanie, a następnie wybierz polecenie **Kompiluj**.  
  
    ![Kompiluj projekt pakietu systemu Android](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji dla biblioteki udostępnionej systemu Android i aplikacji systemu Android.  
  
    ![Dane wyjściowe kompilacji dla projektów systemu Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Wybierz jeden z profilów systemu Android (x86) dla programu VS jako cel wdrożenia.  
  
    ![Wybierz cel wdrożenia](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Jeśli zostały zainstalowane inne emulatory lub podłączone urządzenie z systemem Android, możesz je wybrać z listy rozwijanej cel wdrożenia. Aby uruchomić aplikację, skompilowana platforma rozwiązania musi być zgodna z platformą urządzenia docelowego.  
  
4. Naciśnij klawisz F5, aby rozpocząć debugowanie, lub klawisze Shift + F5, aby rozpocząć bez debugowania.  
  
    Program Visual Studio uruchamia emulator, który zajmuje kilka sekund, aby załadować i wdrożyć swój kod. Oto jak aplikacja pojawia się w emulatorze programu Visual Studio dla systemu Android.  
  
    ![Aplikacja działająca w Emulator systemu Android](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera do przechodzenia przez kod, badania wartości lokalnych i obserwacji.  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
    Emulator to oddzielny proces, który jest nadal uruchamiany. Można edytować, kompilować i wdrażać kod wielokrotnie w tym samym emulatorze. Aplikacja zostanie wyświetlona w kolekcji aplikacji na emulatorze i może być od razu uruchomiona.  
  
   Wygenerowana aplikacja systemu Android Native i projekty bibliotek umieszczają kod współużytkowany C++ w bibliotece dynamicznej, która zawiera kod "Glue" do interfejsu z platformą systemu Android. Oznacza to, że większość kodu aplikacji znajduje się w bibliotece, a instrukcje manifestu, zasobów i kompilacji znajdują się w projekcie pakietu. Kod współużytkowany jest wywoływany z Main. cpp w projekcie natywnym. Aby uzyskać więcej informacji o tym, jak programować działanie systemu Android Native, zobacz stronę [pojęcia](https://developer.android.com/ndk/guides/concepts.html) dla deweloperów systemu Android.  
  
   Visual Studio kompiluje natywne projekty aktywności systemu Android przy użyciu zestawu Android NDK, który używa Clang jako zestawu narzędzi platformy. Program Visual Studio mapuje właściwości w projekcie natywnym do przełączników wiersza polecenia i opcji, które są używane do kompilowania, łączenia i debugowania na platformie docelowej. Aby uzyskać szczegółowe informacje, Otwórz okno dialogowe **strony właściwości** dla projektu MyOpenGLESApp. Android. Native. Aby uzyskać więcej informacji na temat przełączników wiersza polecenia, zobacz [Podręcznik użytkownika kompilatora Clang](http://clang.llvm.org/docs/UsersManual.html).  
  
## <a name="build-and-run-the-ios-app"></a><a name="BuildIOS"></a> Kompilowanie i uruchamianie aplikacji systemu iOS  
 Projekt aplikacji systemu iOS jest tworzony i edytowany w programie Visual Studio, ale z powodu ograniczeń licencjonowania należy go skompilować i wdrożyć z poziomu komputera Mac. Program Visual Studio komunikuje się ze zdalnym agentem uruchomionym na komputerze Mac w celu transferu plików projektu oraz wykonywania poleceń kompilowania, wdrażania i debugowania. Aby można było skompilować aplikację dla systemu iOS, należy najpierw skonfigurować i skonfigurować komputery Mac i program Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Gdy Agent zdalny jest uruchomiony i program Visual Studio jest sparowany z komputerem Mac, możesz skompilować i uruchomić aplikację systemu iOS, aby zweryfikować instalację i konfigurację.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Aby skompilować i uruchomić aplikację systemu iOS  
  
1. Sprawdź, czy Agent zdalny jest uruchomiony na komputerze Mac, a program Visual Studio jest sparowany z agentem zdalnym. Aby uruchomić agenta zdalnego, Otwórz okno aplikacji terminalowej i wprowadź `vcremote` . Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego agenta w programie Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Okno terminalu Mac z systemem vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Jeśli nie została jeszcze wybrana, wybierz pozycję **x86** z listy rozwijanej **platformy rozwiązań** .  
  
    ![Ustaw platformę rozwiązania na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Użyj procesora x86, aby przekierować symulatorem systemu iOS. Jeśli chcesz uzyskać urządzenie z systemem iOS, Wybierz platformę rozwiązania opartą na procesorze urządzeń (zazwyczaj procesor ARM). Jeśli lista **platform rozwiązania** nie zostanie wyświetlona, wybierz pozycję **platformy rozwiązań** z listy **Dodaj/Usuń przyciski** , a następnie wybierz swoją platformę.  
  
3. W Eksplorator rozwiązań otwórz menu skrótów dla projektu MyOpenGLESApp. iOS. Application i wybierz polecenie **Kompiluj**.  
  
    ![Kompiluj projekt aplikacji systemu iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji dla biblioteki statycznej systemu iOS i aplikacji systemu iOS. Na komputerze Mac okno terminalu z uruchomionym agentem zdalnym pokazuje działanie polecenia i transferu plików.  
  
    Na komputerze Mac może zostać wyświetlony monit o zaakceptowanie żądania podpisania kodu. Wybierz pozycję Zezwól, aby kontynuować.  
  
4. Wybierz **symulator systemu iOS** na pasku narzędzi, aby uruchomić aplikację w symulatorze systemu iOS na komputerze Mac. Uruchomienie symulatora może chwilę potrwać. Może być konieczne przełączenie symulatora na pierwszy plan na komputerze Mac, aby zobaczyć jego dane wyjściowe.  
  
    ![Aplikacja działająca w symulatorze systemu iOS](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera programu Visual Studio, aby sprawdzić ustawienia regionalne, zobaczyć stos wywołań i obserwować wartości.  
  
    ![Debuger w aplikacji systemu iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Naciśnij klawisze Shift + F5, aby zatrzymać debugowanie.  
  
    Symulator systemu iOS to oddzielny proces, który jest nadal uruchamiany na komputerze Mac. Można edytować, kompilować i wdrażać kod wielokrotnie w tym samym wystąpieniu symulatora systemu iOS. Możesz również uruchomić kod bezpośrednio w symulatorze po jego wdrożeniu.  
  
   Wygenerowane projekty aplikacji i biblioteki systemu iOS umieszczają kod języka C++ w bibliotece statycznej, która implementuje tylko kod współużytkowany. Większość kodu aplikacji znajduje się w projekcie aplikacji. Wywołania kodu biblioteki udostępnionej w tym projekcie szablonu są wykonywane w pliku GameViewController. m. Aby skompilować aplikację dla systemu iOS, program Visual Studio używa zestawu narzędzi platformy Xcode, który wymaga komunikacji z klientem zdalnym działającym na komputerze Mac.  
  
   Program Visual Studio transferuje pliki projektu i wysyła polecenia do zdalnego klienta w celu skompilowania aplikacji przy użyciu Xcode. Klient zdalny wysyła informacje o stanie kompilacji z powrotem do programu Visual Studio. Po pomyślnym skompilowaniu aplikacji możesz użyć programu Visual Studio do wysyłania poleceń do uruchamiania i debugowania aplikacji. Debuger w programie Visual Studio kontroluje aplikację działającą w symulatorze systemu iOS działającym na komputerze Mac lub na podłączonym urządzeniu z systemem iOS. Program Visual Studio mapuje właściwości w projekcie StaticLibrary do przełączników wiersza polecenia i opcji, które są używane do kompilowania, łączenia i debugowania na docelowej platformie systemu iOS. Aby uzyskać szczegółowe informacje na temat opcji wiersza polecenia kompilatora, Otwórz okno dialogowe **strony właściwości** dla projektu MyOpenGLESApp. iOS. StaticLibrary.  
  
## <a name="customize-your-apps"></a><a name="Customize"></a> Dostosowywanie aplikacji  
 Możesz zmodyfikować współużytkowany kod języka C++, aby dodać lub zmienić typowe funkcje. Należy zmienić wywołania kodu udostępnionego w projektach MyOpenGLESApp. Android. Native i MyOpenGLESApp. iOS. Application w celu dopasowania. Można użyć makr preprocesora, aby określić sekcje specyficzne dla platformy w danym wspólnym kodzie. Makro preprocesora `__ANDROID__` jest wstępnie zdefiniowane podczas kompilowania dla systemu Android. Makro preprocesora `__APPLE__` jest wstępnie zdefiniowane podczas kompilowania dla systemu iOS.  
  
 Aby wyświetlić funkcję IntelliSense dla konkretnej platformy projektu, wybierz projekt na liście rozwijanej przełącznik kontekstu na pasku nawigacyjnym w górnej części okna edytora.  
  
 ![Lista rozwijana z przełącznikiem kontekstu projektu w edytorze](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Problemy z technologią IntelliSense w bieżącym projekcie są oznaczone czerwoną linią falistą. Problemy w innych projektach są oznaczone purpurową linią falistą. Domyślnie program Visual Studio nie obsługuje kolorowania kodu ani funkcji IntelliSense dla plików Java lub języków języka C. Jednak nadal można modyfikować pliki źródłowe i zmieniać zasoby, aby ustawić nazwę aplikacji, ikonę i inne szczegóły implementacji.
