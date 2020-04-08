---
title: Konfigurowanie agenta testowego
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc00598595ee3e3d958562682900bde9aad2a353
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880185"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Jak: Konfigurowanie agenta testowego do uruchamiania testów, które wchodzą w interakcję z pulpitem

::: moniker range="vs-2017"
Jeśli chcesz uruchomić automatyczne testy, które współdziałają z pulpitem, należy skonfigurować agenta do uruchamiania jako proces zamiast usługi. Na przykład jeśli chcesz uruchomić kodowany test interfejsu użytkownika zdalnie przy użyciu kontrolera testów i agenta testowego lub chcesz uruchomić test i przechwycić nagranie wideo po uruchomieniu go, należy skonfigurować agenta do uruchomienia jako proces. Podczas przypisywania agentów do ról w ustawieniach testu przy użyciu programu Visual Studio lub przypisywania agentów do ról w danym środowisku przy użyciu menedżera testów firmy Microsoft należy zmienić konfigurację dla wszystkich agentów przypisanych do ról, które muszą wchodzić w interakcje z pulpitem.
::: moniker-end
::: moniker range=">=vs-2019"
Jeśli chcesz uruchomić automatyczne testy, które współdziałają z pulpitem, należy skonfigurować agenta do uruchamiania jako proces zamiast usługi. Na przykład jeśli chcesz uruchomić kodowany test interfejsu użytkownika zdalnie przy użyciu kontrolera testów i agenta testowego lub chcesz uruchomić test i przechwycić nagranie wideo po uruchomieniu go, należy skonfigurować agenta do uruchomienia jako proces. Podczas przypisywania agentów do ról w ustawieniach testu przy użyciu programu Visual Studio należy zmienić konfigurację dla wszystkich agentów przypisanych do ról, które muszą wchodzić w interakcje z pulpitem.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Jeśli używasz Programu Microsoft Test Manager do skonfigurowania środowiska laboratoryjnego, instaluje agenta testowego. W **Kreatorze tworzenia środowiska** można określić, że chcesz skonfigurować jedną z ról do uruchamiania kodowanych testów interfejsu użytkownika.
:::moniker-end

> [!IMPORTANT]
> Komputer z uruchomionym agentem, na którym mają być uruchamiane kodowane testy interfejsu użytkownika, nie może zostać zablokowany ani mieć aktywnego wygaszacza ekranu.

Jeśli używasz kodowanych testów interfejsu użytkownika, które uruchamiają przeglądarkę, konto usługi dla agenta testowego jest używane do uruchamiania tej przeglądarki. To konto usługi musi być takie samo jak konto użytkownika, które jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest to to samo konto użytkownika, przeglądarka nie zostanie uruchomiony.

> [!IMPORTANT]
> Jeśli używasz kodowany test interfejsu użytkownika, który uruchamia przeglądarkę jako część definicji kompilacji, konto usługi dla usługi kompilacji jest używany do uruchomienia tej przeglądarki. To konto usługi musi być takie samo jak konto użytkownika, które jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest to to samo konto użytkownika, przeglądarka nie zostanie uruchomiony.

Poniższa procedura służy do konfigurowania agentów, którzy są przypisani do roli, która wykonuje zadanie, które musi wchodzić w interakcje z pulpitem.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Aby skonfigurować agenta do uruchamiania jako proces

1. Aby skonfigurować agenta testowego zainstalowanego do uruchomienia jako proces, przejdź do **narzędzia Uruchom** > **narzędzie konfiguracji agenta testowego**.

   Zostanie wyświetlone okno dialogowe **Konfigurowanie agenta testowego.**

   ![Konfigurowanie agenta testowego dla programu Visual Studio](media/configure-test-agent.png)

2. Wybierz **interaktywny proces**. Agent testowy zostanie uruchomiony jako proces zamiast usługi. Wybierz pozycję **Dalej**.

3. Wprowadź nazwę użytkownika i hasło dla użytkownika, który uruchomi proces agenta testowego.

   > [!NOTE]
   > - Użytkownik, który można dodać do rozpoczęcia procesu musi również zostać dodany jako członek grupy TeamTestAgentService na komputerze dla kontrolera testów dla tego agenta. Jeśli ten użytkownik jest bieżącym użytkownikiem, po dodaniu tego użytkownika do komputera kontrolera testów należy wylogować się lub ponownie uruchomić.
   > - Hasła zerowe nie są obsługiwane dla kont użytkowników.
   > - Jeśli chcesz użyć IntelliTrace lub karty danych emulacji sieciowej i karty diagnostycznej, konto użytkownika musi być członkiem grupy Administratorzy. Jeśli na komputerze, na który jest uruchomiony agent testowy jest uruchomiony system operacyjny, który ma najmniej uprzywilejowane konto użytkownika, należy uruchomić go jako administrator również (podwyższone). Jeśli nazwa użytkownika agenta nie znajduje się w usłudze agenta, spróbuje ją dodać, co wymaga uprawnień do kontrolera testów.
   > - Użytkownik próbujący użyć kontrolera testów musi znajdować się na koncie Użytkowników kontrolera testów lub nie będzie mógł uruchomić testów kontrolera.

4. Aby upewnić się, że komputer, który ma agenta testowego można uruchomić testy po ponownym uruchomieniu komputera, można skonfigurować komputer, aby zalogować się automatycznie jako użytkownik agenta testowego. Wybierz **pozycję Zaloguj się automatycznie**. Spowoduje to zapisanie nazwy użytkownika i hasła w zaszyfrowanej formie w rejestrze.

   > [!NOTE]
   > Po połączeniu ze środowiskiem laboratoryjnym przy użyciu pulpitu zdalnego lub połączenia opartego na gościu mogą wystąpić częste, nieoczekiwane rozłączenia. Jedną z możliwych przyczyn utraty połączenia jest skonfigurowanie urządzenia do automatycznego logowania się do sieci.

5. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to kolidować z automatycznymi testami, które muszą współdziałać z pulpitem, wybierz pozycję Upewnij się, że **wygaszacz ekranu jest wyłączony**.

   > [!WARNING]
   > Istnieje ryzyko bezpieczeństwa, jeśli zalogujesz się automatycznie lub wyłączysz wygaszacz ekranu. Włączenie automatycznego logowania umożliwia innym użytkownikom uruchamianie tego komputera i korzystanie z konta, które automatycznie się loguje. Jeśli wyłączysz wygaszacz ekranu, komputer może nie monitować o zalogowanie się użytkownika w celu odblokowania komputera. Dzięki temu każdy może uzyskać dostęp do komputera, jeśli ma fizyczny dostęp do komputera. Jeśli te funkcje zostaną włączone na komputerze, upewnij się, że te komputery są fizycznie bezpieczne. Na przykład te komputery znajdują się w fizycznie bezpiecznym laboratorium. Jeśli wyczyść **opcję Upewnij się, że wygaszacz ekranu jest wyłączony,** nie spowoduje to wygaszacza ekranu.

   Aby zmienić agenta z powrotem do uruchomienia jako usługa, można użyć tego narzędzia i wybrać **opcję Usługa**.

6. Aby zastosować zmiany, wybierz pozycję **Zastosuj ustawienia**.

   Zostanie wyświetlone okno dialogowe **Podsumowanie konfiguracji,** w których wyświetlany jest stan każdego z kroków konfigurowania agenta testowego.

7. Aby zamknąć okno dialogowe **Podsumowanie konfiguracji,** wybierz pozycję **Zamknij**. Następnie wybierz przycisk **Zamknij** ponownie, aby zamknąć **narzędzie konfiguracji agenta testowego**.

   > [!NOTE]
   > Istnieje ikona obszaru powiadomień, który działa na komputerze dla agenta testowego, który jest uruchomiony jako proces. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces za pomocą tego narzędzia. Aby uruchomić agenta testowego jako proces, jeśli nie jest uruchomiony, wybierz pozycję **Uruchom program Visual** > **Studio** > **Microsoft Visual Studio Test Agent**.

   ::: moniker range="vs-2017"
   Jeśli kontroler testów dla tego agenta testowego jest zarejestrowany w programie Team Foundation Server, stan agenta testowego działającego jako proces interaktywny jest wyświetlany w widoku **Kontrolery** w **Centrum laboratorium** dla menedżera testów firmy Microsoft. Jest on wymieniony z poprzednim symbolem gwiazdki, aby oznaczyć, że jest uruchomiony jako proces interaktywny. Aby ponownie uruchomić tego agenta testowego, należy użyć narzędzia, które działa na komputerze dla agenta testowego, a nie **widoku Kontrolery.**
   ::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)
