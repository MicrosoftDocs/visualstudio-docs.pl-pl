---
title: Programowanie aplikacji mobilnych dla wielu platform C++ za pomocą programu | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: bc4164ec405aed2941e807934ee8d66b7ae72504
ms.sourcegitcommit: ca3bb6db949f5e405f6ffe1afa5f430662c1173f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2019
ms.locfileid: "74098973"
---
# <a name="cross-platform-mobile-development-with-c"></a>Opracowywanie aplikacji mobilnych na wiele platform w języku C++

Możesz tworzyć natywne C++ aplikacje dla urządzeń z systemami iOS, Android i Windows za pomocą międzyplatformowych narzędzi dostępnych w programie Visual Studio. **Programowanie aplikacji C++ mobilnych** w programie to obciążenie dostępne w Instalatorze programu Visual Studio. Instaluje zestawy SDK i narzędzia potrzebne do tworzenia międzyplatformowych bibliotek udostępnionych i aplikacji natywnych. Po zainstalowaniu programu możesz użyć C++ programu, aby utworzyć kod, który jest uruchamiany na urządzeniach z systemem iOS lub Android oraz na platformach, Windows, sklepie Windows i konsoli Xbox.

Pisanie kodu dla wielu platform jest często frustrujące. Podstawowe języki deweloperskie i narzędzia dla systemów iOS, Android i Windows różnią się w zależności od platformy. Jednak wszystkie platformy obsługują pisanie kodu w C++. Jest to typowy mianownik, który umożliwia ponowne użycie kodu podstawowego na różnych platformach. Kod natywny pisany C++ w programie może być jednocześnie bardziej wydajny i odporny na odtwarzanie przez proces odtwarzania. Ponowne użycie kodu może zaoszczędzić czas i nakład pracy podczas tworzenia aplikacji dla wielu platform.

Programowanie za C++ pomocą aplikacji mobilnych dla wielu platform ma kilka zalet:

- **Łatwa instalacja.** Instalator programu Visual Studio uzyskuje i instaluje wymagane narzędzia innych firm i zestawy SDK potrzebne do kompilowania aplikacji lub bibliotek dla systemów Android i iOS. Konfiguracja i konfiguracja są proste i najczęściej automatyczne.

- **Zaawansowane i znane środowisko kompilacji.** Łatwo twórz udostępnione rozwiązania i projekty dla wielu platform za pomocą szablonów programu Visual Studio. Zarządzanie właściwościami wszystkich projektów przy użyciu jednego wspólnego interfejsu. Edytuj cały kod w edytorze programu Visual Studio i Skorzystaj z wbudowanej wieloplatformowej funkcji IntelliSense do uzupełniania kodu i wyróżniania błędów.

- **Ujednolicone środowisko debugowania.** Korzystaj z światowej klasy narzędzi do debugowania w programie Visual Studio, aby oglądać C++ i przełączać kod na wszystkich platformach: urządzenia z systemem Android i emulatory, symulatory systemu iOS i urządzenia, a także systemy Windows i emulatory systemu Windows.

## <a name="get-the-tools"></a>Pobierz narzędzia

Programowanie aplikacji mobilnych C++ za pomocą programu to z możliwością instalacji, która jest dostarczana z programem Visual Studio. Aby uzyskać wymagania wstępne i instrukcje dotyczące instalacji, zobacz [Instalowanie aplikacji mobilnych dla C++wielu platform za pomocą programu ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Do utworzenia kodu dla systemu iOS potrzebny jest również komputer Mac i konto dewelopera systemu Apple iOS. Aby uzyskać więcej informacji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="come-up-to-speed"></a>Szybsze

Jeśli korzystasz z programowania w systemie Android lub iOS, mamy doskonały materiał na temat rozpoczynania pracy. Program Visual Studio jest środowiskiem deweloperskim i obsługującym. Aby dowiedzieć się, jak z niej korzystać, wypróbuj [deweloperów systemu Android](/previous-versions/windows/apps/dn275875\(v=win.10\)) lub Rozpocznij [pracę dla deweloperów systemu iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Te artykuły zawierają wprowadzenie do programu Visual Studio i koncepcje potrzebne do tworzenia aplikacji dla wielu platform dla systemu Windows i sklepu Windows. Aby rozpocząć tworzenie pierwszej aplikacji dla wielu platform dla systemów iOS i Android, zobacz [Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).

Tworzenie aplikacji mobilnych przy C++ użyciu obciążeń obejmuje kilka szablonów, które ułatwiają rozpoczęcie pracy z aplikacjami:

- Aplikacja natywna (Android)

  Tworzy kompletną C++ aplikację OpenGL jako projekt natywnej aktywności systemu Android.

- Aplikacja OpenGLs (Android, iOS)

  Tworzy rozwiązanie z zestawem projektów do kompilowania zarówno aplikacji natywnej aktywności systemu Android, jak i aplikacji systemu iOS. Aplikacje te używają bibliotek specyficznych dla platformy utworzonych przy użyciu C++ wspólnego kodu OpenGL ES do rysowania tego samego obracającego się modułu w każdej aplikacji.

- Biblioteka udostępniona (Android, iOS)

  Tworzy rozwiązanie z projektami, aby utworzyć plik biblioteki dynamicznej systemu Android (. so) i plik statycznej biblioteki systemu iOS (. a) przy użyciu C++ wspólnego kodu w projekcie udostępnionym.

- Aplikacja podstawowa (Android, ANT)

  Tworzy projekt aplikacji "Hello, World" dla systemu Android, który używa tylko kodu źródłowego Java i systemu kompilacji ANT.

- Aplikacja podstawowa (Android, Gradle)

  Tworzy projekt aplikacji "Hello, World" dla systemu Android, który używa tylko kodu źródłowego Java i systemu kompilacji Gradle.

- Biblioteka podstawowa (Android, ANT)

  Tworzy projekt biblioteki dla systemu Android "Hello, World", który używa tylko kodu źródłowego Java i systemu kompilacji ANT.

- Biblioteka podstawowa (Android, Gradle)

  Tworzy projekt biblioteki dla systemu Android "Hello, World", który używa tylko kodu źródłowego Java i systemu kompilacji Gradle.

- Dynamiczna biblioteka udostępniona (Android)

  Tworzy plik biblioteki dynamicznej systemu Android (. so) za pomocą C++ kodu.

- Aplikacja OpenGLs 2 (iOS)

  Tworzy rozwiązanie z zestawem projektów do kompilowania aplikacji dla systemu iOS w technologii OpenGL ES 2. Aplikacja używa biblioteki oprogramowania C++ OpenGL ES Code do rysowania obracającego się modułu w aplikacji systemu iOS. Ta aplikacja może być dobrym punktem wyjścia do wyświetlania sposobu importowania C++ bibliotek do aplikacji systemu iOS.

- Biblioteka statyczna (Android)

  Tworzy projekt do kompilowania biblioteki statycznej dla systemu Android. Można połączyć tylko jedną bibliotekę dynamiczną w aplikacji systemu Android, ale można połączyć dowolną liczbę bibliotek statycznych.

- Biblioteka statyczna (iOS)

  Tworzy projekt do kompilowania biblioteki statycznej dla systemu iOS.

- Projekt pliku reguł programu make (Android)

  Tworzy otokę projektu dla własnych projektów programu make dla systemu Android.

## <a name="try-out-sample-code"></a>Wypróbuj przykładowy kod

Pobierz przykłady pokazujące sposób tworzenia udostępnionych bibliotek kodu, których można używać w aplikacjach dla systemów Windows, Android i iOS. I Zobacz przykłady tworzenia kompletnych natywnych aplikacji aktywności dla systemu Android. Aby rozpocząć, zobacz [przykłady tworzenia aplikacji mobilnych dla wielu platform](../cross-platform/cross-platform-mobile-development-examples.md).

## <a name="see-also"></a>Zobacz także

[Instalowanie międzyplatformowego opracowywania aplikacji C++ mobilnych za pomocą](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md) \
[Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu \ systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)
[Tworzenie aplikacji dla systemu Android native activity](../cross-platform/create-an-android-native-activity-app.md) \
[Tworzenie aplikacji OpenGL ES w systemach Android i iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md) \
[Przykłady tworzenia aplikacji mobilnych dla wielu platform](../cross-platform/cross-platform-mobile-development-examples.md)
