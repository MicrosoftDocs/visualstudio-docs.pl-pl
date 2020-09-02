---
title: Kontenery języka R i platformy Docker
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810223"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Używanie kontenerów platformy Docker z R Tools for Visual Studio

Program R Tools for Visual Studio (RTVS) w wersji 1.3 + wraz z instalacją [Docker for Windows](https://www.docker.com/docker-windows)obsługuje pracę z kontenerami platformy Docker.

## <a name="create-a-container"></a>Tworzenie kontenera

1. Wybierz przycisk **kontenery** w prawym górnym rogu okna **obszary robocze** (w obszarze roboczym**Narzędzia R Tools**  >  **Windows**  >  **Workspaces**). Okno informuje użytkownika, jeśli nie masz zainstalowanego Docker for Windows i udostępniono link do pobierania. Zainstalowanie platformy Docker może wymagać ponownego uruchomienia komputera.

    ![Okno obszary robocze w R Tools for Visual Studio (program VS2017) z kontenerami — polecenie](media/container-workspaces-window.png)

1. W oknie **kontenery** wybierz pozycję **Utwórz**:

    ![Utwórz polecenie w oknie kontenerów](media/containers-window-create.png)

1. Wypełnij wymagane informacje w oknie dialogowym i wybierz pozycję **Utwórz**. Wprowadzone poświadczenia są również używane do tworzenia konta w systemie Linux, za pomocą którego logujesz się później.

    ![Wprowadzanie nazwy kontenera i poświadczeń podczas tworzenia kontenera](media/containers-window-create-fill.png)

1. Utworzenie obrazu może zająć trochę czasu. Okno **danych wyjściowych** w programie Visual Studio pokazuje postęp, ale może wydawać się, że nie jest to czasochłonne podczas pobierania obrazów. Przygotuj się jako pacjent. Po skompilowaniu obrazu RTVS uruchamia kontener i pojawia się w oknie **kontenera** . Kontrolki z prawej strony zatrzymają, usuwają lub ponownie uruchamiają kontener.

    ![Okno kontenerów przedstawiające ukończony kontener](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Nawiązywanie połączenia z kontenerem

1. Sekcja **lokalne uruchomione kontenery** w oknie **obszary robocze** przedstawia kontenery, na których działa demon RTVS na porcie 5444. (Zobacz [zdalne R Server dla systemu Linux](setting-up-remote-r-service-on-linux.md) , aby uzyskać szczegółowe informacje na temat konfiguracji demona).

    ![Okno obszary robocze przedstawiające dostępne kontenery](media/workspaces-window-running-containers.png)

1. Aby nawiązać połączenie z kontenerem, kliknij dwukrotnie nazwę kontenera lub wybierz przycisk strzałki do przodu po prawej stronie. Po nawiązaniu połączenia zostanie wyświetlone okno **R Interactive** (zobacz [Work with the R Interactive Window](interactive-repl-for-r-in-visual-studio.md)):

    ![Okno obszary robocze i okno REPL otwarte dla kontenera](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Korzystanie z obrazów utworzonych niestandardowo

RTVS wykrywa i umożliwia zarządzanie kontenerami utworzonymi przy użyciu wbudowanych obrazów, takich jak obraz Microsoft/RTVS opisany w pliku Docker poniżej. Obraz podstawowy użyty w tym miejscu ma RTVS-demona, R 3.4.2 i Common R Packages preinstalowane. **Uwaga**: w razie konieczności zmień nazwę użytkownika i hasło.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Użyj następującego polecenia, aby skompilować obraz, zmieniając nazwę kontenera ( `--name` argument) zgodnie z potrzebami:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444`Argument mapuje port 6056 na wewnętrzny port 5444, który RTVS używa do wykrywania demona RTVS. Każdy kontener, który uwidacznia port 5444 jest wymieniony w oknie **obszary robocze** . Można następnie użyć okna **obszary robocze** do łączenia się z kontenerem za pomocą `<<unix>>\ruser1` nazwy użytkownika i "Foobar" jako hasła, chyba że w pliku Docker określono inne poświadczenia.
