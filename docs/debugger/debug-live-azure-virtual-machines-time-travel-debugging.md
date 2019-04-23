---
title: Czas podróży debugowania na żywo ASP.NET maszyn wirtualnych platformy Azure
description: Dowiedz się, jak rejestrować i odtworzenia działających aplikacji platformy ASP.NET na maszynach wirtualnych platformy Azure przy użyciu rozszerzenia Snapshot Debugger.
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 3a81f6aa138b361a44a272ebda3557d27a914c64
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112360"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Rejestrowanie i powtarzanie na żywo aplikacji ASP.NET na maszynach wirtualnych platformy Azure przy użyciu rozszerzenia Snapshot Debugger

Czas podróży debugowania (TTD) (wersja zapoznawcza) w programie Visual Studio Enterprise umożliwia rejestrowanie aplikacji internetowej uruchomionej na maszynie Wirtualnej platformy Azure maszyna wirtualna () i następnie dokładnie rekonstrukcji i odtwarzania ścieżki wykonywania. TTD integruje się z rozszerzenia Snapshot Debugger i umożliwia temu przewinąć do tyłu i odtworzenia wszystkich wierszy kodu dowolną liczbę razy, której potrzebujesz, pomagając Ci wyizolować i zidentyfikować problemy, które mogą występować tylko w środowiskach produkcyjnych.

Przechwytywanie nagranie TTD nie zostanie zatrzymany aplikacji. Jednak nagrywanie TDD znacznie zwiększa obciążenie do uruchomionego procesu, spowalniania na podstawie czynników, które obejmują rozmiar procesu i liczba aktywnych wątków.

Ta funkcja jest dostępna w wersji zapoznawczej dla wersji programu Visual Studio 2019 Przejdź licencją na żywo.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom rozszerzenie Snapshot Debugger z włączonym debugowaniem podróży czasu
> * Ustawianie punktu przyciągania i zbieranie przez czas podróży nagrywanie
> * Start debugging czas podróży nagrywanie

## <a name="prerequisites"></a>Wymagania wstępne

* Czas podróży debugowania dla usługi Azure Virtual Machines (VM) jest dostępne tylko dla programu Visual Studio Enterprise 2019 lub wyższe w przypadku **obciążenie programistyczne platformy Azure**. (W obszarze **poszczególne składniki** karty, możesz znaleźć go w folderze **debugowanie i testowanie** > **rozszerzenia Snapshot debugger**.)

    Jeśli jeszcze nie jest zainstalowany, zainstaluj [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Debugowanie w czasie podróży jest dostępna dla następujących aplikacji sieci web maszyny Wirtualnej platformy Azure:
  * Aplikacje ASP.NET (AMD64) działające w programie .NET Framework 4.8 lub nowszym.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Otwórz swój projekt i uruchomić rozszerzenia Snapshot Debugger z włączonym debugowaniem podróży czasu

1. Otwórz projekt, dla której chcesz zbierać czas podróży rejestrowania.

    > [!IMPORTANT]
    > Aby rozpocząć TTD, należy otworzyć *tę samą wersję kodu źródłowego* , są publikowane w usłudze maszyny Wirtualnej platformy Azure.

1. Wybierz **Debuguj > Dołączanie rozszerzenia Snapshot Debugger...** . Wybierz maszyny Wirtualnej platformy Azure, aplikacji sieci web jest wdrażana i konto magazynu platformy Azure. Wybierz **włączyć debugowanie czas podróży** opcji w wersji zapoznawczej, a następnie kliknij przycisk **Dołącz**.

      ![Wybierz zasób platformy Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Po raz pierwszy wybierzesz **dołączyć rozszerzenie Snapshot Debugger** dla swojej maszyny Wirtualnej usług IIS jest automatycznie uruchamiany ponownie.

    Metadane dla **modułów** nie został początkowo uaktywniony. Przejdź do aplikacji sieci web i **Rozpocznij zbieranie** przycisk staje się aktywny. Program Visual Studio jest teraz w trybie debugowania migawek.

   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Rozszerzenie witryny usługi Application Insights obsługuje również debugowania migawek. Jeśli wystąpią "rozszerzenie nieaktualna witryny" komunikat o błędzie, zobacz [rozwiązania problemu wskazówki i znanych problemów dotyczących debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md) dla uaktualnienie szczegółowe informacje.

   **Modułów** okna dowiesz się, gdy wszystkie moduły są ładowane dla maszyny Wirtualnej platformy Azure (wybierz **Debuguj > Windows > modułów** otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Ustawianie punktu przyciągania i zbieranie przez czas podróży nagrywanie

1. W edytorze kodu kliknij lewym marginesie na oprawę w metodzie, który Cię interesuje można ustawić punktu przyciągania. Upewnij się, że kod, który będzie wykonywać.

   ![Ustaw punkt przyciągania](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (piłka puste), a następnie wybierz **akcje**. W **ustawienia migawek** okna, kliknij przycisk **akcji** pole wyboru. Następnie kliknij przycisk **zbierać dane śledzenia podróży czas na końcu tej metody** pole wyboru.

   ![Zbieranie czasu podróży śledzenia na końcu metody](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Kliknij przycisk **Rozpocznij zbieranie** włączenie punktu przyciągania.

   ![Włącz punkt przyciągania](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Utwórz migawkę

Po włączeniu punktu przyciągania przechwytuje migawki zawsze wtedy, gdy wykonuje wiersza kodu, w którym znajduje się punkt przyciągania. To wykonanie może być spowodowane rzeczywistego żądania na serwerze. Aby wymusić Twojego punktu przyciągania trafień, przejdź do widoku przeglądarki witryny sieci web i podjąć działania wymaganego co powodować Twojego punktu przyciągania na.

## <a name="start-debugging-a-time-travel-recording"></a>Start debugging czas podróży nagrywanie

1. Po osiągnięciu punktu przyciągania migawki pojawia się w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz **Debuguj > Windows > Pokaż narzędzia diagnostyczne**.

   ![Otwarcie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij łącze Wyświetl migawkę można otworzyć czas podróży, rejestrowanie w edytorze kodu.
  
   Można wykonywać każdy wiersz kodu, rejestrowane przez TTD przy użyciu **Kontynuuj** i **odwrotnego nadal** przycisków. Ponadto **debugowania** narzędzi można używać do **Pokaż następną instrukcję**, **Step Into**, **Step Over**, **Step Out**, **Krok z powrotem do**, **ponownie Przekrocz**, **kroku wycofywanie**.

   ![Rozpocznij debugowanie](../debugger/media/time-travel-debugging-step-commands.png)

   Można również użyć **lokalne**, **zegarki**, i **stos wywołań** systemu windows, a także obliczać wyrażeń.

   ![Sprawdź dane migawki](../debugger/media/time-travel-debugging-start-debugging.png)

    Nadal działa z witryną, a użytkownicy końcowi nie ma wpływ na dowolnych następnych działań TTD. Tylko jedna migawka jest przechwytywany na punkt przyciągania domyślnie: po przechwyceniu migawkę punktu przyciągania zostanie wyłączony. Chcesz przechwytywać innego migawkę punktu przyciągania, można włączyć punkt przyciągania ponownie, klikając **Aktualizuj kolekcję**.

**Potrzebujesz pomocy?** Zobacz [Rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) i [często zadawane pytania dotyczące debugowania migawek](../debugger/debug-live-azure-apps-faq.md) stron.

## <a name="set-a-conditional-snappoint"></a>Ustaw warunkowego punktu przyciągania

Jeśli jest trudne do odtworzenia w określonym stanie w swojej aplikacji, należy rozważyć, czy korzystanie z warunkowego punktu przyciągania mogą pomóc w. Warunkowe punkty przyciągania uniknąć zbieranie przez czas podróży, rejestrowanie, aż aplikacja przejdzie do żądanego stanu, na przykład w przypadku zmiennej określonej wartości, które chcesz sprawdzić. [Możesz ustawić warunki, używając wyrażeń i filtry, lub liczbą trafień](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku wyjaśniono sposób zbierania czasu podróży, rejestrowania usługi Azure Virtual Machines. Warto przeczytać więcej na temat rozszerzenia Snapshot Debugger.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)