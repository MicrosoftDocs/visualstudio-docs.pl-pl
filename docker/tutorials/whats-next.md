---
title: Samouczek platformy Docker — co dalej
description: Opisuje opcje rozszerzania aplikacji platformy Docker za pomocą aranżacji przy użyciu projektów Cloud Native Computing Foundation.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: e777d80f44c9a11e4d2a893c968d33e348ca442a
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222698"
---
# <a name="whats-next"></a>Co dalej

Mimo że wszystko jest gotowe do pracy z samouczkiem, nadal możesz dowiedzieć się o wielu innych kontenerach.
Nie zamierzasz tutaj zagłębiać się w to, ale oto kilka innych obszarów, które należy przyjrzeć się następnej!

## <a name="container-orchestration"></a>Aranżacja kontenerów

Uruchamianie kontenerów w środowisku produkcyjnym jest trudne. Nie chcesz logować się do maszyny i po prostu uruchom plik `docker run` lub `docker-compose up` . Czemu nie? Co się stanie, jeśli kontenery zginą? Jak można skalować na kilku maszynach? Aranżacja kontenerów rozwiązuje ten problem. Wszystkie narzędzia, takie jak Kubernetes, Swarm, Nomad i AKS, pomagają rozwiązać ten problem w nieco inny sposób.

Ogólnie rzecz biorąc, masz "menedżerów", którzy otrzymują **oczekiwany stan**. Może to być stan "Chcę uruchomić dwa wystąpienia mojej aplikacji internetowej i uwidocznić port 80". Następnie menedżerowie przyjrzyją się wszystkim maszynom w klastrze i delegują pracę do węzłów "procesu roboczego". Menedżerowie obserwują zmiany (takie jak zamykanie kontenera), a następnie pracują nad tym, aby rzeczywisty stan **odzwierciedlał** oczekiwany stan.

## <a name="cloud-native-computing-foundation-projects"></a>Projekty Cloud Native Computing Foundation

THE EMAF to neutralny dla dostawcy dom dla różnych projektów typu open source, w tym Kubernetes, Prometheus, Envoy, Linkerd, NATS i innych. W tym miejscu możesz przejrzeć stopniowane i [inkubowane](https://www.cncf.io/projects/) projekty oraz cały [krajobraz CYKLUŚNiowy tutaj.](https://landscape.cncf.io/) Istnieje wiele projektów, które ułatwiają rozwiązywanie problemów związanych z monitorowaniem, rejestrowaniem, zabezpieczeniami, rejestrami obrazów, wiadomościami i nie tylko.

Jeśli więc jesteś nowym użytkownikiem krajobrazu kontenerów i tworzenia aplikacji natywnych dla chmury, zapraszamy! Połącz się ze społecznością, zadawaj pytania i ucz się dalej. Cieszymy się, że Cię masz!

## <a name="working-with-docker-in-vs-code"></a>Praca z programem Docker w programie VS Code

Dowiedz się więcej na temat używania VS Code platformy Docker:

- [VS Code Omówienie rozszerzenia platformy Docker](https://code.visualstudio.com/docs/containers/overview)
- [Wprowadzenie do Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Wprowadzenie do języka Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Rozpoczynanie pracy z programem .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Debugowanie aplikacji konteneryzowanych](https://code.visualstudio.com/docs/containers/debug-common)
