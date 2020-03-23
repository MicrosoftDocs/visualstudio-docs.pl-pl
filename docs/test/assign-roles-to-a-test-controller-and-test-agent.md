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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0ea644294ea79f1e4c044c0cebf3f427f5b672a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591193"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Przypisywanie ról do kontrolera testów i agenta testowego

W tym artykule pokazano, jak utworzyć i skonfigurować ustawienie testu, który używa kontrolera testów i agenta testowego do dystrybucji testowania na kilku komputerach przy użyciu programu Visual Studio. Pokazano również, jak dodać karty diagnostyczne i karty danych do ustawienia testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Utwórz testy jednostkowe lub kodowane testy interfejsu użytkownika do uruchomienia z ustawieniem testu.

- Zainstaluj kontroler testów i agentów testowych. Aby uzyskać informacje dotyczące instalowania kontrolera testów i agentów testowych, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Aby utworzyć i skonfigurować ustawienie testowe

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję Elementy rozwiązania,** wskaż polecenie **Dodaj**, a następnie wybierz polecenie **Nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

2. W okienku **Zainstalowane szablony** wybierz pozycję **Ustawienia testu**.

3. W polu **Nazwa** wpisz **TestSettingDistributedTestWalkthrough**.

4. Wybierz **pozycję Dodaj**.

     Nowy test *TestSettingDistributedTestWalkthrough.testsettings* plik pojawia się w **Eksploratorze rozwiązań**, w folderze **Elementy rozwiązania.**

     Zostanie wyświetlone okno dialogowe **Ustawienia testu.** Zostanie wybrana strona **Ogólne.**

     Teraz można edytować i zapisywać wartości ustawień testu.

5. W obszarze **Nazwa**wpisz nazwę ustawień testu.

6. W obszarze **Opis**wpisz **Ustawienia testu rozproszonego**.

7. Pozostaw **domyślny schemat nazewnictwa** zaznaczony.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Przypisywanie ról do kontrolera testów i agentów testowych

1. Wybierz **pozycję Role**.

     Zostanie wyświetlona strona **Role.**

2. Aby zdalnie uruchomić test, użyj listy rozwijanej **Metoda wykonywania testu** i wybierz opcję **Zdalne wykonanie.**

3. Na liście rozwijanej **Kontroler** wpisz nazwę komputera [kontrolera testów](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Jeśli jest to pierwszy raz, gdy dodajesz kontroler, na liście rozwijanej nie ma żadnych kontrolerów. Lista jest wypełniana przez poprzednie kontrolery, które zostały określone w innych ustawieniach testu.

4. W obszarze **Role**wybierz pozycję **Dodaj**.

5. W wyróżnionym wierszu w kolumnie **Nazwa** wpisz **Test rozproszony**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Aby przypisać kartę diagnostyczną i kartę danych do ustawienia testu

1. Wybierz **pozycję Dane i diagnostyka**.

     Zostanie wyświetlona strona **Dane i diagnostyka.**

2. W obszarze **Rola**sprawdź, czy wybrano rolę **testu rozproszonego.**

3. W obszarze **Dane i diagnostyka dla wybranej roli**wybierz kartę **IntelliTrace** i **Informacje o systemie.**

     Aby uzyskać informacje o tych kartach i innych kartach, których można użyć w ustawieniu testowym, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Wybierz **pozycję Hosty**.

5. (Opcjonalnie) Jeśli komputer działa w 64-bitowej wersji systemu Microsoft Windows i został skompilowany przy użyciu dowolnej konfiguracji **procesora,** użyj testu Uruchom na liście rozwijanej **procesu 32-bitowego lub 64-bitowego** i wybierz **opcję Uruchom testy w procesie 64-bitowym na komputerze 64-bitowym**.

    > [!TIP]
    > Aby uzyskać maksymalną elastyczność, należy skompilować projekty testowe z dowolną konfiguracją **procesora CPU.** Następnie można uruchomić zarówno na agentach 32-bitowych, jak i 64-bitowych. Nie ma żadnych korzyści do kompilacji projektów testowych z konfiguracją **64-bitową.**

6. Aby zapisać nowe ustawienia testu, wybierz pozycję **Zastosuj**.

7. Wybierz **pozycję Zamknij**.

::: moniker range="vs-2017"

8. W menu **Test** wybierz opcję **Ustawienia** > testu **Wybierz plik ustawień testu,** a następnie wybierz plik *TestSettingDistributedTestWalkthrough.testsettings.*

::: moniker-end

::: moniker range=">=vs-2019"

8. W menu **Test** wybierz **polecenie Wybierz plik ustawień**. Przejdź do pliku *TestSettingDistributedTestWalkthrough.testsettings* i wybierz.

::: moniker-end

9. Uruchom test jak zwykle.

     Gdy kontroler testów przetwarza testy jednostkowe i zakodowane testy interfejsu użytkownika, kontroler testów dzieli testy na grupy 100 i wysyła je do komputera agenta testowego. Na przykład jeśli masz 250 testów jednostkowych i trzech agentów testowych, pierwsze 100 testów jednostkowych zostanie wysłanych do agenta1, następne 100 testów jednostkowych zostanie wysłanych do agenta2, a pozostałe 50 testów jednostkowych zostanie wysłanych do agenta3.

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
