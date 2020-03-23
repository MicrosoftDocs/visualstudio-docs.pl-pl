---
title: Publikowanie aplikacji języka Python w usłudze Azure App Service
description: Opcje publikowania aplikacji języka Python w usłudze Azure App Service, w tym wdrażania git i kontenerów dla systemu Linux i wdrażania w usługach IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c3c8d6c16f2f7e432b6b5e988bf63521f3dfc8c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784118"
---
# <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Obecnie python jest obsługiwany w usłudze Azure App Service dla systemu Linux i można publikować aplikacje przy użyciu [git wdrażania](#publish-to-app-service-on-linux-using-git-deploy) i [kontenerów](#publish-to-app-service-on-linux-using-containers), zgodnie z opisem w tym artykule.

> [!Note]
> Obsługa języka Python w usłudze Azure App Service dla systemu Windows jest oficjalnie przestarzała. W rezultacie polecenie **Publikowania** w programie Visual Studio jest oficjalnie obsługiwane tylko dla [obiektu docelowego usług IIS,](#publish-to-iis)a zdalne debugowanie w usłudze Azure App Service nie jest już oficjalnie obsługiwane.
>
> Jednak [publikowanie w usłudze app service w systemie Windows](publish-to-app-service-windows.md) funkcje nadal działa na razie, jak rozszerzenia Języka Python dla usługi App Service w systemie Windows pozostają dostępne, ale nie będą obsługiwane lub aktualizowane.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikowanie w usłudze App Service w systemie Linux przy użyciu wdrożenia git

Git deploy łączy usługę aplikacji w systemie Linux z określoną gałęzią repozytorium Git. Zatwierdzanie kodu w tej gałęzi automatycznie wdraża w usłudze App Service, a usługa App Service automatycznie instaluje wszystkie zależności wymienione w *pliku requirements.txt*. W takim przypadku usługa App Service w systemie Linux uruchamia kod w wstępnie skonfigurowanym obrazie kontenera, który używa serwera sieci Web Gunicorn. Obecnie ta usługa jest w wersji zapoznawczej i nie jest obsługiwana do użytku produkcyjnego.

Aby uzyskać więcej informacji, zobacz następujące artykuły w dokumentacji platformy Azure:

- [Szybki start: Tworzenie aplikacji sieci Web języka Python w usłudze App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) zawiera krótki instruktaż procesu wdrażania Git przy użyciu prostej aplikacji Flask i wdrożenia z lokalnego repozytorium Git.
- [Jak skonfigurować Python](/azure/app-service/containers/how-to-configure-python) opisuje cechy usługi App Service w kontenerze systemu Linux i jak dostosować gunicorn polecenia uruchamiania dla aplikacji.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikowanie w usłudze App Service w systemie Linux przy użyciu kontenerów

Zamiast polegać na wstępnie utworzony kontener z usługą App Service w systemie Linux, można podać własny kontener. Ta opcja umożliwia wybranie serwerów sieci Web, których używasz, oraz dostosowanie zachowania kontenera.

Istnieją dwie opcje tworzenia kontenerów, zarządzania nimi i wypychania:

- Użyj programu Visual Studio Code i rozszerzenia platformy Docker, zgodnie z opisem w [deploy Python przy użyciu kontenerów platformy Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Nawet jeśli nie używasz programu Visual Studio Code, w tym artykule przedstawiono przydatne szczegóły dotyczące tworzenia obrazów kontenerów dla aplikacji Flask i Django przy użyciu gotowych do produkcji serwerów sieci Web uwsgi i nginx. Następnie można wdrożyć te same kontenery przy użyciu interfejsu wiersza polecenia platformy Azure.

- Użyj wiersza polecenia i interfejsu wiersza polecenia platformy Azure, zgodnie z opisem w [temacie Użyj niestandardowego obrazu platformy Docker](/azure/app-service/containers/tutorial-custom-docker-image) w dokumentacji platformy Azure. Ten przewodnik jest jednak ogólny i nie jest specyficzny dla Języka Python.

## <a name="publish-to-iis"></a>Publikowanie w uis

W programie Visual Studio można publikować na maszynie wirtualnej systemu Windows lub innym komputerze obsługującym usługi IIS za pomocą polecenia **Publikuj.** Korzystając z usług IIS, należy utworzyć lub zmodyfikować plik *web.config* w aplikacji, który informuje usługi IIS, gdzie znajduje się interpreter języka Python. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji sieci Web dla usług IIS](configure-web-apps-for-iis-windows.md).
