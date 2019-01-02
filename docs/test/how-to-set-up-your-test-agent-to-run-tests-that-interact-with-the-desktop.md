---
title: Skonfiguruj agenta testowego
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5fdfa625404ff934faf8e8901bf133d6bc7f873f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968569"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem

Jeśli chcesz uruchomić testy automatyczne, które współdziałają z pulpitem, musi skonfigurować agenta do uruchamiania jako procesu zamiast usługi. Na przykład jeśli chcesz uruchomić kodowany test interfejsu użytkownika zdalnie przy użyciu kontrolera testów i agenta testowego lub chcesz uruchomić test i przechwytywać nagrania, po uruchomieniu wideo, możesz ustawić agenta do uruchamiania jako proces. Podczas przypisywania agentów do ról w ustawieniach testu przy użyciu programu Visual Studio lub podczas przypisywania agentów do ról w Twoim środowisku za pomocą programu Microsoft Test Manager, możesz zmienić ustawienia dla wszelkich agentów przypisanych do ról, które muszą współdziałać z pulpitem.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Jeśli używasz Microsoft Test Manager do skonfigurowania środowiska laboratoryjnego, instaluje agenta testowego. Można określić w **kreatorze tworzenia środowiska** chcesz skonfigurować jedną z ról, aby uruchamiać kodowane testy interfejsu użytkownika.

> [!IMPORTANT]
> Komputera, na którym jest uruchomiony agent, na którym chcesz uruchomić kodowane testy interfejsu użytkownika nie może być zablokowany lub masz aktywnego wygaszacza ekranu.

Jeśli używasz kodowanych testów interfejsu użytkownika, które uruchamiają przeglądarkę, konto usługi dla agenta testowego jest używany do uruchomienia tej przeglądarki. To konto usługi musi być taka sama, jak konto użytkownika, który jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest tego samego konta użytkownika, przeglądarka nie zostanie uruchomiona.

> [!IMPORTANT]
> Jeśli korzystasz z kodowanego testu interfejsu użytkownika, który uruchamia przeglądarkę jako część definicji kompilacji, konto usługi dla usługi kompilacji jest używany do uruchomienia tej przeglądarki. To konto usługi musi być taka sama, jak konto użytkownika, który jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest tego samego konta użytkownika, przeglądarka nie zostanie uruchomiona.

Użyj poniższej procedury do ustawiania agentów, które są przypisane do roli, która wykonuje zadanie, które musi współdziałać z pulpitem.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Aby skonfigurować agenta do uruchamiania jako procesu

1. Aby skonfigurować agenta testowego ma zainstalowany do uruchamiania jako proces, przejdź do **Start** > **narzędzie konfiguracji agenta testowego**.

   **Konfigurowanie agenta testowego** zostanie wyświetlone okno dialogowe.

   ![Skonfiguruj agenta testowego programu Visual Studio](media/configure-test-agent.png)

2. Wybierz **procesu interaktywnego**. Agent testowy zostanie uruchomiony jako proces a nie jako usługa. Wybierz **dalej**.

3. Wprowadź nazwę użytkownika i hasło dla użytkownika, który uruchomi proces agenta testowego.

   > [!NOTE]
   > - Użytkownik, który dodasz do rozpoczęcia procesu musi być również dodany jako członek grupy TeamTestAgentService na komputerze dla kontrolera testów dla tego agenta. Jeśli ten użytkownik jest bieżącym użytkownikiem, gdy ten użytkownik zostanie dodany do komputera kontrolera testu, musisz się wylogować lub ponowne uruchomienie.
   > - Hasła puste nie są obsługiwane dla kont użytkowników.
   > - Jeśli chcesz użyć IntelliTrace lub danych emulacji sieci i adaptera diagnostycznego, konto użytkownika musi być członkiem grupy Administratorzy. Jeśli komputer, na którym jest uruchomiony agent testowy jest uruchomiony systemu operacyjnego zawierającego najmniej uprzywilejowane konto użytkownika, należy również uruchomić jako administrator (podniesione uprawnienia). Jeśli nazwa użytkownika agenta nie jest w usłudze agenta spróbuje ją dodać, co wymaga uprawnień na kontrolerze testów.
   > - Użytkownik próbujący użyć kontrolera testu musi znajdować na koncie użytkownika kontrolera testów lub nie będzie mógł uruchamiać testów dla kontrolera.

4. Aby upewnić się, że komputerze z agentem testowym można uruchomić testy po ponownym uruchomieniu, należy skonfigurować komputer do automatycznego logowania jako użytkownika agenta testowego. Wybierz **automatycznego logowania**. Spowoduje to przechowywanie nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

   > [!NOTE]
   > Po nawiązaniu połączenia środowiskiem laboratoryjnym przy użyciu pulpitu zdalnego lub połączenia, mogą wystąpić częste, nieoczekiwane rozłącza. Jedną z możliwych przyczyn utraty połączenia jest, że komputer jest skonfigurowany do automatycznego logowania do sieci.

5. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to kolidować ze zautomatyzowanymi testami, które muszą współdziałać z pulpitem, wybierz **upewnij się, że wygaszacz ekranu jest wyłączony**.

   > [!WARNING]
   > Istnieją zagrożenia bezpieczeństwa, jeśli logujesz się automatycznie lub wyłączysz wygaszacz ekranu. Po włączeniu automatycznego logowania na, umożliwiasz innym użytkownikom, aby uruchomić ten komputer, a aby można było korzystać z konta, które loguje się automatycznie. Po wyłączeniu wygaszacza ekranu komputer może nie monitować użytkownika do logowania się do odblokowania komputera. To umożliwia wszystkim użytkownikom dostępu do komputera, jeśli mają fizyczny dostęp do komputera. Po włączeniu tych funkcji na komputerze, należy pamiętać, że te komputery są zabezpieczony fizycznie. Na przykład komputery te znajdują się w fizycznie bezpiecznych laboratorium. Jeśli wyczyścisz **upewnij się, że wygaszacz ekranu jest wyłączony**, wygaszacz ekranu nie zostanie włączony.

   Aby zmienić agenta do uruchamiania jako usługa, można użyć tego narzędzia i wybrać **usługi**.

6. Aby zastosować zmiany, wybierz opcję **Zastosuj ustawienia**.

   A **Podsumowanie konfiguracji** wyświetlane jest okno dialogowe, pokazujący stan każdego kroki, aby skonfigurować agenta testowego.

7. Aby zamknąć **Podsumowanie konfiguracji** okna dialogowego wybierz **Zamknij**. Następnie wybierz **Zamknij** ponownie, aby zamknąć **narzędzie konfiguracji agenta testowego**.

   > [!NOTE]
   > Istnieje ikona obszaru powiadomień, która jest uruchamiana na komputerze dla agenta testowego, który jest uruchomiony jako proces. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces, za pomocą tego narzędzia. Aby uruchomić agenta testowego jako proces, jeśli nie jest uruchomiony, wybierz opcję **Start** > **programu Visual Studio** > **programu Microsoft Visual Studio Test Agent**.

   Jeżeli kontroler testów dla tego agenta testowego jest zarejestrowany w programie Team Foundation Server, stan agenta testowego, który działa jako proces interaktywny, jest wyświetlany w **kontrolerów** wyświetlać w **Centrum laboratoryjnego**dla programu Microsoft Test Manager. Jest on wymieniony z poprzedzającym symbolem gwiazdki oznaczają, że jest on uruchomiony jako proces interaktywny. Aby ponownie uruchomić tego agenta testowego, należy użyć narzędzia, który jest uruchamiany na komputerze dla agenta testowego i nie **kontrolerów** widoku.

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)