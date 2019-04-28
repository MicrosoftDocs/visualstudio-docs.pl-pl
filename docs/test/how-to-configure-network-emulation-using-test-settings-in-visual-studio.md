---
title: Konfiguracja funkcji emulacji sieci za pomocą ustawień testów
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c4738caa4fac8596db5b92c6cafa1c0f370e0363
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979409"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Instrukcje: Konfiguracja funkcji emulacji sieci za pomocą ustawień testów w programie Visual Studio

Można skonfigurować adapter danych diagnostycznych do testowania aplikacji w różnych środowiskach sieciowych w programie Visual Studio. Może być również skonfigurowane do testowania sztuczne obciążenie sieciowe lub wąskich gardeł, po uruchomieniu testów.

> [!WARNING]
> Po uruchomieniu testów w prawdziwej sieci, która jest typu wolniejszego niż sieć, którą emulujesz, testy będą nadal działać w niższej szybkości sieci. Emulacja może tylko spowolnić środowisko sieciowe, nie go przyśpieszyć.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Poniższa procedura opisuje sposób konfigurowania emulacji sieci z edytora konfiguracji. Te kroki dotyczą zarówno edytora konfiguracji w programie Microsoft Test Manager i programu Visual Studio.

> [!NOTE]
> Adapter danych diagnostycznych emulacji sieciowej ma zastosowanie tylko do ustawień testowych Visual Studio. Nie jest używana do ustawień testu w Microsoft Test Manager.

Konta mającego uprawnienia administratora może służyć do emulacji sieci. Jeśli wybrano emulację sieci dla lokalnej roli, która uruchamia testy ręcznie, należy uruchomić program Microsoft Test Manager za pomocą uprawnień administratora. Jeśli wybrano emulację sieci dla żadnych innych ról, należy sprawdzić, czy agent testowy na komputerze dla danej roli używa konta użytkownika, który jest członkiem grupy Administratorzy. Aby uzyskać więcej informacji na temat sposobu konfigurowania konta dla agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

> [!NOTE]
> Konto Usługa sieciowa, która jest domyślnym kontem dla agenta testowego, nie jest członkiem grupy Administratorzy.

**Emulacja sieci true**

Visual Studio używa emulacja sieciowej true bazującej na oprogramowanie dla wszystkich typów testu. Obejmuje to testy obciążenia. Emulacja sieci true symuluje warunki w sieci przez bezpośrednią manipulację pakietami sieciowymi. Emulator sieci może emulować zachowanie zarówno sieci przewodowych i bezprzewodowych, za pomocą niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone w prawdziwą emulację sieci:

- Czas obustronnej konwersji w sieci (opóźnienie)

- Dostępna przepustowość

- Zachowanie usługi kolejkowania wiadomości

- Utrata pakietów

- Zmiana kolejności pakietów

- Propagacje błędów.

Emulacja sieci true również zapewnia elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Emulacja sieci TRUE może służyć przez sieciowych deweloperów i testerów do emulowania pożądanego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu z testami sprzętu, emulacji sieci true jest rozwiązaniem znacznie tańszym i bardziej elastycznym.

## <a name="configure-network-emulation-for-your-test-settings"></a>Skonfiguruj emulację sieci dla ustawień testu

Przed wykonaniem kroków w tej procedurze należy otworzyć Ustawienia testu z programu Visual Studio, a następnie wybierz **dane i Diagnostyka** strony.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Aby skonfigurować emulację sieci ustawień testu

1. Wybierz rolę Aby używać do emulowania konkretnej sieci.

    > [!NOTE]
    > Musisz skonfigurować kartę emulacji sieci tylko dla roli klienta lub roli serwera. Nie trzeba korzystać z karty dla obu ról. Adapter emuluje hałas sieci, który ma wpływ na komunikację między obiema rolami, tak aby nie trzeba go używać na obu. Jeśli nie jest konieczne, należy wybrać rolę klienta dla karty emulacji sieci, aby uniknąć dodatkowych obciążeń roli serwera.

2. Wybierz **emulacji sieci** , a następnie wybierz **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe konfigurowania emulacji sieci.

3. Wybierz strzałkę obok **wybierz profil sieci**i wybierz typ sieci, który chcesz emulować po uruchomieniu testu (na przykład **Cable-DSL 768Kps**).

    > [!WARNING]
    > Po uruchomieniu testów w prawdziwej sieci, która jest typu wolniejszego niż sieć, którą emulujesz, testy będą nadal działać w niższej szybkości sieci. Emulacja może tylko spowolnić środowisko sieciowe, nie go przyśpieszyć.

4. Jeśli dołączysz adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, następnie należy również powiązać sterownik emulacji sieci do jednej z kart sieciowych na komputerze. Sterownik emulacji sieci jest wymagana dla adaptera danych diagnostycznych emulacji sieciowej do funkcji. Sterownik emulacji sieci jest zainstalowany i powiązany z kartą sieciową na dwa sposoby:

    - **Sterownik emulacji sieci instalowany z programu Microsoft Visual Studio Test Agent:** Microsoft Visual Studio Test Agent może służyć zarówno komputerów zdalnych, jak i komputerze lokalnym. Po zainstalowaniu programu Visual Studio Test Agent, proces instalacji obejmuje krok konfiguracji, który wiąże sterownik emulacji sieci z kartą sieciową. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

    - **Sterownik emulacji sieci instalowany z programu Microsoft Visual Studio Test Professional:** Podczas korzystania z emulacji sieci po raz pierwszy monit powiązanie sterownika emulacji sieci z kartą sieciową.

    > [!TIP]
    > Można również zainstalować sterownik emulacji sieci z poziomu wiersza polecenia na komputerze lokalnym bez konieczności instalowania agenta testowego programu Visual Studio przy użyciu następującego polecenia: **VSTestConfig NETWORKEMULATION/Install**

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchamianie testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/run-manual-tests?view=vsts)