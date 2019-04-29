---
title: Visual C++ for Cross-Platform Mobile Development | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573069"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Język Visual C++ dla opracowywania aplikacji mobilnych na wiele platform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz tworzyć aplikacje natywne w języku C++ dla systemów iOS, Android i Windows i udziału wspólny kod w bibliotekach skompilowany dla systemów iOS, Android i Windows przy użyciu języka Visual C++ for Cross-Platform Mobile Development. Ta opcja jest dostępna w Visual Studio 2015, który instaluje zestawy SDK i narzędzia potrzebne do tworzenia aplikacji dla wielu platform, biblioteki udostępnione i natywne aplikacje. Po zainstalowaniu, można użyć Visual C++ do pisania kodu, który jest uruchamiany w systemach iOS i urządzenia z systemem Android i platformy, oprócz Windows, Windows Phone i Xbox.  
  
 Pisanie kodu dla wielu platform mogą być irytujące. Języki programowania podstawowego i narzędzia dla systemów iOS, Android i Windows różnią się na każdej platformie. Jednak wszystkie platformy obsługują pisanie kodu w języku C++. Jest to uniwersalność, którego można użyć, aby umożliwić ponowne użycie kodu core między platformami. Macierzystego kodu napisanego w języku C++ może być zarówno wydajniej i odporne na odtwarzanie. Ponowne wykorzystanie kodu może skrócić czas i nakład pracy, podczas tworzenia aplikacji dla wielu platform.  
  
 Tworzenie rozwiązań za pomocą języka Visual C++ for Cross-Platform Mobile Development ma kilka zalet:  
  
1. **Łatwa instalacja.** Instalator programu Visual Studio pobiera i instaluje wymagane narzędzia innych firm i zestawy SDK, których potrzebujesz do tworzenia aplikacji lub biblioteki dla systemów Android i iOS. Konfiguracja i instalacja jest proste i przede wszystkim automatyczne.  
  
2. **Środowisko zaawansowanych i dobrze znanych kompilacji.** Które można udostępnić rozwiązania dla wielu platform i projekty łatwo utworzyć za pomocą szablonów programu Visual Studio. Zarządzanie właściwościami dla wszystkich projektów za pomocą jednego wspólnego interfejsu. Edytuj kod w edytorze programu Visual Studio i korzystanie z zalet wbudowana funkcja IntelliSense dla wielu platform, uzupełniania kodu i wyróżniania błędów.  
  
3. **Ujednolicone środowisko debugowania.** Umożliwia światowej klasy narzędziom do debugowania w programie Visual Studio wyrażenie kontrolne i Przechodź przez kod C++ na wszystkich platformach, w tym urządzeń z systemem Android i emulatorów, symulatorach systemu iOS wymaga urządzeń i urządzeń Windows lub Windows Phone i emulatorów.  
  
## <a name="get-the-tools"></a>Pobierz narzędzia  
 W języku Visual C++ Cross-Platform Mobile Development jest opcją do zainstalowania, dostarczanego z Visual Studio 2015. Wymagania wstępne i instrukcje dotyczące instalacji, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Aby skompilować kod dla systemu iOS, należy również na komputerze Mac oraz konto dewelopera systemu iOS firmy Apple. Aby uzyskać więcej informacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Pochodzą się wszystkiego  
 Jeśli podchodzisz od etapu programowania systemu Android lub iOS mamy kilka wspaniałych materiału o tym, jak rozpocząć pracę. Visual Studio to środowisko ekspresyjna i nadaje się do rozwoju. Aby dowiedzieć się, jak z niej korzystać, spróbuj [wprowadzenie dla deweloperów systemu Android](https://msdn.microsoft.com/library/windows/apps/dn275875.aspx) lub [wprowadzenie dla deweloperów systemu iOS](https://msdn.microsoft.com/library/windows/apps/xaml/jj657966.aspx). Te tematy podstawowe informacje na temat programu Visual Studio i pojęcia, potrzebne do opracowywania aplikacji dla wielu platform Windows i Windows Phone. Aby rozpocząć pracę, pisania pierwszej aplikacji dla wielu platform dla systemów iOS i Android, zobacz [tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 W języku Visual C++ Cross-Platform Mobile Development zawiera kilka szablonów, aby pomóc Ci rozpocząć pracę w aplikacjach:  
  
- Aplikacja Opengles 2 (systemy Android i iOS, Windows Universal)  
  
     Tworzy to rozwiązanie, które zawiera zestaw projektów do kompilacji aplikacji Android Native Activity, aplikację systemu iOS i w przypadku aplikacji Universal Windows wraz z udostępnionej biblioteki kodu C++. Te aplikacje możliwe używanie bibliotek specyficzne dla platformy utworzone za pomocą wspólnego kodu C++ OpenGL ES do rysowania tego samego modułu rotowania w każdej aplikacji. Po zainstalowaniu programu Visual Studio, aby użyć tego szablonu, musi zawierać opcję Narzędzia do programowania uniwersalnych aplikacji Windows.  
  
- Aplikacja klasy Nativeactivity (Android)  
  
     Tworzy pełnej aplikacji C++ OpenGL jako projekt Android Native Activity.  
  
- Aplikacja OpenGLES (Android, iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilacji aplikacji systemu iOS i aplikacji Android Native Activity. Te aplikacje możliwe używanie bibliotek specyficzne dla platformy utworzone za pomocą wspólnego kodu C++ OpenGL ES do rysowania tego samego modułu rotowania w każdej aplikacji.  
  
- Biblioteka udostępniona (systemy Android i iOS)  
  
     Tworzy rozwiązanie z projektami tworzenia plikiem systemu Android Biblioteka dynamiczna (SO) i plik biblioteka statyczna (.a) dla systemu iOS przy użyciu wspólnego kodu w języku C++ w projekcie udostępnionym.  
  
- Podstawowa aplikacja (Android, Ant)  
  
     Tworzy aplikację Android "Hello, World" Projekt aplikacji, który używa tylko kod źródłowy Java i Ant system kompilacji.  
  
- Podstawowa aplikacja (Android, Gradle)  
  
     Tworzy aplikację Android "Hello, World" Projekt aplikacji, który używa tylko kod źródłowy Java i narzędzie Gradle system kompilacji.  
  
- Biblioteka podstawowa (Android, Ant)  
  
     Tworzy aplikację Android projektu biblioteki "Hello, World", który używa tylko kod źródłowy Java i Ant system kompilacji.  
  
- Biblioteka podstawowa (Android, Gradle)  
  
     Tworzy aplikację Android projektu biblioteki "Hello, World", który używa tylko kod źródłowy Java i narzędzie Gradle system kompilacji.  
  
- Dynamiczna Biblioteka udostępniona (Android)  
  
     Tworzy plik dla systemu Android Biblioteka dynamiczna (SO) przy użyciu kodu w języku C++.  
  
- Aplikacja Opengles 2 (iOS)  
  
     Tworzy rozwiązanie z zestawem projektów do kompilacji aplikacji systemu iOS ze specyfikacji OpenGL ES 2. Aplikacja używa biblioteki kodu C++ OpenGL ES, aby narysować modułu rotowania w aplikacji systemu iOS. Ta aplikacja może być dobry punkt wyjścia do zobaczenia jak zaimportować bibliotek C++ do aplikacji systemu iOS.  
  
- Biblioteka statyczna (Android)  
  
     Tworzy projekt do tworzenia biblioteki statycznej dla systemu Android. Możesz tylko jednego dynamicznego biblioteką w aplikacji systemu Android, ale możesz połączyć dowolną liczbę bibliotek statycznych.  
  
- Biblioteka statyczna (iOS)  
  
     Tworzy projekt do tworzenia biblioteki statycznej dla systemu iOS.  
  
- Projekt makefile (Android)  
  
     Tworzy otokę projektu dla projektów dla systemu Android pliku reguł programu make.  
  
## <a name="try-out-sample-code"></a>Wypróbuj przykładowy kod  
 Pobierz przykłady pokazujące sposób tworzenia udostępnionych bibliotek kodu używanych w aplikacji systemu iOS, systemów Android i Windows oraz jak utworzyć działanie natywne aplikacje dla systemu Android. Aby rozpocząć pracę, zobacz [Cross-Platform Mobile Development przykłady](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
1. [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2. [Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3. [Tworzenie aplikacji systemu Android działania natywnego](../cross-platform/create-an-android-native-activity-app.md)  
  
4. [Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5. [Przykłady programowania międzyplatformowych aplikacji mobilnych](../cross-platform/cross-platform-mobile-development-examples.md)
