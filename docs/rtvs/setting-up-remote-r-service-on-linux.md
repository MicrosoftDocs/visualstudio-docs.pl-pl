---
title: Konfigurowanie zdalnej usługi R w systemie Linux
description: Jak skonfigurować zdalną usługę R w systemie Ubuntu i podsystem Windows dla systemu Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 586f3038ff4bb091fb99160d7965ad927eda070a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851819"
---
# <a name="remote-r-service-for-linux"></a>Usługa zdalnego języka R dla systemu Linux

Usługa zdalnego języka R dla systemu Linux jest obecnie spakowana jako demon RTVS. Demon jest obsługiwany i testowany na Ubuntu 16,04, 16,10 LTS Desktop, serwer i podsystem Windows dla systemu Linux z systemem Ubuntu. Ten artykuł zawiera instrukcje dotyczące konfigurowania zdalnej usługi R w tych różnych systemach.

Po skonfigurowaniu maszyny zdalnej wykonaj następujące kroki, aby połączyć R Tools for Visual Studio (RTVS) z tą usługą:

1. Wybierz pozycję **R Tools**  >  **Windows**  >  **Workspaces** , aby otworzyć okno **obszary robocze** .
1. Wybierz pozycję **Dodaj połączenie**.
1. Nadaj nazwę Connect a i podaj jej adres URL, na przykład `https://localhost:5444` (podsystem Windows dla systemu Linux) lub `https://public-ip:5444` (kontener platformy Azure). Wybierz pozycję **Zapisz** po zakończeniu.
1. Wybierz ikonę połączenia lub kliknij dwukrotnie element połączenie.
1. Podaj poświadczenia logowania. Nazwa użytkownika musi być poprzedzona znakiem `<<unix>>\` AS `<<unix>>\ruser1` (zgodnie z wymaganiami dla wszystkich połączeń z komputerami zdalnymi z systemem Linux).
1. Jeśli używasz certyfikatu z podpisem własnym, może zostać wyświetlone ostrzeżenie. Komunikat zawiera instrukcje umożliwiające poprawienie ostrzeżenia.

## <a name="set-up-remote-r-service"></a>Skonfiguruj zdalną usługę R

W tej sekcji opisano następujące opcje:

- [Fizyczny komputer Ubuntu](#physical-ubuntu-computer)
- [Maszyna wirtualna serwera Ubuntu lub Data Science VM na platformie Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Lokalny lub zdalny kontener platformy Docker (czysta Kompilacja)](#local-or-remote-docker-container-clean-build)
- [Kontener uruchomiony w Azure Container Instances](#container-running-on-azure-container-instances)

W każdym przypadku komputer zdalny musi mieć zainstalowany jeden z następujących interpreterów języka R:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R dla systemu Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fizyczny komputer Ubuntu

1. Po zalogowaniu się na komputerze Pobierz RTVS demona plik tar:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Uruchom skrypt instalacyjny:

    ```bash
    sudo ./rtvs-install
    ```

    W przypadku automatyzacji dyskretnej Użyj `sudo ./rtvs-install -s` .

1. Włącz i uruchom usługę:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Skonfiguruj certyfikat SSL (wymagany dla środowiska produkcyjnego). Domyślnie demon RTVS używa `ssl-cert-snakeoil.pem` i jest `ssl-cert-snakeoil.pem` generowany przez `ssl-cert` pakiet. Podczas instalacji są one łączone w `ssl-cert-snakeoil.pfx` . W celach produkcyjnych Użyj certyfikatu SSL dostarczonego przez administratora. Certyfikat SSL można skonfigurować, podając plik *PFX* i opcjonalne hasło importu w programie: */etc/RTVS/rtvsd.config.json*.

1. Obowiązkowe Sprawdź, czy usługa jest uruchomiona:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Jeśli nie widzisz procesu działającego w ramach nazwy użytkownika `rtvssvc` . Uruchom go za pomocą następującego polecenia:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Aby dodatkowo skonfigurować demona RTVS, zobacz `man rtvsd` .

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Maszyna wirtualna serwera Ubuntu lub Data Science VM na platformie Azure

#### <a name="create-a-vm"></a>Tworzenie maszyny wirtualnej

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com).
1. Przejdź do Virtual Machines, a następnie wybierz pozycję **Dodaj**.
1. Na liście dostępnych obrazów maszyn wirtualnych Wyszukaj i wybierz jedną z następujących opcji:
    - Serwer Ubuntu: `Ubuntu Server 16.04 LTS`
    - Data Science VM: `Linux Data Science` (patrz [Virtual Machines nauki](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) dotyczącej danych, aby uzyskać szczegółowe informacje)
1. Ustaw model wdrażania na `Resource manager` i wybierz pozycję **Utwórz**.
1. Wybierz nazwę dla maszyny wirtualnej, podaj wartość Nazwa użytkownika i hasło (hasło jest wymagane, ponieważ logowanie za pomocą klucza publicznego SSH nie jest obsługiwane).
1. Wprowadź inne żądane zmiany w konfiguracji maszyny wirtualnej.
1. Wybierz rozmiar maszyny wirtualnej, sprawdź konfigurację i wybierz pozycję **Utwórz**. Po utworzeniu maszyny wirtualnej przejdź do następnej sekcji.

#### <a name="configure-the-vm"></a>Konfigurowanie maszyny wirtualnej

1. W sekcji **Sieć** maszyny wirtualnej Dodaj 5444 jako dozwolony port przychodzący. Aby użyć innego portu, Zmień ustawienie w pliku konfiguracji demona RTVS (*/etc/rtvs/rtvsd.config.json*).
1. Obowiązkowe Ustaw nazwę DNS; Możesz również użyć adresu IP.
1. Nawiąż połączenie z maszyną wirtualną przy użyciu klienta SSH, takiego jak polecenia wyszukiwać dla systemu WIndows.
1. Postępuj zgodnie z instrukcjami dotyczącymi [fizycznego komputera Ubuntu](#physical-ubuntu-computer) .

### <a name="windows-subsystem-for-linux-wsl"></a>Podsystem Windows dla systemu Linux (WSL)

1. Postępuj zgodnie z instrukcjami dotyczącymi instalacji WSL w [systemie Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) lub [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Uruchom program bash w systemie Windows i postępuj zgodnie z wcześniejszymi instrukcjami na [fizycznym komputerze Ubuntu](#physical-ubuntu-computer) z jednym wyjątkiem. W kroku 3 Uruchom usługę przy użyciu polecenia, `rtvsd` ponieważ WSL obecnie nie obsługuje interfejsów systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Lokalny lub zdalny kontener platformy Docker (czysta Kompilacja)

1. Utwórz plik platformy Docker o poniższej zawartości, co spowoduje zainstalowanie zdalnego demona usługi R i najnowszej wersji języka R. **Uwaga**: ten skrypt tworzy użytkownika o nazwie "ruser1" z hasłem "Foobar", które można zmodyfikować zgodnie z potrzebami w ostatnich dwóch `RUN` instrukcjach.

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

1. Kompiluj i uruchamiaj plik platformy Docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Aby nawiązać połączenie z programem Contains z RTVS, użyj `https://localhost:5444` jako ścieżki, nazwy użytkownika `<<unix>>\ruser1` i hasła `foobar` . Jeśli kontener jest uruchomiony na komputerze zdalnym, użyj `https://remote-host-name:5444` jako ścieżki zamiast tego. Port można zmienić przez zaktualizowanie *rtvsd.config.js/etc/RTVS/na*.

### <a name="container-running-on-azure-container-instances"></a>Kontener uruchomiony w Azure Container Instances

1. Postępuj zgodnie z instrukcjami w [lokalnym lub zdalnym kontenerze platformy Docker](#local-or-remote-docker-container-clean-build) , aby utworzyć obraz.
1. Wypchnij kontener do usługi Docker Hub lub repozytorium kontenerów platformy Azure.
1. Rozpocznij pracę z interfejsem wiersza polecenia platformy Azure i zaloguj się przy użyciu narzędzia `az login` .
1. Użyj `az container create` polecenia, aby utworzyć kontener przy użyciu, `--command-line "rtvsd"` Jeśli nie skonfigurowano kontenera do uruchamiania `rtvsd` jako `systemd` Usługa. W poniższym poleceniu obraz powinien znajdować się w usłudze Docker Hub. Repozytorium kontenerów platformy Azure można również użyć przez dodanie argumentów poświadczeń repozytorium kontenera do wiersza polecenia.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Użyj `az container list` polecenia, aby sprawdzić stan. Wyszukaj `provisioningState` : `Succeeded` .
1. Jeśli Inicjowanie obsługi powiodło się, możesz teraz połączyć się z kontenerem. Poszukaj publicznego adresu IP w `ipAddress` polu, którego używasz z poświadczeniami w pliku Docker, aby nawiązać połączenie z kontenerem z RTVS.
