---
title: Wymagania dla kontrolera testów i agentów testowych niezbędnych do testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, requirements
- controllers, requirements
ms.assetid: 372d97ce-12e4-46a9-9863-da508adba68f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8a5cc1f58e0cbdb59458311a1b9a4390bf69bbff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051458"
---
# <a name="test-controller-and-test-agent-requirements-for-load-testing"></a>Testowanie wymagania agenta kontrolera i testu do testowania obciążenia

Kilka typów, w tym jednostkowe, wydajności sieci web, obciążenia testu, a testy ręczne są zintegrowane z Visual Studio. Program Visual Studio umożliwia użytkownikom programu Visual Studio Application Lifecycle Management do uruchamiania testów na komputerach zdalnych przy użyciu kontrolera testów i jednego lub kilku agentów. Zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="hardware-and-software-requirements"></a>Wymagania sprzętowe i programowe

Kontrolera testów i komputerów agentów testowych należy mieć określone wymagania dotyczące sprzętu i oprogramowania. Ponadto jeśli chcesz wdrożyć kontroler testowy i agenta testowego w wielu językach, należy zaplanować obsługę tych języków.

### <a name="hardware-requirements"></a>Wymagania sprzętowe

W poniższej tabeli przedstawiono zalecane wymagania sprzętowe dotyczące wdrażania kontrolera testów i agentów testowych.

|**Konfiguracja**|**Składnik**|**CPU**|**HD**|**Pamięć**|
|-|-------------------|-|------------|-|
|< 500 użytkowników wirtualnych|Agent testowy|2,6 procesor GHz|10 GB|2 GB|
|< 1000 użytkowników wirtualnych|Agent testowy|Dwurdzeniowy procesor 2,6 GHz|10 GB|2 GB|
|Użytkownicy wirtualni x 1000 N|Agent testowy|Skalowanie w poziomie do agentów N, każdego z Dual 2,6 Ghz|10GB|2GB|
|\< 30 komputerów w środowisku testowym. Obejmuje to agentów i serwerów w ramach testu.|Kontroler testów|2,6 procesor GHz|||
|N x 30 komputerów w środowisku testowym. Obejmuje to agentów i serwerów w ramach testu.|Kontroler testów|N procesorów 2,6 GHz|||

> [!NOTE]
> Liczba użytkowników wirtualnych różnią się znacznie między poszczególnymi testami. Kluczowym powodem tego odchylenia jest odchylenie w *czasy reakcji*, lub opóźnienia użytkowników. Aby uzyskać więcej informacji, zobacz [reakcji edycji razy do symulacji witryny sieci Web symulujący opóźnienia wynikające z](../test/edit-think-times-in-load-test-scenarios.md). W teście obciążenia testy sieci web są zazwyczaj wydajniejsze i generują większe obciążenie niż testy jednostkowe. Liczby w powyższej tabeli są prawidłowe dla wykonywanie testów sieci web 3 – 5-sekundowych w aplikacji sieci web typowy.

Wskazówki przedstawione tutaj są dostarczane jako ogólne wskazówki dotyczące planowania sprzętowego. Wydajność testów różni się znacznie w zależności od ilości danych testowych i liczby agentów testowych. Dla agentów testowych szybkość procesora CPU i pamięci będzie ograniczają obciążenie badawcze. Kontrolery testowe potrzebują więcej zasobów, w zależności od liczby agentów testowych i ilość danych, które są zaangażowane w testy.

Serwera, na którym jest uruchomiony program Visual Studio powinien mieć niezawodne połączenie sieciowe z minimalną przepustowość 1 MB/s oraz czas oczekiwania maksymalnie 350 MS. Powinno być żadnych zapór między agentami testowymi a kontrolerem testów. Jeśli Twoje wyniki testu nie spełniają Twoich oczekiwań, rozważ aktualizację konfiguracji sprzętu.

### <a name="additional-hardware-considerations"></a>Uwagi dodatkowe dotyczące sprzętu

Agenci testowi generują duże ilości danych na kontrolerach testowych, w zależności od tego, czy czas trwania testu i wielkości testu. Ogólnie rzecz biorąc należy również zaplanować dodatkowe 10 GB miejsca na dysku twardym na dane z badań co 24 godziny.

Oprócz urządzeń zalecanych w tym miejscu należy rozważyć użycie dodatkowego sprzętu dla krytycznych serwerów, takich jak nadmiarowe zasilacze i wentylatory nadmiarowe.

### <a name="language-requirements"></a>Wymagania dotyczące języka

Aby uniknąć nieporozumień i uprościć operację, należy skonfigurować agentów testowych i kontrolera testów do użycia tego samego języka jako systemu operacyjnego i serwera Team Foundation Server. Jeśli agent testowy i kontroler testowy są zainstalowane na różnych komputerach, musi być skonfigurowany do użycia tego samego języka. Można jednak zainstalować inną wersję językową programu Visual Studio w systemie operacyjnym język angielski, tak długo, jak ten język jest zgodny z typem wdrożenia Team Foundation Server.

## <a name="monitor-agent-resources"></a>Monitorowanie zasobów agenta

Możesz monitorować maszyny agenta, aby określić ich zapotrzebowanie na zasoby, obserwując *QTAgent\*.exe* procesów, które wykonywania i skalowania podczas testów. Najbardziej typowym wąskim gardłem w *QTAgent\*.exe* procesów jest użycie procesora CPU. Jeśli wykorzystanie procesora CPU jest stale w wysokiej nineties to wskazanie, że agent jest ładowany dużym stopniu. Dalej typowym wąskim gardłem jest użycie pamięci. Dla wymagających testy, monitorowanie tych zasobów może pomóc ustalenia, czy należy zwiększyć zasoby maszyny lub inaczej dystrybuować testy.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)