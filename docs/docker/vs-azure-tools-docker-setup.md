---
title: Konfigurowanie hosta platformy Docker przy użyciu VirtualBox | Dokumentacja firmy Microsoft
description: Instrukcje krok po kroku, aby skonfigurować domyślne wystąpienie platformy Docker przy użyciu maszyny platformy Docker i VirtualBox
services: azure-container-service
documentationcenter: na
author: mlearned
manager: jillfra
ms.assetid: 0b1335a2-7720-42a8-8260-4e06fc00c9f6
ms.service: multiple
ms.devlang: dotnet
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: multiple
ms.date: 06/08/2016
ms.author: mlearned
ms.openlocfilehash: a3c02d59021f7596c4c754e185782c591b71fd11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965753"
---
# <a name="configure-a-docker-host-with-virtualbox"></a>Konfigurowanie hosta platformy Docker przy użyciu rozwiązania VirtualBox
## <a name="overview"></a>Omówienie
Ten artykuł przeprowadzi Cię przez Konfigurowanie domyślnego wystąpienia platformy Docker przy użyciu maszyny platformy Docker i VirtualBox.
Jeśli używasz [Docker for Windows](https://www.docker.com/products/docker-desktop), ta konfiguracja nie jest konieczne.

## <a name="prerequisites"></a>Wymagania wstępne
Następujące narzędzia muszą być zainstalowane.

* [Docker Toolbox](https://github.com/docker/toolbox/releases)

## <a name="configuring-the-docker-client-with-windows-powershell"></a>Konfigurowanie klienta platformy Docker przy użyciu programu Windows PowerShell
Aby skonfigurować klienta platformy Docker, po prostu otwórz program Windows PowerShell i wykonaj następujące czynności:

1. Tworzenie hosta platformy docker domyślnego wystąpienia.

    ```PowerShell
    docker-machine create --driver virtualbox default
    ```
2. Sprawdź, czy wystąpienie domyślne to skonfigurowany i uruchomiony. (Powinna być widoczna wystąpienia o nazwie "default" systemem.

    ```PowerShell
    docker-machine ls
    ```

    ![dane wyjściowe ls maszyny platformy docker](media/vs-azure-tools-docker-setup/docker-machine-ls.png)
3. Ustaw wartość domyślną jako bieżący host, a następnie skonfiguruj powłoki.

    ```PowerShell
    docker-machine env default | Invoke-Expression
    ```
4. Wyświetlanie aktywnych kontenerów platformy Docker. Lista powinna być pusta.

    ```PowerShell
    docker ps
    ```

    ![dane wyjściowe programu platformy docker ps](media/vs-azure-tools-docker-setup/docker-ps.png)

> [!NOTE]
> Każdym ponownym uruchomieniu komputera deweloperskiego, będzie konieczne ponowne uruchomienie usługi hosta lokalnego platformy docker.
> Aby to zrobić, należy wydać następujące polecenie w wierszu polecenia: `docker-machine start default`.
