---
title: Publikowanie aplikacji w języku Python w celu Azure App Service
description: Opcje publikowania aplikacji w języku Python do Azure App Service, w tym narzędzia Git Deploy i kontenerów dla systemu Linux oraz wdrażania w usługach IIS.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b2848a54ddbce41b538bf58f82db42ede76026d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912408"
---
# <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

W tej chwili środowisko Python jest obsługiwane w Azure App Service dla systemu Linux i można publikować aplikacje za pomocą [narzędzia Git Deploy](#publish-to-app-service-on-linux-using-git-deploy) and [Containers](#publish-to-app-service-on-linux-using-containers), zgodnie z opisem w tym artykule.

> [!Note]
> Obsługa języka Python w Azure App Service dla systemu Windows jest oficjalnie przestarzała. W efekcie polecenie **Publikuj** w programie Visual Studio jest oficjalnie obsługiwane tylko dla [obiektu docelowego usług IIS](#publish-to-iis)i zdalne debugowanie na Azure App Service nie jest już oficjalnie obsługiwane.
>
> Jednak [Publikowanie w usłudze App Service w funkcjach systemu Windows](publish-to-app-service-windows.md) nadal działa przez czas, ponieważ rozszerzenia języka Python dla App Service w systemie Windows pozostają dostępne, ale nie będą obsługiwane ani aktualizowane.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikowanie w usłudze App Service w systemie Linux przy użyciu narzędzia Git Deploy

Funkcja wdrażania usługi git łączy App Service w systemie Linux z określoną gałęzią repozytorium git. Zatwierdzenie kodu do tej gałęzi powoduje automatyczne wdrożenie do App Service, a App Service automatycznie instaluje wszystkie zależności wymienione w *requirements.txt*. W takim przypadku App Service w systemie Linux uruchamia swój kod w wstępnie skonfigurowanym obrazie kontenera, który używa serwera sieci Web Gunicorn. W tej chwili ta usługa jest dostępna w wersji zapoznawczej i nie jest obsługiwana w przypadku użycia w środowisku produkcyjnym.

Aby uzyskać więcej informacji, zobacz następujące artykuły w dokumentacji platformy Azure:

- [Szybki Start: Tworzenie aplikacji sieci Web w języku Python w App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) zawiera krótki przewodnik po procesie wdrażania usługi git przy użyciu prostej aplikacji do kolby i wdrożenia z lokalnego repozytorium git.
- [Jak skonfigurować język Python](/azure/app-service/containers/how-to-configure-python) zawiera opis cech App Service w kontenerze systemu Linux i sposobu dostosowywania Gunicorn uruchamiania aplikacji.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikowanie w usłudze App Service w systemie Linux przy użyciu kontenerów

Zamiast polegać na wstępnie skompilowanym kontenerze z App Service w systemie Linux, możesz udostępnić własny kontener. Ta opcja umożliwia wybranie używanych serwerów sieci Web i dostosowanie zachowania kontenera.

Dostępne są dwie opcje kompilowania i wypychania kontenerów, zarządzania nimi:

- Użyj Visual Studio Code i rozszerzenia Docker, zgodnie z opisem w temacie [wdrażanie języka Python przy użyciu kontenerów platformy Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Nawet jeśli nie używasz Visual Studio Code, artykuł zawiera przydatne szczegóły dotyczące tworzenia obrazów kontenerów dla aplikacji do kolb i Django przy użyciu uwsgiych w środowisku produkcyjnym i serwerów sieci Web Nginx. Następnie można wdrożyć te same kontenery przy użyciu interfejsu wiersza polecenia platformy Azure.

- Użyj wiersza poleceń i interfejsu wiersza polecenia platformy Azure, zgodnie z opisem na stronie [Korzystanie z niestandardowego obrazu platformy Docker](/azure/app-service/containers/tutorial-custom-docker-image) w dokumentacji platformy Azure. Ten przewodnik jest jednak ogólny i nie jest specyficzny dla języka Python.

## <a name="publish-to-iis"></a>Publikowanie w usługach IIS

Program Visual Studio umożliwia publikowanie na maszynie wirtualnej z systemem Windows lub innym komputerze z obsługą usług IIS za pomocą polecenia **Publikuj** . W przypadku korzystania z usług IIS należy utworzyć lub zmodyfikować plik *web.config* w aplikacji, która informuje usługi IIS, gdzie znajduje się interpreter języka Python. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji sieci Web dla usług IIS](configure-web-apps-for-iis-windows.md).
