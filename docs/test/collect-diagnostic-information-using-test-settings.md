---
title: Zbieranie informacji diagnostycznych za pomocą ustawień testów
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cdaa86e2eb7562f4a3347c942e193da22a9e256e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948839"
---
# <a name="collect-diagnostic-information-using-test-settings"></a>Zbieranie informacji diagnostycznych za pomocą ustawień testów

Możesz użyć *ustawienia testu* w programie Visual Studio, aby zbierać dodatkowe dane podczas wykonywania testów. Na przykład można wprowadzić nagrywać wideo podczas wykonywania testu. Dostępne są adaptery danych diagnostycznych do:

-   Zbieraj każdy krok działania interfejsu użytkownika w formacie tekstowym

-   Zapisz wszystkie akcje interfejsu użytkownika do odtwarzania

-   Zbieranie informacji o systemie

-   Zbieranie danych dziennika zdarzeń

-   Zbieranie danych IntelliTrace aby pomóc wyizolować nieodtwarzalne błędy

Adaptery danych diagnostycznych można również zmienić zachowanie na komputerze testowym. Na przykład za pomocą ustawień testów w programie Visual Studio, możesz emulować różnych wąskich gardeł topologii sieci do oceny wydajności aplikacji zespołu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="use-test-settings-with-visual-studio"></a>Ustawienia testu za pomocą programu Visual Studio

Do uruchomienia danej jednostki, coded UI, wydajności sieci web lub testy obciążenia przy użyciu programu Visual Studio, możesz można dodać, skonfigurować i wybrać ustawień testu do użycia podczas uruchamiania testów. Aby uruchomić testy, zbierać dane lub zdalnie wpływać na komputer testowy, należy określić kontroler testów w ustawieniach testu. Kontroler testów ma agentów, które mogą być używane dla każdej roli w ustawieniach testu.

## <a name="diagnostic-data-adapter-details"></a>Szczegóły karty danych diagnostycznych

Poniższa tabela zawiera omówienie różnych sposobów, które można skonfigurować do użytku z rolami na komputerze lokalnym lub zdalnym adapterów danych diagnostycznych.

|Adapter danych diagnostycznych, który jest używany w ustawieniach testu|Ręczne testy na komputerze lokalnym|Testy automatyczne|Testy ręczne: Zbieranie danych przy użyciu zestawu ról i środowiska|Uwagi|
|-|-|-|-|-|
|**Serwer Proxy klienta ASP.NET dla IntelliTrace i wpływu Test:** Ten serwer proxy umożliwia zbieranie informacji na temat połączeń http od klienta do serwera sieci web dla adapterów danych diagnostycznych IntelliTrace i badanie wpływu.|Tak|Yes|Tak|— Użyj tego tylko wtedy, gdy wybrano karty danych diagnostycznych IntelliTrace lub wpływ na testowanie dla roli klienta.|
|**ASP.NET profiler:** Można utworzyć ustawienie testu zawierające profilowania, ASP.NET, która zbiera dane dotyczące wydajności w aplikacji sieci web platformy ASP.NET.|Nie|Tak (zobacz Uwagi)|Nie|— Ta karta danych diagnostycznych jest obsługiwana tylko wtedy, gdy uruchamiasz testy obciążenia w programie Visual Studio.|
|**Pokrycie kodu:** Można utworzyć ustawienie testu, zawierające informacje kodu zapotrzebowania, które są używane do badania, jaka część kodu jest objęta testami.|Nie|Tak (zobacz Uwagi)|Nie|— Możesz użyć pokrycia kodu tylko po uruchomieniu automatycznych testów z programu Visual Studio lub *mstest.exe*i tylko z komputera, na której uruchamiany jest test. Zdalne zbieranie nie jest obsługiwane.<br />— Zbierania danych pokrycie kodu nie działa, jeśli masz również ustawienie testu skonfigurowane do zbierania informacji IntelliTrace. **Uwaga:**  Ten adapter danych diagnostycznych ma zastosowanie tylko do ustawień testowych Visual Studio. Nie jest używana do ustawień testu w Microsoft Test Manager. Ponadto ta karta jest potrzeby utrzymywania zgodności z projektami testowymi programu Visual Studio 2010. **Uwaga:**  Dla zgodności pokrycie kodu ma zastosowanie, gdy testy automatyczne są uruchamiane z programu Microsoft Test Manager lub na zdalnym agencie testowym z programu Visual Studio przy użyciu starszego modułu uruchamiającego MSTest.|
|**Dziennik zdarzeń:** Można skonfigurować ustawienie testu by obejmowało gromadzenie dzienników zdarzeń, który znajduje się w wynikach testu.|Tak|Yes|Tak||
|**IntelliTrace:** Można skonfigurować adapter danych diagnostycznych dla *IntelliTrace* do zbierania informacji diagnostycznych śledzenia w celu pomocy w oddzieleniu błędów, które są trudne do odtworzenia. Spowoduje to utworzenie pliku IntelliTrace, który zawiera te informacje. Plik IntelliTrace ma rozszerzenie *.iTrace*. Gdy test zakończy się niepowodzeniem, można utworzyć usterkę. Plik IntelliTrace, który jest zapisywany łącznie z wyników testów jest automatycznie połączony z tym błędem. Dane, które są gromadzone w pliku IntelliTrace zwiększają produktywność debugowania, skracając czas wymagany do odtworzenia i diagnozy błędu w kodzie. Z tej funkcji IntelliTrace plik sesja lokalna może być symulowana na innym komputerze. Zmniejsza to ryzyko nieodtwarzalnego błędu.|Tak|Yes|Tak|— Jeśli włączysz zbierania danych funkcji IntelliTrace, zbieranie danych pokrycia kodu nie działa.<br />— Jeśli używasz narzędzia IntelliTrace dla roli klienta sieci web, możesz również wybrać serwer Proxy klienta ASP.NET dla IntelliTrace i wpływu Test adapter danych diagnostycznych.<br />-Tylko następujące wersje programu IIS są obsługiwane: IIS 7.0, IIS 7.5 and IIS 8.0.|
|**Emulacja sieci:** Można określić, że chcesz umieścić sztuczne obciążenie sieciowe w badaniu, korzystając z ustawienia testu. Emulacja sieci ma wpływ na komunikację do i z komputera poprzez emulację szybkości połączenia określonej sieci, takich jak połączenie dodzwaniane. |Nie|Tak (zobacz Uwagi)|Nie|Za pomocą adaptera danych diagnostycznych emulacji sieciowej dla roli klienta lub serwera. Nie trzeba korzystać z karty dla obu tych ról, które komunikują się ze sobą. **Uwaga:**  Ten adapter danych diagnostycznych ma zastosowanie tylko do ustawień testowych Visual Studio. Nie jest używana do ustawień testu w Microsoft Test Manager. **Uwaga:**  Emulacja sieci nie można zwiększyć szybkość połączenia sieciowego. **Ostrzeżenie:**  Jeśli dołączysz adapter danych diagnostycznych emulacji sieci w ustawieniach testu i zamierzasz używać go na komputerze lokalnym, następnie należy również powiązać sterownik emulacji sieci do jednej z kart sieciowych na komputerze. Sterownik emulacji sieci jest wymagana dla adaptera danych diagnostycznych emulacji sieciowej do funkcji. Sterownik emulacji sieci jest zainstalowany i powiązany z kartą sieciową na dwa sposoby: <ul><li>**Sterownik emulacji sieci instalowany z programu Microsoft Visual Studio Test Agent:** Visual Studio Test Agent może służyć zarówno komputerów zdalnych, jak i komputerze lokalnym. Po zainstalowaniu programu Visual Studio Test Agent, proces instalacji obejmuje krok konfiguracji, który wiąże sterownik emulacji sieci z kartą sieciową. Aby uzyskać więcej informacji, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).</li><li>**Sterownik emulacji sieci instalowany z programu Microsoft Visual Studio Test Professional:** Podczas korzystania z emulacji sieci po raz pierwszy monit powiązanie sterownika emulacji sieci z kartą sieciową.</li></ul> Można również zainstalować sterownik emulacji sieci z poziomu wiersza polecenia na komputerze lokalnym bez konieczności instalowania agenta testowego programu Visual Studio przy użyciu następującego polecenia: **VSTestConfig NETWORKEMULATION/Install** **ostrzeżenia:**  Karta emulacji sieci jest ignorowana przez testy obciążenia. Zamiast tego testy obciążenia używają ustawień, które są określone w mieszanym profilu sieciowym Scenariusz testów obciążenia.|
|**Informacje o systemie:** Ustawienia testu można skonfigurować pod kątem obejmujący informacje o systemie dotyczących urządzenia, na którym wykonywany jest test.|Tak|Yes|Tak||
|**Testowanie skutków:** Możesz zbierać informacje o tym, jakie zastosowano metody kodu aplikacji po uruchomieniu przypadku testowego. Może to służyć razem ze zmianami w kodzie aplikacji poczynionymi przez deweloperów, aby określić który test miały wpływ te zmiany deweloperskie.|Tak|Yes|Tak|— Jeśli są zbierane dane dotyczące wpływu testu dla roli klienta sieci web, możesz również wybrać serwer Proxy klienta ASP.NET dla IntelliTrace i wpływu na testowanie adaptera danych diagnostycznych.<br />-Tylko następujące wersje programu IIS są obsługiwane: IIS 7.0, IIS 7.5 and IIS 8.0.|
|**Rejestrator wideo:** Możesz utworzyć nagranie wideo swojej sesji pulpitu, kiedy przeprowadzasz test. Nagranie wideo może pomóc innym członkom zespołu wyizolować elementy aplikacji, które są trudne do odtworzenia.|Tak|Tak (zobacz Uwagi)|Tak|— Jeśli włączeniu oprogramowanie agenta testowego do uruchamiania jako procesu zamiast usługi można utworzyć nagranie wideo po uruchomieniu automatycznych testów.|