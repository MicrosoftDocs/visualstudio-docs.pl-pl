---
title: Konfigurowanie usługi Zdalne R w systemie Linux
description: Jak skonfigurować usługę Remote R na Ubuntu i podsystemie Windows dla Systemu Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809560"
---
# <a name="remote-r-service-for-linux"></a>Usługa zdalnego języka R dla systemu Linux

Usługa Zdalnego R dla Linuksa jest obecnie pakowany jako rtvs-daemon. Demon jest obsługiwany i testowany na Ubuntu 16.04, 16.10 LTS pulpitu, serwera i podsystemu Windows dla Linuksa z systemem Ubuntu. Większość tego artykułu zawiera instrukcje dotyczące konfigurowania usługi zdalnego r w tych różnych systemach.

Po skonfigurowaniu komputera zdalnego następujące kroki łączą narzędzia R dla programu Visual Studio (RTVS) z tą usługą:

1. Wybierz **pozycję Narzędzia** > R Obszary**robocze systemu** **Windows,** > aby otworzyć okno Obszary **robocze.**
1. Wybierz **pozycję Dodaj połączenie**.
1. Nadaj nazwie connect i podaj jej adres URL, taki jak `https://localhost:5444` (Podsystem windows dla systemu Linux) lub `https://public-ip:5444` (kontener platformy Azure). Wybierz **pozycję Zapisz** po zakończeniu.
1. Wybierz ikonę połączenia lub kliknij dwukrotnie element połączenia.
1. Podaj dane logowania. Nazwa użytkownika musi być `<<unix>>\` poprzedzony jak w `<<unix>>\ruser1` (zgodnie z wymaganiami dla wszystkich połączeń z komputerami zdalnymi systemu Linux).
1. Jeśli używasz certyfikatu z podpisem własnym, może zostać wyświetlone ostrzeżenie. Komunikat zawiera instrukcje, aby poprawić ostrzeżenie.

## <a name="set-up-remote-r-service"></a>Konfigurowanie usługi zdalnego r

W tej sekcji opisano następujące opcje:

- [Komputer Fizyczny Ubuntu](#physical-ubuntu-computer)
- [Maszyna wirtualna serwera Ubuntu lub maszyna wirtualna do nauki o danych na platformie Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Lokalny lub zdalny kontener platformy Docker (czysta kompilacja)](#local-or-remote-docker-container-clean-build)
- [Kontener uruchomiony w wystąpieniach kontenera platformy Azure](#container-running-on-azure-container-instances)

W każdym przypadku komputer zdalny musi mieć zainstalowany jeden z następujących interpreterów R:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Komputer Fizyczny Ubuntu

1. Po zalogowaniu się do komputera, pobierz rtvs-daemon tarball:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Uruchom skrypt instalacji:

    ```bash
    sudo ./rtvs-install
    ```

    Aby uzyskać cichą automatyzację, użyj `sudo ./rtvs-install -s`.

1. Włącz i uruchom usługę:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Skonfiguruj certyfikat SSL (wymagany do produkcji). Domyślnie rtvs-daemon używa `ssl-cert-snakeoil.pem` i `ssl-cert-snakeoil.pem` generowane `ssl-cert` przez pakiet. Podczas instalacji są one `ssl-cert-snakeoil.pfx`łączone w . Do celów produkcyjnych należy użyć certyfikatu SSL dostarczonego przez administratora. Certyfikat SSL można skonfigurować, udostępniając plik *.pfx* i opcjonalne hasło importu w: */etc/rtvs/rtvsd.config.json*.

1. (Opcjonalnie) Sprawdź, czy usługa jest uruchomiona:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Jeśli nie widzisz procesu uruchomionego pod `rtvssvc`nazwą użytkownika . Uruchom go za pomocą następującego polecenia:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Aby jeszcze bardziej skonfigurować demon rtvs, zobacz `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Maszyna wirtualna serwera Ubuntu lub maszyna wirtualna do nauki o danych na platformie Azure

#### <a name="create-a-vm"></a>Tworzenie maszyny wirtualnej

1. Zaloguj się do [Portalu Azure](https://portal.azure.com).
1. Przejdź do pozycji Maszyny wirtualne, a następnie wybierz pozycję **Dodaj**.
1. Na liście dostępnych obrazów maszyn wirtualnych wyszukaj i wybierz jedną z następujących opcji:
    - Serwer Ubuntu:`Ubuntu Server 16.04 LTS`
    - Maszyna wirtualna `Linux Data Science` do nauki o danych: (szczegółowe informacje można znaleźć na [maszynach wirtualnych do nauki o danych)](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)
1. Ustaw model wdrażania `Resource manager` i wybierz pozycję **Utwórz**.
1. Wybierz nazwę maszyny Wirtualnej, podaj nazwę użytkownika i hasło (hasło jest wymagane, ponieważ logowanie klucza publicznego SSH nie jest obsługiwane).
1. Wprowadzać inne żądane zmiany w konfiguracji maszyny Wirtualnej.
1. Wybierz rozmiar maszyny Wirtualnej, sprawdź konfigurację i wybierz pozycję **Utwórz**. Po utworzeniu maszyny Wirtualnej przejdź do następnej sekcji.

#### <a name="configure-the-vm"></a>Konfigurowanie maszyny wirtualnej

1. W sekcji Sieć maszyny **Wirtualnej** dodaj 5444 jako dozwolony port przychodzący. Aby użyć innego portu, zmień ustawienie w pliku konfiguracyjny demona RTVS (*/etc/rtvs/rtvsd.config.json*).
1. (Opcjonalnie) Ustawianie nazwy DNS; można również użyć adresu IP.
1. Połącz się z maszyną wirtualną przy użyciu klienta SSH, takiego jak PuTTY for WIndows.
1. Postępuj zgodnie z instrukcjami dotyczącymi [komputera Ubuntu powyżej.](#physical-ubuntu-computer)

### <a name="windows-subsystem-for-linux-wsl"></a>Podsystem Windows dla systemu Linux (WSL)

1. Postępuj zgodnie z instrukcjami instalacji WSL dla [systemu Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) lub [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Rozpocznij bash w systemie Windows i postępuj zgodnie z wcześniejszymi instrukcjami [komputer Ubuntu fizyczne](#physical-ubuntu-computer) z jednym wyjątkiem. W kroku 3 uruchom usługę `rtvsd`za pomocą polecenia, ponieważ WSL obecnie nie obsługuje interfejsów systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Lokalny lub zdalny kontener platformy Docker (czysta kompilacja)

1. Utwórz plik platformy Docker z poniższą zawartością, który instaluje demona usługi Remote R i najnowszą wersję R. **Uwaga:** ten skrypt tworzy użytkownika o nazwie `RUN` "ruser1" z hasłem "foobar", które można zmodyfikować zgodnie z potrzebami w ostatnich dwóch instrukcji.

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

1. Tworzenie i uruchamianie pliku docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Aby połączyć się z plikami z RTVS, użyj `https://localhost:5444` jako ścieżki, nazwy użytkownika `<<unix>>\ruser1`i hasła `foobar`. Jeśli kontener jest uruchomiony na komputerze `https://remote-host-name:5444` zdalnym, użyj jako ścieżki. Port można zmienić, aktualizując */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Kontener uruchomiony w wystąpieniach kontenera platformy Azure

1. Postępuj zgodnie z instrukcjami w [lokalnym lub zdalnym kontenerze platformy Docker (czysta kompilacja),](#local-or-remote-docker-container-clean-build) aby utworzyć obraz.
1. Wypchnij kontener do centrum platformy Docker lub repozytorium kontenerów platformy Azure.
1. Uruchom interfejsu wiersza polecenia `az login` platformy Azure i zaloguj się przy użyciu polecenia.
1. Użyj `az container create` polecenia, aby utworzyć `--command-line "rtvsd"` kontener, używając, jeśli nie `rtvsd` skonfigurować `systemd` kontenera do uruchomienia jako usługa. W poniższym poleceniu obraz ma znajdować się w centrum platformy Docker. Można również użyć repozytorium kontenerów platformy Azure, dodając argumenty poświadczeń repozytorium kontenerów do wiersza polecenia.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Użyj `az container list` polecenia, aby sprawdzić stan. Poszukaj `provisioningState`: `Succeeded`.
1. Jeśli inicjowanie obsługi administracyjnej powiodło się, można teraz połączyć się z kontenerem. Poszukaj publicznego adresu `ipAddress` IP w polu, którego używasz z poświadczeniami w pliku docker, aby połączyć się z kontenerem z RTVS.
