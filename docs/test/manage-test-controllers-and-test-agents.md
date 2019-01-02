---
title: Zarządzanie kontrolerami testów i agentami testowymi
ms.date: 09/18/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b687504ae69d7b133aba107c7705eeb50f6f8953
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891404"
---
# <a name="manage-test-controllers-and-test-agents"></a>Zarządzanie kontrolerami testów i agentami testowymi

Jeśli chcesz użyć programu Visual Studio, aby zdalnie uruchomić testy, rozpowszechnić testy na wielu komputerach lub uruchomić testy obciążenia, należy skonfigurować kontroler testów, agentów testowych i plik ustawień testu. W tym temacie opisano sposób zarządzania kontrolerami testów i agentami testowymi po zainstalowaniu i skonfigurowaniu ich po raz pierwszy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Jeśli używasz Microsoft Test Manager do uruchomienia testów w środowisku laboratoryjnym, możesz zarządzać kontrolerami testów i ich agentami za pomocą **Menedżera kontrolera testów** w **Centrum laboratoryjnego** dla programu Microsoft Test Manager. Ten temat dotyczy tylko wtedy, gdy używasz programu Visual Studio, aby uruchomić testy.

Aby uzyskać informacji na temat sposobu instalowania i konfigurowanie agentów testowych i kontrolerów, aby uruchomić testy w programie Visual Studio testów, zobacz [Konfigurowanie agentów testowych i kontrolerów](../test/configure-test-agents-and-controllers-for-load-tests.md).

Aby skonfigurować i monitorować kontroler testów oraz wszelkich zarejestrowanych agentów, musi mieć plik ustawień testu w projekcie testu, który zawiera testy, które chcesz uruchomić. Otwórz plik ustawień testu, wybierz polecenie **roli** i wybierz polecenie **Zarządzaj kontrolerami testów** z listy rozwijanej dla **kontrolera** pola.

Dla projektu testu obciążeniowego można także **Zarządzaj kontrolerami testów** z **Test obciążenia** menu.

## <a name="add-a-test-agent-to-a-test-controller"></a>Dodaj agenta testowego do kontrolera testów

Możesz chcieć dodać agenta testowego do innego kontrolera testów lub może być dodać agenta testowego do kontrolera testów, który właśnie zainstalowałeś.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Aby dodać agenta testowego do kontrolera testów

1. Wybierz **Start** > **Test Agent Configuration Tool**.

     **Konfigurowanie agenta testowego** zostanie wyświetlone okno dialogowe.

    > [!NOTE]
    > Konieczne jest posiadanie agenta testowego już zainstalowane, aby dodać go do kontrolera testów. Aby uzyskać więcej informacji na temat instalowania agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

2. Pojawi się informacja o jak uruchomić agenta testowego na dwa sposoby:

   - **Usługa**: Jeśli jest konieczne Uruchamianie testów automatycznych, które współdziałają z pulpitem, takich jak kodowane testy interfejsu użytkownika czy tworzenie nagrania podczas wykonywania testu, w obszarze wideo **Uruchom agenta testowego jako**, wybierz opcję **usługi**. Agent testowy zostanie uruchomiony jako usługa. Wybierz **dalej**.

      Można teraz wprowadzić szczegóły na temat użytkownika, kiedy czynnik testowy startuje jako usługa.

      1. Wprowadź nazwę w **nazwa_użytkownika**.

      2. Wprowadź hasło w **hasło**.

        |**Informacje o koncie użytkownika ważne**|
        |-|
        |-O wartości null hasła nie są obsługiwane dla kont użytkowników.|
        |— Jeśli chcesz użyć narzędzia zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.|
        |— Jeśli nazwa użytkownika agenta nie jest w usłudze agenta spróbuje ją dodać, co wymaga uprawnień na kontrolerze testów.|
        |-Użytkownik próbujący użyć kontrolera testu musi znajdować na koncie użytkownika kontrolera testów lub będzie mógł uruchamiać testów dla kontrolera.|

   - **Proces interaktywny**: Jeśli chcesz uruchomić testy automatyczne, które muszą współdziałać z pulpitem, takich jak kodowane testy interfejsu użytkownika czy tworzenie nagrania wideo podczas wykonywania testu, wybierz **procesu interaktywnego**. Agent testowy zostanie uruchomiony jako proces interaktywny, a nie jako usługa.

      Na następnej stronie wprowadź szczegółowe informacje o użytkowniku, gdy czynnik testowy startuje jako proces albo inne opcje.

      1. Wprowadź nazwę w **nazwa_użytkownika**.

      2. Wprowadź hasło w **hasło**.

        > [!NOTE]
        > Jeśli skonfigurujesz agenta testowego do uruchamiania jako interaktywnego procesu z innym użytkownikiem, który nie jest aktualnie aktywnych użytkowników, należy ponownie uruchomić komputer i zalogować się jako ten inny użytkownik, aby można było uruchomić agenta. Ponadto hasła puste nie są obsługiwane dla kont użytkowników. Jeśli chcesz użyć narzędzia zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.

      3. Aby upewnić się, że komputerze z agentem testowym można uruchomić testy po ponownym uruchomieniu, należy skonfigurować komputer do automatycznego logowania jako Użyj agenta testowego. Wybierz **automatycznego logowania**. Spowoduje to przechowywanie nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

      4. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to kolidować ze zautomatyzowanymi testami, które muszą współdziałać z pulpitem, wybierz **upewnij się, że wygaszacz ekranu jest wyłączony**.

        > [!WARNING]
        > Istnieją zagrożenia bezpieczeństwa, jeśli logujesz się automatycznie lub wyłączysz wygaszacz ekranu. Po włączeniu automatycznego logowania na, umożliwiasz innym użytkownikom, aby uruchomić ten komputer, a aby można było korzystać z konta, które loguje się automatycznie. Po wyłączeniu wygaszacza ekranu komputer może nie monitować użytkownika do logowania się do odblokowania komputera. Dzięki temu każdy dostęp do komputera, jeśli mają fizyczny dostęp do komputera. Po włączeniu tych funkcji na komputerze, należy pamiętać, że te komputery są zabezpieczony fizycznie. Na przykład komputery te znajdują się w fizycznie bezpiecznych laboratorium. (Po wyczyszczeniu **upewnij się, że wygaszacz ekranu jest wyłączony**, wygaszacz ekranu nie zostanie włączony.)

3. Aby zarejestrować tego agenta za pomocą innego kontrolera testów, wybierz pozycję **zarejestrować za pomocą kontrolera testów.** Wpisz nazwę kontrolera testów, a następnie **:** i numer portu, którego używasz w **rejestrowaniu agenta testowego z następującym kontrolerem testów**. Na przykład wpisz **agent1: 6901**.

    > [!NOTE]
    > Domyślny numer portu to 6901.

4. Aby zapisać zmiany, wybierz opcję **Zastosuj ustawienia**. Zamknij **Podsumowanie konfiguracji** okno dialogowe, a następnie Zamknij **narzędzie konfiguracji agenta testowego**.

> [!WARNING]
> Jeśli agent jest obecnie skonfigurowany do uruchamiania na innym kontrolerze testów, należy usunąć agenta testowego z tego kontrolera.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Usuń agenta testowego z kontrolera testów

Agent testowy musi być równa stanu offline, można było usunąć.

> [!NOTE]
> Nie można Użyj tej procedury, aby usunąć agentów, które są zarejestrowane z kontrolerem jako część środowiska laboratoryjnego. Aby usunąć tych agentów z kontrolerem, należy usunąć środowisko przy użyciu programu Microsoft Test Manager.

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Aby usunąć agenta testowego z kontrolerem testów

1. Jeśli kontroler testów nie jest zarejestrowany w projekcie, wykonaj następujące kroki.

    1. W programie Visual Studio Otwórz plik ustawień testu dla projektu testowego, wybierz polecenie **roli** i wybierz polecenie **Zarządzaj kontrolerami testów** z listy rozwijanej dla **kontrolera** pola.

         **Administrowanie kontrolerem testów** zostanie wyświetlone okno dialogowe.

    2. W **kontrolera** listy rozwijanej liście, wpisz nazwę komputera, na którym skonfigurowano kontroler testów. Jeśli administrowano określonym kontrolerem testów wcześniej, można wybrać nazwę z listy.

    3. W **agentów** okienku, wybierz nazwę agenta testowego. Jeśli agent jest nadal w trybie online, wybierz opcję **Offline.** Aby usunąć, wybierz opcję **Usuń**.

        > [!NOTE]
        > Usuwanie agenta testowego, po prostu usunięcie go z kontrolera testów. Aby całkowicie odinstalować agenta testowego, użyj **programy i funkcje** Panelu sterowania na komputerze agenta testowego.

2. Jeśli kontroler testów jest zarejestrowany w projekcie, Usuń agenta przy użyciu Microsoft Test Manager.

## <a name="change-the-settings-for-a-test-agent"></a>Zmień ustawienia dla agenta testowego

Stan agenta testowego może być jednym z następujących wartości:

|Stan|Opis|
|-|-----------------|
|Uruchamianie testu|Uruchamianie testów|
|Gotowe|Dostępne do uruchomienia testów lub zbierania danych i informacji diagnostycznych|
|Offline|Dostępne do uruchomienia testów lub zbierania danych i informacji diagnostycznych|
|Odłączony|Agent testowy nie jest uruchomiony.|

Można zmienić stan i inne ustawienia dla agenta testowego, korzystając z poniższych procedur.

### <a name="to-change-the-settings-of-a-test-agent"></a>Aby zmienić ustawienia agenta testowego

> [!NOTE]
> Jeśli agent testowy jest zarejestrowany na kontrolerze testów, który jest zarejestrowany w projekcie, należy zmienić ustawienia w programie Microsoft Test Manager.

1. Aby skonfigurować i monitorować kontroler testów oraz wszelkich zarejestrowanych agentów dla testu obciążenia, wybierz opcję **Test obciążenia** menu w programie Visual Studio, a następnie wybierz **Zarządzaj kontrolerami testów**. Do innych testów, otwórz plik ustawień testu dla projektu testowego w programie Visual Studio, wybierz polecenie **roli** i wybierz polecenie **Zarządzaj kontrolerami testów** z listy rozwijanej dla **kontrolera**pola.

   **Zarządzaj kontrolerem testów** zostanie otwarte okno dialogowe.

1. Wybierz nazwę kontrolera testów, którego agentów testowych chcesz zmienić na liście kontrolera testów. Jeśli kontroler testów nie ma na liście, sprawdź, czy kontroler testów jest poprawnie zarejestrowany. Aby uzyskać więcej informacji zobacz poniższą procedurę dotyczące konfigurowania kontrolera testów.

1. (Opcjonalnie) W **agenci testowi** okienku zaznacz komputerze agenta testowego, dla którego chcesz zmienić właściwości.

1. Wybierz **właściwości**.

1. Zmień następujące właściwości agenta badania zgodnie z wymaganiami:

|Właściwości agenta testowego|Opis|
|-|-----------------|
|**Wagi**|Używane do dystrybucji obciążenia, podczas korzystania z agentów testowych z różnymi poziomami osiągów. Na przykład agent testowy przy zastosowaniu wagi 100 otrzymuje dwa razy obciążenia jako agent testowy przy zastosowaniu wagi 50.|
|**Przełączanie adresów IP**|Używane do konfigurowania przełączania IP. Przełączanie IP pozwala agentowi testowemu wysyłać żądania do serwera przy użyciu zakresu adresów IP. Symuluje to wywołania, które pochodzą z różnych komputerów klienckich.<br /><br /> Przełączanie IP jest ważne, jeśli test obciążenia uzyskuje dostęp do farmy sieci web. Większość usług równoważenia obciążenia ustanawia koligację między klientem i serwerem namierzenie internetowego przy użyciu adresu IP klienta. Jeśli wszystkie żądania wydają się przychodzić od jednego klienta, moduł równoważenia obciążenia nie zrównoważy obciążenia. Aby uzyskać równowagę obciążenia w kolektywie serwerów sieci web, upewnij się, że żądania pochodzą z zakresu adresów IP. **Uwaga:**  Możesz określić kartę sieciową lub użyć **(wszystkie nieprzypisane)** Aby automatycznie wybrać taką, która obecnie nie jest używany. <br /><br /> Aby użyć funkcji przełączania IP, usługa Visual Studio Test Agent musi działać jako użytkownik w grupie Administratorzy dla tego komputera agenta. Ten użytkownik jest zaznaczany podczas instalacji agenta, ale może zostać zmieniona przez zmodyfikowanie właściwości usługi i ponowne jej uruchomienie.<br /><br /> Aby sprawdzić, czy przełączanie IP działa poprawnie, Włącz rejestrowanie na serwerze sieci web usług IIS, sprawdź, że żądania pochodzą z adresów IP, które skonfigurowano przy użyciu funkcji rejestrowania usług IIS.|
|**Atrybuty**|Zestaw par nazwa/wartość, które mogą być używane podczas wybierania agenta testowego. Na przykład test może wymagać określonego systemu operacyjnego. Możesz dodać atrybuty w **role** kartę testu pliku ustawień i może służyć do wybierania agenta testowego, który ma pasujące atrybuty. Jeśli chcesz uruchomić test na wielu komputerach, Utwórz atrybut w roli ustawień testów, który jest skonfigurowany do uruchamiania testów, a następnie skonfiguruj pasujący atrybut na każdym agencie testowym, którego chcesz użyć w tej roli... **Uwaga:**  To ustawienie jest dostępna tylko dla agentów testowych, które są zarejestrowane z kontrolerem testów, który nie jest zarejestrowany do projektu, ponieważ te atrybuty są używane tylko w ustawieniach testu dla programu Visual Studio.|

Przetestuj agenta wagę test agent atrybutów i zmiany zaczną obowiązywać natychmiast, ale nie ma wpływu na testy, które są uruchomione. Zakres adresów IP staje się skuteczny po ponownym uruchomieniu kontrolera testów.

(Opcjonalnie) Aby zmienić stan agenta testowego, wybierz agenta na liście, a następnie wybierz akcję z listy dostępnych opcji na podstawie bieżącego stanu agenta.

> [!NOTE]
> Jeśli agenta testowego jest uruchomiona jako proces, można zarządzać stanem agenta testowego z to ikonę obszaru powiadomień uruchomione na komputerze, w którym zainstalowano agenta testowego. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces, za pomocą tego narzędzia.

## <a name="configure-a-test-controller"></a>Skonfiguruj kontroler testu

Aby skonfigurować kontroler testów, należy użyć **narzędzie konfiguracji kontrolera testów zespołu**. Podczas konfigurowania kontrolera testów, możesz zarejestrować kontroler testów z innym zbiorze projektów lub wyrejestrować kontroler testów z kolekcji projektu.

Jeśli chcesz zarejestrować kontroler testów z kolekcji projektów Team Foundation Server, konto, którego używasz dla usługi kontrolera testu musi być członkiem grupy kont usług testowych kolekcji projektów dla kolekcji projektu lub konto Czy używasz do uruchamiania narzędzia konfiguracji kontrolera testów musi być administratorem kolekcji projektów.

> [!NOTE]
> Jeśli wyrejestrujesz kontroler testów z kolekcji projektu, który ma istniejące środowiska w kolekcji projektów, środowiska nadal są obsługiwane, jeśli przeniesiono tej kolekcji projektu i ponownie zarejestrować kontroler testów do tej kolekcji projektu przeniesione.

### <a name="to-configure-a-test-controller"></a>Aby skonfigurować kontroler testu

1. Aby uruchomić narzędzie, aby ponownie skonfigurować kontroler testów w dowolnym momencie, wybierz **Start** > **Test Controller Configuration Tool**.

     **Konfigurowanie kontrolera testowego** zostanie wyświetlone okno dialogowe.

2. Wybierz użytkownika do użycia jako konto logowania usługi kontrolera testowego.

    > [!NOTE]
    > Hasła puste nie są obsługiwane dla kont użytkowników.

4. (Opcjonalnie) Jeśli nie chcesz użyć kontrolera testu w środowisku laboratoryjnym, ale tylko do uruchomienia testów z programu Visual Studio, usuń zaznaczenie **Zarejestruj kontroler testów z kolekcji projektów zespołowych**.

5. (Opcjonalnie) Aby skonfigurować kontroler testu do testowania obciążenia, wybierz **Konfiguruj kontroler testów do testowania obciążenia**. Wprowadź wystąpienie programu SQL Server w ramach **wyniki testu obciążeniowego tworzenie bazy danych w następującym wystąpieniu programu SQL Server**.

> [!NOTE]
> Aby uzyskać więcej informacji o kontrolerów testów rozwiązywaniu problemów, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Zarządzanie agentów, gdy uruchamiasz testy za pomocą kontrolera testów

Po dodaniu ról dla aplikacji do ustawień testu dla programu Visual Studio, można dodać właściwości agenta dla każdej z ról. Określa, które agenty testowe są dostępne dla tej roli. Po uruchomieniu testów przy użyciu tych ustawień, kontroler testów, który został wybrany do ustawień testu określa dostępność wymaganych agentów. Są to następujące sytuacje, które mogą wystąpić po określeniu dostępności agenta:

-   Brak nie jest dostępny agent dla roli, która musi uruchamiać testy. Nie można uruchomić testy. Możesz wykonać jedną z następujących czynności, a następnie ponownie uruchom testy:

    -   Możesz poczekać, aż agent stanie się dostępny dla tej roli uruchomić testy.

    -   Jeśli istnieją agenci, którzy są w trybie offline, może służyć do tej roli, można ponownie uruchomić agenta tak, że jest ona dostępna.

    -   Można dodać innego agenta o prawidłowych właściwościach dla tej roli do kontrolera testów.

    -   Można zmienić właściwości agenta dla tej roli w ustawieniach testowych, aby włączyć innych agentów, które chcesz użyć.

-   Agent nie jest dostępny dla co najmniej jedną rolę, systemem adapterów danych diagnostycznych. Testy mogą być uruchamiane, ale nie można uruchomić adaptera danych diagnostycznych. Można uruchomić testy bez karty danych diagnostycznych lub możesz wykonać jedną z następujących czynności i ponownie uruchomić testy:

    -   Możesz poczekać, aż agent stanie się dostępny dla tych ról.

    -   Jeśli istnieją agenci, którzy są w trybie offline, który może służyć do tej roli, należy zmienić stan agenta na online za pomocą **administrowanie kontrolerem testów** na **testu** menu. Ponadto trzeba będzie ponownie uruchomić agenta, jeśli został odłączony od kontrolera.

    -   Upewnij się, że żadnych agentów, które mogą wymagać dla tego przebiegu testu nie zajęty przeprowadzaniem testów. Możesz sprawdzić stan wszelkich agentów z **administrowanie kontrolerem testów** na **testu** menu.

    -   Można dodać innego agenta o prawidłowych właściwościach dla roli do kontrolera testów.

    -   Można zmienić właściwości agenta dla roli w ustawieniach testu, aby włączyć innych agentów, których chcesz użyć.

## <a name="load-tests-from-delay-signed-assemblies"></a>Ładowanie testów z zestawów podpisanych z opóźnieniem

Agentów testowych i kontrolera testów można ładować tylko zestawy testów, które są zestawami podpisanymi, lub zestawami niepodpisanymi. Niektóre zestawy badawcze są podpisywane z opóźnieniem, ponieważ muszą mieć dostęp do zestawów produkcyjnych dla aplikacji. Jednak te zestawy nie mają silnego podpisu, ponieważ są tylko zestawami testowymi i nie są rozpowszechniane. Nie można załadować tych zestawów, ponieważ są podpisywane z opóźnieniem, więc musisz wyłączyć weryfikacją silnych nazw dla tych zestawów na wszystkich komputerach, na których zestawy będą załadowane, w tym na komputerze kontrolera testów. Aby wyłączyć weryfikację podpisu z opóźnieniem, użyj *sn.exe*. Token klucza publicznego zestawu podpisanego z opóźnieniem dla którego wymagana jest weryfikacja silnej nazwy, pominięte może również wymagać dołączenia.

Użyj *Sn.exe* (narzędzie silnych nazw), aby wyłączyć weryfikację podpisu z opóźnieniem.

Powoduje to wyłączenie Weryfikacja silnej nazwy, dla określonego zestawu, na komputerze, na którym uruchomiono polecenie. Można to zrobić tylko wtedy, gdy masz wystarczające uprawnienia.

Po zakończeniu przebiegu testu ponownie Włącz weryfikację opóźnionego podpisywania za pomocą *SN.exe* polecenia.

Zalecanym sposobem wyłączenia i ponownego włączenia weryfikacji podpisu jest użycie *SN.exe* polecenia w skryptach. Można wyłączyć weryfikację w skrypcie instalacji i ponownie Włącz weryfikację w skrypcie oczyszczania.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)