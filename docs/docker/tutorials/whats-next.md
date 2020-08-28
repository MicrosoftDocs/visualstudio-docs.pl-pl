---
title: Samouczek platformy Docker — co dalej
description: W tym artykule opisano opcje rozszerzania aplikacji platformy Docker z aranżacją przy użyciu natywnych projektów rozwiązania do obsługi rozwiązań w chmurze.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039075"
---
# <a name="whats-next"></a>Co dalej

Mimo że korzystasz z samouczka, nadal znajdziesz więcej informacji na temat kontenerów.
Nie zamierzasz tutaj przeszukać głębokiej szczegółowe tutaj, ale Oto kilka innych obszarów, które chcesz zobaczyć dalej.

## <a name="container-orchestration"></a>Aranżacja kontenerów

Uruchomione kontenery w środowisku produkcyjnym są trudne. Nie chcesz zalogować się do maszyny i po prostu uruchomić program `docker run` lub `docker-compose up` . Czemu nie? Co się stanie, gdy kontenery są zachodzą? Jak skalować na kilku komputerach? Aranżacja kontenerów rozwiązuje ten problem. Narzędzia, takie jak Kubernetes, Swarm, Nomad i AKS, pomagają rozwiązać ten problem, a wszystko to na nieco różne sposoby.

Ogólnym pomysłem jest to, że masz "menedżerów", którzy otrzymują **oczekiwany stan**. Ten stan może mieć wartość "chcę uruchomić dwa wystąpienia mojej aplikacji sieci Web i uwidocznić port 80". Menedżerowie sprawdzają następnie wszystkie maszyny w klastrze i delegowanie pracy do węzłów "proces roboczy". Menedżerowie oglądają zmiany (na przykład zamykające kontenery), a następnie pracują w celu zapewnienia **rzeczywistego stanu** odzwierciedlają oczekiwany stan.

## <a name="cloud-native-computing-foundation-projects"></a>Natywne projekty obliczeniowe w chmurze

CNCF to niezależny od dostawcy dom dla różnych projektów typu "open source", w tym Kubernetes, Prometheus, wysłannika, konsolidatora, NAT i wiele innych. Możesz wyświetlić [stopniowane i inkubowane projekty tutaj](https://www.cncf.io/projects/) i cały [CNCF poziomą](https://landscape.cncf.io/). Istnieje wiele projektów pomagających w rozwiązywaniu problemów dotyczących monitorowania, rejestrowania, zabezpieczeń, rejestrów obrazów, wiadomości i innych elementów.

Tak więc, jeśli dopiero zaczynasz Tworzenie aplikacji na poziomie kontenera i w chmurze, Witamy! Połącz się ze społecznością, zadawaj pytania i Kontynuuj naukę. Przyjemnościąmy!

## <a name="working-with-docker-in-vs-code"></a>Praca z platformą Docker w VS Code

Dowiedz się więcej o korzystaniu z rozszerzenia VS Code Docker:

- [Przegląd rozszerzenia VS Code Docker](https://code.visualstudio.com/docs/containers/overview)
- [Wprowadzenie do Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Wprowadzenie do języka Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Wprowadzenie do platformy .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Debugowanie aplikacji w kontenerze](https://code.visualstudio.com/docs/containers/debug-common)
