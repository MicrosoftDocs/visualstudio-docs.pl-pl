---
title: Konfigurowanie emulacji sieci przy użyciu ustawień testowych
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 685b22f25c7138c4c3e7c9068ba52864e40648e1
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880146"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Jak: Konfigurowanie emulacji sieci przy użyciu ustawień testowych w programie Visual Studio

Można skonfigurować kartę danych diagnostycznych, aby przetestować aplikację w różnych środowiskach sieciowych z programu Visual Studio. Można również skonfigurować do testowania sztucznego obciążenia sieci lub wąskie gardło, po uruchomieniu testów.

> [!WARNING]
> Jeśli uruchomisz testy w sieci rzeczywistej, która jest wolniejszym typem niż emulująca sieć, test będzie nadal uruchamiany z mniejszą szybkością sieci. Emulacja może tylko spowolnić środowisko sieciowe, a nie przyspieszyć.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
W poniższej procedurze opisano sposób konfigurowania emulacji sieci z edytora konfiguracji. Te kroki dotyczą edytora konfiguracji w programie Microsoft Test Manager i Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
W poniższej procedurze opisano sposób konfigurowania emulacji sieci z edytora konfiguracji. Te kroki dotyczą edytora konfiguracji w programie Visual Studio.
::: moniker-end

> [!NOTE]
> Karta danych diagnostycznych emulacji sieciowej ma zastosowanie tylko do ustawień testowych programu Visual Studio. Nie jest używany dla ustawień testowych w programie Microsoft Test Manager (przestarzałe w programie Visual Studio 2017).

::: moniker range="vs-2017"
Konto z uprawnieniami administratora musi być używane do emulacji sieci. Jeśli wybrano emulację sieci dla roli lokalnej, która uruchamia testy ręczne, należy uruchomić Menedżera testów firmy Microsoft przy użyciu uprawnień administratora. Jeśli wybrano emulację sieciową dla dowolnej innej roli, należy sprawdzić, czy agent testowy na komputerze dla tej roli używa konta użytkownika, który jest członkiem grupy administratorów. Aby uzyskać więcej informacji na temat konfigurowania konta agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).
::: moniker-end

> [!NOTE]
> Konto usługi sieciowej, które jest domyślnym kontem agenta testowego, nie jest członkiem grupy administratorów.

**Prawdziwa emulacja sieci**

Visual Studio używa emulacji sieci true oparte na oprogramowaniu dla wszystkich typów testów. Obejmuje to testy obciążenia. Prawdziwa emulacja sieci symuluje warunki sieciowe poprzez bezpośrednią manipulację pakietami sieciowymi. Prawdziwy emulator sieci może emulować zachowanie zarówno sieci przewodowych, jak i bezprzewodowych przy użyciu niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone do emulacji sieci true:

- Czas podróży w obie strony w sieci (opóźnienie)

- Ilość dostępnej przepustowości

- Zachowanie kolejkowania

- Utrata pakietów

- Ponowne kolejność pakietów

- Propagacja błędów.

Prawdziwa emulacja sieci zapewnia również elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Prawdziwa emulacja sieci może być używana przez programistów i testerów opartych na sieci do emulowania żądanego środowiska testowego, oceny wydajności, przewidywania skutków zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu do łóżek testowych sprzętu, prawdziwa emulacja sieci jest znacznie tańszym i bardziej elastycznym rozwiązaniem.

## <a name="configure-network-emulation-for-your-test-settings"></a>Konfigurowanie emulacji sieci dla ustawień testowych

Przed wykonaniem kroków w tej procedurze, należy otworzyć ustawienia testu z programu Visual Studio, a następnie wybierz **dane i diagnostyki** strony.

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Aby skonfigurować emulację sieciową dla ustawień testowych

1. Wybierz rolę, która ma być używana do emulacji określonej sieci.

    > [!NOTE]
    > Należy skonfigurować kartę emulacji sieci tylko na roli klienta lub roli serwera. Nie trzeba używać karty w obu rolach. Karta emuluje szum sieciowy, który wpływa na komunikację między obiema rolami, dzięki czemu nie trzeba go używać w obu. O ile nie jest to konieczne, należy wybrać rolę klienta dla karty emulacji sieci, aby uniknąć dodatkowych narzutów na rolę serwera.

2. Wybierz **pozycję Emulacja sieci,** a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe do konfigurowania emulacji sieci.

3. Wybierz strzałkę obok **pozycji Wybierz profil sieciowy do użycia**i wybierz typ sieci, który chcesz emulować po uruchomieniu testu (na przykład **Cable-DSL 768Kps**).

    > [!WARNING]
    > Jeśli uruchomisz testy w sieci rzeczywistej, która jest wolniejszym typem niż sieć, którą emulujesz, test będzie nadal uruchamiany z mniejszą szybkością sieci. Emulacja może tylko spowolnić środowisko sieciowe, a nie przyspieszyć.

4. Jeśli karta danych diagnostycznych emulacji sieciowej zostanie uwzględnina w ustawieniach testowych i zamierzasz jej używać na komputerze lokalnym, należy również powiązać sterownik emulacji sieciowej z jedną z kart sieciowych komputera. Sterownik emulacji sieci jest wymagany do działania karty danych diagnostycznych emulacji sieciowej. Sterownik emulacji sieci jest zainstalowany i powiązany z kartą na dwa sposoby:

    - **Sterownik emulacji sieci zainstalowany z programem Microsoft Visual Studio Test Agent:** Agent testowy programu Microsoft Visual Studio może być używany zarówno na komputerach zdalnych, jak i na komputerze lokalnym. Po zainstalowaniu programu Visual Studio Test Agent, proces instalacji zawiera krok konfiguracji, który wiąże sterownik emulacji sieci do karty sieciowej. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

    - **Sterownik emulacji sieci zainstalowany w programie Microsoft Visual Studio Test Professional:** Podczas korzystania z emulacji sieci po raz pierwszy zostanie wyświetlony monit o powiązanie sterownika emulacji sieci z kartą sieciową.

    > [!TIP]
    > Sterownik emulacji sieciowej można również zainstalować z wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia: **VSTestConfig NETWORKEMULATION /install**

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchamianie testów ręcznych (plany testów platformy Azure)](/azure/devops/test/run-manual-tests?view=vsts)
