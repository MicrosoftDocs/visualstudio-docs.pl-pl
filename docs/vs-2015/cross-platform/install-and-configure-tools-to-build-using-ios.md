---
title: Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 695cbeaba5a108c61b5e81078a9651c0df9237f5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299813"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć wizualizacji C++ do wieloplatformowego opracowywania aplikacji mobilnych, aby edytować, debugować i wdrażać kod systemu iOS w symulatorze systemu iOS lub na urządzeniu z systemem iOS, ale z powodu ograniczeń licencjonowania kod musi być zbudowany i uruchamiany zdalnie na komputerze Mac. Aby kompilować i uruchamiać aplikacje dla systemu iOS przy użyciu programu Visual Studio, należy skonfigurować i skonfigurować agenta zdalnego, [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)na komputerze Mac. Agent zdalny obsługuje żądania kompilacji z programu Visual Studio i uruchamia aplikację na urządzeniu z systemem iOS podłączonym do komputera Mac lub w symulatorze systemu iOS na komputerze Mac.  
  
> [!NOTE]
> Aby uzyskać informacje na temat korzystania z usług Mac hostowanych w chmurze zamiast komputerów Mac, zobacz [Kompilowanie i symulowanie systemu iOS w chmurze](https://taco.visualstudio.com/docs/build_ios_cloud/). Instrukcje służą do kompilowania przy użyciu Visual Studio Tools Apache Cordova. Aby skorzystać z instrukcji do kompilowania aplikacji C++ mobilnych na wiele platform, należy zastąpić vcremote dla programu vs-MDA-Remote.  
  
 Po zainstalowaniu narzędzi do kompilowania przy użyciu systemu iOS zapoznaj się z tym tematem, aby szybko skonfigurować i zaktualizować agenta zdalnego dla tworzenia aplikacji dla systemu iOS w programie Visual Studio i na komputerze Mac.  
  
 [Wymagania wstępne](#Prerequisites)  
  
 [Zainstaluj agenta zdalnego dla systemu iOS](#Install)  
  
 [Uruchom agenta zdalnego](#Start)  
  
 [Konfigurowanie agenta zdalnego w programie Visual Studio](#ConfigureVS)  
  
 [Generuj nowy zabezpieczający kod PIN](#GeneratePIN)  
  
 [Wygeneruj nowy certyfikat serwera](#GenerateCert)  
  
 [Konfigurowanie zdalnego agenta na komputerze Mac](#ConfigureMac)  
  
## <a name="Prerequisites"></a> Wymagania wstępne  
 Aby zainstalować i użyć agenta zdalnego do opracowania kodu dla systemu iOS, należy najpierw spełnić te wymagania wstępne:  
  
- Komputer Mac z systemem OS X Mavericks lub nowszym  
  
- [Identyfikator Apple ID](https://appleid.apple.com/)  
  
- Aktywne konto [programu dla deweloperów systemu iOS](https://developer.apple.com/programs/ios/) z firmą Apple  
  
- [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6 można pobrać ze sklepu z aplikacjami.  
  
- Narzędzia wiersza polecenia Xcode  
  
     Aby zainstalować narzędzia wiersza polecenia Xcode, Otwórz aplikację terminala na komputerze Mac i wprowadź następujące polecenie:  
  
     `xcode-select --install`  
  
- Tożsamość podpisywania systemu iOS skonfigurowana w Xcode  
  
     Aby uzyskać szczegółowe informacje na temat uzyskiwania tożsamości podpisywania systemu iOS, zobacz temat [Obsługa tożsamości podpisywania i certyfikatów](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) w bibliotece deweloperów systemu iOS. Aby wyświetlić lub ustawić tożsamość podpisywania w programie Xcode, otwórz menu **Xcode** i wybierz polecenie **Preferences (Preferencje**). Wybierz pozycję **konta** i wybierz swój identyfikator Apple ID, a następnie wybierz przycisk **Wyświetl szczegóły** .  
  
- Jeśli używasz urządzenia z systemem iOS do tworzenia aplikacji, profil aprowizacji skonfigurowany w Xcode dla urządzenia  
  
     Aby uzyskać szczegółowe informacje na temat tworzenia profilów aprowizacji, zobacz [Tworzenie profilów aprowizacji za pomocą centrum elementów członkowskich](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) w bibliotece deweloperów systemu iOS.  
  
- [Node.js](https://nodejs.org/en/)  
  
- Zaktualizowana wersja programu npm  
  
     Wersja npm, która jest dostarczana z Node. js, może być niewystarczająca do zainstalowania vcremote. Aby zaktualizować npm, Otwórz aplikację terminala na komputerze Mac i wprowadź następujące polecenie:  
  
     `sudo npm install -g npm@latest`  
  
## <a name="Install"></a>Zainstaluj agenta zdalnego dla systemu iOS  
 W przypadku instalowania wizualizacji C++ dla wieloplatformowego opracowywania aplikacji mobilnych program Visual Studio może komunikować się z usługą [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988), zdalnym agentem uruchomionym na komputerze Mac w celu transferu plików, kompilowania i uruchamiania aplikacji dla systemu iOS oraz wysyłania poleceń debugowania.  
  
 Przed zainstalowaniem agenta zdalnego upewnij się, że spełniono [wymagania wstępne](#Prerequisites) i zainstalowano [wizualizację C++ na potrzeby opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
### <a name="DownloadInstall"></a>Aby pobrać i zainstalować agenta zdalnego  
  
- Z poziomu aplikacji terminalowej na komputerze Mac wpisz:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Przełącznik instalacji globalnej ( **-g**) jest zalecany, ale nie jest wymagany.  
  
   Podczas instalacji program vcremote jest zainstalowany, a na komputerze Mac jest aktywowany Tryb dewelopera. Instalowane są również [oprogramowania Homebrew](https://brew.sh/) i dwa pakiety npm, vcremote-lib i vcremote.  
  
  > [!NOTE]
  > Aby zainstalować oprogramowania homebrew, musisz mieć dostęp do programu sudo (Administrator). Jeśli musisz zainstalować vcremote bez sudo, możesz zainstalować oprogramowania Homebrew ręcznie w lokalizacji usr/local i dodać jej folder bin do ścieżki. Aby uzyskać więcej informacji, zapoznaj się z [dokumentacją oprogramowania Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Aby ręcznie włączyć tryb dewelopera, wprowadź następujące polecenie w aplikacji terminalowej: `DevToolsSecurity –enable`  
  
  W przypadku aktualizacji do nowej wersji programu Visual Studio należy również zaktualizować ją do bieżącej wersji agenta zdalnego. Aby zaktualizować agenta zdalnego, powtórz kroki, aby pobrać i zainstalować agenta zdalnego.  
  
## <a name="Start"></a>Uruchom agenta zdalnego  
 Aby program Visual Studio mógł skompilować i uruchomić kod systemu iOS, Agent zdalny musi być uruchomiony. Program Visual Studio musi być sparowany z agentem zdalnym, aby mógł się komunikować. Domyślnie zdalny Agent jest uruchamiany w trybie połączenia zabezpieczonego, który wymaga, aby numer PIN został sparowany z programem Visual Studio.  
  
### <a name="RemoteAgentStartServer"></a>Aby uruchomić agenta zdalnego  
  
- Z poziomu aplikacji terminalowej na komputerze Mac wpisz:  
  
   `vcremote`  
  
   Spowoduje to uruchomienie zdalnego agenta z domyślnym katalogiem kompilacji ~/vcremote. Aby uzyskać dodatkowe opcje konfiguracji, zobacz [Konfigurowanie zdalnego agenta na komputerze Mac](#ConfigureMac).  
  
  Przy pierwszym uruchomieniu agenta i dowolnym momencie tworzenia nowego certyfikatu klienta zostaną podane informacje wymagane do skonfigurowania agenta w programie Visual Studio, w tym nazwy hosta, portu i numeru PIN.  
  
  ![Użyj vcremote do wygenerowania bezpiecznego numeru PIN](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Jeśli zamierzasz skonfigurować agenta zdalnego w programie Visual Studio przy użyciu nazwy hosta, Wyślij polecenie ping do komputera Mac z systemu Windows przy użyciu nazwy hosta, aby sprawdzić, czy jest osiągalny. W przeciwnym razie może być konieczne użycie tego adresu IP.  
  
  Wygenerowany kod PIN jest używany do jednorazowego użycia i jest prawidłowy tylko przez ograniczony czas. Jeśli program Visual Studio nie zostanie sparowany z agentem zdalnym przed upływem czasu, konieczne będzie wygenerowanie nowego numeru PIN. Aby uzyskać więcej informacji, zobacz [generowanie nowego numeru PIN zabezpieczeń](#GeneratePIN).  
  
  Agenta zdalnego można używać w trybie niezabezpieczonym. W trybie niezabezpieczonym Agent zdalny może być sparowany z Visual Studio bez numeru PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Aby wyłączyć tryb bezpiecznego połączenia  
  
- Aby wyłączyć tryb bezpiecznego połączenia w vcremote, wprowadź to polecenie w aplikacji terminalowej na komputerze Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Aby włączyć tryb połączenia zabezpieczonego  
  
- Aby włączyć tryb połączenia zabezpieczonego, wprowadź następujące polecenie:  
  
   `vcremote --secure true`  
  
  Po uruchomieniu zdalnego agenta można go użyć z programu Visual Studio, dopóki nie zostanie zatrzymany.  
  
#### <a name="to-stop-the-remote-agent"></a>Aby zatrzymać agenta zdalnego  
  
- W oknie terminalu vcremote jest uruchomiona w systemie, wprowadź `Control+C`.  
  
## <a name="ConfigureVS"></a>Konfigurowanie agenta zdalnego w programie Visual Studio  
 Aby połączyć się z agentem zdalnym z poziomu programu Visual Studio, należy określić konfigurację zdalną w opcjach programu Visual Studio.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Aby skonfigurować agenta zdalnego z programu Visual Studio  
  
1. Jeśli Agent nie jest jeszcze uruchomiony na komputerze Mac, wykonaj kroki opisane w sekcji [Uruchamianie zdalnego agenta](#Start). Aby program Visual Studio mógł pomyślnie sparować, nawiązać połączenie i skompilować projekt, na komputerze Mac musi być uruchomiona vcremote.  
  
2. Na komputerze Mac Pobierz nazwę hosta lub adres IP komputera Mac.  
  
    Adres IP można uzyskać za pomocą polecenia **ifconfig** w oknie terminalu. Użyj adresu inet podanego w ramach aktywnego interfejsu sieciowego.  
  
3. Na pasku menu programu Visual Studio wybierz **Narzędzia**, **Opcje**.  
  
4. W oknie dialogowym **Opcje** rozwiń pozycję **Międzyplatformowe**, **C++** system **iOS**.  
  
5. W polach **Nazwa hosta** i **port** wprowadź wartości określone przez agenta zdalnego podczas jego uruchamiania. Nazwą hosta może być nazwa DNS lub adres IP komputera Mac. Domyślnym portem jest 3030.  
  
   > [!NOTE]
   > Jeśli nie można wysłać polecenia ping do komputera Mac przy użyciu nazwy hosta, może być konieczne użycie adresu IP.  
  
6. Jeśli używasz zdalnego agenta w domyślnym trybie bezpiecznego połączenia, zaznacz pole wyboru **bezpieczne** , a następnie wprowadź wartość numeru PIN określoną przez agenta zdalnego w polu **kod PIN** . Jeśli używasz zdalnego agenta w trybie niezabezpieczonego połączenia, wyczyść pole wyboru **bezpieczne** i pozostaw puste pole **numeru PIN** .  
  
7. Wybierz **parę** , aby włączyć parowanie.  
  
    ![Konfigurowanie połączenia vcremote dla kompilacji systemu iOS](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Parowanie jest zachowywane do momentu zmiany nazwy hosta lub portu. Jeśli zmienisz nazwę hosta lub port w oknie dialogowym **Opcje** , aby cofnąć zmianę, wybierz przycisk **Przywróć** , aby przywrócić poprzednią parowanie.  
  
    Jeśli parowanie nie powiedzie się, sprawdź, czy Agent zdalny działa, wykonując kroki opisane w temacie [Uruchamianie zdalnego agenta](#Start). Jeśli upłynął zbyt dużo czasu od momentu wygenerowania numeru PIN agenta zdalnego, wykonaj kroki opisane w sekcji [generowanie nowego numeru PIN zabezpieczeń](#GeneratePIN) na komputerze Mac, a następnie spróbuj ponownie. Jeśli używasz nazwy hosta dla komputera Mac, zamiast tego spróbuj użyć adresu IP w polu **Nazwa hosta** .  
  
8. Zaktualizuj nazwę folderu w polu **zdalny katalog główny** , aby określić folder używany przez agenta zdalnego w katalogu głównym (~) na komputerze Mac. Domyślnie agent zdalny używa/users/`username`/vcremote jako zdalnego katalogu głównego.  
  
9. Wybierz **przycisk OK** , aby zapisać ustawienia połączenia zdalnego parowania.  
  
   Program Visual Studio używa tych samych informacji do łączenia się z agentem zdalnym na komputerze Mac za każdym razem, gdy jest używany. Nie trzeba ponownie łączyć programu Visual Studio z agentem zdalnym, chyba że zostanie wygenerowany nowy certyfikat zabezpieczeń na komputerze Mac lub jego nazwa hosta lub adres IP.  
  
## <a name="GeneratePIN"></a>Generuj nowy zabezpieczający kod PIN  
 Po pierwszym uruchomieniu zdalnego agenta wygenerowany kod PIN jest ważny przez ograniczoną ilość czasu — domyślnie 10 minut. Jeśli nie połączysz programu Visual Studio z agentem zdalnym przed upływem czasu, konieczne będzie wygenerowanie nowego numeru PIN.  
  
#### <a name="to-generate-a-new-pin"></a>Aby wygenerować nowy kod PIN  
  
1. Zatrzymaj agenta lub Otwórz drugie okno aplikacji terminala na komputerze Mac i Użyj tego polecenia, aby wprowadzić polecenie.  
  
2. Wprowadź to polecenie w aplikacji terminalowej:  
  
     `vcremote generateClientCert`  
  
     Agent zdalny generuje nowy tymczasowy numer PIN. Aby sparować program Visual Studio przy użyciu nowego numeru PIN, powtórz czynności opisane w sekcji [Konfigurowanie zdalnego agenta w programie Visual Studio](#ConfigureVS).  
  
## <a name="GenerateCert"></a>Wygeneruj nowy certyfikat serwera  
 Ze względów bezpieczeństwa certyfikaty serwera, które kojarzą program Visual Studio z agentem zdalnym, są powiązane z adresem IP lub nazwą hosta komputera Mac. Jeśli te wartości zmienią się, należy wygenerować nowy certyfikat serwera, a następnie ponownie skonfigurować program Visual Studio przy użyciu nowych wartości.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Aby wygenerować nowy certyfikat serwera  
  
1. Zatrzymaj agenta vcremote.  
  
2. Wprowadź to polecenie w aplikacji terminalowej:  
  
     `vcremote resetServerCert`  
  
3. Po wyświetleniu monitu o potwierdzenie wprowadź `Y`.  
  
4. Wprowadź to polecenie w aplikacji terminalowej:  
  
     `vcremote generateClientCert`  
  
     Spowoduje to wygenerowanie nowego tymczasowego numeru PIN.  
  
5. Aby sparować program Visual Studio przy użyciu nowego numeru PIN, powtórz czynności opisane w sekcji [Konfigurowanie zdalnego agenta w programie Visual Studio](#ConfigureVS).  
  
## <a name="ConfigureMac"></a>Konfigurowanie zdalnego agenta na komputerze Mac  
 Agenta zdalnego można skonfigurować przy użyciu różnych opcji wiersza polecenia. Na przykład można określić port do nasłuchiwania żądań kompilacji i określić maksymalną liczbę kompilacji do utrzymania w systemie plików. Domyślnie limit wynosi 10 kompilacji. Agent zdalny usunie kompilacje, które przekraczają maksymalną wartość przy zamykaniu.  
  
#### <a name="to-configure-the-remote-agent"></a>Aby skonfigurować agenta zdalnego  
  
- Aby wyświetlić pełną listę poleceń agenta zdalnego, w aplikacji terminala wprowadź:  
  
     `vcremote --help`  
  
- Aby wyłączyć tryb bezpieczny i włączyć proste połączenia oparte na protokole HTTP, wprowadź:  
  
     `vcremote --secure false`  
  
     W przypadku korzystania z tej opcji Wyczyść pole wyboru **bezpieczne** i pozostaw pole **numeru PIN** puste podczas konfigurowania agenta w programie Visual Studio.  
  
- Aby określić lokalizację plików agenta zdalnego, wprowadź:  
  
     `vcremote --serverDir directory_path`  
  
     gdzie *directory_path* to lokalizacja na komputerze Mac, w której mają zostać umieszczone pliki dziennika, kompilacje i certyfikaty serwera. Domyślnie ta lokalizacja to/Users/*username*/vcremote. Kompilacje są zorganizowane według numeru kompilacji w tej lokalizacji.  
  
- Aby użyć procesu w tle do przechwytywania `stdout` i `stderr` do pliku o nazwie Server. log, wpisz:  
  
     `vcremote > server.log 2>&1 &`  
  
     Plik Server. log może pomóc w rozwiązywaniu problemów z kompilacją.  
  
- Aby uruchomić agenta przy użyciu pliku konfiguracji zamiast parametrów wiersza polecenia, wpisz:  
  
     `vcremote --config config_file_path`  
  
     gdzie *config_file_path* jest ścieżką do pliku konfiguracji w formacie JSON. Opcje uruchamiania i ich wartości nie mogą zawierać kresek.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
