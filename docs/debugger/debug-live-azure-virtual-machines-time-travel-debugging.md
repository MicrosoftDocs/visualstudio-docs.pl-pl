---
title: Czas debugowania podróży na żywo ASP.NET na maszynie wirtualnej platformy Azure
description: Dowiedz się, jak rejestrować i powtarzać aplikacje ASP.NET na żywo na maszynach wirtualnych platformy Azure przy użyciu Snapshot Debugger.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: eb0db0bab5295925f71a81645e64fdeb5f2077df
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809573"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Rejestruj i Odtwarzaj na żywo aplikacje ASP.NET na maszynach wirtualnych platformy Azure przy użyciu Snapshot Debugger

Wersja zapoznawcza debugowania czasu podróży (docelowy) w Visual Studio Enterprise umożliwia rejestrowanie aplikacji sieci Web działającej na maszynie wirtualnej platformy Azure, a następnie dokładne odtworzenie i odtwarzanie ścieżki wykonywania. DOCELOWY integruje się z Snapshot Debugger i pozwala na przewinięcie i powtórzenie każdego wiersza kodu dowolną liczbę razy, pomagając w izolowaniu i identyfikowaniu problemów, które mogą wystąpić tylko w środowiskach produkcyjnych.

Przechwytywanie nagrania docelowy nie spowoduje zatrzymania aplikacji. Jednak nagranie TDD dodaje znaczne obciążenie dla uruchomionego procesu, spowalniając je w oparciu o czynniki, które obejmują rozmiar procesu i liczbę aktywnych wątków.

Ta funkcja jest dostępna w wersji zapoznawczej programu Visual Studio 2019 z licencją na żywo.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom Snapshot Debugger z włączonym debugowaniem czasu trwania
> * Ustaw punkt przyciągania i zbierz nagranie w czasie podróży
> * Rozpocznij debugowanie nagrania czasu podróży

## <a name="prerequisites"></a>Wymagania wstępne

* Debugowanie czasu podróży dla usługi Azure Virtual Machines (VM) jest dostępne tylko dla programu Visual Studio 2019 Enterprise lub nowszego przy użyciu **obciążeń programistycznych platformy Azure**. (Na karcie **poszczególne składniki** znajdziesz ją w obszarze **debugowanie i testowanie**  >  **Debuger migawek**.)

    Jeśli nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Debugowanie czasu podróży jest dostępne dla następujących aplikacji sieci Web maszyny wirtualnej platformy Azure:
  * Aplikacje ASP.NET (AMD64) działają w .NET Framework 4,8 lub nowszych.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Uruchom Snapshot Debugger z włączonym debugowaniem czasu trwania

1. Otwórz projekt, dla którego chcesz zebrać nagrania czasu podróży.

    > [!IMPORTANT]
    > Aby rozpocząć docelowy, należy otworzyć tę *samą wersję kodu źródłowego* , która jest publikowana w usłudze Azure VM.

1. Wybierz **> debugowania Snapshot Debugger Dołącz...**. Wybierz maszynę wirtualną platformy Azure, do której wdrożono aplikację sieci Web, oraz konto usługi Azure Storage. Wybierz opcję **Włącz debugowanie czasu trwania w** wersji zapoznawczej, a następnie kliknij przycisk **Dołącz**.

      ![Wybierz zasób platformy Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Po pierwszym wybraniu opcji **dołącz Snapshot Debugger** dla maszyny wirtualnej usługi IIS zostaną automatycznie uruchomione ponownie.

    Metadane dla **modułów** nie są początkowo aktywowane. Przejdź do aplikacji sieci Web, a następnie przycisk **Rozpocznij zbieranie** zostanie uaktywniony. Program Visual Studio jest teraz w trybie debugowania migawek.

   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Rozszerzenie witryny Application Insights obsługuje również debugowanie migawek. Jeśli zostanie wyświetlony komunikat o błędzie "nieaktualne rozszerzenie witryny", zobacz [wskazówki dotyczące rozwiązywania problemów i znane problemy dotyczące debugowania migawek](../debugger/debug-live-azure-apps-troubleshooting.md) na potrzeby uaktualniania szczegółów.

   Okno **moduły** pokazuje, kiedy wszystkie moduły są ładowane dla maszyny wirtualnej platformy Azure (wybierz polecenie **debuguj > modułów > systemu Windows** , aby otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Ustaw punkt przyciągania i zbierz nagranie w czasie podróży

1. W edytorze kodu kliknij lewy margines w danej metodzie, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który ma być wykonywany.

   ![Ustaw punkt przyciągania](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (kulka pusta) i wybierz polecenie **Akcje**. W oknie **Ustawienia migawki** kliknij pole wyboru **Akcja** . Następnie kliknij pole wyboru **Zbierz dane śledzenia czasu podróży do końca tej metody** .

   ![Zbieraj dane śledzenia czasu podróży na końcu metody](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Kliknij pozycję **Rozpocznij zbieranie** , aby włączyć punkt przyciągania.

   ![Włącz punkt przyciągania](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Tworzenie migawki

Gdy punkt przyciągania jest włączona, przechwytuje migawkę zawsze wtedy, gdy jest wykonywany wiersz kodu, w którym jest umieszczane punkt przyciągania. To wykonanie może być spowodowane rzeczywistym żądaniem na serwerze. Aby wymusić punkt przyciągania, przejdź do widoku przeglądarki witryny sieci Web i wykonaj wszelkie wymagane akcje, które powodują trafienie punkt przyciągania.

## <a name="start-debugging-a-time-travel-recording"></a>Rozpocznij debugowanie nagrania czasu podróży

1. Po trafieniu punkt przyciągania zostanie wyświetlona migawka w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz **debuguj > Windows > pokaż narzędzia diagnostyczne**.

   ![Otwórz punkt przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij link Wyświetl migawkę, aby otworzyć okno Rejestracja czasu podróży w edytorze kodu.
  
   Każdy wiersz kodu rejestrowany przez docelowy można wykonać za pomocą przycisków **Kontynuuj** i **Cofnij Kontynuuj** . Ponadto pasek narzędzi **debugowania** może służyć do **wyświetlania następnej instrukcji**, **wkroczenia**, **przekroczenia,** **stopniowego**, krokowego, przekroczenia **,** krok do **tyłu** **, krok z powrotem.**

   ![Rozpocznij debugowanie](../debugger/media/time-travel-debugging-step-commands.png)

   Możesz również użyć okien **zmiennych lokalnych**, **zegarki**i **stosu wywołań** , a także obliczyć wyrażenia.

   ![Sprawdzanie danych migawek](../debugger/media/time-travel-debugging-start-debugging.png)

    Sama witryna sieci Web jest nadal na żywo, a użytkownicy końcowi nie wpływają na żadną kolejną aktywność docelowy. Tylko jedna migawka jest domyślnie przechwytywana na punkt przyciągania: Po przechwyceniu migawki punkt przyciągania wyłączone. Jeśli chcesz przechwycić kolejną migawkę w punkt przyciągania, możesz włączyć punkt przyciągania ponownie, klikając polecenie **Aktualizuj kolekcję**.

**Potrzebujesz pomocy?** Zapoznaj się z tematami [Rozwiązywanie problemów i znanych problemów](../debugger/debug-live-azure-apps-troubleshooting.md) oraz [często zadawanych pytań dotyczących debugowania migawek](../debugger/debug-live-azure-apps-faq.md) .

## <a name="set-a-conditional-snappoint"></a>Ustaw punkt przyciągania warunkowe

Jeśli nie można ponownie utworzyć określonego stanu w aplikacji, należy rozważyć, czy użycie punkt przyciągania warunkowego może pomóc. Punkty przyciągania warunkowe pomagają uniknąć zbierania danych o czasie podróży do momentu, aż aplikacja przejdzie do żądanego stanu, na przykład gdy zmienna ma konkretną wartość, którą chcesz sprawdzić. [Można ustawić warunki przy użyciu wyrażeń, filtrów lub liczby trafień](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku pokazano, jak zbierać informacje o czasie podróży dla Virtual Machines platformy Azure. Warto zapoznać się z dodatkowymi informacjami na temat Snapshot Debugger.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)