---
title: Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c1eaa934c83676ee11854701f372b972f3045e66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792866"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Instalowanie i konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Możesz używać Visual C++ for Cross-Platform Mobile Development, edytowanie, debugowanie i wdrażanie kodu z systemem iOS w narzędziu iOS Simulator lub na urządzeniu z systemem iOS, ale z powodu ograniczeń licencyjnych, kod musi można skompilować i uruchomić zdalnie na komputerach Mac. Aby skompilować i uruchomić aplikacje dla systemu iOS przy użyciu programu Visual Studio, musisz Instalowanie i Konfigurowanie agenta zdalnego [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), na komputerze Mac. Obsługuje zdalnego agenta kompilacji żądania z programu Visual Studio i uruchamia aplikację na urządzeniu z systemem iOS podłączone do komputera Mac lub w narzędziu iOS Simulator na komputerze Mac.  
  
> [!NOTE]
>  Aby uzyskać informacji na temat korzystania z usług hostowanych w chmurze Mac zamiast komputera Mac, zobacz [tworzenie i symulowanie systemu iOS w chmurze](https://taco.visualstudio.com/docs/build_ios_cloud/). Instrukcje dotyczą tworzenia przy użyciu programu Visual Studio Tools for Apache Cordova. W celu postępuj zgodnie z instrukcjami, aby kompilować przy użyciu języka Visual C++ for Cross-Platform Mobile Development, należy zastąpić vcremote dla programu vs-mda-remote.  
  
 Po zainstalowaniu narzędzia do tworzenia przy użyciu systemu iOS można znaleźć w tym temacie, aby poznać sposoby szybko skonfigurować i zaktualizować agenta zdalnego dla programowania w systemie iOS w programie Visual Studio i na komputerze Mac.  
  
 [Wymagania wstępne](#Prerequisites)  
  
 [Zainstaluj agenta zdalnego dla systemu iOS](#Install)  
  
 [Uruchom agenta zdalnego](#Start)  
  
 [Konfigurowanie agenta zdalnego w programie Visual Studio](#ConfigureVS)  
  
 [Generowanie nowego zabezpieczającego numeru PIN](#GeneratePIN)  
  
 [Wygeneruj nowy certyfikat serwera](#GenerateCert)  
  
 [Konfigurowanie zdalnego agenta na komputerze Mac](#ConfigureMac)  
  
##  <a name="Prerequisites"></a> Wymagania wstępne  
 Aby zainstalować i używać zdalnego agenta do tworzenia kodu dla systemu iOS, najpierw musisz mieć następujące wymagania wstępne:  
  
-   Komputer Mac z systemem OS X Mavericks lub nowszej  
  
-   [Identyfikatora Apple ID](https://appleid.apple.com/)  
  
-   Aktywne [systemu iOS w programie dla deweloperów](https://developer.apple.com/programs/ios/) konta z danymi firmy Apple  
  
-   [Edytor Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Edytor Xcode 6 można pobrać z Store aplikacji.  
  
-   Narzędzia wiersza polecenia programu Xcode  
  
     Aby zainstalować narzędzia wiersza polecenia programu Xcode, Otwórz aplikację Terminal na komputerze Mac i wprowadź następujące polecenie:  
  
     `xcode-select --install`  
  
-   Tożsamość skonfigurowane w środowisku Xcode do podpisywania systemu iOS  
  
     Aby uzyskać szczegółowe informacje dotyczące uzyskiwania tożsamości podpisywania systemu iOS, zobacz [zachowaniu tożsamości podpisywania i certyfikaty](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) w bibliotece deweloperów systemu iOS. Aby wyświetlić lub ustaw tożsamość podpisywania w środowisku Xcode, otwórz **Xcode** menu i wybrać **preferencje**. Wybierz **kont** i wybierz identyfikator Apple ID, a następnie wybierz **Wyświetl szczegóły** przycisku.  
  
-   Jeśli używasz urządzenia z systemem iOS do tworzenia aplikacji, profil aprowizacji skonfigurowane w środowisku Xcode dla Twojego urządzenia  
  
     Aby uzyskać szczegółowe informacje na temat tworzenia profilów aprowizacji, zobacz [tworzenie Provisioning profile Using Member Center](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) w bibliotece deweloperów systemu iOS.  
  
-   [Node.js](http://nodejs.org/)  
  
-   Zaktualizowana wersja Menedżera npm  
  
     Wersja programu npm, dostarczanego przy użyciu środowiska Node.js nie może być wystarczająco długi, aby zainstalować vcremote. Aby zaktualizować npm, Otwórz aplikację Terminal na komputerze Mac, a następnie wprowadź następujące polecenie:  
  
     `sudo npm install -g npm@latest`  
  
##  <a name="Install"></a> Zainstaluj agenta zdalnego dla systemu iOS  
 Po zainstalowaniu programu Visual C++ for Cross-Platform Mobile Development w Visual Studio może komunikować się z [vcremote](http://go.microsoft.com/fwlink/p/?LinkId=534988), zdalnego agenta uruchomionego na komputerze Mac do transferu plików, tworzenie i uruchamianie aplikacji systemu iOS oraz wysyłania poleceń do debugowania.  
  
 Przed zainstalowaniem agenta zdalnego, upewnij się, że zostały spełnione [wymagania wstępne](#Prerequisites) i zainstalowane [Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools).  
  
###  <a name="DownloadInstall"></a> Aby pobrać i zainstalować agenta zdalnego  
  
- W terminalu aplikacji na komputerze Mac wprowadź:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Globalne instalacji (**-g**) przełącznik jest zalecane, ale nie jest wymagane.  
  
   Podczas instalacji vcremote zainstalowano i włączono tryb dewelopera na komputerze Mac. [Homebrew](http://brew.sh/) i dwa pakiety npm vcremote lib i vcremote utils, są również instalowane.  
  
  > [!NOTE]
  >  Aby zainstalować program Homebrew, musi mieć dostęp "sudo" (administrator). Jeśli musisz zainstalować vcremote bez "sudo", można ręcznie zainstalować Homebrew w lokalizacji usr/elementu lokalnego i dodać jego folder bin do ścieżki. Aby uzyskać więcej informacji, zobacz [dokumentacji Homebrew](https://github.com/Homebrew/homebrew/wiki/Installation). Aby ręcznie włączyć tryb dewelopera, wprowadź polecenie w terminalu aplikacji: `DevToolsSecurity –enable`  
  
  Jeżeli zostanie zaktualizowany do nowej wersji programu Visual Studio, należy zaktualizować do bieżącej wersji agenta zdalnego. Aby zaktualizować agenta zdalnego, powtórz kroki, aby pobrać i zainstalować agenta zdalnego.  
  
##  <a name="Start"></a> Uruchom agenta zdalnego  
 Agent zdalny musi być uruchomiony dla programu Visual Studio skompilować i uruchomić kod dla systemu iOS. Program Visual Studio muszą być skojarzone z agentem zdalnym, zanim będzie mogła komunikować się. Domyślnie agent zdalny jest uruchamiany w trybie bezpiecznego połączenia, który wymaga numeru PIN łączyć się z programu Visual Studio.  
  
###  <a name="RemoteAgentStartServer"></a> Aby uruchomić agenta zdalnego  
  
- W terminalu aplikacji na komputerze Mac wprowadź:  
  
   `vcremote`  
  
   Ten cykl zaczyna agent zdalny katalog kompilacji domyślnej ~ / vcremote. Aby uzyskać dodatkowe opcje konfiguracji, zobacz [konfigurowania zdalnego agenta na komputerze Mac](#ConfigureMac).  
  
  Przy pierwszym uruchomieniu agenta i każdym utworzeniu nowego certyfikatu klienta, użytkownicy otrzymywali wymaganych informacji w celu skonfigurowania agenta w programie Visual Studio, w tym nazwy hosta, portu i numer PIN.  
  
  ![Umożliwia generowanie numeru PIN bezpiecznego vcremote](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Jeśli zamierzasz skonfigurować agenta zdalnego w programie Visual Studio przy użyciu nazwy hosta, należy wysłać polecenie ping Mac z Windows przy użyciu nazwy hosta, aby sprawdzić, czy jest dostępny. W przeciwnym razie konieczne może być zamiast tego użyj adresu IP.  
  
  Wygenerowany kod PIN jest przeznaczony dla jednego czasu i jest prawidłowy tylko przez ograniczony czas. Visual Studio nie parowania z agentem zdalnym przed wygaśnięciem, należy wygenerować nowy kod PIN. Aby uzyskać więcej informacji, zobacz [Generowanie nowego zabezpieczającego numeru PIN](#GeneratePIN).  
  
  Za pomocą agenta zdalnego w trybie niezabezpieczona. W trybie niezabezpieczonym agenta zdalnego mogą być parowane do programu Visual Studio bez numeru PIN.  
  
#### <a name="to-disable-secured-connection-mode"></a>Aby wyłączyć tryb bezpiecznego połączenia  
  
-   Aby wyłączyć tryb połączenia zabezpieczonego w vcremote, wprowadź polecenie w terminalu aplikacji na komputerze Mac:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>Aby włączyć tryb bezpiecznego połączenia  
  
- Aby włączyć tryb połączenia zabezpieczonego, wprowadź to polecenie:  
  
   `vcremote --secure true`  
  
  Po uruchomieniu agenta zdalnego można użyć go w programie Visual Studio, dopóki nie zostanie zatrzymana.  
  
#### <a name="to-stop-the-remote-agent"></a>Aby zatrzymać agenta zdalnego  
  
-   W terminalu działa vcremote okna, wprowadź `Control+C`.  
  
##  <a name="ConfigureVS"></a> Konfigurowanie agenta zdalnego w programie Visual Studio  
 Aby połączyć się z agentem zdalnym z programu Visual Studio, należy określić konfigurację zdalnego w opcjach programu Visual Studio.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>Aby skonfigurować agenta zdalnego w programie Visual Studio  
  
1. Jeśli agent nie jest już uruchomiona na komputerze Mac, wykonaj kroki opisane w [uruchomić agenta zdalnego](#Start). Komputer Mac musi być uruchomiona vcremote dla programu Visual Studio pomyślnie pair, łączenie i skompiluj projekt.  
  
2. Na komputerze Mac Pobierz nazwę hosta lub adres IP Twojego komputera Mac.  
  
    Adres IP można uzyskać za pomocą **ifconfig** polecenia w oknie terminala. Użyj adresu inet interfejsu sieciowego z aktywnego na liście.  
  
3. Na pasku menu programu Visual Studio, wybierz **narzędzia**, **opcje**.  
  
4. W **opcje** okna dialogowego rozwiń **Międzyplatformowe**, **C++**, **iOS**.  
  
5. W **nazwy hosta** i **portu** wprowadź wartości określonych przez agenta zdalnego, po jego uruchomieniu. Nazwa hosta może zawierać nazwy DNS lub adres IP Twojego komputera Mac. Domyślny port to 3030.  
  
   > [!NOTE]
   >  Nie można wykonać polecenie ping Mac przy użyciu nazwy hosta, może być konieczne używanie adresu IP.  
  
6. Jeśli używasz zdalnego agenta w domyślnym trybie bezpiecznego połączenia, sprawdź **bezpiecznego** pole wyboru, wprowadź wartość numeru PIN, określony przez agenta zdalnego w **numeru Pin** pola. Jeśli używasz zdalnego agenta w trybie niezabezpieczone połączenie, wyczyść **bezpiecznego** pole wyboru i pozostawić **numeru Pin** pole puste.  
  
7. Wybierz **pary** umożliwia kojarzenie.  
  
    ![Konfigurowanie połączenia vcremote dla kompilacji dla systemu iOS](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Parowanie będzie się powtarzać, dopóki nie zmienisz nazwę hosta lub portu. Jeśli zmienisz nazwę hosta lub port w **opcje** okno dialogowe, aby cofnąć zmianę, wybierz **Przywróć** przycisk, aby powrócić do poprzedniego parowania.  
  
    Jeśli skojarzenie nie powiedzie się, sprawdź, czy agent zdalny jest uruchomiony, wykonując kroki opisane w [uruchomić agenta zdalnego](#Start). Jeśli zbyt dużo czasu minęło od czasu wygenerowania agenta zdalnego numeru PIN, wykonaj kroki opisane w [Generowanie nowego zabezpieczającego numeru PIN](#GeneratePIN) na komputerach Mac i spróbuj wykonać operację ponownie. Jeśli używasz nazwę hosta komputera Mac, spróbuj użyć adresu IP w **nazwy hosta** zamiast tego pola.  
  
8. Zaktualizuj nazwę folderu, w **zdalny katalog główny** pola, aby wskazać folder, używane przez agenta zdalnego w katalogu głównym (~) na komputerze Mac. Domyślnie zdalny agent używa /Users/`username`/vcremote jako zdalny katalog główny.  
  
9. Wybierz **OK** można zapisać ustawień połączenia zdalnego parowania.  
  
   Visual Studio używa te same informacje, aby nawiązać połączenie zdalnego agenta na komputerze Mac, zawsze możesz użyć. Nie trzeba wykonać parowania programu Visual Studio z agentem zdalnym ponownie chyba że Wygeneruj nowy certyfikat zabezpieczeń na komputerze Mac lub zmian adresów IP lub nazwy hosta.  
  
##  <a name="GeneratePIN"></a> Generowanie nowego zabezpieczającego numeru PIN  
 Po uruchomieniu agenta zdalnego po raz pierwszy, wygenerowany kod PIN jest ważny przez ograniczony okres — domyślnie 10 minut. Visual Studio nie parowania z agentem zdalnym przed wygaśnięciem, należy wygenerować nowy kod PIN.  
  
#### <a name="to-generate-a-new-pin"></a>Aby wygenerować nowy kod PIN  
  
1.  Zatrzymaj agenta, lub Otwórz drugie okno terminala aplikacji na komputerze Mac, a następnie go użyć, aby wprowadzić polecenie.  
  
2.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote generateClientCert`  
  
     Agent zdalny generuje nowy tymczasowy numer PIN. Aby sparować programu Visual Studio za pomocą nowego numeru PIN, powtórz kroki opisane w [skonfigurować agenta zdalnego w programie Visual Studio](#ConfigureVS).  
  
##  <a name="GenerateCert"></a> Wygeneruj nowy certyfikat serwera  
 Ze względów bezpieczeństwa serwera certyfikatów tej pary programu Visual Studio z agentem zdalnym są powiązane z nazwy hosta lub adres IP Twojego komputera Mac. W przypadku zmiany tych wartości, należy wygenerować nowy certyfikat serwera i następnie ponownie skonfigurować program Visual Studio z nowymi wartościami.  
  
#### <a name="to-generate-a-new-server-certificate"></a>Aby wygenerować nowy certyfikat serwera  
  
1.  Zatrzymaj agenta vcremote.  
  
2.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote resetServerCert`  
  
3.  Po wyświetleniu monitu o potwierdzenie, wprowadź `Y`.  
  
4.  Wprowadź następujące polecenie w terminalu aplikacji:  
  
     `vcremote generateClientCert`  
  
     Spowoduje to wygenerowanie nowego, tymczasowego numeru PIN.  
  
5.  Aby sparować programu Visual Studio za pomocą nowego numeru PIN, powtórz kroki opisane w [skonfigurować agenta zdalnego w programie Visual Studio](#ConfigureVS).  
  
##  <a name="ConfigureMac"></a> Konfigurowanie zdalnego agenta na komputerze Mac  
 Można skonfigurować agenta zdalnego przy użyciu różnych opcji wiersza polecenia. Na przykład można określić port do nasłuchiwania żądań kompilacji i określ maksymalną liczbę kompilacji do obsługi w systemie plików. Domyślnie limit wynosi 10 kompilacji. Spowoduje to usunięcie zdalnego agenta kompilacji, które przekraczają maksimum podczas zamykania.  
  
#### <a name="to-configure-the-remote-agent"></a>Aby skonfigurować agenta zdalnego  
  
-   Aby wyświetlić pełną listę poleceń agenta zdalnego, w aplikacji Terminal, wpisz:  
  
     `vcremote --help`  
  
-   Aby wyłączyć tryb bezpieczny i prosty połączeń oparty na protokole HTTP, wpisz:  
  
     `vcremote --secure false`  
  
     Usuń zaznaczenie tej opcji **bezpiecznego** pole wyboru i pozostawić **numeru Pin** pole puste, podczas konfigurowania agenta w programie Visual Studio.  
  
-   Aby określić lokalizację dla plików agenta zdalnego, wpisz:  
  
     `vcremote --serverDir directory_path`  
  
     gdzie *directory_path* znajduje się na komputerze Mac, aby umieścić pliki dziennika, kompilacji i certyfikaty serwera. Domyślnie ta lokalizacja jest /Users/*username*/vcremote. Kompilacje są uporządkowane według numeru kompilacji w tej lokalizacji.  
  
-   Na potrzeby przechwytywania przez proces w tle `stdout` i `stderr` do pliku o nazwie server.log, wpisz:  
  
     `vcremote > server.log 2>&1 &`  
  
     Plik server.log mogą pomóc w rozwiązywaniu problemów z kompilacją.  
  
-   Aby uruchomić agenta przy użyciu pliku konfiguracji zamiast parametrów wiersza polecenia, wpisz:  
  
     `vcremote --config config_file_path`  
  
     gdzie *config_file_path* jest ścieżka do pliku konfiguracji w formacie JSON. Opcje uruchamiania i ich wartości nie może zawierać łączników.  
  
## <a name="see-also"></a>Zobacz też  
 [Instalowanie języka Visual C++ dla opracowywania aplikacji mobilnych na wiele platform](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
