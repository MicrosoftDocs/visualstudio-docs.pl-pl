---
title: Zdalne obszary robocze dla R
description: Jak skonfigurować zdalne obszary robocze języka R i połączyć się z nim z programu Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 686f98aaaade035f1632139d255ccff8b37eddf3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75850067"
---
# <a name="set-up-remote-workspaces"></a>Konfigurowanie zdalnych obszarów roboczych

W tym artykule wyjaśniono, jak skonfigurować serwer zdalny z SSL i odpowiednią usługą R. Dzięki temu narzędzia R Tools for Visual Studio (RTVS) mogą łączyć się ze zdalnym obszarem roboczym na tym serwerze.

## <a name="remote-computer-requirements"></a>Wymagania dotyczące komputera zdalnego

- Windows 10, Windows Server 2016 lub Windows Server 2012 R2. RTVS wymaga również
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub więcej

## <a name="install-an-ssl-certificate"></a>Instalowanie certyfikatu SSL

RtVS wymaga, aby cała komunikacja z serwerem zdalnym odbywała się za pośrednictwem protokołu HTTP, który wymaga certyfikatu SSL na serwerze. Można użyć certyfikatu podpisanego przez zaufany urząd certyfikacji (zalecane) lub certyfikatu z podpisem własnym. (Certyfikat z podpisem własnym powoduje, że RTVS wydaje ostrzeżenia po podłączeniu). W każdym z nich należy zainstalować go na komputerze i zezwolić na dostęp do jego klucza prywatnego.

### <a name="obtain-a-trusted-certificate"></a>Uzyskiwanie zaufanego certyfikatu

Zaufany certyfikat jest wystawiany przez urząd certyfikacji (zobacz [urzędy certyfikacji w Wikipedii w](https://en.wikipedia.org/wiki/Certificate_authority) tle). Podobnie jak uzyskanie rządowej karty identyfikacyjnej, wydanie zaufanego certyfikatu wiąże się z większym procesem i możliwymi opłatami, ale weryfikuje autentyczność żądania i żądającego.

Pole klucza, które musi znajdować się w certyfikacie, to w pełni kwalifikowana nazwa domeny komputera serwera R. Urząd certyfikacji wymaga dowodu, że użytkownik jest upoważniony do utworzenia nowego serwera dla domeny, do której należy serwer.

Aby uzyskać więcej informacji na ten temat, zobacz [certyfikaty kluczy publicznych](https://en.wikipedia.org/wiki/Public_key_certificate) w Wikipedii.

## <a name="install-an-ssl-certificate-on-windows"></a>Instalowanie certyfikatu SSL w systemie Windows

Certyfikat SSL musi być zainstalowany ręcznie w systemie Windows. Postępuj zgodnie z poniższymi instrukcjami, aby zainstalować certyfikat SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Uzyskiwanie certyfikatu z podpisem własnym (Windows)

Pomiń tę sekcję, jeśli masz zaufany certyfikat. W porównaniu z certyfikatem od zaufanego urzędu, certyfikat z podpisem własnym jest jak tworzenie karty identyfikacyjnej dla siebie. Proces ten jest oczywiście znacznie prostszy niż praca z zaufanym urzędem, ale brakuje również silnego uwierzytelniania, co oznacza, że osoba atakująca może zastąpić własny certyfikat niepodpisanym certyfikatem i przechwycić cały ruch między klientem a Serwera. W związku z tym *certyfikat z podpisem własnym powinny być używane tylko do testowania scenariuszy, w zaufanej sieci i nigdy w produkcji.*

Z tego powodu RTVS zawsze wydaje następujące ostrzeżenie podczas łączenia się z serwerem z certyfikatem z podpisem własnym:

![Okno dialogowe z ostrzeżeniem o certyfikatie z podpisem własnym](media/workspaces-remote-self-signed-certificate-warning.png)

Aby wystawić certyfikat z podpisem własnym:

1. Zaloguj się do komputera serwera języka R przy użyciu konta administratora.
1. Otwórz nowy wiersz polecenia programu PowerShell administratora `"remote-machine-name"` i wydaj następujące polecenie, zastępując w pełni kwalifikowaną nazwą domeny komputera serwera.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Jeśli program PowerShell nigdy wcześniej nie był uruchamiany na komputerze z serwerem języka R, uruchom następujące polecenie, aby jawnie włączyć uruchamianie poleceń:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Zobacz też: [Certyfikaty z podpisem własnym](https://en.wikipedia.org/wiki/Self-signed_certificate) w Wikipedii.

### <a name="install-the-certificate"></a>Instalowanie certyfikatu

Aby zainstalować certyfikat na komputerze zdalnym, uruchom *plik certlm.msc* (menedżera certyfikatów) z wiersza polecenia. Kliknij prawym przyciskiem myszy folder **osobisty** i wybierz polecenie**Importuj** **wszystkie zadania:** > 

![Importowanie certyfikatu, polecenie](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Udzielanie uprawnień do odczytywania klucza prywatnego certyfikatu SSL

Po zaimportowaniu certyfikatu `NETWORK SERVICE` należy udzielić uprawnienia do odczytu klucza prywatnego zgodnie z opisem w poniższych instrukcjach. `NETWORK_SERVICE`to konto używane do uruchamiania brokera usług R, czyli usługi, która kończy przychodzące połączenia SSL z komputerem serwera.

1. Uruchom *plik certlm.msc* (Menedżer certyfikatów) z wiersza polecenia administratora.
1. Rozwiń węzeł**Certyfikaty** **osobiste** > , kliknij prawym przyciskiem myszy certyfikat i wybierz pozycję **Zarządzanie wszystkimi zadaniami** > **Zarządzaj kluczami prywatnymi**.
1. Kliknij prawym przyciskiem myszy certyfikat i wybierz polecenie **Zarządzaj kluczami prywatnymi** w obszarze **Wszystkie zadania**.
1. W wyświetlonym oknie **Add** dialogowym `NETWORK SERVICE` wybierz pozycję Dodaj i wprowadź jako nazwę konta:

    ![Okno dialogowe Zarządzanie kluczami prywatnymi, dodawanie NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Wybierz **przycisk OK** dwa razy, aby odrzucić okna dialogowe i zatwierdzić zmiany.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Instalowanie certyfikatu SSL na Ubuntu

Pakiet `rtvs-daemon` domyślnie zainstaluje certyfikat z podpisem własnym jako część instalacji.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Uzyskiwanie certyfikatu z podpisem własnym (Ubuntu)

Korzyści i zagrożenia związane z używaniem certyfikatu z podpisem własnym można znaleźć w opisie systemu Windows. Pakiet `rtvs-daemon` generuje i konfiguruje certyfikat z podpisem własnym podczas instalacji. Należy to zrobić tylko wtedy, gdy chcesz zastąpić automatycznie wygenerowany certyfikat z podpisem własnym.

Aby samodzielnie wystawić certyfikat z podpisem własnym:

1. SSH lub zaloguj się do komputera z Systemem Linux.
2. Pakiet `ssl-cert` instalacyjny:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Uruchom, `make-ssl-cert` aby wygenerować domyślny certyfikat SSL z podpisem własnym:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Przekonwertuj wygenerowany klucz i pliki PEM na PFX. Wygenerowany PFX powinien znajdować się w folderze domowym:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurowanie demona RTVS

Ścieżka pliku certyfikatu SSL (ścieżka do PFX) musi być ustawiona w */etc/rtvs/rtvsd.config.json*. Aktualizacja `X509CertificateFile` `X509CertificatePassword` i odpowiednio ze ścieżką pliku i hasłem.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Zapisz plik i uruchom ponownie `sudo systemctl restart rtvsd`demona, .

## <a name="install-r-services-on-windows"></a>Instalowanie usług R w systemie Windows

Aby uruchomić kod R, komputer zdalny musi mieć zainstalowany interpreter R w następujący sposób:

1. Pobierz i zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R dla systemu Windows](https://cran.r-project.org/bin/windows/base/)

     Oba mają identyczną funkcjonalność, ale Microsoft R Open korzysta z dodatkowych sprzętowych bibliotek algebry liniowej dzięki uprzejmości [Intel Math Kernel Library.](https://software.intel.com/intel-mkl)

2. Uruchom [instalator usług R](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) i uruchom ponownie po wyświetleniu monitu. Instalator wykonuje następujące czynności:

    - Utwórz folder w *programie %PROGRAMFILES%\R Tools for\\ Visual Studio\1.0* i skopiuj wszystkie wymagane pliki binarne.
    - Zainstaluj `RHostBrokerService` `RUserProfileService` i skonfiguruj, aby uruchamiać się automatycznie.
    - Skonfiguruj `seclogon` usługę tak, aby uruchamiała się automatycznie.
    - Dodaj *microsoft.r.host.exe* i *Microsoft.R.Host.Broker.exe* do reguł przychodzących zapory na domyślnym porcie 5444.

Usługi R uruchamiają się automatycznie po ponownym uruchomieniu komputera:

- **Usługa brokera hostów R** obsługuje cały ruch HTTPS między programem Visual Studio i procesem, w którym kod języka R jest uruchamiany na komputerze.
- **R Usługa profilu użytkownika** jest uprzywilejowanym składnikiem, który obsługuje tworzenie profilu użytkownika systemu Windows. Usługa jest wywoływana, gdy nowy użytkownik po raz pierwszy loguje się do komputera serwera R.

Możesz zobaczyć te usługi w konsoli zarządzania usługami (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Instalowanie usług R na linuksie

Aby uruchomić kod R, komputer zdalny musi mieć zainstalowany interpreter R w następujący sposób:

1. Pobierz i zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Oba mają identyczną funkcjonalność, ale Microsoft R Open korzysta z dodatkowych sprzętowych bibliotek algebry liniowej dzięki uprzejmości [Intel Math Kernel Library.](https://software.intel.com/intel-mkl)

2. Postępuj zgodnie z instrukcjami dotyczącymi [usługi Zdalne R dla systemu Linux](setting-up-remote-r-service-on-linux.md), która obejmuje fizyczne komputery Ubuntu, maszyny wirtualne Ubuntu platformy Azure, podsystem windows dla systemu Linux (WSL) i kontenery platformy Docker, w tym kontenery uruchomione w repozytorium kontenerów platformy Azure.

## <a name="configure-r-services"></a>Konfigurowanie usług R

W usługach R uruchomionych na komputerze zdalnym należy również utworzyć konta użytkowników, ustawić reguły zapory, skonfigurować sieć platformy Azure i skonfigurować certyfikat SSL.

1. Konta użytkowników: tworzenie kont dla każdego użytkownika uzyskującego dostęp do komputera zdalnego. Można utworzyć standardowe (nieuprzywilejowane) konta użytkowników lokalnych lub dołączyć komputer serwera R do domeny i dodać `Users` odpowiednie grupy zabezpieczeń do grupy zabezpieczeń.

1. Reguły zapory: `R Host Broker` Domyślnie nasłuchuje na porcie TCP 5444. W związku z tym upewnij się, że istnieją reguły zapory systemu Windows włączone zarówno dla ruchu przychodzącego i wychodzącego (ruch wychodzący jest potrzebny do instalowania pakietów i podobnych scenariuszy).  Instalator usług R automatycznie ustawia te reguły dla wbudowanej zapory systemu Windows. Jeśli jednak używasz zapory innej firmy, otwórz port 5444 ręcznie. `R Host Broker`

1. Konfiguracja platformy Azure: Jeśli komputer zdalny jest maszyną wirtualną na platformie Azure, otwórz port 5444 dla ruchu przychodzącego w sieci platformy Azure, która jest niezależna od zapory systemu Windows. Aby uzyskać szczegółowe informacje, zobacz [Filtrowanie ruchu sieciowego z sieciową grupą zabezpieczeń](/azure/virtual-network/virtual-networks-nsg) w dokumentacji platformy Azure.

1. Poinformuj brokera hosta R, który certyfikat SSL należy załadować: Jeśli instalujesz certyfikat na serwerze intranetowym, prawdopodobnie w pełni kwalifikowana nazwa domeny serwera jest taka sama jak jego nazwa NETBIOS. W takim przypadku nie ma nic, co należy zrobić, ponieważ jest to domyślny certyfikat, który jest ładowany.

    Jeśli jednak certyfikat jest instalowany na serwerze internetowym (takim jak maszyna wirtualna platformy Azure), należy użyć w pełni kwalifikowanej nazwy domeny (FQDN) serwera, ponieważ nazwa FQDN serwera z widokiem na Internet nigdy nie jest taka sama jak jego nazwa NETBIOS.

    Aby użyć nazwy FQDN, przejdź do miejsca, w którym są zainstalowane usługi R (*%PROGRAM FILES%\R Remote Service for Visual Studio\1.0* domyślnie), otwórz plik *Microsoft.R.Host.Broker.Config.json* w `foo.westus.cloudapp.azure.com`edytorze tekstu i zastąp jego zawartość następującym elementem, przypisując CN do dowolnej nazwy FQDN serwera, na przykład:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Zapisz plik i uruchom ponownie komputer, aby zastosować zmiany.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

**P. Komputer serwera R nie odpowiada, co mam zrobić?**

Spróbuj wykonać polecenie ping komputera zdalnego z wiersza polecenia: `ping remote-machine-name`. Jeśli ping nie powiedzie się, upewnij się, że komputer jest uruchomiony.

**P. W interaktywnym oknie języka R jest włączone, ale dlaczego usługa nie jest uruchomiona?**

Istnieją trzy możliwe powody:

- [Program .NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub wyższy nie jest zainstalowany na komputerze.
- Reguły `Microsoft.R.Host.Broker` zapory dla i `Microsoft.R.Host` nie są włączone zarówno dla połączeń przychodzących, jak i wychodzących na porcie 5444.
- Certyfikat SSL `CN=<remote-machine-name>` z nie został zainstalowany.

Uruchom ponownie komputer po dokonaniu któregokolwiek z powyższych zmian. Następnie upewnij `RHostBrokerService` się, że i `RUserProfileService` są uruchomione za pośrednictwem Menedżera zadań (karta usługi) lub *services.msc*.

**P. Dlaczego w oknie interaktywnym języka R jest komunikat "Odmowa dostępu 401" podczas łączenia się z serwerem języka R?**

Istnieją dwa możliwe powody:

- Jest wysoce prawdopodobne, `NETWORK SERVICE` że konto nie ma dostępu do klucza prywatnego certyfikatu SSL. Postępuj zgodnie z wcześniejszymi instrukcjami, aby udzielić `NETWORK SERVICE` dostępu do klucza prywatnego.
- Upewnij się, że `seclogon` usługa jest uruchomiona. Użyj *services.msc,* `seclogon` aby skonfigurować automatyczne uruchamianie.

**P. Dlaczego interaktywne okno języka R mówi "Nie znaleziono 404" podczas łączenia się z serwerem języka R?**

Ten błąd jest prawdopodobnie ze względu na brak bibliotek redystrybucyjnych visual C++. Sprawdź okno interaktywne języka R, aby sprawdzić, czy jest wyświetlany komunikat dotyczący brakującej biblioteki (DLL). Następnie sprawdź, czy jest zainstalowana redystrybucja programu VS 2015 i czy zainstalowano również funkcję R.

**P. Nie mogę uzyskać dostępu do Internetu/zasobu z interaktywnego okna R, co mam zrobić?**

Upewnij się, że `Microsoft.R.Host.Broker` `Microsoft.R.Host` zapora jest regułą i zezwalaj na dostęp wychodzący na porcie 5444. Uruchom ponownie komputer po zastosowaniu zmian.

**P. Próbowałem wszystkich tych rozwiązań i nadal nie działa. Co teraz?**

Poszukaj w plikach dziennika w *języku C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Ten folder zawiera oddzielne pliki dziennika dla każdego wystąpienia usługi brokera R, która została uruchomiony. Nowy plik dziennika jest tworzony przy każdym ponownym uruchomieniu usługi. Sprawdź najnowszy plik dziennika, aby uzyskać wskazówki dotyczące tego, co może się nie udać.
