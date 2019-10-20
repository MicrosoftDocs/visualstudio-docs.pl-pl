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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ae46db2d99024b598ff655452ca748298b528a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665303"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Przypisywanie ról do kontrolera testów i agenta testowego

W tym artykule przedstawiono sposób tworzenia i konfigurowania ustawienia testu, które używa kontrolera testów i agenta testowego do dystrybucji testów na kilku komputerach przy użyciu programu Visual Studio. Przedstawiono w nim również sposób dodawania adapterów diagnostycznych i danych do ustawienia testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Utwórz testy jednostkowe lub kodowane testy interfejsu użytkownika, aby uruchomić je z ustawieniem testowym.

- Zainstaluj kontroler testów i agentów testowych. Aby uzyskać informacje na temat sposobu instalowania kontrolera testów i agentów testowych, zobacz [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Aby utworzyć i skonfigurować ustawienie testu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **elementy rozwiązania,** wskaż polecenie **Dodaj**, a następnie wybierz polecenie **nowy element**.

     Pojawi się okno dialogowe **Dodaj nowy element** .

2. W okienku **zainstalowane szablony** wybierz pozycję **Ustawienia testu**.

3. W polu **Nazwa** wpisz **TestSettingDistributedTestWalkthrough**.

4. Wybierz pozycję **Dodaj**.

     Nowy plik testu *TestSettingDistributedTestWalkthrough. testsettings* pojawia się w **Eksplorator rozwiązań**w folderze **elementy rozwiązania** .

     Zostanie wyświetlone okno dialogowe **Ustawienia testu** . Wybrana jest strona **Ogólne** .

     Możesz teraz edytować i zapisywać wartości ustawień testu.

5. W polu **Nazwa**wpisz nazwę dla ustawień testu.

6. W obszarze **Opis**wpisz **Ustawienia testu rozproszonego**.

7. Pozostaw wybrany **domyślny schemat nazewnictwa** .

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Aby przypisać role do kontrolera testów i agentów testowych

1. Wybierz **role**.

     Zostanie wyświetlona strona **role** .

2. Aby zdalnie uruchomić test, Użyj listy rozwijanej **Metoda wykonania testu** i wybierz **wykonanie zdalne**.

3. Z listy rozwijanej **kontroler** wpisz nazwę komputera [kontrolera testów](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Jeśli po raz pierwszy dodajesz kontrolera, nie ma kontrolerów wymienionych na liście rozwijanej. Lista jest wypełniana przez wcześniejsze kontrolery, które określono w innych ustawieniach testu.

4. W obszarze **role**wybierz pozycję **Dodaj**.

5. W wyróżnionym wierszu pod kolumną **Nazwa** wpisz **Test rozłożony**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Aby przypisać adapter diagnostyki i danych do ustawienia testu

1. Wybierz **dane i Diagnostyka**.

     Zostanie wyświetlona strona **dane i Diagnostyka** .

2. W obszarze **rola**Sprawdź, czy jest zaznaczona rola **test rozproszona** .

3. W obszarze **dane i Diagnostyka dla wybranej roli**wybierz pozycję **IntelliTrace** i karty **informacji o systemie** .

     Aby uzyskać informacje o tych adapterach i innych adapterach, których można użyć w ustawieniu testu, zobacz [Konfigurowanie testów jednostkowych](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Wybierz pozycję **hosty**.

5. Obowiązkowe Jeśli maszyna działa w 64-bitowej wersji systemu Microsoft Windows i został skompilowany test przy użyciu **dowolnej konfiguracji procesora** , Użyj listy rozwijanej **Uruchom test w programie 32 bit lub 64 bit** i wybierz pozycję **Uruchom testy w procesie 64-bitowym na 64-bitowym Maszyna**.

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, należy skompilować projekty testowe z dowolną konfiguracją **procesora CPU** . Następnie można uruchomić zarówno na 32-bitowym, jak i 64-bitowym agencie. Nie ma możliwości kompilowania projektów testowych z konfiguracją **64-bitową** .

6. Aby zapisać nowe ustawienia testu, wybierz pozycję **Zastosuj**.

7. Wybierz pozycję **Zamknij**.

::: moniker range="vs-2017"

8. W menu **test** wybierz pozycję **Ustawienia testu** > **Wybierz plik ustawień testu** , a następnie wybierz plik *TestSettingDistributedTestWalkthrough. testsettings* .

::: moniker-end

::: moniker range=">=vs-2019"

8. W menu **test** wybierz **pozycję Wybierz plik ustawień**. Przejdź do pliku *TestSettingDistributedTestWalkthrough. testsettings* i wybierz go.

::: moniker-end

9. Uruchom test w zwykły sposób.

     Gdy kontroler testów przetwarza testy jednostkowe i kodowane testy interfejsu użytkownika, kontroler testu dzieli testy na grupy 100 i wysyła je do maszyny agenta testowego. Na przykład jeśli masz 250 testów jednostkowych i trzech agentów testowych, pierwsze 100 testów jednostkowych zostanie wysłanych do agenta 1, następne 100 testów jednostkowych zostanie wysłanych do agenta 2, a pozostałe testy jednostkowe programu 50 będą wysyłane do agenta 3.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)