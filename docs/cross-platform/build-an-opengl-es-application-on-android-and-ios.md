---
title: Tworzenie aplikacji OpenGL ES w systemach Android i iOS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/16/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: aa8ffe308f8a1181ed18af52ba7537c46007de94
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317648"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Tworzenie aplikacji OpenGL ES w systemach Android i iOS

Można tworzyć rozwiązania programu Visual Studio i projekty dla aplikacji systemu iOS i aplikacje dla systemu Android, które współużytkują wspólny kod. Ten artykuł przeprowadzi Cię przez szablon rozwiązania, która tworzy zarówno w przypadku aplikacji systemu iOS proste, jak i aplikacji Android Native Activity. Aplikacje wspólnym kodu w języku C++, których używa OpenGL ES do wyświetlenia tego samego modułu rotacji animowany na każdej platformie. OpenGL ES (OpenGL dla systemów osadzone lub GLES) jest grafiki 2D i 3D interfejsu API, który jest obsługiwany na wiele urządzeń przenośnych.

## <a name="requirements"></a>Wymagania

Przed utworzeniem aplikacji OpenGL ES dla systemów iOS i Android, upewnij się, że zostały spełnione wszystkie wymagania systemowe. Jeśli jeszcze nie, zainstaluj programowanie aplikacji mobilnych za pomocą C++ obciążenie w Instalatorze programu Visual Studio. Aby kompilowanie dla systemu iOS, należy dołączyć opcjonalny C++ narzędzi programistycznych dla systemu iOS. Aby utworzyć dla systemu Android, należy zainstalować C++ narzędziami programistycznymi systemu Android oraz wymagane narzędzia innych firm: Android NDK, Apache Ant, Emulator systemu Google Android i sprzęt firmy Intel przyspieszone menedżera wykonywania. Następnie skonfiguruj Intel HAXM i emulatora systemu Android do uruchomienia w systemie. Aby uzyskać więcej informacji oraz szczegółowe instrukcje, zobacz [zainstalować Visual C++ dla opracowywania aplikacji mobilnych dla wielu platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Do tworzenia i testowania aplikacji dla systemu iOS, będzie potrzebny jest komputer Mac komputer, skonfigurowany zgodnie z instrukcjami instalacji. Aby uzyskać więcej informacji o tym, jak skonfigurować do tworzenia aplikacji dla systemu iOS, zobacz [zainstalować i skonfigurować narzędzia umożliwiające tworzenie za pomocą systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)

## <a name="create-a-new-opengles-application-project"></a>Utwórz nowy projekt aplikacja OpenGLES

W tym samouczku najpierw utwórz nowy projekt aplikacji OpenGL ES i następnie skompilować i uruchomić aplikację domyślnej w Visual Studio Emulator dla systemu Android. Następnie utwórz aplikację dla systemu iOS i uruchom aplikację na urządzeniu z systemem iOS.

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** okno dialogowe, w obszarze **szablony**, wybierz **Visual C++**  > **Międzyplatformowe**, a następnie wybierz pozycję **Aplikacja OpenGLES (Android, iOS)** szablonu.

1. Nadaj aplikacji nazwę, takich jak `MyOpenGLESApp`, a następnie wybierz **OK**.

   ![Nowy projekt aplikacji OpenGLES](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio tworzy nowego rozwiązania i otwiera w Eksploratorze rozwiązań.

   ![MyOpenGLESApp w Eksploratorze rozwiązań](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

   Nowe rozwiązanie aplikacji OpenGL ES obejmuje trzy projekty biblioteki i dwa projekty aplikacji. Folder biblioteki zawiera projekt współużytkowanego kodu i dwa projekty specyficzne dla platformy, odwołujące się do udostępnionego kodu:

- `MyOpenGLESApp.Android.NativeActivity` zawiera odwołania i kod sklejający, który implementuje aplikację jako działania natywnego w systemie Android. Punkty wejścia z kodu pośredniczącego są implementowane w *main.cpp*, która obejmuje wspólny kod udostępniony w `MyOpenGLESApp.Shared`. Prekompilowane nagłówki znajdują się w *pch.h*. Ten projekt aplikacji Native Activity jest skompilowany w bibliotece udostępnionej (*SO*) plik, który zostaje pobrana przez `MyOpenGLESApp.Android.Packaging` projektu.

- `MyOpenGLESApp.iOS.StaticLibrary` Tworzy bibliotekę statycznych dla systemu iOS ( *.a*) plik, który zawiera kod udostępniony w `MyOpenGLESApp.Shared`. Jest on połączony aplikację utworzoną przez `MyOpenGLESApp.iOS.Application` projektu.

- `MyOpenGLESApp.Shared` zawiera kod udostępniony, który działa na różnych platformach. Makra preprocesora używa dla kompilacji warunkowej kodu specyficznego dla platformy. Kod udostępniony zostaje pobrana przez odwołanie do projektu w obu `MyOpenGLESApp.Android.NativeActivity` i `MyOpenGLESApp.iOS.StaticLibrary`.

Rozwiązanie zawiera dwa projekty do tworzenia aplikacji dla platformy Android i iOS:

- `MyOpenGLESApp.Android.Packaging` Tworzy *.apk* plik dla wdrożenia na urządzeniu z systemem Android lub w emulatorze. Ten plik zawiera zasoby i pliku AndroidManifest.xml, można ustawić właściwości manifestu. Zawiera ona także *build.xml* pliku, który kontroluje Ant procesu kompilacji. Ustawiana jest jako projekt startowy domyślnie, tak że można wdrożyć i uruchomić bezpośrednio z programu Visual Studio.

- **MyOpenGLESApp.iOS.Application** zawiera zasoby i kodu pośredniczącego języka Objective-C, aby utworzyć aplikację dla systemu iOS prowadzący do kodu C++ biblioteki statycznej w `MyOpenGLESApp.iOS.StaticLibrary`. Ten projekt tworzy pakiet kompilacji, który jest przekazywany do komputera Mac, program Visual Studio i zdalnego agenta. Podczas tworzenia tego projektu programu Visual Studio wysyła pliki i polecenia do tworzenia i wdrażania aplikacji na komputerach Mac.

## <a name="build-and-run-the-android-app"></a>Kompilowanie i uruchamianie aplikacji systemu Android

Rozwiązanie utworzone przez szablon ustawia aplikacji dla systemu Android jako domyślny projekt.  Można skompilować i uruchomić tę aplikację, aby zweryfikować instalacji i konfiguracji. Dla testu wstępnego, uruchom aplikację na jeden z profilów urządzeń instalowane przez emulator dla systemu Android. Jeśli chcesz testować swoją aplikację na innym elementem docelowym można ładować emulatora docelowego, lub podłącz urządzenie do komputera.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Aby skompilować i uruchomić aplikację systemu Android działania natywnego

1. Jeśli nie została jeszcze wybrana, wybierz opcję **x86** z **platformy rozwiązania** listy rozwijanej.

   ![Ustaw platforma rozwiązania x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   Użyj x86 pod kątem emulatora. Do urządzenia, wybierz platformę rozwiązania oparte na procesorze urządzenia. Jeśli **platformy rozwiązania** lista nie jest wyświetlona, wybierz polecenie **platformy rozwiązania** z **Dodaj lub usuń przyciski** , a następnie wybierz platformy.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla `MyOpenGLESApp.Android.Packaging` projektu, a następnie wybierz **kompilacji**.

   ![Kompiluj projekt pakowania dla systemu Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji dla programu Android udostępnionych, biblioteki i aplikacji dla systemu Android.

   ![Dane wyjściowe kompilacji dla projektów systemu Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Wybierz jeden z profilów emulowanej urządzenia z systemem Android jako urządzenie docelowe wdrożenia.

   ![Wybierz cel wdrożenia](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Jeśli masz zainstalowany innych emulatorów lub podłączone urządzenie z systemem Android, można je na liście rozwijanej cel wdrożenia. Aby uruchomić aplikację, wbudowanego platforma rozwiązania muszą być zgodne platforma urządzenia docelowego.

1. Naciśnij klawisz F5, aby rozpocząć debugowanie lub Shift + F5, aby uruchomić bez debugowania.

   Program Visual Studio uruchamia emulatora, który zajmuje kilka sekund, aby załadować i wdrożyć swój kod. Poniżej przedstawiono, jak aplikacja jest wyświetlana w emulatorze:

   ![Aplikacja uruchomiona w emulatorze systemu Android](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i użyć debugera, aby przejść przez kod, Sprawdź zmienne lokalne i obejrzyj wartości.

1. Naciśnij klawisz **Shift**+**F5** Aby zatrzymać debugowanie.

   Emulator jest oddzielny proces, który będzie nadal działać. Można edytować, skompiluj i wdróż swój kod wielokrotnie do tego samego emulatora. Aplikacja pojawia się w kolekcji aplikacji w emulatorze, i może być uruchamiany z tego miejsca bezpośrednio.

   Wygenerowany Android Native Activity aplikacji i bibliotekę projektów C++ kodu udostępnionego w Biblioteka dynamiczna, która zawiera kod "skleić" interfejs za pomocą platformy systemu Android. Większość kodu aplikacji znajduje się w bibliotece i manifestu, zasoby i instrukcje kompilacji są podczas pakowania projektu. Kod udostępniony jest wywoływana z main.cpp w projekcie klasy NativeActivity. Aby uzyskać więcej informacji na temat sposobu programowania dla systemu Android Native Activity Zobacz zestawu Android NDK Developer [pojęcia](https://developer.android.com/ndk/guides/concepts.html) strony.

   Program Visual Studio tworzy Android Native Activity projektów przy użyciu zestawu Android NDK, który używa zestawu narzędzi platformy Clang. Program Visual Studio mapuje właściwości w projekcie klasy NativeActivity opcje używane do kompilowania, link i debugowanie na platformie docelowej. Aby uzyskać szczegółowe informacje, otwórz **stron właściwości** okno dialogowe dla projektu MyOpenGLESApp.Android.NativeActivity. Aby uzyskać więcej informacji na temat przełączników wiersza polecenia, zobacz [Clang kompilatora obsługi](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Kompilowanie i uruchamianie aplikacji dla systemu iOS na urządzeniu z systemem iOS

Projekt aplikacji systemu iOS jest tworzony i edytować w programie Visual Studio, ale z powodu ograniczeń licencyjnych, musi być utworzone i wdrożone z komputerów Mac. Program Visual Studio komunikuje się z agenta zdalnego uruchomiona na komputerze Mac do przesyłania plików projektu i wykonania kompilacji, wdrażania i debugowania poleceń. Instalowanie i konfigurowanie systemów Mac i Visual Studio, do komunikowania się przed utworzeniem aplikacji dla systemu iOS. Aby uzyskać szczegółowe instrukcje, zobacz [zainstalować i skonfigurować narzędzia umożliwiające tworzenie za pomocą systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Gdy agent zdalny jest uruchomiony na komputerze Mac i sparowane z programem Visual Studio, można tworzyć i uruchom aplikację dla systemu iOS, aby zweryfikować instalacji i konfiguracji.

Aby wdrożyć aplikację systemu iOS na urządzeniu z systemem iOS, należy również skonfigurować automatyczne podpisywanie w środowisku Xcode na komputerze Mac. Automatyczne podpisywanie automatycznie zarządza podpisywania aplikacji i tworzy profil aprowizowania do podpisania kompilacji aplikacji.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Aby skonfigurować automatyczne podpisywanie w środowisku Xcode

1. Jeśli jeszcze nie, zainstaluj [Xcode](https://developer.apple.com/xcode/downloads/) wersji 10.2.1 lub później na komputerze Mac.

1. Otwórz aplikację Xcode na komputerze Mac.

1. Utwórz nową **aplikacja pojedynczego widoku** projektu Xcode. Wypełnij wymagane pola podczas tworzenia projektu. Wartości mogą być dowolnego, projektu jest używana wyłącznie do utworzenia profilu aprowizacji, który jest później używany do podpisywania kompilacji aplikacji.

1. Dodaj identyfikator Apple ID zarejestrowanej w [Apple Developer Program](https://developer.apple.com/programs/) konta w narzędziu Xcode. Identyfikator Apple ID jest używany jako tożsamość podpisywania do podpisywania aplikacji. Aby dodać tożsamość podpisywania w środowisku Xcode, otwórz **Xcode** menu i wybrać **preferencje**. Wybierz **kont** i kliknij przycisk Dodaj (+), aby dodać identyfikator Apple ID. Aby uzyskać szczegółowe instrukcje, zobacz [Dodaj swoje konto Apple ID](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. W ustawieniach "Ogólne" Projekt Xcode, zmień wartość właściwości **identyfikatora pakietu** do `com.<NameOfVSProject>`, gdzie `<NameOfVSProject>` jest taką samą nazwę jak projekt rozwiązania Visual Studio został utworzony. Na przykład, jeśli utworzono projekt o nazwie `MyOpenGLESApp` w programie Visual Studio, następnie ustawić **identyfikatora pakietu** do `com.MyOpenGLESApp`.

   ![Identyfikator pakietu programu Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Aby włączyć automatyczne podpisywanie, należy sprawdzić. Automatycznie zarządzała podpisywania **.

   ![Automatyczne podpisywanie programu Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Wybierz nazwę zespołu identyfikatora Apple ID, dodawane w miarę rozwoju **zespołu**.

   ![Zespół programu Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Aby skompilować i uruchomić aplikację systemu iOS na urządzeniu z systemem iOS

1. Uruchamianie zdalnego agenta na komputerze Mac i sprawdź, czy program Visual Studio jest sparowana z agentem zdalnym. Aby uruchomić agenta zdalnego, Otwórz okno terminalu aplikacji, a następnie wprowadź `vcremote`. Aby uzyskać więcej informacji, zobacz [skonfigurować agenta zdalnego w programie Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Okno terminala na komputerze Mac vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Dołączanie urządzenia z systemem iOS na komputerze Mac. Po dołączeniu urządzenia do komputera po raz pierwszy alert pyta, czy ufasz komputerowi dostęp do urządzenia. Urządzenie ma zaufanie do komputera Mac włączyć.

1. W programie Visual Studio, jeśli nie została jeszcze wybrana, wybierz platformę rozwiązania z **platformy rozwiązania** listy rozwijanej oparte na procesorze Twojego urządzenia. W tym przykładzie jest **ARM64** procesora.

   ![Ustaw platforma rozwiązania ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu MyOpenGLESApp.iOS.Application, a następnie wybierz **Zwolnij projekt** zwalnianie projektu.

1. Ponownie otwórz menu skrótów dla projektu MyOpenGLESApp.iOS.Application zwolnione i wybierz **Edytuj project.pbxproj** do edycji pliku projektu. W `project.pbxproj` pliku, poszukaj `buildSettings` atrybutu i Dodaj `DEVELOPMENT_TEAM` przy użyciu swojego identyfikatora Apple zespołu. Poniższy zrzut ekranu przedstawia przykład wartość `123456ABC` dla identyfikatora zespołu firmy Apple. Wartość Identyfikatora firmy Apple zespołu można znaleźć z narzędzia Xcode. Przejdź do **ustawieniach kompilacji** i umieść kursor nad swoją nazwę zespołu rozwoju, aby wyświetlić etykietkę narzędzia. Etykietki narzędzia jest wyświetlana Twoja nazwa zespołu.

   ![Ustawianie zespołu programistycznego](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Zamknij `project.pbxproj` pliku, a następnie otwórz menu skrótów dla projektu MyOpenGLESApp.iOS.Application zwolnione i wybierz **Załaduj ponownie projekt** ponownie załadować projektu.

1. Tworzenie projektu MyOpenGLESApp.iOS.Application, otwierając menu skrótów dla projektu i wybierając pozycję **kompilacji**.

   ![Tworzenie projektu aplikacji systemu iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   W oknie danych wyjściowych wyświetla dane wyjściowe z procesu kompilacji dla biblioteki statycznej dla systemu iOS oraz aplikacji dla systemu iOS. Na komputerze Mac, uruchamianie zdalnego agenta Pokazuje okno terminalu polecenia i transferu plików działania.

   Na komputerze Mac może monit umożliwia codesign na dostęp do pęku kluczy. Wybierz **Zezwalaj** aby kontynuować.

1. Wybierz swoje urządzenie z systemem iOS, na pasku narzędzi, aby uruchomić aplikację na urządzeniu dołączone do Twojego komputera Mac. Jeśli aplikacja nie stanie, sprawdź, czy urządzenie daje uprawnienia do Twojej wdrożonej aplikacji, można wykonać na urządzeniu. To uprawnienie można ustawić, przechodząc do **ustawienia** > **ogólne** > **zarządzania urządzeniami** na urządzeniu. Wybierz konto usługi dla deweloperów aplikacji, Twoje konto zaufania i Sprawdź aplikację. Spróbuj ponownie uruchomić aplikację w programie Visual Studio.

   ![Aplikacja systemu iOS na urządzeniu z systemem iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")
   
   Po uruchomieniu aplikacji, możesz ustawić punkty przerwania i za pomocą debugera programu Visual Studio do badania zmiennych lokalnych, zobaczyć stos wywołań i obejrzyj wartości.

   ![Debuger w punkcie przerwania w aplikacji dla systemu iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Naciśnij klawisz **Shift**+**F5** Aby zatrzymać debugowanie.

   Projekty aplikacji i biblioteki wygenerowany dla systemu iOS umieść kod C++ w bibliotece statycznej, która implementuje udostępnionego kodu. Większość kodu aplikacji znajduje się w `Application` projektu. Wywołania do biblioteki udostępnionej kodu w tym projekcie szablonu są dokonywane w *GameViewController.m* pliku. Tworzenie aplikacji dla systemu iOS, Visual Studio korzysta z narzędzia Xcode zestaw narzędzi platformy, która wymaga komunikacji z klientem zdalnym, który działa na komputerach Mac.

   Visual Studio przesyła pliki projektu i wysyła polecenia do zdalnego klienta, aby skompilować aplikację za pomocą środowiska Xcode. Klient zdalny wysyła kompilacji informacje o stanie do programu Visual Studio. Gdy aplikacja została pomyślnie skompilowane, można użyć programu Visual Studio do wysyłania poleceń do uruchamiania i debugowania aplikacji. W debugerze programu Visual Studio kontroluje działanie aplikacji na urządzeniu z systemem iOS dołączone do Twojego komputera Mac. Program Visual Studio mapuje właściwości w projekcie StaticLibrary opcje używane do kompilowania, link i debugowanie na platformę docelową dla systemu iOS. Dla opcji wiersza polecenia kompilatora uzyskać więcej informacji, otwórz **stron właściwości** okno dialogowe dla projektu MyOpenGLESApp.iOS.StaticLibrary.

## <a name="customize-your-apps"></a>Dostosowywanie aplikacji

Można zmodyfikować współdzielonym kodem C++, aby dodać lub zmienić typowych funkcji. Należy zmienić wywołania współużytkowanym kodem w `MyOpenGLESApp.Android.NativeActivity` i `MyOpenGLESApp.iOS.Application` projekty do dopasowania. Makra preprocesora służy do określania sekcje specyficzne dla platformy w kodzie wspólnej. Makro preprocesora `__ANDROID__` jest wstępnie zdefiniowane podczas kompilowania dla systemu Android. Makro preprocesora `__APPLE__` jest wstępnie zdefiniowane podczas kompilowania dla systemu iOS.

Aby wyświetlić funkcję IntelliSense dla platform konkretnego projektu, wybierz projekt w menu rozwijanym przełącznik kontekstu na pasku nawigacyjnym, w górnej części okna edytora.

![Projekt z listy rozwijanej przełącznik kontekst, w edytorze](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Czerwona linia falista są oznaczone problemów IntelliSense w kodzie, który jest używany przez bieżącego projektu. Purpurowa linia falista są oznaczone problemów w innych projektach. Program Visual Studio nie obsługuje kod kolorowania i technologii IntelliSense dla plików języka Java lub języka Objective-C. Można nadal zmodyfikować pliki źródłowe i zmienić zasoby, aby ustawić nazwę swojej aplikacji, ikony i inne szczegóły implementacji.
