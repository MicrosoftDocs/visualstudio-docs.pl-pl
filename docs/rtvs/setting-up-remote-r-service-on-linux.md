---
title: Konfigurowanie zdalnego usługi języka R w systemie Linux
description: Jak skonfigurować zdalnej usługi języka R na platformach Ubuntu i podsystemu Windows dla systemu Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 3fd7f8be7b2de02fb89c9eec3ea7859241beb0f2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945823"
---
# <a name="remote-r-service-for-linux"></a>Usługa zdalnego języka R dla systemu Linux

Usługa zdalnego języka R dla systemu Linux jest obecnie dostarczana w rtvs demon. Demon jest obsługiwana i testowane na Ubuntu 16.04 16.10 pulpitu LTS, serwera i podsystemu Windows dla systemu Linux z systemem Ubuntu. Duża część tego artykułu zawiera instrukcje dotyczące konfigurowania zdalnej usługi języka R w różnych systemach.

Po skonfigurowaniu komputera zdalnego następujące kroki nawiązać R Tools for Visual Studio (RTVS) tej usługi:

1. Wybierz **R Tools** > **Windows** > **obszary robocze** otworzyć **obszary robocze** okna.
1. Wybierz **Dodaj połączenie**.
1. Nadaj nazwę połączenia i podaj adres URL, taki jak `https://localhost:5444` (podsystem Windows dla systemu Linux) lub `https://public-ip:5444` (kontenera platformy Azure). Wybierz **Zapisz** po zakończeniu.
1. Wybierz ikonę połączenia lub kliknij dwukrotnie element połączenie.
1. Podaj poświadczenia logowania. Nazwa użytkownika musi być poprzedzona znakiem `<<unix>>\` jak `<<unix>>\ruser1` (co jest wymagane dla wszystkich połączeń z komputerami zdalnymi z systemem Linux).
1. Jeśli używasz certyfikatu z podpisem własnym, może pojawić się ostrzeżenie. Komunikat zawiera instrukcje, aby poprawić to ostrzeżenie.

## <a name="set-up-remote-r-service"></a>Konfigurowanie zdalnego usługi języka R

W tej sekcji opisano następujące opcje:

- [Komputer fizyczny Ubuntu](#physical-ubuntu-computer)
- [Serwer Ubuntu maszyny Wirtualnej lub maszyny Wirtualnej na platformie Azure do analizy danych](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Lokalnym lub zdalnym kontenerze platformy Docker (czysta Kompilacja)](#local-or-remote-docker-container-clean-build)
- [Kontenera uruchomionego w usłudze Azure Container Instances](#container-running-on-azure-container-instances)

W każdym przypadku komputera zdalnego musi mieć jedną z następujących interpreterów języka R, zainstalowane:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [R CRAN dla Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Komputer fizyczny Ubuntu

1. Po zalogowaniu się do komputera, pobierania pliku tar demona rtvs:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Uruchom skrypt instalacji:

    ```bash
    sudo ./rtvs-install
    ```

    Dyskretnej automatyzacji, można użyć `sudo ./rtvs-install -s`.

1. Włącz i uruchom usługę:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Konfigurowanie certyfikatu SSL (wymagane dla trybu produkcyjnego). Domyślnie używa demona rtvs `ssl-cert-snakeoil.pem` i `ssl-cert-snakeoil.pem` generowane przez `ssl-cert` pakietu. Podczas instalacji są łączone w `ssl-cert-snakeoil.pfx`. Do celów produkcyjnych należy używać certyfikatu SSL dostarczonego przez administratora. Certyfikat SSL można skonfigurować, zapewniając *PFX* pliku i hasło opcjonalny import w: */etc/rtvs/rtvsd.config.json*.

1. (Opcjonalnie) Upewnij się, że usługa jest uruchomiona:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Jeśli nie widzisz proces uruchomiony przy użyciu nazwy użytkownika `rtvssvc`. Uruchom za pomocą następującego polecenia:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Aby skonfigurować dalsze demona rtvs, zobacz `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Serwer Ubuntu maszyny Wirtualnej lub maszyny Wirtualnej na platformie Azure do analizy danych

#### <a name="create-a-vm"></a>Tworzenie maszyny wirtualnej

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com).
1. Przejdź do maszyn wirtualnych, a następnie wybierz **Dodaj**.
1. Na liście dostępnych obrazów maszyn wirtualnych Wyszukaj i wybierz jedną z następujących czynności:
    - Serwer Ubuntu: `Ubuntu Server 16.04 LTS`
    - Maszyny Wirtualnej analizy danych: `Linux Data Science` (zobacz [maszyn wirtualnych do nauki o danych](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) szczegóły)
1. Ustaw modelu wdrażania przy użyciu `Resource manager` i wybierz **Utwórz**.
1. Wybierz nazwę maszyny wirtualnej, podaj nazwę użytkownika i hasło (wymagane jest hasło, jako protokół SSH publicznego klucza logowania nie jest obsługiwane).
1. Wprowadź inne żądane zmiany w konfiguracji maszyny Wirtualnej.
1. Wybieranie rozmiaru maszyny Wirtualnej, sprawdź konfigurację, a następnie wybierz **Utwórz**. Po utworzeniu maszyny Wirtualnej, przejdź do następnej sekcji.

#### <a name="configure-the-vm"></a>Konfigurowanie maszyny Wirtualnej

1. Na maszynie wirtualnej **sieć** Dodaj 5444 jako port dozwolony dla ruchu przychodzącego. Aby użyć innego portu, zmień ustawienie w pliku konfiguracji demona RTVS (*/etc/rtvs/rtvsd.config.json*).
1. (Opcjonalnie) Ustaw nazwę DNS; można także użyć adresu IP.
1. Łączenie z maszyną wirtualną przy użyciu klienta SSH, takiego jak PuTTY dla systemu WIndows.
1. Postępuj zgodnie z instrukcjami dotyczącymi [komputera fizycznego w systemie Ubuntu](#physical-ubuntu-computer) powyżej.

### <a name="windows-subsystem-for-linux-wsl"></a>Podsystem Windows dla systemu Linux (WSL)

1. Postępuj zgodnie z instrukcjami instalacji WSL dla dowolnego [systemu Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) lub [systemu Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Uruchom powłokę bash na Windows i postępuj zgodnie z instrukcjami wcześniej [komputera fizycznego w systemie Ubuntu](#physical-ubuntu-computer) z jednym wyjątkiem. W kroku 3, uruchom usługę za pomocą polecenia `rtvsd`zamiast ponieważ WSL aktualnie nie obsługuje interfejsów systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Lokalnym lub zdalnym kontenerze platformy Docker (czysta Kompilacja)

1. Utwórz plik Docker przy użyciu poniższych zawartości instalująca demona usługa zdalnego języka R i najnowszą wersję języka R. **Uwaga**: ten skrypt tworzy użytkownika o nazwie "ruser1" hasło "foobar", którą można modyfikować zgodnie z potrzebami w końcowe dwóch `RUN` instrukcji.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Kompilowanie i uruchamianie pliku platformy docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Aby nawiązać połączenie zawiera z RTVS, użyj `https://localhost:5444` jako ścieżka, nazwa użytkownika `<<unix>>\ruser1`i hasło `foobar`. Jeśli kontener jest uruchomiony na komputerze zdalnym, należy użyć `https://remote-host-name:5444` jako ścieżkę zamiast tego. Numer portu można zmienić, aktualizując */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Kontenera uruchomionego w usłudze Azure Container Instances

1. Postępuj zgodnie z instrukcjami w [lokalnym lub zdalnym kontenerze platformy Docker (czysta Kompilacja)](#local-or-remote-docker-container-clean-build) do utworzenia obrazu.
1. Wypchnij kontenera do usługi Docker hub lub Azure repozytorium kontenerów.
1. Uruchom interfejs wiersza polecenia platformy Azure i zaloguj się przy użyciu `az login` polecenia.
1. Użyj `az container create` polecenie, aby utworzyć kontener, za pomocą `--command-line "rtvsd"` , jeśli nie zdefiniowano kontenera Uruchom `rtvsd` jako `systemd` usługi. W poniższym poleceniu obraz powinien znajdować się w usłudze Docker hub. Umożliwia także repozytorium kontenerów platformy Azure, dodając repozytorium kontenerów poświadczeń argumentów do wiersza polecenia.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```
1. Użyj `az container list` polecenie, aby sprawdzić stan. Wyszukaj `provisioningState`: `Succeeded`.
1. Jeśli aprowizacja została wykonana pomyślnie, teraz można podłączyć do kontenera. Znajdź publiczny adres IP w `ipAddress` pola, które są używane przy użyciu poświadczeń w pliku platformy docker do łączenia się do kontenera z RTVS.
