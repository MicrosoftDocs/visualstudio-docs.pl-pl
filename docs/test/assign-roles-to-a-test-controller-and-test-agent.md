---
title: Role kontrolera testów i agenta testowego dla testów automatycznych
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
manager: jillfra
ms.openlocfilehash: dc7936041746872fdf30ce3159506d93c378376d
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490601"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Przypisywanie ról do kontrolera testów i agenta testowego

W tym artykule przedstawiono sposób tworzenia i konfigurowania ustawienia testu, które używa kontrolera testów i agenta testowego do dystrybucji testów na kilku komputerach przy użyciu programu Visual Studio. Przedstawiono w nim również sposób dodawania adapterów diagnostycznych i danych do ustawienia testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Utwórz testy jednostkowe lub kodowane testy interfejsu użytkownika, aby uruchomić je z ustawieniem testowym.

- Zainstaluj kontroler testów i agentów testowych. Aby uzyskać informacje na temat sposobu instalowania kontrolera testów i agentów testowych, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Aby utworzyć i skonfigurować ustawienie testu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **elementy rozwiązania,** wskaż polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

2. W **zainstalowane szablony** okienku wybierz **ustawienia testu**.

3. W polu **Nazwa** wpisz **TestSettingDistributedTestWalkthrough**.

4. Wybierz **Dodaj**.

     Nowy plik testu *TestSettingDistributedTestWalkthrough. testsettings* pojawia się w **Eksplorator rozwiązań**w folderze **elementy rozwiązania** .

     **Ustawienia testu** zostanie wyświetlone okno dialogowe. **Ogólne** została zaznaczona strona.

     Można teraz edytować i zapisać wartości ustawień testu.

5. W obszarze **nazwa**, wpisz nazwę ustawień testu.

6. W obszarze **Opis**wpisz **Ustawienia testu rozproszonego**.

7. Pozostaw wybrany **domyślny schemat nazewnictwa** .

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Aby przypisać role do kontrolera testów i agentów testowych

1. Wybierz **role**.

     **Role** zostanie wyświetlona strona.

2. Aby zdalnie uruchomić test, Użyj listy rozwijanej **Metoda wykonania testu** i wybierz **wykonanie zdalne**.

3. Z listy rozwijanej **kontroler** wpisz nazwę komputera [kontrolera testów](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Jeśli po raz pierwszy dodajesz kontrolera, nie ma kontrolerów wymienionych na liście rozwijanej. Lista jest wypełniana przez wcześniejsze kontrolery, które określono w innych ustawieniach testowych.

4. W obszarze **role**wybierz pozycję **Dodaj**.

5. W wyróżnionym wierszu pod kolumną **Nazwa** wpisz **Test rozłożony**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Aby przypisać adapter diagnostyki i danych do ustawienia testu

1. Wybierz **dane i Diagnostyka**.

     **Dane i Diagnostyka** zostanie wyświetlona strona.

2. W obszarze **rola**Sprawdź, czy jest zaznaczona rola **test rozproszona** .

3. W obszarze **dane i Diagnostyka dla wybranej roli**wybierz pozycję **IntelliTrace** i karty **informacji o systemie** .

     Aby uzyskać informacje o tych adapterach i innych adapterach, których można użyć w ustawieniu testu, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Wybierzpozycję hosty.

5. Obowiązkowe Jeśli maszyna działa w 64-bitowej wersji systemu Microsoft Windows i został skompilowany test przy użyciu **dowolnej konfiguracji procesora** , Użyj listy rozwijanej **Uruchom test w programie 32 bit lub 64 bit** i wybierz pozycję **Uruchom testy w procesie 64-bitowym na 64-bitowym Maszyna**.

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, należy skompilować projekty testowe z dowolną konfiguracją **procesora CPU** . Następnie można uruchomić zarówno 32-bitowych i 64-bitowych agentów. Nie ma możliwości kompilowania projektów testowych z konfiguracją **64-bitową** .

6. Aby zapisać nowe ustawienia testu, wybierz pozycję **Zastosuj**.

7. Wybierz **Zamknij**.

::: moniker range="vs-2017"

8. W menu test wybierz opcję **Wybierz plik ustawień testu** , a następnie wybierz *TestSettingDistributedTestWalkthrough. testsettings*.

::: moniker-end

::: moniker range=">=vs-2019"

8. W **Eksploratorze testów**wybierz strzałkę na przycisku **Ustawienia** , a następnie wybierz pozycję **Wybierz plik ustawień**. Przejdź do pliku *TestSettingDistributedTestWalkthrough. testsettings* i wybierz go.

::: moniker-end

9. Uruchom test w zwykły sposób.

     Gdy kontroler testów przetwarza testy jednostkowe i kodowane testy interfejsu użytkownika, kontroler testu dzieli testy na grupy 100 i wysyła je do maszyny agenta testowego. Na przykład jeśli masz 250 testów jednostkowych i trzech agentów testowych, pierwsze 100 testów jednostkowych zostanie wysłanych do agenta 1, następne 100 testów jednostkowych zostanie wysłanych do agenta 2, a pozostałe testy jednostkowe programu 50 będą wysyłane do agenta 3.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)