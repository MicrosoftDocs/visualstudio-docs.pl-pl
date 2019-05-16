---
title: Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele Platform | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1aa81017f1a3d73e4ade1556ab141878e8a773f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698463"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wizualne C++ for Cross-Platform Mobile Development] (http://go.microsoft.com/fwlink/p/?LinkId=536383) jest składnikiem do zainstalowania programu Visual Studio 2015. Zawiera szablony programu Visual Studio dla wielu platform i pozwala na zainstalowanie narzędzi dla wielu platform i zestawy SDK na szybkie rozpoczęcie pracy, bez konieczności zlokalizować, pobrać i skonfigurować je samodzielnie. Te narzędzia w programie Visual Studio umożliwia łatwe tworzenie, edytowanie, debugowanie i testowanie projektów dla wielu platform. W tym temacie opisano sposób instalowania narzędzi i oprogramowania innych firm, wymagane do rozwoju aplikacji dla wielu platform przy użyciu programu Visual Studio. Aby zapoznać się z omówieniem składnika, zobacz [Visual C++ Cross-Platform Mobile](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Wymagania](#Requirements)   
 [Pobierz narzędzia](#GetTheTools)   
 [Instalowanie narzędzi](#InstallTheTools)   
 [Instalowanie narzędzi dla systemu iOS](#InstallForiOS)   
 [Ręczne instalowanie lub aktualizowanie zależności](#ThirdParty)  
  
## <a name="Requirements"></a> Wymagania  
  
- Aby uzyskać wymagania dotyczące instalacji, zobacz [wymagania systemowe programu Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  > Jeśli używasz, Windows 7 lub Windows Server 2008 R2, możesz tworzyć kod dla aplikacji klasycznych Windows i aplikacji Android Native Activity i bibliotek, aplikacji i bibliotek kodu dla systemu iOS, ale nie aplikacje Windows Store lub Universal Windows.  
  
  Aby tworzyć aplikacje dla konkretnych platform sprzętowych, istnieją pewne dodatkowe wymagania:  
  
- Emulatory Windows Phone i Microsoft Visual Studio Emulator for Android wymagają komputera, która może działać na funkcji Hyper-V. Musi być włączona funkcja Hyper-V w Windows, zanim można instalować i uruchamiać emulatorów. Aby uzyskać więcej informacji, zobacz emulatora usługi [wymagania systemowe](https://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf).  
  
- X86 emulatorów systemu Android, które pochodzą z zestawu SDK systemu Android działają najlepiej na komputerach, które można uruchomić sterownika Intel HAXM. Ten sterownik wymaga procesora Intel x64 z obsługą Bit wykonania wyłączyć i VT-x. Aby uzyskać więcej informacji, zobacz [instrukcje dotyczące instalacji dla Intel® sprzętu Accelerated menedżera wykonywania — Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
- Tworzenie kodu dla systemu iOS wymaga identyfikatora Apple ID, konta dewelopera programu z systemem iOS i komputera Mac, która może działać [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) lub później na OS X mavericks z przeglądarką lub nowszy. Instalacja prosta kroki opisane w artykule [instalowania narzędzi dla systemu iOS](#InstallForiOS).  
  
## <a name="GetTheTools"></a> Pobierz narzędzia  
 W języku Visual C++ Cross-Platform Mobile Development jest składnika do zainstalowania, dostępna w wersjach programu Visual Studio Community, Professional i Enterprise. Aby uzyskać program Visual Studio, przejdź do [pobieranie Visual Studio 2015](http://go.microsoft.com/fwlink/p/?linkid=517106) strony i Pobierz program Visual Studio 2015 z aktualizacją Update 2 lub nowszym.  
  
## <a name="InstallTheTools"></a> Instalowanie narzędzi  
 Instalator programu Visual Studio 2015 obejmuje możliwość zainstalowania języka Visual C++ for Cross-Platform Mobile Development. Spowoduje to zainstalowanie wymaganych narzędzi języka C++, szablony i składniki dla programu Visual Studio, GCC i Clang zestawy narzędzi, wymagane dla systemu Android kompilacji debugowania i składników do komunikowania się z komputerem Mac do tworzenia aplikacji dla systemu iOS. Instaluje także wszystkich narzędzi innych firm i software development kit, które są wymagane do obsługi systemów iOS i rozwoju aplikacji dla systemu Android. Większość tych narzędzi innych firm to oprogramowanie typu open-source wymagane do obsługi platformy systemu Android.  
  
- Dla systemu android natywnych Development Kit (zestawu NDK) jest wymagany do kompilowania kodu C++, który jest przeznaczony dla platformy systemu Android.  
  
- Zestaw SDK systemu android, Apache Ant i Java SE Development Kit są wymagane dla procesu kompilacji dla systemu Android.  
  
- Microsoft Visual Studio Emulator for Android jest opcjonalne przydatne do testowania i debugowania kodu, emulator o wysokiej wydajności.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Aby zainstalować Visual C++ Cross-Platform Mobile Development i narzędziami innych firm  
  
1. Uruchom Instalatora programu Visual Studio 2015, który został pobrany następujące łącze w [Pobierz narzędzia](#GetTheTools). Aby zainstalować składniki opcjonalne, wybierz **niestandardowe** jako typ instalacji. Wybierz **dalej** zaznacz opcjonalne składniki do zainstalowania.  
  
2. W polu Wybierz funkcje, rozwiń węzeł **Cross Platform Mobile Development** i sprawdź **programowanie aplikacji mobilnych Visual C++**.  
  
     ![Wybierz pozycję Visual C&#43; &#43; opracowywania aplikacji mobilnych](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Domyślnie po wybraniu **programowanie aplikacji mobilnych Visual C++**, **języków programowania** opcja jest ustawiona na instalowanie **Visual C++** i **popularnych narzędzi a Software Development Kit** opcje są ustawione na instalowanie wymaganych składników innych firm. Możesz wybrać dodatkowe składniki, gdy ich potrzebujesz. Domyślnie **programu Microsoft Visual Studio Emulator for Android** zostanie również wybrane. Składniki, które są już zainstalowane są wyświetlane jako nieaktywne na liście.  
  
     Tworzenie aplikacji Windows Universal apps i udostępnianie kodu między nimi i projektów dla systemów Android i iOS, w **wybierz funkcje**, rozwiń węzeł **Windows i aplikacji sieci Web** i sprawdź **uniwersalnej aplikacji Windows Narzędzia programistyczne**. Jeśli nie zamierzasz tworzyć aplikacje Windows Universal, możesz pominąć tę opcję.  
  
     Wybierz **dalej** aby kontynuować.  
  
3. Składników innych firm ma postanowień licencyjnych. Postanowienia licencyjne można wyświetlić, wybierając **postanowienia licencyjne** łącze obok każdego składnika. Wybierz **zainstalować** Dodaj składniki do zainstalowania programu Visual Studio i Visual C++ for Cross-Platform Mobile Development.  
  
4. Po ukończeniu instalacji zamknij Instalatora i uruchom ponownie komputer. Niektóre akcje instalacji składników innych firm obowiązują do momentu ponownego uruchomienia komputera.  
  
    > [!IMPORTANT]
    > Należy ponownie uruchomić upewnij się, że wszystko jest poprawnie zainstalowane.  
  
     W przypadku niepowodzenia instalacji programu Microsoft Visual Studio Emulator for składnika zestawu Android komputera nie może mieć włączone funkcji Hyper-V. Użyj **Windows Włącz lub wyłącz funkcje** aplikacji Panelu sterowania, aby umożliwić funkcji Hyper-V, a następnie ponownie uruchom Instalatora programu Visual Studio.  
  
    > [!NOTE]
    > Jeśli komputer lub używanej wersji systemu Windows nie obsługuje funkcji Hyper-V, nie można użyć programu Microsoft Visual Studio Emulator dla składnika zestawu Android. Strona główna wersja systemu Windows nie obejmuje obsługę funkcji Hyper-V.  
  
5. Otwórz program Visual Studio. Jeśli to przy pierwszym uruchomieniu programu Visual Studio, potrwać trochę czasu, aby skonfigurować i zaloguj się. Po wykonaniu tych czynności w Visual Studio **narzędzia** menu, wybierz opcję **rozszerzenia i aktualizacje**, **aktualizacje**. W przypadku programu Visual Studio aktualizacje dostępne dla języka Visual C++ for Cross-Platform Mobile Development lub programu Microsoft Visual Studio Emulator dla systemu Android, należy je zainstalować.  
  
## <a name="InstallForiOS"></a> Instalowanie narzędzi dla systemu iOS  
 Można użyć Visual C++ for Cross-Platform Mobile Development, edytowanie, debugowanie i wdrażanie kodu z systemem iOS w narzędziu iOS Simulator lub na urządzeniu z systemem iOS, ale z powodu ograniczeń licencyjnych, kod muszą zostać skompilowane na zdalnie na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, musisz skonfigurować i skonfiguruj agenta zdalnego na komputerze Mac. Aby uzyskać szczegółowe instrukcje dotyczące instalacji i wymagania wstępne opcje konfiguracji, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jeśli nie tworzysz dla systemu iOS, możesz pominąć ten krok.  
  
## <a name="ThirdParty"></a> Ręczne instalowanie lub aktualizowanie zależności  
 Jeśli nie chcesz zainstalować jedną lub więcej zależności innych firm za pomocą Instalatora programu Visual Studio, po zainstalowaniu opcji programowania aplikacji mobilnych Visual C++, można zainstalować je później wykonując kroki opisane w [zainstalować narzędzia](#InstallTheTools). Można także zainstalować lub zaktualizować je niezależnie od programu Visual Studio.  
  
> [!CAUTION]
> Zależności można zainstalować w dowolnej kolejności, z wyjątkiem języka Java. Należy zainstalować i skonfigurować zestaw JDK, przed zainstalowaniem zestawu Android SDK.  
  
 Przeczytaj poniższe informacje, a następnie użyj poniższych linków, aby ręcznie zainstalować zależności.  
  
- [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Domyślnie Instalator narzędzia Java stosuje w przypadku \Java C:\Program Files (x86).  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Podczas instalacji należy zaktualizować interfejsów API, zgodnie z zaleceniami. Upewnij się, że co najmniej zainstalowano zestaw SDK dla systemu Android 5.0 Lollipop (poziom 21 interfejsu API). Domyślnie Instalator zestawu Android SDK stosuje w przypadku C:\Program Files (x86) \Android\android-sdk.  
  
   Możesz uruchomić aplikację Menedżer zestawów SDK, w katalogu zestawu SDK systemu Android ponownie, aby zaktualizować zestaw SDK i zainstaluj opcjonalnych narzędzi oraz dodatkowe poziomy interfejsu API. Aktualizacji może zakończyć się niepowodzeniem do zainstalowania, chyba że używasz **Uruchom jako administrator** do uruchomienia aplikacji Menedżer zestawów SDK. Jeśli masz problemy z tworzenia aplikacji systemu Android, sprawdź Menedżer zestawów SDK, aktualizacje usługi zainstalowanych zestawów SDK.  
  
   Aby korzystać z niektórych z emulatorami systemu Android, które pochodzą z zestawu SDK systemu Android, należy zainstalować opcjonalne sterowniki Intel HAXM. Może być konieczne usuwania funkcji Hyper-V Windows do pomyślnego zainstalowania sterowników Intel HAXM. Należy przywrócić emulatory Windows Phone i Microsoft Visual Studio Emulator for Android używać funkcji Hyper-V.  
  
- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Domyślnie Instalator umieszcza zestawu Android NDK w C:\ProgramData\Microsoft\AndroidNDK. Można pobrać i zainstalować zestawu Android NDK ponownie, aby zaktualizować instalację zestawu NDK.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Domyślnie Instalator umieszcza Apache Ant w C:\Program Files (x86) \Microsoft 14.0\Apps programu Visual Studio.  
  
- [Microsoft Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Można zainstalować i zaktualizować programu Microsoft Visual Studio Emulator for Android z galerii Visual Studio.  
  
  W większości przypadków Visual Studio może wykrywać konfiguracje dla oprogramowania innych firm, zainstalowanych i utrzymuje ścieżek instalacji w zmiennych środowiskowych wewnętrznego. Można zastąpić domyślne ścieżki tych narzędzi programowanie dla wielu platform w środowisku IDE programu Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Można ustawić ścieżki do narzędzi innych firm  
  
1. Na pasku menu programu Visual Studio wybierz **narzędzia**, **opcje**.  
  
2. W **opcje** okna dialogowego rozwiń **Międzyplatformowe**, **C++** i wybierz **Android**.  
  
     ![Opcje narzędzia dla systemu android do ścieżki](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3. Aby zmienić ścieżkę używaną przez narzędzie, zaznacz pole wyboru obok ścieżkę, a następnie Edytuj ścieżkę folderu, w polu tekstowym. Umożliwia także przycisk przeglądania (**...** ) aby otworzyć **wybierz lokalizację** okna dialogowego, aby wybrać folder.  
  
4. Wybierz **OK** można zapisać narzędzie niestandardowe lokalizacje folderów.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ Cross-Platform Mobile](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
