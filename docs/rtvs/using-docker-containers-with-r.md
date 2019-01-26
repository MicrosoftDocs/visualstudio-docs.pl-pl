---
title: R i kontenerów rozwiązania Docker
description: Jak skonfigurować kontenerów platformy Docker dla języka R i połączyć się z nimi za pomocą programu Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: aff41dbf0d3f0130c1158806c9420e8edd651fb3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036514"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Za pomocą kontenerów platformy Docker narzędzia R Tools for Visual Studio

R Tools for Visual Studio (RTVS) w wersji 1.3 +, wraz z instalacji z [Docker for Windows](https://www.docker.com/docker-windows), obsługuje pracę z kontenerami platformy Docker.

## <a name="create-a-container"></a>Tworzenie kontenera

1. Wybierz **kontenery** przycisk w prawym rogu **obszary robocze** okna (**R Tools** > **Windows**  >  **Obszary robocze**). Okno informuje użytkownika, czy masz Docker for Windows zainstalowany i zawiera również link do pobrania. Instalowanie platformy Docker może wymagać ponownego uruchomienia komputera.

    ![Okno obszarów roboczych w R Tools for Visual Studio (VS2017) za pomocą polecenia kontenerów](media/container-workspaces-window.png)

1. W **kontenery** wybierz **Utwórz**:

    ![Utwórz polecenie w oknie kontenerów](media/containers-window-create.png)

1. Uzupełnij wymagane informacje w oknie dialogowym i wybierz pozycję **Utwórz**. Wprowadzone poświadczenia są umożliwia również tworzenie konta usługi w systemie Linux za pomocą którego możesz zalogować się później.

    ![Wprowadzanie nazwy kontenera i poświadczeń podczas tworzenia kontenera](media/containers-window-create-fill.png)

1. Może upłynąć trochę czasu, RTVS utworzyć obraz. **Dane wyjściowe** okna w programie Visual Studio Pokazuje postęp, ale może wydawać się nie można wykonać większość podczas długich obrazu, pliki do pobrania; należy przygotować się na o cierpliwość. Gdy obraz jest kompilowany, RTVS uruchamia kontener i wyświetlone w **kontenera** okna. Kontrolki do prawego stop, usuń lub ponownego uruchomienia kontenera.

    ![Okno kontejneru przedstawiający kontenera zakończone](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Łączenie do kontenera

1. **Lokalne uruchamianie kontenerów** części **obszary robocze** kontenery działające demona RTVS na porcie 5444 jest wyświetlana w oknie. (Zobacz [zdalnego R Server for Linux](setting-up-remote-r-service-on-linux.md) szczegółowe informacje na temat sposobu skonfigurowania demona.)

    ![Obszary robocze okna przedstawiający dostępnych kontenerów](media/workspaces-window-running-containers.png)

1. Aby połączyć się z kontenerem, kliknij dwukrotnie nazwę kontenera, lub wybierz przycisk ze strzałką do przodu po jego prawej stronie. Po nawiązaniu połączenia zostanie wyświetlony **interaktywne R** okna (zobacz [pracować okno interaktywne R](interactive-repl-for-r-in-visual-studio.md)):

    ![Obszary robocze okna i okna REPL otwarte dla kontenera](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Korzystanie z niestandardowych obrazów

RTVS wykrywa i umożliwia zarządzanie kontenery utworzone przy użyciu niestandardowych obrazów, takich jak obraz microsoft/rtvs opisane w poniższych pliku platformy docker. Obraz podstawowy użyty tutaj ma rtvs demona, R 3.4.2 i popularnych pakietów języka R wstępnie zainstalowane. **Uwaga**: Zmień nazwę użytkownika i hasło podane tu zgodnie z potrzebami.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Użyj następującego polecenia, aby utworzyć obraz, zmiana nazwy kontenera ( `--name` argument) zgodnie z potrzebami:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` Argument mapowania portów 6056 do portu wewnętrznej 5444, używający RTVS wykrywania rtvs demon. Dowolnego kontenera, który udostępnia z kontenera typu port 5444 znajduje się w **obszary robocze** okna. Następnie można użyć **obszary robocze** okna, aby nawiązać połączenie z kontenera przy użyciu `<<unix>>\ruser1` jako nazwy użytkownika i "foobar" jako hasło, chyba że określone inne poświadczenia w pliku platformy docker.
