---
title: Zarządzanie kontrolerami testów i agentami testowymi
ms.date: 09/18/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 086601cb8cde00d63e3be85c028201922ebe5b76
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880198"
---
# <a name="manage-test-controllers-and-test-agents"></a>Zarządzanie kontrolerami testów i agentami testowymi

Jeśli chcesz użyć programu Visual Studio do zdalnego uruchamiania testów, dystrybucji testów na wielu komputerach lub uruchamiania testów obciążenia, należy skonfigurować kontroler testów, agentów testowych i plik ustawień testowych. W tym temacie opisano sposób zarządzania kontrolerami testów i agentami testowymi po zainstalowaniu i skonfigurowaniu ich po raz pierwszy.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
Jeśli używasz Programu Microsoft Test Manager do uruchamiania testów w środowiskach laboratoryjnych, zarządzasz kontrolerami testów i ich agentami za pomocą **Menedżera kontrolerów testów** w **Centrum laboratorium** dla Menedżera testów firmy Microsoft. Ten temat ma zastosowanie tylko wtedy, gdy do uruchamiania testów jest używany program Visual Studio.
::: moniker-end

Aby uzyskać informacje dotyczące instalowania i konfigurowania agentów testowych i kontrolerów testów do uruchamiania testów w programie Visual Studio, zobacz [Konfigurowanie agentów testowych i kontrolerów](../test/configure-test-agents-and-controllers-for-load-tests.md).

Aby skonfigurować i monitorować kontroler testów i wszystkich zarejestrowanych agentów, musisz mieć plik ustawień testu w projekcie testowym, który zawiera testy, które chcesz uruchomić. Otwórz plik ustawień testu, wybierz pozycję **Rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **Kontroler.**

W przypadku projektu testu obciążenia można również wybrać **polecenie Zarządzaj kontrolerami testów** z menu **Testuj obciążenie.**

## <a name="add-a-test-agent-to-a-test-controller"></a>Dodawanie agenta testowego do kontrolera testów

Warto dodać agenta testowego do innego kontrolera testów lub może być trzeba dodać agenta testowego do kontrolera testów, który właśnie został zainstalowany.

### <a name="to-add-a-test-agent-to-a-test-controller"></a>Aby dodać agenta testowego do kontrolera testów

1. Wybierz **polecenie Uruchom** > **narzędzie konfiguracji agenta testowego**.

     Zostanie wyświetlone okno dialogowe **Konfigurowanie agenta testowego.**

    > [!NOTE]
    > Aby dodać go do kontrolera testów, musi być już zainstalowany agent testowy. Aby uzyskać więcej informacji na temat instalowania agenta testowego, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

2. Zostaną wyświetlone dwie opcje uruchamiania agenta testowego:

   - **Usługa**: Jeśli nie trzeba uruchamiać automatycznych testów, które współdziałają z pulpitem, takich jak kodowane testy interfejsu użytkownika lub tworzenie nagrywania wideo po uruchomieniu testu, w obszarze **Uruchom agenta testowego jako**, wybierz **usługę**. Agent testowy zostanie uruchomiony jako usługa. Wybierz pozycję **Dalej**.

      Teraz można wprowadzić szczegóły dotyczące użytkownika, gdy agent testowy uruchamia się jako usługa.

      1. Wprowadź nazwę w pliku **Nazwa użytkownika**.

      2. Wprowadź hasło w pliku **Password**.

        |**Ważne informacje o koncie użytkownika**|
        |-|
        |- Hasła null nie są obsługiwane dla kont użytkowników.|
        |- Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.|
        |- Jeśli nazwa użytkownika agenta nie znajduje się w usłudze agenta, spróbuje ją dodać, co wymaga uprawnień do kontrolera testów.|
        |- Użytkownik, który próbuje użyć kontrolera testów musi znajdować się na koncie Użytkowników kontrolera testów lub nie będzie mógł uruchomić testów przeciwko kontrolerowi.|

   - **Proces interaktywny:** Jeśli chcesz uruchomić zautomatyzowane testy, które muszą wchodzić w interakcje z pulpitem, takie jak kodowane testy interfejsu użytkownika lub tworzenie nagrywania wideo po uruchomieniu testu, wybierz opcję **Proces interaktywny**. Agent testowy zostanie uruchomiony jako proces interaktywny zamiast usługi.

      Na następnej stronie wprowadź szczegóły dotyczące użytkownika, gdy agent testowy uruchamia się jako proces i inne opcje.

      1. Wprowadź nazwę w pliku **Nazwa użytkownika**.

      2. Wprowadź hasło w pliku **Password**.

        > [!NOTE]
        > Jeśli skonfigurować agenta testowego do uruchamiania jako proces interaktywny z innym użytkownikiem, który nie jest aktualnie aktywnym użytkownikiem, należy ponownie uruchomić komputer i zalogować się jako ten inny użytkownik, aby móc uruchomić agenta. Ponadto hasła null nie są obsługiwane dla kont użytkowników. Jeśli chcesz użyć modułu zbierającego IntelliTrace lub emulacji sieci, konto użytkownika musi być członkiem grupy Administratorzy.

      3. Aby upewnić się, że komputer, który ma agenta testowego, może uruchamiać testy po ponownym uruchomieniu, można skonfigurować komputer do automatycznego logowania jako używanego przez agenta testowego. Wybierz **pozycję Zaloguj się automatycznie**. Spowoduje to zapisanie nazwy użytkownika i hasła w zaszyfrowanej formie w rejestrze.

      4. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to kolidować z automatycznymi testami, które muszą współdziałać z pulpitem, wybierz pozycję Upewnij się, że **wygaszacz ekranu jest wyłączony**.

        > [!WARNING]
        > Istnieje ryzyko bezpieczeństwa, jeśli zalogujesz się automatycznie lub wyłączysz wygaszacz ekranu. Włączenie automatycznego logowania umożliwia innym użytkownikom uruchamianie tego komputera i korzystanie z konta, które automatycznie się loguje. Jeśli wyłączysz wygaszacz ekranu, komputer może nie monitować o zalogowanie się użytkownika w celu odblokowania komputera. Dzięki temu każdy może uzyskać dostęp do komputera, jeśli ma fizyczny dostęp do komputera. Jeśli te funkcje zostaną włączone na komputerze, upewnij się, że te komputery są fizycznie bezpieczne. Na przykład te komputery znajdują się w fizycznie bezpiecznym laboratorium. (Jeśli **wyczyszczysz wygaszacz ekranu jest wyłączony,** nie spowoduje to wygaszacz ekranu).

3. Aby zarejestrować tego agenta z innym kontrolerem testów, wybierz zarejestruj **się za pomocą kontrolera testów.** Wpisz nazwę kontrolera testów, a **następnie:** i numer portu, którego używasz w **Zarejestruj agenta testowego z następującym kontrolerem testów**. Na przykład wpisz **agent1:6901**.

    > [!NOTE]
    > Domyślny numer portu to 6901.

4. Aby zapisać zmiany, wybierz pozycję **Zastosuj ustawienia**. Zamknij okno dialogowe **Podsumowanie konfiguracji,** a następnie zamknij **narzędzie konfiguracji agenta testowego**.

> [!WARNING]
> Jeśli agent jest obecnie skonfigurowany do uruchamiania na innym kontrolerze testów, należy usunąć agenta testowego z tego kontrolera.

## <a name="remove-a-test-agent-from-a-test-controller"></a>Usuwanie agenta testowego z kontrolera testów

Agent testowy musi być ustawiony na stan offline, zanim będzie można go usunąć.

::: moniker range="vs-2017"
> [!NOTE]
> Tej procedury nie można użyć do usuwania agentów, które są zarejestrowane w kontrolerze jako część środowiska laboratoryjnego. Aby usunąć tych agentów z kontrolera, należy usunąć środowisko za pomocą menedżera testów firmy Microsoft.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Tej procedury nie można użyć do usuwania agentów, które są zarejestrowane w kontrolerze jako część środowiska laboratoryjnego.
::: moniker-end

### <a name="to-remove-a-test-agent-from-a-test-controller"></a>Aby usunąć agenta testowego z kontrolera testów

::: moniker range=">=vs-2019"
W programie Visual Studio 2019 nie można usunąć agenta testowego, jeśli kontroler testów jest zarejestrowany w projekcie.
::: moniker-end
Jeśli kontroler testów nie jest zarejestrowany w projekcie, wykonaj następujące kroki.

1. W programie Visual Studio otwórz plik ustawień testu dla projektu testowego wybierz pozycję **Rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **Kontroler.**

   Zostanie wyświetlone okno dialogowe **Administruj kontrolerem** testów.

2. Na liście rozwijanej **Kontroler** wpisz nazwę komputera, na którym skonfigurowany jest kontroler testów. Jeśli wcześniej podawano określony kontroler testów, można wybrać nazwę z listy.

3. W okienku **Agenci** wybierz nazwę agenta testowego. Jeśli agent jest nadal w trybie online, wybierz pozycję **Offline.** Aby go usunąć, wybierz pozycję **Usuń**.

   > [!NOTE]
   > Usunięcie agenta testowego po prostu usuwa go z kontrolera testów. Aby całkowicie odinstalować agenta testowego, użyj Panelu sterowania **programy i funkcje** na komputerze agenta testowego.

::: moniker range="vs-2017"
Jeśli kontroler testów jest zarejestrowany w projekcie, usuń agenta przy użyciu menedżera testów firmy Microsoft.
::: moniker-end

## <a name="change-the-settings-for-a-test-agent"></a>Zmienianie ustawień agenta testowego

Stan agenta testowego może być jedną z następujących wartości:

|Stan|Opis|
|-|-----------------|
|Test uruchomiony|Uruchamianie testów|
|Gotowy|Dostępne do uruchamiania testów lub zbierania danych i diagnostyki|
|W trybie offline|Niedostępne do uruchamiania testów lub zbierania danych i diagnostyki|
|Odłączony|Agent testowy nie został uruchomiony|

Można zmienić stan i inne ustawienia dla agenta testowego, korzystając z następujących procedur.

### <a name="to-change-the-settings-of-a-test-agent"></a>Aby zmienić ustawienia agenta testowego

::: moniker range="vs-2017"
> [!NOTE]
> Jeśli agent testowy jest zarejestrowany na kontrolerze testów zarejestrowanym w projekcie, zmień ustawienia w programie Microsoft Test Manager.
::: moniker-end

1. Aby skonfigurować i monitorować kontroler testów i wszystkich zarejestrowanych agentów dla testu obciążenia, wybierz menu **Testuj obciążenie** w programie Visual Studio, a następnie wybierz polecenie **Zarządzaj kontrolerami testów**. W przypadku innych testów otwórz plik ustawień testu dla projektu testowego w programie Visual Studio, wybierz pozycję **Rola** i wybierz pozycję **Zarządzaj kontrolerami testów** z listy rozwijanej dla pola **Kontroler.**

   Zostanie otwarte okno dialogowe **Zarządzanie kontrolerem testów.**

1. Wybierz nazwę kontrolera testów, których agentów testowych chcesz zmienić na liście kontrolera testów. Jeśli kontroler testów nie pojawia się na liście, sprawdź, czy kontroler testu jest poprawnie zarejestrowany. Aby uzyskać więcej informacji, zobacz poniższą procedurę dotyczącą konfigurowania kontrolera testów.

1. (Opcjonalnie) W okienku **Agenci testowania** wybierz komputer agenta testowego, dla którego chcesz zmienić właściwości.

1. Wybierz pozycję **Właściwości**.

1. W razie potrzeby zmień następujące właściwości agenta testowego:

|Właściwość agenta testowego|Opis|
|-|-----------------|
|**Ważenia**|Służy do dystrybucji obciążenia podczas korzystania z agentów testowych o różnych poziomach wydajności. Na przykład agent testowy o wadze 100 otrzymuje dwa razy więcej niż jako środek testowy o wadze 50.|
|**Przełączanie IP**|Służy do konfigurowania przełączania IP. Przełączanie adresów IP umożliwia agentowi testowe wysyłanie żądań do serwera przy użyciu zakresu adresów IP. Symuluje wywołania pochodzące z różnych komputerów klienckich.<br /><br /> Przełączanie adresów IP jest ważne, jeśli test obciążenia uzyskuje dostęp do farmy internetowej. Większość modułów równoważenia obciążenia ustanawia koligacji między klientem a określonym serwerem sieci web przy użyciu adresu IP klienta. Jeśli wszystkie żądania wydają się pochodzić z jednego klienta, moduł równoważenia obciążenia nie zrównoważy obciążenia. Aby uzyskać dobre równoważenie obciążenia w farmie sieci web, upewnij się, że żądania pochodzą z zakresu adresów IP. **Uwaga:**  Można określić kartę sieciową lub użyć **(Wszystkie nieprzypisane),** aby automatycznie wybrać kartę, która nie jest obecnie używana. <br /><br /> Aby korzystać z funkcji przełączania adresów IP, usługa programu Visual Studio Test Agent musi być uruchomiona jako użytkownik w grupie Administratorzy dla tego komputera agenta. Ten użytkownik jest wybierany podczas konfigurowania agenta, ale można go zmienić, modyfikując właściwości usługi i uruchamiając ją ponownie.<br /><br /> Aby sprawdzić, czy przełączanie adresów IP działa poprawnie, włącz rejestrowanie usług IIS na serwerze sieci web, użyj funkcji rejestrowania usług IIS, aby sprawdzić, czy żądania pochodzą ze skonfigurowanych adresów IP.|
|**Atrybuty**|Zestaw par nazw/wartości, które mogą być używane w wyborze agenta testowego. Na przykład test może wymagać określonego systemu operacyjnego. Można dodać atrybuty na karcie **Role** pliku ustawień testu i mogą być używane do wybierania agenta testowego, który ma pasujące atrybuty. Jeśli chcesz uruchomić test na wielu komputerach, utwórz atrybut w roli ustawień testu, który jest skonfigurowany do uruchamiania testów, a następnie skonfiguruj pasujący atrybut dla każdego agenta testowego, którego chcesz użyć w tej roli.. **Uwaga:**  To ustawienie jest dostępne tylko dla agentów testowych, którzy są zarejestrowani przy użyciu kontrolera testów, który nie jest zarejestrowany w projekcie, ponieważ te atrybuty są używane tylko w ustawieniach testu programu Visual Studio.|

Zmiany atrybutu agenta testowego i agenta testowego wchodzą w życie natychmiast, ale nie mają wpływu na uruchomione testy. Zakres adresów IP staje się skuteczny po ponownym uruchomieniu kontrolera testów.

(Opcjonalnie) Aby zmienić stan agenta testowego, wybierz agenta na liście, a następnie wybierz akcję z dostępnych wyborów na podstawie bieżącego stanu agenta.

> [!NOTE]
> Jeśli agent testowy jest uruchomiony jako proces, można zarządzać stan agenta testowego z ikony obszaru powiadomień, który działa na komputerze, na którym jest zainstalowany agent testowy. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces za pomocą tego narzędzia.

## <a name="configure-a-test-controller"></a>Konfigurowanie kontrolera testów

Aby skonfigurować kontroler testów, należy użyć **narzędzia konfiguracji kontrolera testów zespołowych**. Podczas konfigurowania kontrolera testów, można zarejestrować kontroler testów z innej kolekcji projektu lub wyrejestrować kontrolera testów z kolekcji projektu.

Jeśli chcesz zarejestrować kontroler testów w kolekcji projektów team foundation server, konto używane dla usługi kontrolera testów musi być członkiem grupy Konta usługi testowej kolekcji projektu dla kolekcji projektu lub konto używane do uruchamiania narzędzia konfiguracji kontrolera testów musi być administratorem kolekcji projektu.

> [!NOTE]
> Jeśli wyrejestrujesz kontroler testów z kolekcji projektu, która ma istniejące środowiska w kolekcji projektów, środowiska są nadal obsługiwane, jeśli przeniesiono tę kolekcję projektu i ponownie zarejestrujesz kontroler testów do tej przeniesionej kolekcji projektu.

### <a name="to-configure-a-test-controller"></a>Aby skonfigurować kontroler testów

1. Aby uruchomić narzędzie do ponownego skonfigurowania kontrolera testów w dowolnym momencie, wybierz polecenie **Uruchom** > **narzędzie konfiguracji kontrolera testów**.

     Zostanie wyświetlone okno dialogowe **Konfigurowanie kontrolera testów.**

2. Wybierz użytkownika, który ma być używany jako konto logowania dla usługi kontrolera testów.

    > [!NOTE]
    > Hasła zerowe nie są obsługiwane dla kont użytkowników.

4. (Opcjonalnie) Jeśli nie chcesz używać kontrolera testów w środowisku laboratoryjnym, ale tylko do uruchamiania testów z programu Visual Studio, wyczyść **kontroler testu rejestru z team project collection.**

5. (Opcjonalnie) Aby skonfigurować kontroler testów do testowania obciążenia, wybierz pozycję **Konfiguruj kontroler testów do testowania obciążenia**. Wprowadź wystąpienie programu SQL Server w obszarze **Tworzenie bazy danych wyników testu obciążenia w następującym wystąpieniu programu SQL Server**.

> [!NOTE]
> Aby uzyskać więcej informacji o rozwiązywaniu problemów dotyczących kontrolerów testów, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="manage-your-agents-when-you-run-your-tests-with-a-test-controller"></a>Zarządzanie agentami po uruchomieniu testów za pomocą kontrolera testów

Po dodaniu ról dla aplikacji do ustawień testu dla programu Visual Studio, można dodać właściwości agenta dla każdej z ról. Określa, które agenci testowi są dostępne dla tej roli. Po uruchomieniu testów przy użyciu tych ustawień testu, kontroler testów, który jest wybrany dla ustawień testu określa dostępność wymaganych agentów. Są to następujące sytuacje, które mogą wystąpić, gdy określa się dostępność agenta:

- Nie ma agenta dostępne dla roli, która musi uruchomić testy. Nie można uruchomić testów. Można wykonać jedną z następujących akcji, a następnie ponownie uruchomić testy:

  - Można poczekać, aż agent staną się dostępne dla tej roli do uruchomienia testów.

  - Jeśli istnieją jakieś agentów, które są w trybie offline, które mogą być używane dla tej roli, można ponownie uruchomić agenta, tak aby był dostępny.

  - Można dodać innego agenta z właściwościami agenta poprawne dla tej roli do kontrolera testów.

  - Można zmienić właściwości agenta dla tej roli w ustawieniach testu, aby włączyć innych agentów, których chcesz użyć.

- Nie ma agenta dostępne dla jednej lub więcej ról, które uruchamiają karty danych diagnostycznych. Testy można uruchomić, ale nie można uruchomić karty danych diagnostycznych. Testy można uruchomić bez karty danych diagnostycznych lub wykonać jedną z następujących akcji i ponownie uruchomić testy:

  - Możesz poczekać, aż agent stanie się dostępny dla tych ról.

  - Jeśli istnieją jakieś agentów, które są w trybie offline, które mogą być używane dla tej roli, należy zmienić stan agenta w trybie online z **Administruj kontrolerem testów** w menu **testowym.** Ponadto może być konieczne ponowne uruchomienie agenta, jeśli został odłączony od kontrolera.

  - Sprawdź, czy wszystkie agentów, które mogą być potrzebne do tego uruchomienia testu nie są zajęte uruchamianie testów. Stan wszystkich agentów z **administruj kontrolerem testów** można sprawdzić w menu **Test.**

  - Można dodać innego agenta z właściwościami agenta poprawne dla roli do kontrolera testów.

  - Można zmienić właściwości agenta dla roli w ustawieniach testu, aby włączyć innych agentów, których chcesz użyć.

## <a name="load-tests-from-delay-signed-assemblies"></a>Testy obciążenia z zestawów z opóźnieniem

Kontroler testów i agentów testowych można załadować tylko zestawy testowe, które są silnie podpisane zestawy lub niepodpisane zestawy. Niektóre zestawy testowe są podpisane z opóźnieniem, ponieważ muszą mieć dostęp do zestawów produkcyjnych dla aplikacji. Jednak te zestawy nie są silnie podpisane, ponieważ są tylko zestawy testowe i nie są dystrybuowane. Nie można załadować tych zestawów, ponieważ są one podpisane z opóźnieniem, dlatego należy wyłączyć weryfikację silnej nazwy dla tych zestawów na wszystkich maszynach, na których zostanie załadowany zestaw, w tym na komputerze kontrolera testów. Aby wyłączyć weryfikację podpisaną z opóźnieniem, użyj *pliku sn.exe*. Może być również konieczne uwzględnienie tokenu klucza publicznego zestawu podpisanego z opóźnieniem, dla którego wymagana jest weryfikacja silnej nazwy.

Użyj *sn.exe* (narzędzie Silne imię i nazwisko), aby wyłączyć weryfikację podpisaną z opóźnieniem.

Spowoduje to wyłączenie weryfikacji silnej nazwy, tylko dla określonego zestawu, na komputerze, na którym uruchomisz polecenie. Można to zrobić tylko wtedy, gdy masz wystarczające uprawnienia.

Po zakończeniu testu ponownie włącz weryfikację opóźnionego podpisywania za pomocą polecenia *SN.exe.*

Zalecanym sposobem wyłączenia i ponownego włączenia weryfikacji podpisywania jest użycie poleceń *SN.exe* w skryptach. Weryfikację można wyłączyć w skrypcie konfiguracji i ponownie włączyć weryfikację w skrypcie oczyszczania.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
