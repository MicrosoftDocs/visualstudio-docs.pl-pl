---
title: Zainstaluj wizualizację C++ dla wieloplatformowego opracowywania aplikacji mobilnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 8046b261021a1147dbf0356c6854968b3d23a1df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299794"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wizualizacja C++ dla wieloplatformowego opracowywania aplikacji mobilnych (https://go.microsoft.com/fwlink/p/?LinkId=536383) jest składnikiem instalowalnym programu Visual Studio 2015. Obejmuje to międzyplatformowe szablony programu Visual Studio, a także instaluje narzędzia i zestawy SDK dla wielu platform, aby szybko rozpocząć pracę bez konieczności lokalizowania, pobierania i konfigurowania. Za pomocą tych narzędzi w programie Visual Studio można łatwo tworzyć, edytować, debugować i testować projekty Międzyplatformowe. W tym temacie opisano sposób instalowania narzędzi i oprogramowania innych firm wymagane do tworzenia aplikacji dla wielu platform przy użyciu programu Visual Studio. Aby zapoznać się z omówieniem składnika, zobacz [ C++ Międzyplatformowe aplikacje mobilne](https://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Wymagania](#Requirements)   
 [Pobierz  narzędzi](#GetTheTools)  
 [Zainstaluj  narzędzi](#InstallTheTools)  
 [Zainstaluj narzędzia dla systemu iOS](#InstallForiOS)   
 [Ręczne instalowanie lub aktualizowanie zależności](#ThirdParty)  
  
## <a name="Requirements"></a> Wymagania  
  
- Wymagania dotyczące instalacji znajdują się w temacie [wymagania systemowe programu Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  > W przypadku korzystania z systemu Windows 7 lub Windows Server 2008 R2 można opracowywać kod dla klasycznych aplikacji systemu Windows, aplikacji i bibliotek działań natywnych platformy Android oraz aplikacji i bibliotek kodu dla systemu iOS, ale nie sklepu Windows ani aplikacji uniwersalnych systemu Windows.  
  
  Aby tworzyć aplikacje dla określonych platform urządzeń, istnieją pewne dodatkowe wymagania:  
  
- Windows Phone emulatory i Microsoft Visual Studio Emulator for Android wymagają komputera z uruchomioną funkcją Hyper-V. Funkcja Hyper-V w systemie Windows musi być włączona, aby można było instalować i uruchamiać emulatory. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](https://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)emulatora.  
  
- Emulatory x86 systemu Android, które są dostarczane z Android SDK działają najlepiej na komputerach, na których można uruchomić sterownik Intel HAXM. Ten sterownik wymaga procesora Intel x64 z emulatorem VT-x i wykonywaniem obsługi bitów wyłączania. Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące instalacji dla technologii Intel® Hardware Accelerated Execution Manager — Microsoft Windows](https://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
- Kompilowanie kodu dla systemu iOS wymaga identyfikatora Apple ID, konta programu dla deweloperów systemu iOS i komputera Mac, na którym można uruchomić [Xcode 6](https://go.microsoft.com/fwlink/p/?LinkId=536387) lub nowszą wersję systemu operacyjnego X Mavericks lub nowszego. Aby zapoznać się z prostymi krokami instalacji, zobacz [Instalowanie narzędzi dla systemu iOS](#InstallForiOS).  
  
## <a name="GetTheTools"></a>Pobierz narzędzia  
 Wizualizacja C++ dla wieloplatformowego opracowywania aplikacji mobilnych to składnik, który można zainstalować w programie Visual Studio Community, wersje Professional i Enterprise. Aby uzyskać program Visual Studio, przejdź do strony [plików do pobrania programu Visual studio 2015](https://go.microsoft.com/fwlink/p/?linkid=517106) i Pobierz program visual Studio 2015 z aktualizacją Update 2 lub nowszą.  
  
## <a name="InstallTheTools"></a>Instalowanie narzędzi  
 Instalator programu Visual Studio 2015 zawiera opcję instalacji wizualizacji C++ na potrzeby tworzenia aplikacji mobilnych na wiele platform. Spowoduje to zainstalowanie wymaganych C++ narzędzi języka, szablonów i składników dla programu Visual Studio, zestawów narzędzi w zatoce i Clang, które są potrzebne do kompilowania i debugowania systemu Android, oraz składniki do komunikowania się z komputerem Mac na potrzeby tworzenia aplikacji dla systemu iOS. Instaluje także wszystkie narzędzia innych firm i zestawy SDK, które są wymagane do obsługi projektowania aplikacji dla systemów iOS i Android. Większość tych narzędzi innych firm to oprogramowanie typu open source wymagane do obsługi platformy Android.  
  
- Zestaw Android Native Development Kit (NDK) jest wymagany do C++ kompilowania kodu przeznaczonego dla platformy Android.  
  
- W procesie kompilacji systemu Android są wymagane Android SDK, Apache Ant i Java SE Development Kit.  
  
- Microsoft Visual Studio Emulator for Android to opcjonalny emulator o wysokiej wydajności przydatny do testowania i debugowania kodu.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Aby zainstalować wizualizację C++ dla wieloplatformowego opracowywania aplikacji mobilnych i narzędzi innych firm  
  
1. Uruchom Instalatora programu Visual Studio 2015, który został pobrany po pobraniu linku w [narzędziu Pobierz narzędzia](#GetTheTools). Aby zainstalować składniki opcjonalne, wybierz opcję **niestandardowy** jako typ instalacji. Wybierz pozycję **dalej** , aby wybrać opcjonalne składniki do zainstalowania.  
  
2. W obszarze Wybieranie funkcji rozwiń pozycję **Programowanie aplikacji mobilnych dla wielu platform** i sprawdź  **C++ Visual Mobile Development**.  
  
     ![Wybierz pozycję Programowanie&#43; &#43; aplikacji mobilnych w języku Visual C](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Domyślnie po wybraniu opcji  **C++ programowanie wizualizacji mobilnej**opcja **Języki programowania** jest ustawiana na wartość **Zainstaluj C++wizualizację** , a w obszarze **popularne narzędzia i zestawy** SDK są ustawiane, aby instalować wymagane składniki innych firm. Jeśli są potrzebne, możesz wybrać dodatkowe składniki. Domyślnie jest również zaznaczona **Microsoft Visual Studio Emulator for Android** . Składniki, które są już zainstalowane, są nieaktywne na liście.  
  
     Aby skompilować aplikacje uniwersalne systemu Windows i udostępnić kod między nimi a projektami z systemami Android i iOS, w obszarze **Wybierz funkcje**rozwiń pozycję **Programowanie dla systemu Windows i sieci Web** i sprawdź **Narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows**. Jeśli nie planujesz kompilowania aplikacji uniwersalnych systemu Windows, możesz pominąć tę opcję.  
  
     Wybierz pozycję **dalej** , aby kontynuować.  
  
3. Składniki innych firm mają własne postanowienia licencyjne. Postanowień licencyjnych można wyświetlić, wybierając link **postanowienia licencyjne** obok każdego składnika. Wybierz pozycję **Zainstaluj** , aby dodać składniki i zainstalować program Visual Studio C++ i wizualizację dla wieloplatformowego opracowywania aplikacji mobilnych.  
  
4. Po zakończeniu instalacji zamknij Instalatora, a następnie uruchom ponownie komputer. Niektóre akcje Instalatora dla składników innych firm nie zaczynają obowiązywać do momentu ponownego uruchomienia komputera.  
  
    > [!IMPORTANT]
    > Musisz ponownie uruchomić system, aby upewnić się, że wszystko jest poprawnie zainstalowane.  
  
     Jeśli zainstalowanie składnika Microsoft Visual Studio Emulator for Android nie powiodło się, komputer może nie mieć włączonej funkcji Hyper-V. Za pomocą **opcji Włącz lub wyłącz funkcje systemu Windows w** panelu sterowania Włącz funkcję Hyper-V, a następnie ponownie uruchom Instalatora programu Visual Studio.  
  
    > [!NOTE]
    > Jeśli komputer lub Twoja wersja systemu Windows nie obsługuje funkcji Hyper-V, nie można użyć składnika Microsoft Visual Studio Emulator for Android. Wersja Home Edition systemu Windows nie obejmuje obsługi funkcji Hyper-V.  
  
5. Otwórz program Visual Studio. W przypadku korzystania z programu Visual Studio po raz pierwszy może upłynąć trochę czasu, aby skonfigurować i zalogować się. Gdy program Visual Studio jest gotowy, w menu **Narzędzia** wybierz opcję **rozszerzenia i aktualizacje**, **aktualizacje**. Jeśli istnieją aktualizacje programu Visual Studio dla wizualizacji C++ na potrzeby programowania aplikacji mobilnych dla wielu Platform lub Microsoft Visual Studio Emulator for Android, zainstaluj je.  
  
## <a name="InstallForiOS"></a>Zainstaluj narzędzia dla systemu iOS  
 Możesz użyć wizualizacji C++ do wieloplatformowego opracowywania aplikacji mobilnych, aby edytować, debugować i wdrażać kod systemu iOS w symulatorze systemu iOS lub na urządzeniu z systemem iOS, ale z powodu ograniczeń licencjonowania kod musi być skompilowany zdalnie na komputerze Mac. Aby kompilować i uruchamiać aplikacje dla systemu iOS przy użyciu programu Visual Studio, należy skonfigurować i skonfigurować agenta zdalnego na komputerze Mac. Szczegółowe instrukcje dotyczące instalacji, wymagania wstępne i opcje konfiguracji znajdują się w temacie [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jeśli nie tworzysz dla systemu iOS, możesz pominąć ten krok.  
  
## <a name="ThirdParty"></a>Ręczne instalowanie lub aktualizowanie zależności  
 Jeśli użytkownik zdecyduje się nie instalować co najmniej jednej zależności innej firmy przy użyciu Instalatora programu Visual Studio podczas instalacji opcji tworzenia C++ aplikacji mobilnej dla urządzeń przenośnych, można zainstalować je później, wykonując kroki opisane w temacie [Instalowanie narzędzi](#InstallTheTools). Można także zainstalować lub zaktualizować je niezależnie od programu Visual Studio.  
  
> [!CAUTION]
> Zależności można zainstalować w dowolnej kolejności, z wyjątkiem języka Java. Przed zainstalowaniem Android SDK należy zainstalować i skonfigurować JDK.  
  
 Przeczytaj poniższe informacje i Użyj tych linków, aby ręcznie zainstalować zależności.  
  
- [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Domyślnie Instalator umieszcza narzędzia języka Java w folderze C:\Program Files (x86) \Java.  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Podczas instalacji zaktualizuj interfejsy API zgodnie z zaleceniami. Upewnij się, że jest zainstalowany co najmniej zestaw SDK dla systemu Android 5,0 (poziom interfejsu API 21). Domyślnie Instalator umieszcza Android SDK w folderze C:\Program Files (x86) \Android\android-SDK.  
  
   Możesz ponownie uruchomić aplikację Menedżer zestawów SDK w katalogu Android SDK, aby zaktualizować zestaw SDK i zainstalować opcjonalne narzędzia i dodatkowe poziomy interfejsu API. Instalacja aktualizacji może się nie powieść, jeśli nie zostanie użyta funkcja **Uruchom jako administrator** do uruchomienia aplikacji Menedżera zestawów SDK. Jeśli masz problemy z tworzeniem aplikacji dla systemu Android, zapoznaj się z menedżerem zestawu SDK, aby uzyskać aktualizacje zainstalowanych zestawów SDK.  
  
   Aby korzystać z niektórych emulatorów systemu Android, które są dostarczane z Android SDK, należy zainstalować opcjonalne sterowniki Intel HAXM. Może być konieczne usunięcie funkcji Hyper-V z systemu Windows w celu pomyślnego zainstalowania sterowników Intel HAXM. Funkcja Hyper-V musi zostać przywrócona, aby można było używać emulatorów Windows Phone i Microsoft Visual Studio Emulator for Android.  
  
- [Zestaw Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Domyślnie Instalator umieszcza zestaw Android NDK w C:\ProgramData\Microsoft\AndroidNDK. Możesz ponownie pobrać i zainstalować zestaw Android NDK, aby zaktualizować instalację NDK.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Domyślnie Instalator umieszcza Apache Ant w folderze C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ Apps.  
  
- [Microsoft Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Możesz zainstalować i zaktualizować Microsoft Visual Studio Emulator for Android z galerii programu Visual Studio.  
  
  W większości przypadków program Visual Studio może wykryć konfiguracje zainstalowanego oprogramowania innej firmy i zachować ścieżki instalacyjne w wewnętrznych zmiennych środowiskowych. Można zastąpić domyślne ścieżki tych narzędzi programistycznych dla wielu platform w środowisku IDE programu Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Aby ustawić ścieżki dla narzędzi innych firm  
  
1. Na pasku menu programu Visual Studio wybierz pozycję **Narzędzia**, **Opcje**.  
  
2. W oknie dialogowym **Opcje** rozwiń pozycję **Międzyplatformowe**, **C++** a następnie wybierz pozycję **Android**.  
  
     ![Opcje ścieżek narzędzi systemu Android](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3. Aby zmienić ścieżkę używaną przez narzędzie, zaznacz pole wyboru obok ścieżki i Edytuj ścieżkę folderu w polu tekstowym. Możesz również użyć przycisku przeglądania ( **...** ), aby otworzyć okno dialogowe **Wybieranie lokalizacji** w celu wybrania folderu.  
  
4. Wybierz **przycisk OK** , aby zapisać lokalizacje folderów narzędzi niestandardowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu  systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
 [Wizualizacja C++ międzyplatformowa dla urządzeń przenośnych](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
