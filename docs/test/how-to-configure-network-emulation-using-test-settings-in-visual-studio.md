---
title: Konfigurowanie emulacji sieci przy użyciu ustawień testu
description: Dowiedz się, jak skonfigurować adapter danych diagnostycznych w celu przetestowania aplikacji w różnych środowiskach sieciowych z programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, network emulation
ms.assetid: ff275cfb-5df9-4710-9a91-9caabaaad34f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 6126441890f34296fa0d8a9cda20bee32752cd81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966763"
---
# <a name="how-to-configure-network-emulation-using-test-settings-in-visual-studio"></a>Instrukcje: Konfigurowanie emulacji sieci za pomocą ustawień testu w programie Visual Studio

Adapter danych diagnostycznych można skonfigurować do testowania aplikacji w różnych środowiskach sieciowych programu Visual Studio. Można go również skonfigurować do testowania sztucznego obciążenia sieci lub wąskich gardeł podczas uruchamiania testów.

> [!WARNING]
> Jeśli uruchamiasz testy w realnej sieci, która jest wolniejszym typem niż sieć, którą emulujesz, test będzie nadal działać przy wolniejszej szybkości sieci. Emulacja może spowolnić działanie środowiska sieciowego, a jego szybkość nie przyspieszy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Poniższa procedura opisuje sposób konfigurowania emulacji sieci z poziomu edytora konfiguracji. Te kroki dotyczą zarówno edytora konfiguracji w Microsoft Test Manager, jak i programu Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Poniższa procedura opisuje sposób konfigurowania emulacji sieci z poziomu edytora konfiguracji. Te kroki dotyczą edytora konfiguracji w programie Visual Studio.
::: moniker-end

> [!NOTE]
> Karta danych diagnostycznych emulacji sieci ma zastosowanie tylko do ustawień testu programu Visual Studio. Nie jest on używany dla ustawień testu w Microsoft Test Manager (przestarzałe w programie Visual Studio 2017).

::: moniker range="vs-2017"
Do emulacji sieci należy użyć konta z uprawnieniami administratora. Jeśli wybrano emulację sieci dla roli lokalnej, która uruchamia testy ręczne, należy uruchomić Microsoft Test Manager przy użyciu uprawnień administratora. Jeśli wybrano emulację sieci dla dowolnej innej roli, należy sprawdzić, czy agent testowy na maszynie dla tej roli korzysta z konta użytkownika, które jest członkiem grupy Administratorzy. Aby uzyskać więcej informacji na temat sposobu konfigurowania konta dla agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).
::: moniker-end

> [!NOTE]
> Konto usługi sieciowej, które jest domyślnym kontem dla agenta testowego, nie jest członkiem grupy Administratorzy.

**Emulacja prawdziwej sieci**

Program Visual Studio używa emulacji sieci opartej na oprogramowaniu dla wszystkich typów testów. Obejmuje to testy obciążenia. Emulacja sieci prawda symuluje warunki sieci przez bezpośrednie manipulowanie pakietami sieciowymi. Prawdziwy emulator sieci może emulować zachowanie zarówno sieci przewodowych, jak i bezprzewodowych, za pomocą niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone w ramach prawdziwej emulacji sieci:

- Czas błądzenia w sieci (opóźnienie)

- Ilość dostępnej przepustowości

- Zachowanie kolejkowania

- Utrata pakietów

- Zmiana kolejności pakietów

- Propagacje błędów.

Emulacja sieci zapewnia również elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Emulacja sieci może być używana przez deweloperów i testerów sieci do emulowania odpowiedniego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu do Beds testu sprzętu prawdziwe Emulacja sieci to znacznie tańsze i bardziej elastyczne rozwiązanie.

## <a name="configure-network-emulation-for-your-test-settings"></a>Skonfiguruj emulację sieci dla ustawień testu

Przed wykonaniem kroków opisanych w tej procedurze należy otworzyć ustawienia testu w programie Visual Studio, a następnie wybrać stronę **dane i Diagnostyka** .

### <a name="to-configure-network-emulation-for-your-test-settings"></a>Aby skonfigurować emulację sieci dla ustawień testu

1. Wybierz rolę, która ma być używana do emulowania określonej sieci.

    > [!NOTE]
    > Kartę emulacji sieci należy skonfigurować tylko na roli klienta lub roli serwera. Nie ma potrzeby używania karty w obu rolach. Karta emuluje hałas sieci, który ma wpływ na komunikację między obiema rolami, dzięki czemu nie trzeba używać jej jednocześnie na obu. O ile nie jest to konieczne, należy wybrać rolę klienta dla karty emulacji sieci, aby uniknąć dodatkowego narzutu na rolę serwera.

2. Wybierz pozycję **Emulacja sieci** , a następnie wybierz pozycję **Konfiguruj**.

     Zostanie wyświetlone okno dialogowe umożliwiające skonfigurowanie emulacji sieci.

3. Wybierz strzałkę obok pozycji **Wybierz profil sieci**, który ma być używany, a następnie wybierz typ sieci, który ma być emulowany podczas uruchamiania testu (na przykład **kabel-DSL 768Kps**).

    > [!WARNING]
    > Jeśli uruchamiasz testy w realnej sieci, która jest wolniejszym typem niż sieć, którą emulujesz, test będzie nadal działać przy wolniejszej szybkości sieci. Emulacja może spowolnić działanie środowiska sieciowego, a jego szybkość nie przyspieszy.

4. Jeśli dołączysz adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, należy również powiązać sterownik emulacji sieci z jedną z kart sieciowych maszyny. Sterownik emulacji sieci jest wymagany dla karty danych diagnostycznych emulacji sieci do działania. Sterownik emulacji sieci jest instalowany i powiązany z kartą na dwa sposoby:

    - **Sterownik emulacji sieci instalowany z Microsoft Visual Studio agentem testowym:** Agent testowy Microsoft Visual Studio może być używany zarówno na komputerach zdalnych, jak i na komputerze lokalnym. Po zainstalowaniu agenta testowego programu Visual Studio proces instalacji obejmuje krok konfiguracji, który wiąże sterownik emulacji sieci z kartą sieciową. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

    - **Sterownik emulacji sieci instalowany z Microsoft Visual Studio Test Professional:** W przypadku korzystania z emulacji sieci po raz pierwszy zostanie wyświetlony monit o powiązanie sterownika emulacji sieci z kartą sieciową.

    > [!TIP]
    > Sterownik emulacji sieci można również zainstalować z poziomu wiersza polecenia na komputerze lokalnym bez instalowania agenta testowego programu Visual Studio za pomocą następującego polecenia: **VSTESTCONFIG NETWORKEMULATION/install**

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
- [Uruchom testy ręczne (Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts&preserve-view=true)
