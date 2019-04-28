---
title: Zdalne obszary robocze dla języka R
description: Jak skonfigurować zdalne R obszary robocze i połączyć je z programu Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 0263afa4eeb9094802fe6272380b6b53106da4a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810199"
---
# <a name="set-up-remote-workspaces"></a>Konfigurowanie zdalnych obszarów roboczych

W tym artykule opisano sposób konfigurowania serwera zdalnego przy użyciu protokołu SSL oraz odpowiednie usługi języka R. Dzięki temu R Tools for Visual Studio (RTVS) aby nawiązać połączenie zdalne obszaru roboczego na tym serwerze.

## <a name="remote-computer-requirements"></a>Wymagania dotyczące komputera zdalnego

- Systemu Windows 10, Windows Server 2016 lub Windows Server 2012 R2. Wymaga również RTVS
- [Program .NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub nowszej

## <a name="install-an-ssl-certificate"></a>Zainstaluj certyfikat SSL

RTVS wymaga, że cała komunikacja z serwerem zdalnym się stanie, za pośrednictwem protokołu HTTP, który wymaga certyfikatu SSL na serwerze. Można użyć certyfikatu podpisanego przez zaufany urząd certyfikacji (zalecane) lub certyfikatu z podpisem własnym. (Certyfikat z podpisem własnym powoduje, że RTVS ostrzeżenia problem po podłączeniu.) Za pomocą pojedynczo należy następnie zainstaluj go na komputerze i zezwolić na dostęp do jego klucz prywatny.

### <a name="obtain-a-trusted-certificate"></a>Uzyskanie zaufanego certyfikatu

Zaufany certyfikat jest wystawiony przez urząd certyfikacji (zobacz [certyfikatów urzędów w witrynie Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) tła). Uzyskiwanie karty identyfikacyjne dla instytucji rządowych, np. wystawienie certyfikatu zaufanego obejmuje więcej procesów i ewentualne opłaty, ale sprawdza autentyczności żądania i osoby zgłaszającej żądanie.

Pole klucza, który musi być w certyfikacie jest w pełni kwalifikowana nazwa domeny dla komputera z programem R server. Urząd certyfikacji wymaga dowód, że masz uprawnienia do utworzenia nowego serwera dla domeny, do której należy serwer.

Aby uzyskać więcej informacji, zobacz [certyfikatów kluczy publicznych](https://en.wikipedia.org/wiki/Public_key_certificate) w witrynie Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Zainstaluj certyfikat SSL na Windows

Certyfikat SSL musi zostać zainstalowany ręcznie na Windows. Postępuj zgodnie z poniższymi instrukcjami, aby zainstalować certyfikat protokołu SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Uzyskiwanie certyfikatu z podpisem własnym (Windows)

Pomiń tę sekcję, jeśli masz zaufanego certyfikatu. W porównaniu z certyfikatu z zaufanego urzędu certyfikatu z podpisem własnym przypomina tworzenie karty identyfikacyjne dla siebie. Ten proces jest oczywiście znacznie prostsze niż praca z zaufanego urzędu, ale również nie ma silnego uwierzytelniania, co oznacza, że atakujący może zastąpić certyfikatów dla certyfikatu bez znaku i przechwytywać cały ruch między klientem a serwer. W związku z tym *certyfikatu z podpisem własnym należy używać w tylko w przypadku testowania scenariuszy, w zaufanej sieci i nigdy nie w środowisku produkcyjnym.*

Z tego powodu RTVS zawsze generuje następujące ostrzeżenie podczas nawiązywania połączenia z serwerem przy użyciu certyfikatu z podpisem własnym:

![Okno dialogowe z ostrzeżeniem certyfikatu z podpisem własnym](media/workspaces-remote-self-signed-certificate-warning.png)

Do wystawiania certyfikatu z podpisem własnym:

1. Zaloguj się do komputera z R server przy użyciu konta administratora.
1. Otwórz nowy wiersz polecenia programu PowerShell administratora i wydać następujące polecenie, zastępując `"remote-machine-name"` z w pełni kwalifikowana nazwa domeny komputera serwera.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Jeśli na komputerze serwera R nigdy nie uruchomiono programu PowerShell przed, uruchom następujące polecenie, aby umożliwić wykonywanie poleceń jawnie:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Aby uzyskać ogólne, zobacz [certyfikaty z podpisem własnym](https://en.wikipedia.org/wiki/Self-signed_certificate) w witrynie Wikipedia.

### <a name="install-the-certificate"></a>Instalowanie certyfikatu

Aby zainstalować certyfikat na komputerze zdalnym, uruchom *certlm.msc* (Menedżer certyfikatów) z wiersza polecenia. Kliknij prawym przyciskiem myszy **osobistych** i wybierz polecenie **wszystkie zadania** > **importu** polecenia:

![Polecenie certyfikatu importu](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Udziel uprawnień do odczytu klucza prywatnego certyfikatu SSL

Po zaimportowaniu certyfikatu udzielić `NETWORK SERVICE` konta z uprawnieniami do odczytu klucza prywatnego, zgodnie z opisem w poniższych instrukcjach. `NETWORK_SERVICE` to konto służy do uruchamiania broker usługi R Services, która to usługa, która kończy przychodzące połączenia SSL z komputerem serwera.

1. Uruchom *certlm.msc* (Menedżer certyfikatów) z wiersza polecenia z uprawnieniami administratora.
1. Rozwiń **osobistych** > **certyfikaty**, kliknij certyfikat prawym przyciskiem myszy i wybierz **wszystkie zadania** > **Zarządzanie prywatne Klucze**.
1. Kliknij prawym przyciskiem myszy certyfikat i wybierz pozycję **Zarządzaj kluczami prywatnymi** polecenia w obszarze **wszystkie zadania**.
1. W wyświetlonym oknie dialogowym wybierz **Dodaj** i wprowadź `NETWORK SERVICE` jako nazwa konta:

    ![Okno dialogowe kluczy prywatnych, dodanie usługi NETWORK_SERVICE Zarządzanie](media/workspaces-remote-manage-private-key-dialog.png)

1. Wybierz **OK** dwa razy, aby zamknąć okna dialogowe, a następnie Zatwierdź zmiany.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Zainstaluj certyfikat SSL w systemie Ubuntu

`rtvs-daemon` Pakiet zostanie zainstalowany certyfikat z podpisem własnym domyślnie jako część instalacji.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Uzyskiwanie certyfikatu z podpisem własnym (Ubuntu)

Zalety i wady używania certyfikatu z podpisem własnym dla opis Windows. `rtvs-daemon` Pakietu generuje i umożliwia skonfigurowanie certyfikatu z podpisem własnym podczas instalacji. Należy to zrobić tylko wtedy, gdy chcesz zastąpić automatycznie wygenerowany certyfikat z podpisem własnym.

Aby samodzielnie wystawiania certyfikatu z podpisem własnym:

1. SSH lub logowanie na maszynie z systemem Linux.
2. Zainstaluj `ssl-cert` pakietu:

    ```sh
    sudo apt-get install ssl-cert
    ```

3. Uruchom `make-ssl-cert` do wygenerowania certyfikatu SSL z podpisem własnym domyślne:

    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```

4. Konwertuj wygenerowany klucz i pliki PEM do pliku PFX. Wygenerowany plik PFX powinna być w folderze głównym:

    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Skonfiguruj demona RTVS

Ścieżka pliku certyfikatu SSL (ścieżka do pliku PFX) musi być ustawiona w */etc/rtvs/rtvsd.config.json*. Aktualizacja `X509CertificateFile` i `X509CertificatePassword` przy użyciu ścieżki pliku i hasła odpowiednio.

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

Zapisz plik i ponownie uruchom demona, `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Zainstaluj usługi języka R na Windows

Aby uruchomić kod języka R, komputer zdalny musi mieć interpreter języka R zainstalować na następujące sposoby:

1. Pobierz i zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [R CRAN dla Windows](https://cran.r-project.org/bin/windows/base/)

     Mają identyczną funkcjonalność, ale Microsoft R Open korzyści związane z dodatkowego sprzętu accelerated bibliotek algebry liniowej dzięki uprzejmości [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl).

2. Uruchom [Instalatora usługi R Services](https://aka.ms/rtvs-services) i uruchom ponownie po wyświetleniu monitu. Instalator wykonuje następujące czynności:

    - Utwórz folder w *%PROGRAMFILES%\R Tools for Visual Studio\1.0\\*  i skopiuj wszystkie wymagane pliki binarne.
    - Zainstaluj `RHostBrokerService` i `RUserProfileService` i skonfigurować do automatycznego uruchamiania.
    - Konfigurowanie `seclogon` automatyczne uruchamianie usługi.
    - Dodaj *Microsoft.R.Host.exe* i *Microsoft.R.Host.Broker.exe* do zapory reguły dla ruchu przychodzącego na domyślnym porcie 5444.

Usługi języka R jest uruchamiana automatycznie przy ponownym uruchomieniu komputera:

- **Usługa Broker hosta R** obsługuje cały ruch HTTPS między Visual Studio i procesem, w którym jest uruchamiany kod R na komputerze.
- **Usługa profilu użytkownika R** jest składnikiem uprzywilejowanych, który obsługuje tworzenie profilu użytkownika Windows. Usługa jest wywoływana, gdy nowy użytkownik najpierw loguje się do komputera z R server.

Możesz zobaczyć te usługi w konsoli zarządzania usługami (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Instalowanie usługi R Services w systemie Linux

Aby uruchomić kod języka R, komputer zdalny musi mieć interpreter języka R zainstalować na następujące sposoby:

1. Pobierz i zainstaluj jedną z następujących czynności:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [R CRAN dla Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Mają identyczną funkcjonalność, ale Microsoft R Open korzyści związane z dodatkowego sprzętu accelerated bibliotek algebry liniowej dzięki uprzejmości [biblioteki jądra matematyczne Intel](https://software.intel.com/intel-mkl).

2. Postępuj zgodnie z instrukcjami [usługa zdalnego języka R dla systemu Linux](setting-up-remote-r-service-on-linux.md), która obejmuje komputery fizyczne Ubuntu maszyn wirtualnych platformy Azure Ubuntu, podsystem Windows dla systemu Linux (WSL) i kontenerów platformy Docker, łącznie z uruchomionymi na repozytorium kontenerów platformy Azure.

## <a name="configure-r-services"></a>Konfigurowanie usługi języka R

Z usługami R services uruchomiony na komputerze zdalnym możesz również muszą tworzyć konta użytkowników, ustawianie reguł zapory, konfigurowanie sieci platformy Azure i konfigurowanie certyfikatu SSL.

1. Konta użytkowników: Tworzenie kont dla każdego użytkownika, który uzyskuje dostęp do komputera zdalnego. Można tworzyć konta albo lokalnego użytkownika standardowego (nieuprzywilejowany) lub Dołącz do komputera z programem R server do domeny i Dodaj grupy zabezpieczeń odpowiednich do `Users` grupy zabezpieczeń.

1. Reguły zapory: Domyślnie `R Host Broker` nasłuchuje na porcie TCP 5444. W związku z tym, upewnij się, że Windows włączonych reguł zapory dla ruchu przychodzącego i wychodzącego (ruchu wychodzącego jest niezbędne do instalowania pakietów i podobne scenariusze).  Instalator usług języka R Określa, że te reguły automatycznie dla wbudowanej zapory Windows. Jeśli używasz zapory innych firm, otwórz port 5444 `R Host Broker` ręcznie.

1. Konfiguracja platformy Azure: Jeśli komputer zdalny jest maszyną wirtualną na platformie Azure, należy otworzyć port 5444 dla ruchu przychodzącego w obrębie platformy Azure, jak również sieci, który jest niezależny od zapory Windows. Aby uzyskać więcej informacji, zobacz [filtrowanie ruchu sieciowego z sieciową grupą zabezpieczeń](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) w dokumentacji platformy Azure.

1. Powiedz brokera hosta R certyfikatu SSL, który można załadować: Jeśli instalujesz certyfikat na serwerze sieci Intranet, jest prawdopodobne, że w pełni kwalifikowana nazwa domeny serwera jest taka sama jak jego nazwa NETBIOS. W takim przypadku nie ma nic, należy wykonać, ponieważ jest to domyślny certyfikat, który jest ładowany.

    Jednakże jeśli certyfikat jest instalowany na serwerze dostępnym z Internetu (na przykład w przypadku maszyn wirtualnych platformy Azure), użyć w pełni kwalifikowana nazwa domeny (FQDN) serwera, ponieważ nazwę FQDN serwera dostępnego z Internetu nigdy nie jest taka sama jak jego nazwa NETBIOS.

    Użyj nazwy FQDN, przejdź na którym zainstalowano usługi języka R (*% PROGRAM FILES%\R usługi zdalnej dla Visual Studio\1.0* domyślnie), otwórz *Microsoft.R.Host.Broker.Config.json* plik w edytorze tekstu i zastąp jego zawartość następujących, przypisywanie CN można niezależnie od serwera w pełni kwalifikowaną nazwę domeny, takich jak `foo.westus.cloudapp.azure.com`:

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

**PYTANIA I ODPOWIEDZI. Nie odpowiada na komputerze serwera R, co należy zrobić?**

Spróbuj wysłać polecenie ping z komputera zdalnego z poziomu wiersza polecenia: `ping remote-machine-name`. Jeśli polecenie ping nie powiedzie się, upewnij się, że na komputerze jest uruchomiony.

**PYTANIA I ODPOWIEDZI. Okno interaktywne języka R jest wyświetlany komunikat, znajduje się na komputerze zdalnym, ale Dlaczego usługa nie działa?**

Istnieją trzy możliwe przyczyny:

- [Program .NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) lub większa nie jest zainstalowany na komputerze.
- Reguły zapory dla `Microsoft.R.Host.Broker` i `Microsoft.R.Host` nie są włączone dla połączeń przychodzących i wychodzących na porcie 5444.
- Certyfikat SSL z `CN=<remote-machine-name>` nie został zainstalowany.

Uruchom ponownie komputer po wykonaniu dowolnej z powyższych zmian. Następnie upewnij się, że `RHostBrokerService` i `RUserProfileService` są uruchomione przy użyciu albo Menedżera zadań (karta usługi) lub *services.msc*.

**PYTANIA I ODPOWIEDZI. Dlaczego oknie interaktywnym r. wskazuje "401 Odmowa dostępu" podczas nawiązywania połączenia z serwerem R?**

Istnieją dwie możliwe przyczyny:

- Istnieje duże prawdopodobieństwo, że `NETWORK SERVICE` konto nie ma dostępu do klucza prywatnego certyfikatu SSL. Postępuj zgodnie z instrukcjami wcześniej, aby udzielić `NETWORK SERVICE` dostęp do klucza prywatnego.
- Upewnij się, że `seclogon` usługa jest uruchomiona. Użyj *services.msc* skonfigurować `seclogon` do automatycznego uruchamiania.

**PYTANIA I ODPOWIEDZI. Dlaczego oknie interaktywnym r. wskazuje "404 Nie znaleziono" podczas nawiązywania połączenia z serwerem R?**

Ten błąd jest prawdopodobnie z powodu braku redystrybucyjnych bibliotek Visual C++. Sprawdź okno interaktywne języka R, aby zobaczyć, czy wiadomość dotyczącą brakujących Biblioteka (DLL). Następnie sprawdź zainstalowanie programu VS 2015 redistributable i czy masz także zainstalowania języka.

**PYTANIA I ODPOWIEDZI. Nie mam dostępu do Internetu lub zasobu w oknie interaktywnym r., co należy zrobić?**

Upewnij się, że Zapora reguł dla `Microsoft.R.Host.Broker` i `Microsoft.R.Host` Zezwalaj na dostęp ruchu wychodzącego na porcie 5444. Po wprowadzeniu zmian, należy ponownie uruchomić komputer.

**PYTANIA I ODPOWIEDZI. Podejmowano tych rozwiązań, a to nie zadziała. Co teraz?**

Szukaj w plikach dziennika w *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Ten folder zawiera osobne pliki dziennika dla każdego wystąpienia usługi Broker języka R, która została uruchomiona. Nowy plik dziennika jest tworzony, zawsze wtedy, gdy usługa jest uruchamiana ponownie. Sprawdź najnowszy plik dziennika dla wskazówek dotyczących co może być pójdzie.
