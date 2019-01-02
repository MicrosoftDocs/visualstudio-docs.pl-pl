---
title: Przypisz role do kontrolera testów i agenta testowego, potrzeby testowania automatycznego
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: a3904efd69763a096504922ee233a927ba69ed8f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847038"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Przypisywanie ról do testów kontrolera i agenta testowego

W tym instruktażu pokazano, jak utworzyć i skonfigurować ustawienie testu, która używa kontrolera testów i agenta testowego do dystrybucji testu na kilku komputerach przy użyciu programu Visual Studio. Ponadto w tym instruktażu przedstawiono sposób dodawania adapterów diagnostycznych i danych w ustawieniach testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

-   Utwórz testy jednostkowe lub kodowane testy interfejsu użytkownika do uruchamiania z ustawieniami testów.

-   Zainstaluj agentów testowych i kontrolera testów. Aby uzyskać informacje o sposobie instalowania kontrolera testów i agentów testowych, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Aby utworzyć i skonfigurować ustawienia testu

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **elementy rozwiązania** wskaż **Dodaj**, a następnie wybierz **nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

2.  W **zainstalowane szablony** okienku wybierz **ustawienia testu**.

3.  W **nazwa** wpisz **TestSettingDistributedTestWalkthrough**.

4.  Wybierz **Dodaj**.

     Nowy test *TestSettingDistributedTestWalkthrough.testsettings* plik pojawia się w **Eksploratora rozwiązań**w obszarze **elementy rozwiązania** folderu.

     **Ustawienia testu** zostanie wyświetlone okno dialogowe. **Ogólne** została zaznaczona strona.

     Można teraz edytować i zapisać wartości ustawień testu.

    > [!NOTE]
    > Wszystkich ustawień testu, tworzonych jest wymieniony jako wyborem dla **zaznacz aktywne ustawienia testu** i **Edytuj ustawienia testu** opcji na **Test** menu.

5.  W obszarze **nazwa**, wpisz nazwę ustawień testu.

6.  W obszarze **opis**, typ **ustawienia testu rozłożonego**.

7.  Pozostaw **domyślny schemat nazewnictwa** wybrane.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Aby przypisać role do kontrolera i testu agentów testowych

1.  Wybierz **role**.

     **Role** zostanie wyświetlona strona.

2.  Aby zdalnie uruchomić test, należy użyć **metoda wykonania testu** listy rozwijanej i wybierz pozycję **zdalne wykonywanie kodu**.

3.  W **kontrolera** listy rozwijanej liście, wpisz nazwę komputera [kontroler testów](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Jest to po raz pierwszy dodajesz kontrolera, czy nie ma kontrolerów wymienionych na liście rozwijanej. Lista jest wypełniana przez wcześniejsze kontrolery, które określono w innych ustawieniach testowych.

4.  W obszarze **role**, wybierz **Dodaj**.

5.  W wierszu wyróżnionym poniżej **nazwa** wpisz **test rozłożony**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Aby przypisać kartę danych diagnostycznych do ustawień testu

1.  Wybierz **dane i Diagnostyka**.

     **Dane i Diagnostyka** zostanie wyświetlona strona.

2.  W obszarze **roli**, upewnij się, że **test rozłożony** zaznaczona została rola.

3.  W obszarze **dane i Diagnostyka dla wybierz rolę**, wybierz opcję **IntelliTrace** i **informacje o systemie** kart.

     Aby uzyskać informacje o tych adapterach i innych adapterach, których można użyć w ustawieniach testów, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4.  Wybierz **hosty**.

5.  (Opcjonalnie) Jeśli komputer działa w 64-bitowej wersji systemu Microsoft Windows i skompilowano test przy użyciu **dowolny Procesor** konfiguracji, użyj **Uruchom test w procesie 32-bitowym lub 64-bitowym** listy rozwijanej i wybierz pozycję **Uruchom testy w procesie 64-bitowym na komputerze 64-bitowym**.

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, należy skompilować testowane projekty z **dowolny Procesor** konfiguracji. Następnie można uruchomić zarówno 32-bitowych i 64-bitowych agentów. Nie posiada zalet kompilowanie projektów testowych mających **64-bitowych** konfiguracji.

6.  Aby zapisać nowe ustawienia testu, wybierz **Zastosuj**.

7.  Wybierz **Zamknij**.

8.  W Test menu wybierz **wybierz aktywne ustawienia testów** , a następnie wybierz **TestSettingDistributedTestWalkthrough.testsettings**.

9. Uruchom test w zwykły sposób.

     Gdy kontroler testów przetwarza testy jednostkowe i kodowane testy interfejsu użytkownika, kontroler testu dzieli testy na grupy po 100 i wysyła je na komputer agenta testowego. Na przykład jeśli masz 250 jednostek testów i trzech dostępnych agentów testowych, 100 pierwszych jednostek testów, zostanie wysłanych do agenta 1, następne 100 testów, które będą wysyłane do agenta 2, a pozostałe 50 testów, które będą wysyłane do agenta 3.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)