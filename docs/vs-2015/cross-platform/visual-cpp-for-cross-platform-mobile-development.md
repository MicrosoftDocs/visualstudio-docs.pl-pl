---
title: Visual C++ dla opracowywania aplikacji mobilnych na wiele platform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e947800c82036b061b2f48303733690a95ec53bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573069"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Język Visual C++ dla opracowywania aplikacji mobilnych na wiele platform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć natywne aplikacje C++ dla urządzeń z systemami iOS, Android i Windows oraz udostępniać wspólny kod w bibliotekach skompilowanych dla systemów iOS, Android i Windows przy użyciu Visual C++ dla opracowywania aplikacji mobilnych na wiele platform. Jest to opcja dostępna w programie Visual Studio 2015, która instaluje zestawy SDK i narzędzia potrzebne do tworzenia międzyplatformowych bibliotek udostępnionych i aplikacji natywnych. Po zainstalowaniu programu można użyć Visual C++, aby utworzyć kod, który jest uruchamiany na urządzeniach z systemem iOS i Android oraz na platformach oraz w systemach Windows, Windows Phone i Xbox.  
  
 Pisanie kodu dla wielu platform może być frustrujące. Podstawowe języki deweloperskie i narzędzia dla systemów iOS, Android i Windows różnią się w zależności od platformy. Jednak wszystkie platformy obsługują pisanie kodu w języku C++. Jest to typowy mianownik, którego można użyć, aby umożliwić ponowne użycie kodu podstawowego na różnych platformach. Kod natywny zapisany w języku C++ może być jednocześnie bardziej wydajny i odporny na odtwarzanie przez odtwarzanie. Ponowne użycie kodu może zaoszczędzić czas i nakład pracy podczas tworzenia aplikacji dla wielu platform.  
  
 Programowanie przy użyciu Visual C++ dla opracowywania aplikacji mobilnych na wiele platform ma kilka zalet:  
  
1. **Łatwa instalacja.** Instalator programu Visual Studio uzyskuje i instaluje wymagane narzędzia innych firm i zestawy SDK potrzebne do kompilowania aplikacji lub bibliotek dla systemów Android i iOS. Konfiguracja i konfiguracja są proste i najczęściej automatyczne.  
  
2. **Zaawansowane i znane środowisko kompilacji.** Łatwo twórz udostępnione rozwiązania i projekty dla wielu platform za pomocą szablonów programu Visual Studio. Zarządzanie właściwościami wszystkich projektów przy użyciu jednego wspólnego interfejsu. Edytuj cały kod w edytorze programu Visual Studio i Skorzystaj z wbudowanej wieloplatformowej funkcji IntelliSense do uzupełniania kodu i wyróżniania błędów.  
  
3. **Ujednolicone środowisko debugowania.** Korzystaj z światowej klasy narzędzi do debugowania w programie Visual Studio, aby oglądać i przeszukiwać kod języka C++ na wszystkich platformach, w tym na urządzeniach z systemem Android i emulatorach, symulatorach i urządzeniach z systemem Windows lub Windows Phone urządzeń i emulatorów.  
  
## <a name="get-the-tools"></a>Pobierz narzędzia  
 Visual C++ dla opracowywania aplikacji mobilnych na wiele platform jest opcją instalowalną dołączoną do programu Visual Studio 2015. Aby uzyskać wymagania wstępne i instrukcje dotyczące instalacji, zobacz [Install Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Do utworzenia kodu dla systemu iOS potrzebny jest również komputer Mac i konto dewelopera systemu Apple iOS. Aby uzyskać więcej informacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Szybsze  
 Jeśli korzystasz z programowania w systemie Android lub iOS, mamy doskonały materiał na temat rozpoczynania pracy. Program Visual Studio jest środowiskiem deweloperskim i obsługującym. Aby dowiedzieć się, jak z niej korzystać, spróbuj [rozpocząć pracę dla deweloperów systemu Android](https://msdn.microsoft.com/library/windows/apps/dn275875.aspx) lub [wprowadzenie do deweloperów systemu iOS](https://msdn.microsoft.com/library/windows/apps/xaml/jj657966.aspx). Te tematy zawierają wprowadzenie do programu Visual Studio i pojęć potrzebnych do tworzenia aplikacji dla wielu platform dla systemu Windows i Windows Phone. Aby rozpocząć tworzenie pierwszej aplikacji dla wielu platform dla systemów iOS i Android, zobacz [Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ dla opracowywania aplikacji mobilnych na wiele platform zawiera kilka szablonów, które ułatwiają rozpoczęcie pracy z aplikacjami:  
  
- Aplikacja OpenGLs 2 (systemy Android, iOS, Universal Windows)  
  
     Tworzy rozwiązanie, które zawiera zestaw projektów do kompilowania aplikacji natywnej aktywności systemu Android, aplikacji dla systemu iOS i uniwersalnej aplikacji systemu Windows wraz z udostępnioną biblioteką kodu C++. Aplikacje te używają bibliotek specyficznych dla platformy utworzonych przy użyciu wspólnego kodu języka C++ OpenGL ES do rysowania tego samego obracającego się modułu w każdej aplikacji. Podczas instalowania programu Visual Studio w celu użycia tego szablonu należy uwzględnić opcję Narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows.  
  
- Aplikacja natywna (Android)  
  
     Tworzy kompletną aplikację języka C++ OpenGL jako projekt natywnych działań systemu Android.  
  
- Aplikacja OpenGLs (Android, iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilowania zarówno aplikacji natywnej aktywności systemu Android, jak i aplikacji systemu iOS. Aplikacje te używają bibliotek specyficznych dla platformy utworzonych przy użyciu wspólnego kodu języka C++ OpenGL ES do rysowania tego samego obracającego się modułu w każdej aplikacji.  
  
- Biblioteka udostępniona (Android, iOS)  
  
     Tworzy rozwiązanie z projektami, aby utworzyć plik biblioteki dynamicznej systemu Android (. so) i plik statycznej biblioteki systemu iOS (. a) przy użyciu wspólnego kodu C++ w projekcie udostępnionym.  
  
- Aplikacja podstawowa (Android, ANT)  
  
     Tworzy projekt aplikacji "Hello, World" dla systemu Android, który używa tylko kodu źródłowego Java i systemu kompilacji ANT.  
  
- Aplikacja podstawowa (Android, Gradle)  
  
     Tworzy projekt aplikacji "Hello, World" dla systemu Android, który używa tylko kodu źródłowego Java i systemu kompilacji Gradle.  
  
- Biblioteka podstawowa (Android, ANT)  
  
     Tworzy projekt biblioteki dla systemu Android "Hello, World", który używa tylko kodu źródłowego Java i systemu kompilacji ANT.  
  
- Biblioteka podstawowa (Android, Gradle)  
  
     Tworzy projekt biblioteki dla systemu Android "Hello, World", który używa tylko kodu źródłowego Java i systemu kompilacji Gradle.  
  
- Dynamiczna biblioteka udostępniona (Android)  
  
     Tworzy plik biblioteki dynamicznej systemu Android (. so) przy użyciu kodu C++.  
  
- Aplikacja OpenGLs 2 (iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilowania aplikacji dla systemu iOS w technologii OpenGL ES 2. Aplikacja używa biblioteki języka C++ z kodem OpenGL ES do rysowania obracającego się modułu w aplikacji systemu iOS. Ta aplikacja może być dobrym punktem wyjścia do wyświetlania sposobu importowania bibliotek C++ do aplikacji systemu iOS.  
  
- Biblioteka statyczna (Android)  
  
     Tworzy projekt do kompilowania biblioteki statycznej dla systemu Android. Można połączyć tylko jedną bibliotekę dynamiczną w aplikacji systemu Android, ale można połączyć dowolną liczbę bibliotek statycznych.  
  
- Biblioteka statyczna (iOS)  
  
     Tworzy projekt do kompilowania biblioteki statycznej dla systemu iOS.  
  
- Projekt pliku reguł programu make (Android)  
  
     Tworzy otokę projektu dla własnych projektów programu make dla systemu Android.  
  
## <a name="try-out-sample-code"></a>Wypróbuj przykładowy kod  
 Pobierz przykłady pokazujące, jak tworzyć udostępnione biblioteki kodu, których można używać w aplikacjach systemu Windows, Android i iOS oraz jak tworzyć kompletne aplikacje natywnych działań dla systemu Android. Aby rozpocząć, zobacz [przykłady tworzenia aplikacji mobilnych dla wielu platform](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
1. [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2. [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3. [Tworzenie aplikacji dla systemu Android Native Activity](../cross-platform/create-an-android-native-activity-app.md)  
  
4. [Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5. [Przykłady tworzenia aplikacji mobilnych dla wielu platform](../cross-platform/cross-platform-mobile-development-examples.md)
