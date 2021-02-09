---
title: Zdalne obszary robocze dla języka R
description: Jak skonfigurować zdalne obszary robocze języka R i połączyć się z nim za pomocą programu Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 96078d1b2fdb5a54c912cbf214024726ce102e4e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851845"
---
# <a name="set-up-remote-workspaces"></a>Konfigurowanie zdalnych obszarów roboczych

W tym artykule wyjaśniono, jak skonfigurować serwer zdalny przy użyciu protokołu SSL i odpowiedniej usługi R. Pozwala to R Tools for Visual Studio (RTVS) na łączenie się ze zdalnym obszarem roboczym na tym serwerze.

## <a name="remote-computer-requirements"></a>Wymagania dotyczące komputera zdalnego

- Windows 10, Windows Server 2016 lub Windows Server 2012 R2. RTVS wymaga również
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub nowsze

## <a name="install-an-ssl-certificate"></a>Instalowanie certyfikatu SSL

RTVS wymaga, aby cała komunikacja z serwerem zdalnym odbywa się za pośrednictwem protokołu HTTP, który wymaga certyfikatu SSL na serwerze. Można użyć certyfikatu podpisanego przez zaufany urząd certyfikacji (zalecane) lub certyfikat z podpisem własnym. (Certyfikat z podpisem własnym powoduje, że RTVS do wystawiania ostrzeżeń po nawiązaniu połączenia). Następnie należy zainstalować go na komputerze i zezwolić na dostęp do jego klucza prywatnego.

### <a name="obtain-a-trusted-certificate"></a>Uzyskaj zaufany certyfikat

Zaufany certyfikat jest wystawiany przez urząd certyfikacji (zobacz [urzędy certyfikacji w witrynie Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) dla tła). Podobnie jak w przypadku uzyskania karty identyfikacyjnej dla instytucji rządowych, wystawianie certyfikatu zaufanego obejmuje więcej informacji na temat procesu i ewentualnych opłat, ale weryfikuje autentyczność żądania oraz osoby żądającej.

Pole klucza, które musi znajdować się w certyfikacie, to w pełni kwalifikowana nazwa domeny komputera z systemem R Server. Urząd certyfikacji wymaga potwierdzenia, że masz uprawnienia do utworzenia nowego serwera dla domeny, do której należy serwer.

Aby uzyskać więcej informacji, zobacz [certyfikaty kluczy publicznych](https://en.wikipedia.org/wiki/Public_key_certificate) w witrynie Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Instalowanie certyfikatu SSL w systemie Windows

Certyfikat SSL musi być instalowany ręcznie w systemie Windows. Postępuj zgodnie z poniższymi instrukcjami, aby zainstalować certyfikat SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Uzyskaj certyfikat z podpisem własnym (Windows)

Pomiń tę sekcję, jeśli masz zaufany certyfikat. W porównaniu z certyfikatem z zaufanego urzędu certyfikat z podpisem własnym jest podobny do tworzenia karty identyfikacyjnej dla siebie. Ten proces jest oczywiście znacznie prostsze niż praca z zaufanym urzędem, ale również nie ma silnego uwierzytelniania, co oznacza, że osoba atakująca może zastąpić własny certyfikat certyfikatem niepodpisanym i przechwycić cały ruch między klientem a serwerem. W związku z tym certyfikat z podpisem *własnym powinien być używany tylko w scenariuszach testowania, w zaufanej sieci, a nigdy w środowisku produkcyjnym.*

Z tego powodu w przypadku nawiązywania połączenia z serwerem z certyfikatem z podpisem własnym RTVS zawsze wystawia następujące ostrzeżenie:

![Okno dialogowe ostrzeżenia certyfikatu z podpisem własnym](media/workspaces-remote-self-signed-certificate-warning.png)

Aby wystawić certyfikat z podpisem własnym:

1. Zaloguj się na komputerze z systemem R Server przy użyciu konta administratora.
1. Otwórz nowy wiersz polecenia programu PowerShell dla administratora i wydaj następujące polecenie, zastępując `"remote-machine-name"` przy użyciu w pełni kwalifikowanej nazwy domeny komputera serwera.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Jeśli na komputerze z programem R Server nigdy nie uruchomiono programu PowerShell, uruchom następujące polecenie, aby jawnie włączyć uruchamianie poleceń:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

W przypadku programu w tle zobacz [certyfikaty z podpisem własnym](https://en.wikipedia.org/wiki/Self-signed_certificate) w witrynie Wikipedia.

### <a name="install-the-certificate"></a>Instalowanie certyfikatu

Aby zainstalować certyfikat na komputerze zdalnym, uruchom *certlm. msc* (Menedżer certyfikatów) z wiersza polecenia. Kliknij prawym przyciskiem myszy folder **osobiste** i wybierz polecenie **Importuj wszystkie zadania**  >   :

![Importuj certyfikat — polecenie](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Przyznaj uprawnienia do odczytu klucza prywatnego certyfikatu SSL

Po zaimportowaniu certyfikatu nadaj `NETWORK SERVICE` kontu uprawnienia do odczytu klucza prywatnego zgodnie z opisem w poniższych instrukcjach. `NETWORK_SERVICE` jest kontem używanym do uruchamiania brokera usługi R Services, który jest usługą, która kończy połączenia przychodzące protokołu SSL z komputerem serwera.

1. Uruchom *certlm. msc* (Menedżer certyfikatów) z wiersza polecenia administratora.
1. Rozwiń węzeł  >  **Certyfikaty** osobiste, kliknij prawym przyciskiem myszy certyfikat, a następnie wybierz pozycję **wszystkie zadania**  >  **Zarządzaj kluczami prywatnymi**.
1. Kliknij prawym przyciskiem myszy certyfikat i wybierz polecenie **Zarządzaj kluczami prywatnymi** w obszarze **wszystkie zadania**.
1. W wyświetlonym oknie dialogowym wybierz pozycję **Dodaj** , a następnie wprowadź `NETWORK SERVICE` nazwę konta:

    ![Okno dialogowe Zarządzanie kluczami prywatnymi, Dodawanie NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Kliknij dwukrotnie **przycisk OK** , aby odrzucić okna dialogowe i zatwierdzić zmiany.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Instalowanie certyfikatu SSL na Ubuntu

`rtvs-daemon`Pakiet zainstaluje certyfikat z podpisem własnym domyślnie w ramach instalacji.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Uzyskaj certyfikat z podpisem własnym (Ubuntu)

Aby uzyskać korzyści i zagrożenia związane z korzystaniem z certyfikatu z podpisem własnym, zobacz opis systemu Windows. `rtvs-daemon`Pakiet generuje i konfiguruje certyfikat z podpisem własnym podczas instalacji. Należy to zrobić tylko wtedy, gdy chcesz zastąpić automatycznie wygenerowany certyfikat z podpisem własnym.

Aby samodzielnie wydać certyfikat z podpisem własnym:

1. SSH lub Zaloguj się na komputerze z systemem Linux.
2. `ssl-cert`Pakiet instalacyjny:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Uruchom `make-ssl-cert` w celu wygenerowania domyślnego certyfikatu SSL z podpisem własnym:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Przekonwertuj wygenerowane klucze i pliki PEM na PFX. Wygenerowany plik PFX powinien znajdować się w folderze głównym:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Konfigurowanie demona RTVS

Ścieżka pliku certyfikatu SSL (ścieżka do PFX) musi być ustawiona w */etc/rtvs/rtvsd.config.jsna*. Zaktualizuj `X509CertificateFile` `X509CertificatePassword` odpowiednio ścieżkę pliku i hasło.

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

Zapisz plik i ponownie uruchom demona, `sudo systemctl restart rtvsd` .

## <a name="install-r-services-on-windows"></a>Instalowanie usług R w systemie Windows

Aby uruchomić kod języka R, komputer zdalny musi mieć zainstalowany interpreter języka R w następujący sposób:

1. Pobierz i Zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R dla systemu Windows](https://cran.r-project.org/bin/windows/base/)

     Obie funkcje mają identyczną funkcjonalność, ale korzyści z używania oprogramowania Microsoft R Open są dostępne na podstawie dodatkowych, przyspieszonego sprzętu algebry bibliotek, które dają dostęp do [biblioteki jądra matematycznej Intel](https://software.intel.com/intel-mkl).

2. Uruchom [instalatora usług R](https://github.com/Microsoft/RTVS/blob/master/doc/rtvsd/rtvs-remote-downloads.md) i uruchom ponownie po wyświetleniu monitu. Instalator wykonuje następujące czynności:

    - Utwórz folder w *narzędziach%PROGRAMFILES%\r Tools for Visual \\ Studio\1.0* i skopiuj wszystkie wymagane pliki binarne.
    - Zainstaluj program `RHostBrokerService` i `RUserProfileService` skonfiguruj go do automatycznego uruchamiania.
    - Skonfiguruj `seclogon` Automatyczne uruchamianie usługi.
    - Dodaj *Microsoft.R.Host.exe* i *Microsoft.R.Host.Broker.exe* do reguł ruchu przychodzącego zapory na domyślnym porcie 5444.

Usługa R Services jest uruchamiana automatycznie po ponownym uruchomieniu komputera:

- **Usługa brokera hosta języka r** obsługuje cały ruch HTTPS między programem Visual Studio i przetwarza, gdzie kod języka R jest uruchamiany na komputerze.
- **Usługa profilu użytkownika R** to uprzywilejowany składnik obsługujący Tworzenie profilu użytkownika systemu Windows. Usługa jest wywoływana, gdy nowy użytkownik najpierw zaloguje się na komputerze z systemem R Server.

Te usługi można wyświetlić w konsoli zarządzania usługami (*compmgmt. msc*).

## <a name="install-r-services-on-linux"></a>Instalowanie usług R Services w systemie Linux

Aby uruchomić kod języka R, komputer zdalny musi mieć zainstalowany interpreter języka R w następujący sposób:

1. Pobierz i Zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Obie funkcje mają identyczną funkcjonalność, ale korzyści z używania oprogramowania Microsoft R Open są dostępne na podstawie dodatkowych, przyspieszonego sprzętu algebry bibliotek, które dają dostęp do [biblioteki jądra matematycznej Intel](https://software.intel.com/intel-mkl).

2. Postępuj zgodnie z instrukcjami dotyczącymi [zdalnej usługi R dla systemu Linux](setting-up-remote-r-service-on-linux.md), które obejmują fizyczne komputery Ubuntu, maszyny wirtualne platformy Azure Ubuntu, podsystem Windows dla systemów Linux (WSL) i kontenerów platformy Docker, w tym te uruchomione w repozytorium kontenerów platformy Azure.

## <a name="configure-r-services"></a>Konfigurowanie usług R Services

Przy użyciu usługi R Services uruchomionej na komputerze zdalnym należy również utworzyć konta użytkowników, ustawić reguły zapory, skonfigurować sieć platformy Azure i skonfigurować certyfikat SSL.

1. Konta użytkowników: Utwórz konta dla każdego użytkownika, który uzyskuje dostęp do komputera zdalnego. Można utworzyć standardowe (nieuprzywilejowane) konta użytkowników lokalnych lub przyłączyć komputer z systemem R Server do domeny i dodać odpowiednie grupy zabezpieczeń do `Users` grupy zabezpieczeń.

1. Reguły zapory: Domyślnie `R Host Broker` nasłuchuje na porcie TCP 5444. W związku z tym upewnij się, że istnieją reguły zapory systemu Windows włączone dla ruchu przychodzącego i wychodzącego (ruch wychodzący jest wymagany do zainstalowania pakietów i podobnych scenariuszy).  Instalator usług R Services automatycznie ustawia te reguły dla wbudowanej zapory systemu Windows. Jeśli korzystasz z zapory innej firmy, należy jednak ręcznie otworzyć port 5444 `R Host Broker` .

1. Konfiguracja platformy Azure: Jeśli komputer zdalny jest maszyną wirtualną na platformie Azure, otwórz port 5444 dla ruchu przychodzącego w sieci platformy Azure, który jest niezależny od zapory systemu Windows. Aby uzyskać szczegółowe informacje, zobacz [Filtrowanie ruchu sieciowego przy użyciu sieciowej grupy zabezpieczeń](/azure/virtual-network/virtual-networks-nsg) w dokumentacji platformy Azure.

1. Poinformuj brokera hosta języka R, który certyfikat SSL ma zostać załadowany: Jeśli certyfikat jest instalowany na serwerze intranetowym, prawdopodobnie w pełni kwalifikowana nazwa domeny serwera jest taka sama jak nazwa NETBIOS. W takim przypadku nie trzeba nic robić, ponieważ jest to domyślny certyfikat, który jest ładowany.

    Jeśli jednak instalujesz certyfikat na serwerze dostępnym z Internetu (na przykład na maszynie wirtualnej platformy Azure), użyj w pełni kwalifikowanej nazwy domeny (FQDN) serwera, ponieważ nazwa FQDN serwera internetowego nie jest taka sama jak nazwa NETBIOS.

    Aby użyć nazwy FQDN, przejdź do lokalizacji, w której usługi R Services są zainstalowane (domyślnie:*% Program Files%\r Remote Service for Visual Studio\1.0* ), Otwórz *Microsoft.R.Host.Broker.Config.jsw* pliku w edytorze tekstów i Zastąp jego zawartość następującym kodem, przypisując do dowolnej nazwy FQDN serwera, na przykład `foo.westus.cloudapp.azure.com` :

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

**Pytania. Komputer z serwerem R Server nie odpowiada, co mam zrobić?**

Spróbuj wysłać polecenie ping do komputera zdalnego z wiersza polecenia: `ping remote-machine-name` . Jeśli polecenie ping zakończy się niepowodzeniem, upewnij się, że komputer jest uruchomiony.

**Pytania. W oknie interaktywnym języka R jest wyświetlana informacja, że komputer zdalny jest włączony, ale dlaczego usługa nie jest uruchomiona?**

Istnieją trzy możliwe przyczyny:

- Na komputerze nie zainstalowano [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub nowszego.
- Reguły zapory dla `Microsoft.R.Host.Broker` i `Microsoft.R.Host` nie są włączone dla połączeń przychodzących i wychodzących na porcie 5444.
- Certyfikat SSL z programem `CN=<remote-machine-name>` nie został zainstalowany.

Uruchom ponownie komputer po wprowadzeniu któregokolwiek z powyższych zmian. Następnie upewnij się, `RHostBrokerService` że `RUserProfileService` są one uruchomione za pomocą Menedżera zadań (usług karta) lub *Services. msc*.

**Pytania. Dlaczego okno programu R Interactive powiedzie "401 Odmowa dostępu" podczas nawiązywania połączenia z serwerem R?**

Istnieją dwie możliwe przyczyny:

- Wysoce istnieje duże ryzyko, że `NETWORK SERVICE` konto nie ma dostępu do klucza prywatnego certyfikatu SSL. Postępuj zgodnie z wcześniejszymi instrukcjami, aby udzielić `NETWORK SERVICE` dostępu do klucza prywatnego.
- Upewnij się, że `seclogon` Usługa jest uruchomiona. Użyj programu *Services. msc* , aby skonfigurować program `seclogon` do automatycznego uruchamiania.

**Pytania. Dlaczego po nawiązaniu połączenia z serwerem R nie znaleziono okna interaktywnego języka R "404"?**

Ten błąd jest prawdopodobnie spowodowany brakiem Visual C++ bibliotek redystrybucyjnych. Zapoznaj się z oknem R Interactive, aby sprawdzić, czy jest wyświetlany komunikat dotyczący brakującej biblioteki (DLL). Następnie sprawdź, czy zainstalowano pakiet redystrybucyjny programu VS 2015 i że masz również zainstalowany język R.

**Pytania. Nie mogę uzyskać dostępu do Internetu/zasobu z okna interaktywnego języka R, co mam zrobić?**

Upewnij się, że reguły zapory dla `Microsoft.R.Host.Broker` i `Microsoft.R.Host` zezwalają na dostęp wychodzący na porcie 5444. Po zastosowaniu zmian Uruchom ponownie komputer.

**Pytania. Wszystkie te rozwiązania zostały wypróbowane i nadal nie działa. Co teraz?**

Przejrzyj pliki dziennika w *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Ten folder zawiera osobne pliki dziennika dla każdego wystąpienia usługi programu R Broker, która została uruchomiona. Nowy plik dziennika jest tworzony za każdym razem, gdy usługa zostanie ponownie uruchomiona. Zapoznaj się z najnowszym plikiem dziennika, aby uzyskać wskazówki dotyczące tego, co może być błędne.
