---
title: Zarządzanie kontrolerami testów i agentami testowymi
description: Dowiedz się, jak zarządzać kontrolerami testów i agentami testowymi po zainstalowaniu i skonfigurowaniu ich po raz pierwszy.
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9a416dc64a9d49d14e367a04023f067c7b595c
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329643"
---
# <a name="manage-test-controllers-and-test-agents"></a>Zarządzanie kontrolerami testów i agentami testowymi

Jeśli chcesz użyć programu Visual Studio do zdalnego uruchamiania testów, rozesłać testy na wielu maszynach lub uruchomić testy obciążenia, należy skonfigurować kontroler testów, agentów testowych i plik ustawień testu. W tym temacie opisano, jak zarządzać kontrolerami testów i agentami testowymi po zainstalowaniu i skonfigurowaniu ich po raz pierwszy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Jeśli używasz Microsoft Test Manager do uruchamiania testów w środowiskach laboratoryjnych, możesz zarządzać kontrolerami testów i ich agentami za pomocą **menedżera Test Controller** w **Centrum laboratoryjnym** dla Microsoft Test Manager. Ten temat ma zastosowanie tylko wtedy, gdy program Visual Studio jest używany do uruchamiania testów.
::: moniker-end

Aby uzyskać informacje o instalowaniu i konfigurowaniu agentów testowych i kontrolerów testów do uruchamiania testów w programie Visual Studio, zobacz [Konfigurowanie agentów testowych i kontrolerów](../test/configure-test-agents-and-controllers-for-load-tests.md).

Aby skonfigurować i monitorować kontroler testów oraz wszelkich zarejestrowanych agentów, w projekcie testowym musi znajdować się plik ustawień testu, który zawiera testy, które chcesz uruchomić. Otwórz plik ustawień testu, wybierz pozycję **rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **kontroler** .

Dla projektu testu obciążenia można również wybrać opcję **Zarządzaj kontrolerami testów** z menu **test obciążenia** .

## <a name="add-a-test-agent-to-a-test-controller"></a>Dodaj agenta testowego do kontrolera testów

Możesz chcieć dodać agenta testowego do innego kontrolera testów lub może być konieczne dodanie agenta testowego do kontrolera testów, który właśnie został zainstalowany.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Aby dodać agenta testowego do kontrolera testów

1. Wybierz **Uruchom**  >  **Narzędzie konfiguracji agenta testowego**.

     Zostanie wyświetlone okno dialogowe **Konfiguruj agenta testowego** .

    > [!NOTE]
    > Aby dodać go do kontrolera testów, należy już zainstalować agenta testowego. Aby uzyskać więcej informacji na temat sposobu instalowania agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

2. Dostępne są dwie opcje dotyczące sposobu uruchamiania agenta testowego:

   - **Usługa**: Jeśli nie musisz uruchamiać testów automatycznych, które współdziałają z pulpitem, takich jak kodowane testy interfejsu użytkownika, lub Utwórz nagrania wideo podczas przebiegu testu, w obszarze **Uruchom agenta testowego jako** wybierz pozycję **Usługa**. Agent testowy zostanie uruchomiony jako usługa. Wybierz pozycję **Next** (Dalej).

      Teraz możesz wprowadzić szczegółowe informacje o użytkowniku, gdy agent testowy uruchamia się jako usługa.

      1. Wprowadź nazwę w polu **Nazwa użytkownika**.

      2. Wprowadź hasło w polu **hasło**.

        |**Ważne informacje o koncie użytkownika**|
        |-|
        |-Hasła o wartości null nie są obsługiwane dla kont użytkowników.|
        |— Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.|
        |— Jeśli nazwa użytkownika agenta nie znajduje się w usłudze agenta, spróbuje ją dodać, co wymaga uprawnień do kontrolera testów.|
        |-Użytkownik próbujący użyć kontrolera testów musi znajdować się na koncie użytkownika kontrolera testów lub nie będzie mógł uruchamiać testów dla kontrolera.|

   - **Proces interaktywny**: Jeśli chcesz uruchomić testy automatyczne, które muszą współdziałać z pulpitem, na przykład kodowane testy interfejsu użytkownika, lub utworzyć nagrania wideo podczas wykonywania testu, wybierz pozycję **proces interaktywny**. Agent testowy zostanie uruchomiony jako proces interaktywny, a nie jako usługa.

      Na następnej stronie Wprowadź szczegółowe informacje o użytkowniku, gdy agent testowy uruchamia się jako proces i inne opcje.

      1. Wprowadź nazwę w polu **Nazwa użytkownika**.

      2. Wprowadź hasło w polu **hasło**.

        > [!NOTE]
        > W przypadku skonfigurowania agenta testowego do uruchamiania jako proces interaktywny dla innego użytkownika, który nie jest obecnie aktywnym użytkownikiem, należy ponownie uruchomić komputer i zalogować się jako inny użytkownik, aby móc uruchomić agenta. Ponadto hasła o wartości null nie są obsługiwane dla kont użytkowników. Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.

      3. Aby upewnić się, że komputer z agentem testowym może uruchamiać testy po ponownym uruchomieniu, można skonfigurować komputer do automatycznego logowania jako agent testowy. Wybierz pozycję **Zaloguj automatycznie**. Spowoduje to zapisanie nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

      4. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to zakłócać wszystkie testy automatyczne, które muszą współdziałać z pulpitem, wybierz pozycję **upewnij się, że wygaszacz ekranu jest wyłączony**.

        > [!WARNING]
        > Jeśli logujesz się automatycznie lub wyłączysz wygaszacz ekranu, występują zagrożenia bezpieczeństwa. Włączenie automatycznego logowania umożliwia innym użytkownikom uruchamianie tego komputera i korzystanie z konta, które automatycznie loguje się. Jeśli wyłączysz wygaszacz ekranu, komputer może nie monitować użytkownika o zalogowanie się w celu odblokowania komputera. Pozwala to wszystkim użytkownikom na dostęp do komputera, jeśli ma fizyczny dostęp do komputera. Jeśli te funkcje są włączone na komputerze, należy upewnić się, że te komputery są fizycznie bezpieczne. Na przykład te komputery znajdują się w fizycznie zabezpieczonym laboratorium. (Jeśli wyczyść pole wyboru **upewnij się, że wygaszacz ekranu jest wyłączony**, nie spowoduje to włączenia wygaszacza ekranu).

3. Aby zarejestrować tego agenta w innym kontrolerze testów, wybierz pozycję **zarejestruj w kontrolerze testów.** Wpisz nazwę kontrolera testów **, a następnie** numer portu, który jest używany w **zarejestrowaniu agenta testowego z następującym kontrolerem testów**. Na przykład wpisz **agenta 1:6901**.

    > [!NOTE]
    > Domyślny numer portu to 6901.

4. Aby zapisać zmiany, wybierz pozycję **Zastosuj ustawienia**. Zamknij okno dialogowe **Podsumowanie konfiguracji** , a następnie zamknij **Narzędzie konfiguracji agenta testowego**.

> [!WARNING]
> Jeśli Agent jest aktualnie skonfigurowany do uruchamiania w innym kontrolerze testów, należy usunąć agenta testowego z tego kontrolera.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Usuń agenta testowego z kontrolera testów

Przed usunięciem agenta testowego musi być ustawiony stan offline.

::: moniker range="vs-2017"
> [!NOTE]
> Nie można użyć tej procedury, aby usunąć agentów zarejestrowanych na kontrolerze w ramach środowiska laboratoryjnego. Aby usunąć tych agentów z kontrolera, należy usunąć środowisko przy użyciu Microsoft Test Manager.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Nie można użyć tej procedury, aby usunąć agentów zarejestrowanych na kontrolerze w ramach środowiska laboratoryjnego.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Aby usunąć agenta testowego z kontrolera testów

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 nie można usunąć agenta testowego, Jeśli kontroler testów jest zarejestrowany w projekcie.
::: moniker-end
Jeśli kontroler testów nie jest zarejestrowany w projekcie, wykonaj następujące kroki.

1. W programie Visual Studio Otwórz plik ustawień testu dla projektu testowego, wybierz pozycję **rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **kontroler** .

   Zostanie wyświetlone okno dialogowe **administruj Test Controller** .

2. Z listy rozwijanej **kontroler** wpisz nazwę komputera, na którym skonfigurowano kontroler testów. Jeśli wcześniej administrujesz określonym kontrolerem testów, możesz wybrać nazwę z listy.

3. W okienku **agenci** wybierz nazwę agenta testowego. Jeśli Agent jest nadal w trybie online, wybierz opcję **offline.** Aby go usunąć, wybierz pozycję **Usuń**.

   > [!NOTE]
   > Usunięcie agenta testowego tylko odkojarzy go z kontrolerem testów. Aby całkowicie odinstalować agenta testowego, należy użyć  **apletu programy i funkcje** w panelu sterowania na komputerze agenta testowego.

::: moniker range="vs-2017"
Jeśli kontroler testów jest zarejestrowany w projekcie, Usuń agenta przy użyciu Microsoft Test Manager.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Zmień ustawienia agenta testowego

Stan agenta testowego może być jedną z następujących wartości:

|Stan|Opis|
|-|-----------------|
|Uruchamianie testu|Uruchamianie testów|
|Gotowy|Dostępne do uruchamiania testów lub zbierania danych i diagnostyki|
|Tryb offline|Niedostępne do uruchamiania testów lub zbierania danych i diagnostyki|
|Odłączony|Agent testowy nie został uruchomiony|

Można zmienić stan i inne ustawienia dla agenta testowego, korzystając z poniższych procedur.

### <a name="to-change-the-settings-of-a-test-agent"></a>Aby zmienić ustawienia agenta testowego

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli agent testowy jest zarejestrowany na kontrolerze testów, który jest zarejestrowany w projekcie, Zmień ustawienia w Microsoft Test Manager.
::: moniker-end

1. Aby skonfigurować i monitorować kontroler testów oraz wszelkich zarejestrowanych agentów do testu obciążenia, wybierz menu **test obciążenia** w programie Visual Studio, a następnie wybierz **Zarządzaj kontrolerami testów**. W przypadku innych testów Otwórz plik ustawień testu dla projektu testowego w programie Visual Studio, wybierz pozycję **rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **kontroler** .

   Zostanie otwarte okno dialogowe **zarządzanie Test Controller** .

1. Wybierz nazwę kontrolera testów, którego agenci testowi chcesz zmienić na liście kontroler testów. Jeśli kontrolera testów nie ma na liście, sprawdź, czy kontroler testów jest poprawnie zarejestrowany. Aby uzyskać więcej informacji, Zobacz Poniższa procedura dotycząca konfigurowania kontrolera testów.

1. Obowiązkowe W okienku **agenci testowi** wybierz komputer agenta testowego, dla którego chcesz zmienić właściwości.

1. Wybierz pozycję **Właściwości**.

1. W razie potrzeby zmień następujące właściwości agenta testowego:

|Właściwość agenta testowego|Opis|
|-|-----------------|
|**Wagę**|Używany do dystrybucji obciążenia w przypadku korzystania z agentów testowych z różnymi poziomami wydajności. Na przykład agent testowy o wadze 100 otrzymuje dwa razy obciążenie jako agent testowy z ważeniem 50.|
|**Przełączanie adresów IP**|Służy do konfigurowania przełączania adresów IP. Przełączanie IP pozwala agentowi testowemu wysyłać żądania do serwera przy użyciu zakresu adresów IP. Symuluje to wywołania pochodzące z różnych komputerów klienckich.<br /><br /> Przełączanie IP jest ważne, jeśli test obciążenia uzyskuje dostęp do kolektywu serwerów sieci Web. Większość modułów równoważenia obciążenia ustanawia koligację między klientem a określonym serwerem sieci Web przy użyciu adresu IP klienta. Jeśli wszystkie żądania wyglądają jak pochodzą z jednego klienta, moduł równoważenia obciążenia nie będzie zrównoważyć obciążenia. Aby uzyskać dobre Równoważenie obciążenia w kolektywie serwerów sieci Web, upewnij się, że żądania pochodzą z zakresu adresów IP. **Uwaga:**  Możesz określić kartę sieciową lub użyć **(wszystkie nieprzypisane)** , aby automatycznie wybrać jedną, która aktualnie nie jest używana. <br /><br /> Aby można było korzystać z funkcji przełączania IP, usługa agenta testowego programu Visual Studio musi być uruchomiona jako użytkownik w grupie Administratorzy dla tego komputera agenta. Ten użytkownik jest wybierany podczas instalacji agenta, ale można go zmienić, modyfikując właściwości usługi i uruchamiając ją ponownie.<br /><br /> Aby sprawdzić, czy przełączanie IP działa prawidłowo, Włącz rejestrowanie usług IIS na serwerze sieci Web, użyj funkcji rejestrowania usług IIS, aby sprawdzić, czy żądania pochodzą z skonfigurowanych adresów IP.|
|**Atrybuty**|Zestaw par nazwa/wartość, które mogą być używane w wyborze agenta testowego. Na przykład test może wymagać określonego systemu operacyjnego. Można dodawać atrybuty na karcie **role** pliku ustawień testu i można ich użyć do wybrania agenta testowego, który ma pasujące atrybuty. Jeśli chcesz uruchomić test na wielu komputerach, Utwórz atrybut w roli ustawień testu, która jest skonfigurowana do uruchamiania testów, a następnie skonfiguruj pasujący atrybut na każdym agencie testowym, który ma być używany w tej roli. **Uwaga:**  To ustawienie jest dostępne tylko dla agentów testowych, które są zarejestrowane w kontrolerze testów, który nie jest zarejestrowany w projekcie, ponieważ te atrybuty są używane tylko w ustawieniach testu dla programu Visual Studio.|

Zmiany dotyczące wagi agenta testowego i agenta testowego zaczynają obowiązywać natychmiast, ale nie mają wpływu na testy, które są uruchomione. Zakres adresów IP zaczyna obowiązywać po ponownym uruchomieniu kontrolera testów.

Obowiązkowe Aby zmienić stan agenta testowego, wybierz agenta z listy, a następnie wybierz akcję z dostępnych opcji na podstawie bieżącego stanu agenta.

> [!NOTE]
> Jeśli agent testowy jest uruchomiony jako proces, można zarządzać stanem agenta testowego z ikony obszaru powiadomień, która jest uruchamiana na komputerze, na którym zainstalowano agenta testowego. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces korzystający z tego narzędzia.

## <a name="configure-a-test-controller"></a>Konfigurowanie kontrolera testów

Aby skonfigurować kontroler testów, należy użyć **Narzędzia konfiguracji kontrolera Team test**. Podczas konfigurowania kontrolera testów można zarejestrować kontroler testów z inną kolekcją projektu lub wyrejestrować kontroler testów z kolekcji projektu.

Jeśli chcesz zarejestrować kontroler testów w Team Foundation Server kolekcji projektów, konto, które jest używane dla usługi kontrolera testów, musi być członkiem grupy kont usługi testowej kolekcji projektów dla kolekcji projektów lub konto używane do uruchamiania narzędzia konfiguracji kontrolera testów musi być administratorem kolekcji projektu.

> [!NOTE]
> Jeśli wyrejestrujesz kontroler testów z kolekcji projektów, która ma istniejące środowiska w kolekcji projektu, środowiska są nadal utrzymywane, jeśli przeniesiono tę kolekcję projektów i ponownie zarejestrujesz kontroler testów w tej przesuniętej kolekcji projektów.

### <a name="to-configure-a-test-controller"></a>Aby skonfigurować kontroler testów

1. Aby uruchomić narzędzie w dowolnym momencie w celu ponownego skonfigurowania kontrolera testów, wybierz **Uruchom**  >  **Narzędzie konfiguracji Test Controller**.

     Zostanie wyświetlone okno dialogowe **konfigurowanie Test Controller** .

2. Wybierz użytkownika, który ma być używany jako konto logowania dla usługi kontrolera testów.

    > [!NOTE]
    > Hasła o wartości null nie są obsługiwane dla kont użytkowników.

4. Obowiązkowe Jeśli nie chcesz używać kontrolera testów w środowisku laboratoryjnym, ale tylko do uruchamiania testów z programu Visual Studio, wyczyść pole **Rejestruj kontroler testów z kolekcją projektu zespołowego**.

5. Obowiązkowe Aby skonfigurować kontroler testu do testowania obciążenia, wybierz pozycję **Konfiguruj kontroler testów na potrzeby testowania obciążenia**. Wprowadź wystąpienie SQL Server w obszarze **Utwórz bazę danych wyników testów obciążenia w następującym wystąpieniu SQL Server**.

> [!NOTE]
> Aby uzyskać więcej informacji o rozwiązywaniu problemów z kontrolerami testów, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Zarządzanie agentami przy uruchamianiu testów przy użyciu kontrolera testów

Po dodaniu ról dla aplikacji do ustawień testu dla programu Visual Studio, można dodać właściwości agenta dla każdej z ról. Określa, którzy agenci testowi są dostępni dla tej roli. Po uruchomieniu testów przy użyciu tych ustawień testu kontroler testów wybrany dla ustawień testu określa dostępność wymaganych agentów. Są to następujące sytuacje, które mogą wystąpić w przypadku określenia dostępności agenta:

- Brak agenta dostępnego dla roli, która musi uruchamiać testy. Nie można uruchomić testów. Można wykonać jedną z następujących czynności, a następnie ponownie uruchomić testy:

  - Możesz poczekać, aż Agent stanie się dostępny dla tej roli, aby uruchomić testy.

  - Jeśli istnieją agenci, którzy są w trybie offline, których można użyć dla tej roli, możesz ponownie uruchomić agenta, aby był dostępny.

  - Można dodać innego agenta z prawidłowymi właściwościami agenta dla tej roli do kontrolera testów.

  - Możesz zmienić właściwości agenta dla tej roli w ustawieniach testu, aby włączyć innych agentów, których chcesz użyć.

- Nie ma agenta dostępnego dla co najmniej jednej roli, która uruchamia adaptery danych diagnostycznych. Testy można uruchomić, ale nie można uruchomić adaptera danych diagnostycznych. Możesz uruchomić testy bez adaptera danych diagnostycznych lub wykonać jedną z następujących czynności i ponownie uruchomić testy:

  - Możesz poczekać, aż Agent stanie się dostępny dla tych ról.

  - Jeśli istnieją agenci, którzy są w trybie offline, których można użyć dla tej roli, należy zmienić stan agenta na online z **administrowania Test Controller** w menu **test** . Ponadto może być konieczne ponowne uruchomienie agenta, jeśli został on odłączony od kontrolera.

  - Sprawdź, czy każdy agent, który może być potrzebny do tego uruchomienia testu, nie jest zajęty uruchomionymi testami. Stan wszystkich agentów można sprawdzić, korzystając z opcji **administrowania Test Controller** w menu **test** .

  - Można dodać innego agenta z prawidłowymi właściwościami agenta dla roli do kontrolera testów.

  - Możesz zmienić właściwości agenta dla roli w ustawieniach testu, aby włączyć innych agentów, których chcesz użyć.

## <a name="load-tests-from-delay-signed-assemblies"></a>Testy obciążenia z zestawów z podpisem opóźnień

Kontroler testów i agenci testowi mogą ładować tylko zestawy testów, które są zestawami silnie podpisanymi lub niepodpisanymi zestawami. Niektóre zestawy testowe są podpisane z opóźnieniem, ponieważ muszą mieć dostęp do zestawów produkcyjnych dla aplikacji. Jednak te zestawy nie są silnie podpisane, ponieważ są tylko zestawami testowymi i nie są dystrybuowane. Nie można załadować tych zestawów, ponieważ są one podpisywane z opóźnieniem, dlatego należy wyłączyć weryfikację silnych nazw dla tych zestawów na wszystkich komputerach, na których zostanie załadowany zestaw, w tym na maszynie kontrolera testów. Aby wyłączyć weryfikację z opóźnieniem, użyj *sn.exe*. Token klucza publicznego zestawu z opóźnieniem, dla którego zażądano pominięcia weryfikacji silnej nazwy, może również być uwzględniony.

Użyj *Sn.exe* (Narzędzie silnej nazwy), aby wyłączyć weryfikację z opóźnieniem.

Spowoduje to wyłączenie weryfikacji silnej nazwy tylko dla określonego zestawu, na komputerze, na którym uruchomiono polecenie. Można to zrobić tylko, jeśli masz wystarczające uprawnienia.

Po zakończeniu przebiegu testu ponownie Włącz weryfikację opóźnionego podpisywania przy użyciu polecenia *SN.exe* .

Zalecanym sposobem wyłączenia i ponownego włączenia weryfikacji podpisywania jest użycie poleceń *SN.exe* w skryptach. Można wyłączyć weryfikację w skrypcie instalacji i ponownie włączyć weryfikację w skrypcie oczyszczania.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
