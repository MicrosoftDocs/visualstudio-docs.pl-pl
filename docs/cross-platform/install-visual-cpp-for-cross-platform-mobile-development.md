---
title: Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele Platform | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 261d26307a212fa44506b21caadf4b7351453e06
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261094"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalowanie aplikacji mobilnych dla wielu platform przy użyciu języka C++

C++ w programie Visual Studio służy do tworzenia aplikacji klasycznych Windows Universal Windows Platform (platformy uwp), aplikacje systemu Linux i teraz aplikacje dla systemów Android i iOS. **Opracowywania aplikacji mobilnych w języku C++** obciążenia to zestaw instalowalnych składników w programie Visual Studio zawiera wieloplatformowych dla systemów iOS, Android i platformy uniwersalnej systemu Windows w programie Visual Studio szablonów. Instaluje narzędzi dla wielu platform i zestawy SDK, musisz szybkie rozpoczęcie pracy, bez konieczności zlokalizować, pobrać i skonfigurować je samodzielnie. Możesz użyć tych narzędzi w programie Visual Studio do łatwego tworzenia, edytowania, debugowania i testowania Twoich projektów dla wielu platform. W tym temacie opisano sposób instalowania narzędzi i oprogramowania innych firm, wymagane do rozwoju aplikacji dla wielu platform w języku C++ za pomocą programu Visual Studio. Aby uzyskać przegląd, zobacz [Visual C++ cross-platform mobile](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>Wymagania

- Aby uzyskać wymagania dotyczące instalacji, zobacz [wymagania systemowe rodziny produktów Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Jeśli używasz, Windows 7 lub Windows Server 2008 R2, możesz tworzyć kod dla aplikacji komputerowych Windows i aplikacji Android Native Activity i bibliotek, aplikacji i bibliotek kodu dla systemu iOS, ale nie Windows Phone aplikacje platformy uniwersalnej systemu Windows.

Aby tworzyć aplikacje dla konkretnych platform sprzętowych, istnieją pewne dodatkowe wymagania:

- Emulatory Windows Phone i Microsoft Visual Studio Emulator for Android wymagają komputera, która może działać na funkcji Hyper-V. Musi być włączona funkcja Hyper-V w Windows, zanim można instalować i uruchamiać emulatorów. Aby uzyskać więcej informacji, zobacz emulatora usługi [wymagania systemowe](system-requirements-for-the-visual-studio-emulator-for-android.md).

- X86 emulatorów systemu Android, które pochodzą z zestawu SDK systemu Android działają najlepiej na komputerach, które można uruchomić sterownika Intel HAXM. Ten sterownik wymaga procesora Intel x64 z obsługą Bit wykonania wyłączyć i VT-x. Aby uzyskać więcej informacji, zobacz [Intel® sprzętu Accelerated menedżera wykonywania (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- Tworzenie kodu dla systemu iOS wymaga identyfikatora Apple ID, konta dewelopera programu z systemem iOS i komputera Mac, która może działać [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) w wersji 6 lub nowszy na OS X mavericks z przeglądarką (w wersji 10.9) lub nowszy. Aby uzyskać link do kroków instalacji, zobacz [instalowania narzędzi dla systemu iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Pobierz narzędzia

Tworzenie aplikacji mobilnych przy użyciu języka C++ jest dostępna w wersjach programu Visual Studio Community, Professional i Enterprise. Aby uzyskać program Visual Studio, przejdź do [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony. Narzędzia do opracowywania aplikacji mobilnych dla wielu platform są dostępne, począwszy od programu Visual Studio 2015.

## <a name="install-the-tools"></a>Instalowanie narzędzi

Instalator programu Visual Studio dla programu Visual Studio 2017 obejmuje **opracowywania aplikacji mobilnych w języku C++** obciążenia, który instaluje narzędzia języka C++, szablony i składniki wymagane dla systemów Android i iOS development w programie Visual Studio. Instaluje GCC i Clang narzędzie zbiorów niezbędnych dla systemu Android kompilacji i debugowania i składników do komunikowania się z komputerem Mac do tworzenia aplikacji dla systemu iOS. Instaluje także wszystkich narzędzi innych firm i software development kit, które są wymagane do obsługi systemów iOS i rozwoju aplikacji dla systemu Android. Większość tych narzędzi innych firm to oprogramowanie typu open-source wymagane do obsługi platformy systemu Android.

- Dla systemu android natywnych Development Kit (zestawu NDK) jest wymagany do kompilowania kodu C++, który jest przeznaczony dla platformy systemu Android.

- Zestaw SDK systemu android, Apache Ant i Java SE Development Kit są wymagane dla procesu kompilacji dla systemu Android.

- Emulator systemu Google Android i menedżera wykonywania Accelerated sprzętu Intel są opcjonalne, ale jest to zalecane, składniki. Programowanie i debugowanie można przeprowadzać bezpośrednio na urządzeniu z systemem Android, ale często jest łatwiejszy w obsłudze emulatora na pulpicie do debugowania. Firma Microsoft udostępnia również Visual Studio Emulator for Android, którą można zainstalować oddzielnie.

### <a name="install-the-mobile-development-with-c-workload"></a>Zainstaluj opracowywania aplikacji mobilnych z obciążeniem C++

1. Uruchom **Instalatora programu Visual Studio** z **Start** menu.

1. Jeśli po zainstalowaniu programu Visual Studio, wybierz opcję **Modyfikuj** przycisk dla zainstalowanej wersji programu Visual Studio, które chcesz zmodyfikować. W przeciwnym razie wybierz **zainstalować** instalowania programu Visual Studio.

1. Za pomocą **obciążeń** wybraną kartą, przewiń w dół i wybierz **opracowywania aplikacji mobilnych w języku C++** obciążenie w Instalatorze programu Visual Studio. Po wybraniu tego obciążenia wybrane zostaną także inne składniki wymagane do programowania w języku C++. Możesz również innymi obciążeniami i poszczególne składniki do zainstalowania w tym samym czasie. Aby utworzyć kod dla wielu platform, który również jest przeznaczony dla platformy uniwersalnej systemu Windows, wybierz **programowania na platformę uniwersalną Windows** obciążenia.

1. W **szczegółowe informacje dotyczące instalacji** okienku rozwiń **opracowywania aplikacji mobilnych w języku C++** . W **opcjonalnie** sekcji, możesz wybrać dodatkowe wersje zestawu NDK, emulatora systemu Google Android, sprzętu Intel Accelerated menedżera wykonywania i IncrediBuild narzędzie przyspieszanie kompilacji.

1. Domyślnie jeden lub więcej składników Instalatora zestawu SDK systemu Android znajdują się przez obciążenie. Dodatkowe wersje zestawu SDK systemu Android są dostępne. Aby dodać je do instalacji, wybierz **poszczególne składniki** kartę, a następnie przewiń w dół do **zestawów SDK, bibliotek i struktur** sekcji, aby dokonać wyboru.

1. Wybierz **Modyfikuj** lub **zainstalować** przycisk, aby zainstalować **opracowywania aplikacji mobilnych w języku C++** wybrano obciążenia i innych obciążeń i składników opcjonalnych.

   Po ukończeniu instalacji zamknij Instalatora i uruchom ponownie komputer. Niektóre akcje instalacji składników innych firm obowiązują do momentu ponownego uruchomienia komputera.

   > [!IMPORTANT]
   > Należy ponownie uruchomić upewnij się, że wszystko jest poprawnie zainstalowane.

1. Otwórz program Visual Studio.

> [!NOTE]
> Jeśli używasz programu Visual Studio 2015, zobacz [zainstalować Visual C++ for Cross-Platform Mobile Development (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015)

## <a name="install-tools-for-ios"></a>Instalowanie narzędzi dla systemu iOS

Można użyć Visual C++ for Cross-Platform Mobile Development, edytowanie, debugowanie i wdrażanie kodu z systemem iOS w narzędziu iOS Simulator lub na urządzeniu z systemem iOS, ale z powodu ograniczeń licencyjnych, kod muszą zostać skompilowane na zdalnie na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, musisz skonfigurować i skonfiguruj agenta zdalnego na komputerze Mac. Aby uzyskać szczegółowe instrukcje dotyczące instalacji i wymagania wstępne opcje konfiguracji, zobacz [zainstalować i skonfigurować narzędzia umożliwiające tworzenie za pomocą systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jeśli nie tworzysz dla systemu iOS, możesz pominąć ten krok.

## <a name="install-or-update-dependencies-manually"></a>Ręczne instalowanie lub aktualizowanie zależności

Jeśli nie chcesz zainstalować jedną lub więcej zależności innych firm za pomocą Instalatora programu Visual Studio po zainstalowaniu **opracowywania aplikacji mobilnych w języku C++** obciążenia (lub w programie Visual Studio 2015, opcja Visual C++ programowanie aplikacji mobilnych), możesz można zainstalować je później wykonując kroki opisane w [zainstalować narzędzia](#install-the-tools). Instalator programu Visual Studio jest regularnie aktualizowana instalowania najnowszych składników innych firm. Służy on do zainstaluj zaktualizowane zestawy SDK i NDKs. Można także zainstalować lub zaktualizować je niezależnie od programu Visual Studio.

> [!CAUTION]
> Zależności można zainstalować w dowolnej kolejności, z wyjątkiem języka Java. Należy zainstalować i skonfigurować zestaw JDK, przed zainstalowaniem zestawu Android SDK.

Przeczytaj poniższe informacje, a następnie użyj poniższych linków, aby ręcznie zainstalować zależności.

- [Java SE Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Domyślnie Instalator umieszcza narzędzia języka Java na platformie *\Java C:\Program Files (x86)* .

- [Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   Podczas instalacji należy zaktualizować interfejsów API, zgodnie z zaleceniami. Upewnij się, że co najmniej zainstalowano zestaw SDK dla systemu Android 5.0 Lollipop (poziom 21 interfejsu API). Domyślnie Instalator umieszcza zestawu SDK systemu Android w *\Android\android-sdk C:\Program Files (x86)* .

   Możesz uruchomić aplikację Menedżer zestawów SDK, w katalogu zestawu SDK systemu Android ponownie, aby zaktualizować zestaw SDK i zainstaluj opcjonalnych narzędzi oraz dodatkowe poziomy interfejsu API. Aktualizacji może zakończyć się niepowodzeniem do zainstalowania, chyba że używasz **Uruchom jako administrator** do uruchomienia aplikacji Menedżer zestawów SDK. Jeśli masz problemy z tworzenia aplikacji systemu Android, sprawdź Menedżer zestawów SDK, aktualizacje usługi zainstalowanych zestawów SDK.

   Aby korzystać z niektórych z emulatorami systemu Android, które pochodzą z zestawu SDK systemu Android, należy zainstalować opcjonalne sterowniki Intel HAXM. Może być konieczne usuwania funkcji Hyper-V Windows do pomyślnego zainstalowania sterowników Intel HAXM. Należy przywrócić emulatory Windows Phone i Microsoft Visual Studio Emulator for Android używać funkcji Hyper-V. Aby uzyskać więcej informacji, zobacz [przyspieszanie sprzętowe emulatora systemu Android](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   Domyślnie Instalator umieszcza zestawu Android NDK w *C:\ProgramData\Microsoft\AndroidNDK*. Można pobrać i zainstalować zestawu Android NDK ponownie, aby zaktualizować instalację zestawu NDK.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Domyślnie Instalator umieszcza Apache Ant w *C:\Program Files (x86) \Microsoft Visual Studio 14.0\Apps*.

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio Emulator for Android jest emulator opcjonalne przydatne do testowania i debugowania kodu. Po wydaniu programu Visual Studio Emulator dla systemu Android firmy Google zaktualizowała swój własny emulator, aby używał przyspieszania sprzętowego za pośrednictwem Intel użytkownika aparatu HAXM. Zaleca się, że używasz jej jako przyspieszonej emulatora firmy Google, gdy to możliwe, ponieważ oferuje on dostęp do najnowszych obrazów systemu operacyjnego Android i sklepu Google Play services.

W większości przypadków Visual Studio może wykrywać konfiguracje dla oprogramowania innych firm, zainstalowanych i utrzymuje ścieżek instalacji w zmiennych środowiskowych wewnętrznego. Można zastąpić domyślne ścieżki tych narzędzi programowanie dla wielu platform w środowisku IDE programu Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Można ustawić ścieżki do narzędzi innych firm

1. Na pasku menu programu Visual Studio wybierz **narzędzia** > **opcje**.

1. W **opcje** okno dialogowe, wybierz opcję **Międzyplatformowe** > **C++**  > **Android**.

   ![Opcje narzędzia dla systemu android do ścieżki](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Aby zmienić ścieżkę używaną przez narzędzie, zaznacz pole wyboru obok ścieżkę, a następnie Edytuj ścieżkę folderu, w polu tekstowym. Umożliwia także przycisk przeglądania ( **...** ) aby otworzyć **wybierz lokalizację** okna dialogowego, aby wybrać folder.

1. Wybierz **OK** można zapisać narzędzie niestandardowe lokalizacje folderów.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i Konfigurowanie narzędzia umożliwiające tworzenie za pomocą systemu iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ cross-platform mobile](https://go.microsoft.com/fwlink/p/?LinkId=536383)
