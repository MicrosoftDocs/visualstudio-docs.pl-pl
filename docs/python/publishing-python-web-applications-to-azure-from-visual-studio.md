---
title: Publikowanie aplikacji w języku Python w usłudze Azure App Service
description: Opcje publikowania wdrażania aplikacji języka Python w usłudze Azure App Service, w tym Git i kontenery dla systemów Linux i wdrażanie w usługach IIS.
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784118"
---
# <a name="publish-to-azure-app-service"></a>Publikowanie w usłudze Azure App Service

Obecnie obsługuje język Python w usłudze Azure App Service dla systemu Linux, a mogą publikować aplikacje za pomocą [wdrożenia Git](#publish-to-app-service-on-linux-using-git-deploy) i [kontenery](#publish-to-app-service-on-linux-using-containers), zgodnie z opisem w tym artykule.

> [!Note]
> Obsługa w języku Python w usłudze Azure App Service dla Windows oficjalnie jest przestarzały. W rezultacie **publikowania** polecenia w programie Visual Studio jest oficjalnie obsługiwana tylko dla [docelowej usługi IIS](#publish-to-iis), i zdalne debugowanie w usłudze Azure App Service jest już oficjalnie obsługiwany.
>
> Jednak [publikowania w usłudze App Service w Windows](publish-to-app-service-windows.md) funkcje nadal działa w chwili obecnej, jak rozszerzenia języka Python dla usługi App Service na Windows pozostają dostępne, ale będzie nie obsłużonych lub zaktualizowane.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Publikowanie do usługi App Service w systemie Linux przy użyciu narzędzia Git wdrożenia

Wdrażanie Git łączy usługi App Service w systemie Linux do określonej gałęzi repozytorium Git. Zatwierdzenie kodu do tej gałęzi automatycznie wdraża w usłudze App Service i usługi App Service automatycznie instaluje wszystkie zależności, na liście *requirements.txt*. W tym przypadku usługi App Service w systemie Linux jest uruchamiany kod w obraz kontenera wstępnie skonfigurowane, który korzysta z serwera sieci web Gunicorn. Obecnie ta usługa jest w wersji zapoznawczej i nie jest obsługiwane do użytku produkcyjnego.

Aby uzyskać więcej informacji zobacz następujące artykuły w dokumentacji platformy Azure:

- [Szybki start: Tworzenie aplikacji sieci web w języku Python w usłudze App Service](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) zawiera krótki przewodnik dotyczący usługi Git wdrażanie proces, korzystając z prostej aplikacji Flask i wdrażanie z lokalnego repozytorium Git.
- [Konfigurowanie języka Python](/azure/app-service/containers/how-to-configure-python) opisuje cechy usługi App Service na kontenera systemu Linux i dostosowywanie Gunicorn polecenie uruchamiania aplikacji.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Publikowanie w usłudze App Service w systemie Linux przy użyciu kontenerów

Zamiast polegania na kontenerze wstępnie utworzonych za pomocą usługi App Service w systemie Linux, możesz podać własne kontenera. Ta opcja umożliwia wybranie serwerów sieci web, które możesz użyć i dostosować zachowanie kontenera.

Istnieją dwa sposoby tworzenia, zarządzania i Wypchnij kontenerów:

- Korzystanie z programu Visual Studio Code i rozszerzenia platformy Docker, zgodnie z opisem na [wdrażania języka Python za pomocą kontenerów platformy Docker](https://code.visualstudio.com/docs/python/tutorial-deploy-containers). Nawet jeśli nie używasz programu Visual Studio Code, artykuł zawiera szczegółowe przydatne na kompilowanie obrazów kontenerów dla aplikacji Flask i Django przy użyciu serwerów sieci web uwsgi i nginx gotowe do produkcji. Następnie można wdrożyć te tego samego kontenera przy użyciu wiersza polecenia platformy Azure.

- Korzystanie z wiersza polecenia i interfejsu wiersza polecenia platformy Azure, zgodnie z opisem na [korzystanie z niestandardowego obrazu platformy Docker](/azure/app-service/containers/tutorial-custom-docker-image) w dokumentacji platformy Azure. Ten przewodnik jest ogólny, jednak i nie jest specyficzne dla języka Python.

## <a name="publish-to-iis"></a>Publikowanie w usługach IIS

W programie Visual Studio, można publikować na maszynę wirtualną Windows lub inny komputer obsługujący usługi IIS za pomocą **Publikuj** polecenia. Korzystając z usług IIS, należy utworzyć lub zmodyfikować *web.config* pliku w aplikacji, która informuje program IIS gdzie znaleźć interpreter języka Python. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji sieci web dla usług IIS](configure-web-apps-for-iis-windows.md).
