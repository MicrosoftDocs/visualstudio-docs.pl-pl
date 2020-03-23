---
title: Kontenery R i Docker
description: Jak skonfigurować kontenery platformy Docker dla języka R i połączyć się z nimi za pomocą programu Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c5b4278ab50aac96703f03e74c014d29831f22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62810223"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Używanie kontenerów platformy Docker z narzędziami języka R dla programu Visual Studio

Narzędzia R dla programu Visual Studio (RTVS) w wersji 1.3+, wraz z instalacją [platformy Docker dla systemu Windows,](https://www.docker.com/docker-windows)obsługuje pracę z kontenerami platformy Docker.

## <a name="create-a-container"></a>Tworzenie kontenera

1. Wybierz przycisk **Kontenery** w prawym rogu okna **Obszary robocze** (**R Tools** > **Windows** > **Workspaces**). Okno informuje, jeśli nie masz zainstalowanego platformy Docker dla systemu Windows i zawiera łącze do pobrania. Instalacja platformy Docker może wymagać ponownego uruchomienia komputera.

    ![Okno obszary robocze w programie R Tools for Visual Studio (VS2017) z poleceniem Kontenery](media/container-workspaces-window.png)

1. W oknie **Kontenery** wybierz pozycję **Utwórz:**

    ![Polecenie Utwórz w oknie Kontenery](media/containers-window-create.png)

1. Wypełnij wymagane informacje w oknie dialogowym i wybierz pozycję **Utwórz**. Wprowadzone poświadczenia są również używane do tworzenia konta w systemie Linux, za pomocą którego logujesz się później.

    ![Wprowadzanie nazwy kontenera i poświadczeń podczas tworzenia kontenera](media/containers-window-create-fill.png)

1. Może upłynąć trochę czasu, aby RTVS zbudować obraz. Okno **Dane wyjściowe** w programie Visual Studio pokazuje postęp, ale może się wydawać, że nie robi wiele podczas długich pobierania obrazów; przygotować się do cierpliwości. Po zbudowaniu obrazu RTVS uruchamia kontener i pojawia się w **oknie Kontener.** Formanty po prawej stronie zatrzymują, usuwają lub ponownie uruchamiają kontener.

    ![Okno kontenerów z wypełnionym kontenerem](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Łączenie się z kontenerem

1. W sekcji **Lokalne kontenery uruchomione** w oknie **Obszary robocze** są wyświetlane kontenery z demonem RTVS na porcie 5444. (Zobacz [Remote R Server for Linux,](setting-up-remote-r-service-on-linux.md) aby uzyskać szczegółowe informacje na temat konfiguracji demona).

    ![Okno obszarów roboczych z dostępnymi kontenerami](media/workspaces-window-running-containers.png)

1. Aby połączyć się z kontenerem, kliknij dwukrotnie nazwę kontenera lub wybierz przycisk strzałki do przodu po prawej stronie. Po podłączeniu zostanie wyświetlone okno **Interaktywne R** (patrz [Praca z oknem Interaktywna R):](interactive-repl-for-r-in-visual-studio.md)

    ![Okno obszarów roboczych i okno REPL otwarte dla kontenera](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Używanie obrazów o własnych i własnych

RTVS wykrywa i umożliwia zarządzanie kontenerami utworzonymi przy użyciu obrazów niestandardowych, takich jak obraz microsoft/rtvs opisany w pliku docker poniżej. Obraz podstawowy używany tutaj ma rtvs-daemon, R 3.4.2 i wspólne pakiety R preinstalowane. **Uwaga:** w razie potrzeby zmień nazwę użytkownika i hasło pokazane tutaj.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Użyj następującego polecenia, aby utworzyć obraz, `--name` zmieniając nazwę kontenera (argument) zgodnie z potrzebami:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Argument `-p 6056:5444` mapuje port 6056 do portu wewnętrznego 5444, którego RTVS używa do wykrywania rtvs-daemon. Każdy kontener, który udostępnia port kontenera 5444 jest wymieniony w oknie **Obszary robocze.** Następnie można użyć okna **Obszary robocze,** aby `<<unix>>\ruser1` połączyć się z kontenerem przy użyciu nazwy użytkownika i "foobar" jako hasło, chyba że określono różne poświadczenia w pliku docker.
