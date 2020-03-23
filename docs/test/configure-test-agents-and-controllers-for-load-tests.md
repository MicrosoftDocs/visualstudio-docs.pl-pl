---
title: Konfigurowanie agentów testowych i kontrolerów testów do testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8824e1836d8a49de91cf0e3b9cccf2e85a7de18
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597350"
---
# <a name="overview-of-test-agents-and-test-controllers-for-running-load-tests"></a>Przegląd agentów testowych i kontrolerów testów do uruchamiania testów obciążenia

Visual Studio można wygenerować symulowane obciążenie dla aplikacji przy użyciu maszyn fizycznych lub wirtualnych. Maszyny te muszą być skonfigurowane jako jeden kontroler badania i jeden lub więcej czynników testowych. Kontroler testów i agentów testowych można użyć do wygenerowania większego obciążenia niż pojedynczy komputer może wygenerować samodzielnie.

> [!NOTE]
> Można również użyć testowania obciążenia opartego na chmurze, aby zapewnić maszyny wirtualne, które generują obciążenie wielu użytkowników uzyskujących dostęp do witryny w tym samym czasie. Jednak przy użyciu konfiguracji kontrolera/agenta testowego na maszynach wirtualnych hostowanych w chmurze nie jest obsługiwana. Dowiedz się więcej o testowaniu obciążenia w chmurze w [witrynie Uruchom testy obciążenia przy użyciu planów testów platformy Azure.](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektura symulacji obciążenia

Architektura symulacji obciążenia składa się z klienta programu Visual Studio, kontroler testów i agentów testowych.

- Klient służy do opracowywania i wykonywania testów oraz do wyświetlania ich wyników.

- Kontroler testów służy do administrowania agentami testowymi i gromadzenia wyników testów.

- Agenci testowi służą do wykonywania testów oraz zbierania danych, w tym informacji systemowych i danych profilowania ze środowiska ASP.NET zdefiniowanych w ustawieniu testu.

Taka architektura ma szereg zalet:

- Możliwość skalowania generowanego obciążenia przez dodawanie kolejnych agentów testowych do kontrolera testów.

- Elastyczność instalowania oprogramowania klienta, kontrolera testów i agentów testowych na tym samym lub różnych komputerach. Przykład:

   **Konfiguracja lokalna:**

  - Komputer 1: program Visual Studio, kontroler, agent.

    ![Maszyna lokalna używająca kontrolera i agenta](./media/load-test-configa.png)

    **Typowa konfiguracja zdalna:**

  - Komputery 1 i 2: program Visual Studio (wielu testerów może używać tego samego kontrolera).

  - Komputer 3: kontroler (mogą być na nim również zainstalowani agenci).

  - Machine4-n: Agent lub agenci wszyscy skojarzone z kontrolerem na machine3.

    ![Maszyny zdalne korzystające ze sterownika i agentów](./media/load-test-configb.png)

Mimo że kontroler testów zarządza zwykle kilkoma agentami testowymi, każdy agent może być powiązany tylko z jednym kontrolerem. Każdego agenta testowego może używać cały zespół deweloperów. Taka architektura pozwala łatwo zwiększać liczbę agentów testowych, a efekcie generować większe obciążenia.

## <a name="test-agent-and-test-controller-interaction"></a>Interakcja agenta testowego i kontrolera testów

Kontroler testów zarządza zbiorem agentów testowych faktycznie wykonujących testy. Kontroler testów komunikuje się z agentami testowymi, aby rozpocząć testy, zatrzymać testy, śledzić stan agenta testowego i zbierać wyniki testów.

### <a name="test-controller"></a>Kontroler testowy

Kontroler testów zapewnia ogólną architekturę wykonywania testów oraz zawiera specjalne funkcje do prowadzenia testów obciążeniowych. Kontroler testów wysyła test obciążeniowy do wszystkich agentów testowych i czeka, aż agenci zainicjują test. Gdy wszyscy agenci testowi są gotowi, kontroler testów wysyła do nich komunikat nakazujący rozpoczęcie testu.

### <a name="test-agent"></a>Agent testowy

Agent testowy działa jako usługa, która nasłuchuje od kontrolera testów żądań rozpoczęcia nowego testu. Gdy agent testowy odbiera żądanie, usługa agenta testowego uruchamia proces, w którym mają być uruchamiane testy. Każdy agent testowy wykonuje ten sam test obciążeniowy.

Administrator przypisuje agentom testowym wagi, według których są następnie rozkładane obciążenia. Na przykład jeśli agent testowy 1 ma wagę 30, agent testowy 2 wagę 70, a obciążenie zostanie ustawione na 1000 użytkowników, agent testowy 1 będzie symulował 300, a agent testowy 2 — 700 wirtualnych użytkowników. Zobacz [Zarządzanie kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Agent testowy przyjmuje zestaw testów i zestaw parametrów symulacji jako dane wejściowe. Kluczową koncepcją jest to, że testy są niezależne od komputera, na którym są uruchamiane.

## <a name="test-controller-and-test-agent-connection-points"></a>Przyłącza kontrolera testowego i agenta testowego

Na poniższej ilustracji pokazano punkty połączenia między kontrolerem testów, agentem testowym i klientem. Określa, które porty są używane do połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń stosowane w tych portach.

![Porty i zabezpieczenia kontrolera testowego i agenta testowego](./media/test-controller-agent-firewall.png)

Aby uzyskać więcej informacji, zobacz [Konfigurowanie portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informacje o kontrolerze testowym i instalacji agenta

Aby uzyskać ważne informacje na temat wymagań sprzętowych i programowych dla kontrolerów testowych i agentów testowych, procedur ich instalowania i konfigurowania środowiska w celu uzyskania optymalnej wydajności, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Użyj sterownika testowego i agenta testowego z testami jednostkowymi

Po zainstalowaniu kontrolera testów i jednego lub więcej agentów testowych można w ustawieniu testów obciążeniowych określić, czy kontroler testów ma wykonywać testy zdalnie. Ponadto można wskazać dane i adaptery diagnostyczne, które mają być używane do roli powiązanej z agentami w ustawieniu testu.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
