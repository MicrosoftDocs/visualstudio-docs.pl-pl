---
title: Kontenery R i Docker
description: Jak skonfigurować kontenery platformy Docker dla platformy R i połączyć się z nimi za pomocą Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3aefba3880443269dbdb1c933e2c12b2f8001469
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551283"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Używanie kontenerów platformy Docker z R Tools for Visual Studio

Program R Tools for Visual Studio (RTVS) w wersji 1.3 lub nowszej wraz z instalacją programu [Docker for Windows](https://www.docker.com/docker-windows)obsługuje pracę z kontenerami platformy Docker.

## <a name="create-a-container"></a>Tworzenie kontenera

1. Wybierz przycisk **Kontenery** w prawym rogu okna **Obszary** robocze **(R Tools**  >  **Windows**  >  **Workspaces**). Okno informuje o tym, jeśli nie masz zainstalowanego Docker for Windows i udostępnia link do pobierania. Instalowanie platformy Docker może wymagać ponownego uruchomienia komputera.

    ![Okno Obszary robocze w programie R Tools for Visual Studio (VS2017) za pomocą polecenia Containers](media/container-workspaces-window.png)

1. W **oknie Kontenery** wybierz pozycję **Utwórz:**

    ![Polecenie Create w oknie Kontenery](media/containers-window-create.png)

1. Uzupełnij wymagane informacje w oknie dialogowym i wybierz pozycję **Utwórz**. Wprowadzane poświadczenia są również używane do utworzenia konta w systemie Linux, za pomocą którego zalogujesz się później.

    ![Wprowadzanie nazwy kontenera i poświadczeń podczas tworzenia kontenera](media/containers-window-create-fill.png)

1. Skompilowanie obrazu przez program RTVS może zająć trochę czasu. Okno **Dane wyjściowe** w Visual Studio postęp, ale może wydawać się, że nie robi zbyt wiele podczas długiego pobierania obrazów; przygotuj się na cierpliwość. Po s zbudowaniu obrazu program RTVS uruchamia kontener i pojawia się w **oknie** Kontener. Kontrolki po prawej stronie zatrzymaj, usuń lub uruchom ponownie kontener.

    ![Okno kontenerów z ukończonym kontenerem](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Łączenie z kontenerem

1. Sekcja **Lokalne uruchomione kontenery** w oknie **Obszary** robocze zawiera kontenery z demonem RTVS na porcie 5444. (Zobacz [zdalne R Server dla systemu Linux](setting-up-remote-r-service-on-linux.md) aby uzyskać szczegółowe informacje na temat sposobu konfigurowania demona).

    ![Okno Obszary robocze z dostępnymi kontenerami](media/workspaces-window-running-containers.png)

1. Aby nawiązać połączenie z kontenerem, kliknij dwukrotnie nazwę kontenera lub wybierz przycisk strzałki w prawo. Po na połączeniu zobaczysz okno **R Interactive** (zobacz [Praca z](interactive-repl-for-r-in-visual-studio.md)R Interactive okna ):

    ![Otwarte okno obszarów roboczych i okno REPL dla kontenera](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Korzystanie z obrazów niestandardowych

Narzędzia RTVS wykrywają kontenery utworzone przy użyciu niestandardowych obrazów utworzonych przy użyciu niestandardowych obrazów, takich jak obraz microsoft/rtvs opisany w poniższym pliku docker. Obraz podstawowy używany w tym miejscu ma wstępnie zainstalowane pakiety rtvs-daemon, R 3.4.2 i typowe pakiety języka R. **Uwaga:** w razie potrzeby zmień nazwę użytkownika i hasło wyświetlane w tym miejscu.

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Użyj następującego polecenia, aby skompilować obraz, zmieniając nazwę kontenera `--name` (argument) zgodnie z potrzebami:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Argument mapuje port 6056 na port wewnętrzny 5444, który jest używany przez usługę RTVS do wykrywania `-p 6056:5444` demona RTVS. Każdy kontener, który uwidacznia port kontenera 5444, jest wymieniony w **oknie Obszary** robocze. Następnie możesz użyć  okna Obszary robocze, aby nawiązać połączenie z kontenerem przy użyciu nazwy użytkownika i "foobar" jako hasła, chyba że w pliku docker określono `<<unix>>\ruser1` inne poświadczenia.
