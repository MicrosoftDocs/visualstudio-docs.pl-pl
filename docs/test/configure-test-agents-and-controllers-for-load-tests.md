---
title: Konfigurowanie agentów testowych i kontrolerów testów obciążenia testów
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test agents and controllers
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: c4462c97febc7f1075080bf659a679647bc7bbe5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899840"
---
# <a name="configure-test-agents-and-test-controllers-for-running-load-tests"></a>Konfigurowanie agentów testowych i kontrolerów do prowadzenia testów obciążeniowych testów

Program Visual Studio może generować symulowane obciążenia aplikacji za pomocą fizycznych lub maszyn wirtualnych. Te maszyny należy skonfigurować jako jednego kontrolera testów oraz jednego lub więcej agentów testowych. Agentów testowych i kontrolera testów służy do generowania obciążenia więcej niż jednym komputerze można wygenerować samodzielnie.

> [!NOTE]
> Umożliwia także testowania obciążenia opartego na chmurze, aby zapewnić maszynom wirtualnym, które generują obciążenie wielu użytkownikom uzyskiwanie dostępu do witryny sieci Web, w tym samym czasie. Dowiedz się więcej na temat testowania obciążenia w chmurze w [Uruchom testy obciążenia przy użyciu planów testów Azure](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="load-simulation-architecture"></a>Architektura symulacji obciążenia

Architektura symulacji obciążenia składa się z klienta programu Visual Studio, kontroler testów i agentów testowych.

-   Klient służy do opracowywania i wykonywania testów oraz do wyświetlania ich wyników.

-   Kontroler testów służy do administrowania agentami testowymi i gromadzenia wyników testów.

-   Agenci testowi służą do wykonywania testów oraz zbierania danych, w tym informacji systemowych i danych profilowania ze środowiska ASP.NET zdefiniowanych w ustawieniu testu.

Taka architektura ma szereg zalet:

- Możliwość skalowania generowanego obciążenia przez dodawanie kolejnych agentów testowych do kontrolera testów.

- Elastyczność instalowania oprogramowania klienta, kontrolera testów i agentów testowych na tym samym lub różnych komputerach. Na przykład:

   **Konfiguracja lokalna:**

  - Komputer1: Program Visual Studio, kontroler, agent.

    ![Za pomocą kontrolera i agenta komputera lokalnego](./media/load-test-configa.png)

    **Typowa konfiguracja zdalna:**

  - Komputery 1 i 2: Program Visual Studio (wielu testerów może używać tego samego kontrolera).

  - KOMPUTER3: Kontroler (mogą być zainstalowani agenci).

  - Komputer 4 n: Agent lub agenci skojarzeni z kontrolerem na KOMPUTER3.

    ![Maszyny zdalne przy użyciu kontrolera i agentów](./media/load-test-configb.png)

Mimo że kontroler testów zarządza zwykle kilkoma agentami testowymi, każdy agent może być powiązany tylko z jednym kontrolerem. Każdego agenta testowego może używać cały zespół deweloperów. Taka architektura pozwala łatwo zwiększać liczbę agentów testowych, a efekcie generować większe obciążenia.

## <a name="test-agent-and-test-controller-interaction"></a>Agent testowy i interakcji z kontrolera testów

Kontroler testów zarządza zbiorem agentów testowych faktycznie wykonujących testy. Kontroler testowy komunikuje się z agentami testowymi w celu rozpoczęcia testów, zatrzymania testów, śledzenia stanu agenta testowego i zbierania wyników testów.

### <a name="test-controller"></a>Kontroler testów

Kontroler testów zapewnia ogólną architekturę wykonywania testów oraz zawiera specjalne funkcje do prowadzenia testów obciążeniowych. Kontroler testów wysyła test obciążeniowy do wszystkich agentów testowych i czeka, aż agenci zainicjują test. Gdy wszyscy agenci testowi są gotowi, kontroler testów wysyła do nich komunikat nakazujący rozpoczęcie testu.

### <a name="test-agent"></a>Agent testowy

Agent testowy działa jako usługa, która nasłuchuje od kontrolera testów żądań rozpoczęcia nowego testu. Gdy agent testowy odbiera żądanie, Usługa agenta testowego uruchamia proces, w którym można uruchomić testy. Każdy agent testowy wykonuje ten sam test obciążeniowy.

 Administrator przypisuje agentom testowym wagi, według których są następnie rozkładane obciążenia. Na przykład jeśli agent testowy 1 ma wagę 30, agent testowy 2 wagę 70, a obciążenie zostanie ustawione na 1000 użytkowników, agent testowy 1 będzie symulował 300, a agent testowy 2 — 700 wirtualnych użytkowników. Zobacz [zarządzać kontrolerami testów i agentami testowymi za pomocą programu Visual Studio](../test/manage-test-controllers-and-test-agents.md).

 Agent testowy przyjmuje zestaw testów i zestaw parametrów symulacji jako dane wejściowe. Kluczową koncepcją to, że testy są niezależne od komputera, na którym działają.

## <a name="test-controller-and-test-agent-connection-points"></a>Kontroler testów i punkty połączenia agenta testowego

Na poniższej ilustracji pokazano punkty połączenia między kontrolerem testów, agentem testowym i klientem. Przedstawia, które porty są używane dla połączeń przychodzących i wychodzących, a także ograniczenia zabezpieczeń używane na tych portach.

 ![Testowanie sterownika i test agent portów i zabezpieczeń](./media/test-controller-agent-firewall.png)

 Aby uzyskać więcej informacji, zobacz [Konfiguracja portów dla kontrolerów testów i agentów testowych](../test/configure-ports-for-test-controllers-and-test-agents.md).

## <a name="test-controller-and-agent-installation-information"></a>Informacje dotyczące instalacji kontrolera i agenta testów

Aby uzyskać ważne informacje o wymaganiach sprzętowych i programowych dla kontrolerów testów i agentów testowych, procedur ich instalowania i konfigurowania środowiska w celu uzyskania optymalnej wydajności, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="use-the-test-controller-and-test-agent-with-unit-tests"></a>Agent testowy kontrolera i testu za pomocą testów jednostkowych

Po zainstalowaniu kontrolera testów i jednego lub więcej agentów testowych można w ustawieniu testów obciążeniowych określić, czy kontroler testów ma wykonywać testy zdalnie. Ponadto można wskazać dane i adaptery diagnostyczne, które mają być używane do roli powiązanej z agentami w ustawieniu testu.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)