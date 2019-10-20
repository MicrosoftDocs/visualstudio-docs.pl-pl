---
title: Konfigurowanie agenta testowego
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55cf32d138d2644e2d2a7a08406eb575a2895400
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653427"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Instrukcje: Konfigurowanie agenta testowego do uruchamiania testów, które współdziałają z pulpitem

Jeśli chcesz uruchomić testy automatyczne, które współdziałają z pulpitem, musisz skonfigurować agenta do uruchamiania jako proces zamiast do usługi. Na przykład, jeśli chcesz uruchomić kodowany test interfejsu użytkownika zdalnie przy użyciu kontrolera testów i agenta testowego lub chcesz uruchomić test i przechwycić nagranie wideo po jego uruchomieniu, musisz skonfigurować agenta do uruchamiania jako proces. W przypadku przypisywania agentów do ról w ustawieniach testu przy użyciu programu Visual Studio lub przypisywania agentów do ról w środowisku przy użyciu Microsoft Test Manager, należy zmienić konfigurację dla wszystkich agentów przypisanych do ról, które muszą współistnieć z pulpitem.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!WARNING]
> Jeśli używasz Microsoft Test Manager do skonfigurowania środowiska laboratoryjnego, zainstaluje agenta testowego. Można określić w **Kreatorze tworzenia środowiska** , który ma skonfigurować jedną z ról do uruchamiania kodowanych testów interfejsu użytkownika.

> [!IMPORTANT]
> Komputer, na którym jest uruchomiony agent, na którym chcesz uruchomić kodowane testy interfejsu użytkownika, nie może być zablokowany lub mieć aktywny wygaszacz ekranu.

W przypadku uruchamiania kodowanych testów interfejsu użytkownika, które uruchamiają przeglądarkę, konto usługi dla agenta testowego służy do uruchamiania tej przeglądarki. To konto usługi musi być takie samo, jak konto użytkownika, który jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest to konto użytkownika, przeglądarka nie zostanie uruchomiona.

> [!IMPORTANT]
> W przypadku korzystania z kodowanego testu interfejsu użytkownika, który uruchamia przeglądarkę w ramach definicji kompilacji, konto usługi dla usługi kompilacji jest używane do uruchamiania tej przeglądarki. To konto usługi musi być takie samo, jak konto użytkownika, który jest aktywnym użytkownikiem na tym komputerze. Jeśli nie jest to konto użytkownika, przeglądarka nie zostanie uruchomiona.

Poniższa procedura umożliwia skonfigurowanie wszystkich agentów przypisanych do roli, która wykonuje zadanie, które musi współdziałać z pulpitem.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Aby skonfigurować agenta do uruchamiania jako proces

1. Aby skonfigurować agenta testowego, który został zainstalowany do uruchamiania jako proces, przejdź do **menu Start**  > **Narzędzia konfiguracji agenta testowego**.

   Zostanie wyświetlone okno dialogowe **Konfiguruj agenta testowego** .

   ![Konfiguruj agenta testowego dla programu Visual Studio](media/configure-test-agent.png)

2. Wybierz pozycję **proces interaktywny**. Agent testowy zostanie uruchomiony jako proces, a nie jako usługa. Wybierz pozycję **dalej**.

3. Wprowadź nazwę użytkownika i hasło dla użytkownika, który uruchomi proces agenta testowego.

   > [!NOTE]
   > - Użytkownik dodawany do uruchomienia procesu musi również zostać dodany jako członek grupy TeamTestAgentService na komputerze dla kontrolera testów dla tego agenta. Jeśli ten użytkownik jest bieżącym użytkownikiem, gdy ten użytkownik zostanie dodany do komputera kontrolera testów, musisz się wylogować lub uruchomić ponownie.
   > - Hasła o wartości null nie są obsługiwane dla kont użytkowników.
   > - Jeśli chcesz użyć IntelliTrace lub danych emulacji sieci i karty diagnostycznej, konto użytkownika musi być członkiem grupy Administratorzy. Jeśli na komputerze z uruchomionym agentem testowym jest uruchomiony system operacyjny z najniższymi uprawnieniami konta użytkownika, należy uruchomić go jako administrator (podwyższony poziom). Jeśli nazwa użytkownika agenta nie znajduje się w usłudze agenta, spróbuje ją dodać, co wymaga uprawnień do kontrolera testów.
   > - Użytkownik próbujący użyć kontrolera testów musi znajdować się na koncie użytkownika kontrolera testów lub nie będzie mógł uruchamiać testów dla kontrolera.

4. Aby upewnić się, że komputer z agentem testowym może uruchamiać testy po ponownym uruchomieniu, można skonfigurować komputer do automatycznego logowania jako użytkownik agenta testowego. Wybierz pozycję **Zaloguj automatycznie**. Spowoduje to zapisanie nazwy użytkownika i hasła w postaci zaszyfrowanej w rejestrze.

   > [!NOTE]
   > Po nawiązaniu połączenia ze środowiskiem laboratoryjnym przy użyciu pulpitu zdalnego lub z połączeniem opartym na gościu może wystąpić częste, nieoczekiwane rozłączenia. Jedną z możliwych przyczyn utraty połączenia jest to, że komputer jest skonfigurowany do automatycznego logowania do sieci.

5. Aby upewnić się, że wygaszacz ekranu jest wyłączony, ponieważ może to zakłócać wszystkie testy automatyczne, które muszą współdziałać z pulpitem, wybierz pozycję **upewnij się, że wygaszacz ekranu jest wyłączony**.

   > [!WARNING]
   > Jeśli logujesz się automatycznie lub wyłączysz wygaszacz ekranu, występują zagrożenia bezpieczeństwa. Włączenie automatycznego logowania umożliwia innym użytkownikom uruchamianie tego komputera i korzystanie z konta, które automatycznie loguje się. Jeśli wyłączysz wygaszacz ekranu, komputer może nie monitować użytkownika o zalogowanie się w celu odblokowania komputera. Dzięki temu każdy użytkownik może uzyskać dostęp do komputera, jeśli ma fizyczny dostęp do komputera. Jeśli te funkcje są włączone na komputerze, należy upewnić się, że te komputery są fizycznie bezpieczne. Na przykład te komputery znajdują się w fizycznie zabezpieczonym laboratorium. Jeśli wyczyścisz opcję **upewnij się, że wygaszacz ekranu jest wyłączony**, nie spowoduje to włączenia wygaszacza ekranu.

   Aby zmienić agenta z powrotem do uruchamiania jako usługa, możesz użyć tego narzędzia i wybrać pozycję **Usługa**.

6. Aby zastosować zmiany, wybierz pozycję **Zastosuj ustawienia**.

   Zostanie wyświetlone okno dialogowe **Podsumowanie konfiguracji** przedstawiające stan poszczególnych kroków konfigurowania agenta testowego.

7. Aby zamknąć okno dialogowe **Podsumowanie konfiguracji** , wybierz przycisk **Zamknij**. Następnie wybierz ponownie przycisk **Zamknij** , aby zamknąć **Narzędzie konfiguracji agenta testowego**.

   > [!NOTE]
   > Istnieje ikona obszaru powiadomień, która jest uruchamiana na komputerze dla agenta testowego, który działa jako proces. Pokazuje stan agenta testowego. Można uruchomić, zatrzymać lub ponownie uruchomić agenta, jeśli jest uruchomiony jako proces korzystający z tego narzędzia. Aby uruchomić agenta testowego jako proces, jeśli nie jest uruchomiony, wybierz **start**  > **Visual Studio**  > **Microsoft Visual Studio Test Agent**.

   Jeśli kontroler testów dla tego agenta testowego jest zarejestrowany w Team Foundation Server, stan agenta testowego, który działa jako proces interaktywny, zostanie wyświetlony w widoku **Kontrolery** w **Centrum laboratoryjnym** dla Microsoft Test Manager. Jest on wyświetlany z poprzednim symbolem gwiazdki, aby zauważyć, że jest uruchomiony jako proces interaktywny. Aby ponownie uruchomić tego agenta testowego, należy użyć narzędzia uruchomionego na komputerze dla agenta testowego, a nie widoku **Kontrolery** .

## <a name="see-also"></a>Zobacz także

- [Instalowanie i konfigurowanie agentów testowych](../test/lab-management/install-configure-test-agents.md)