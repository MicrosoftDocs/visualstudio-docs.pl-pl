---
title: Debugowanie podróży w czasie na żywo ASP.NET maszynie wirtualnej platformy Azure
description: Dowiedz się, jak rejestrować i odtwarzać aplikacje ASP.NET na żywo na maszynach wirtualnych platformy Azure przy użyciu Snapshot Debugger.
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
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798456"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Rejestrowanie i ponowne odtwarzanie aplikacji ASP.NET na żywo na maszynach wirtualnych platformy Azure przy użyciu Snapshot Debugger

Debugowanie podróży w czasie (TTD) w wersji zapoznawczej w usłudze Visual Studio Enterprise umożliwia rejestrowanie aplikacji internetowej uruchomionej na maszynie wirtualnej platformy Azure, a następnie dokładne odtworzenie i odtworzenie ścieżki wykonywania. TTD integruje się z Snapshot Debugger i umożliwia przewijanie do tyłu i powtarzanie każdego wiersza kodu dowolną liczbę razy, co pomaga izolować i identyfikować problemy, które mogą wystąpić tylko w środowiskach produkcyjnych.

Przechwytywanie nagrania TTD nie spowoduje zatrzymania aplikacji. Jednak rejestrowanie TDD zwiększa znaczne obciążenie uruchomionego procesu, spowalniając go na podstawie czynników, które obejmują rozmiar procesu i liczbę aktywnych wątków.

Ta funkcja jest dostępna w wersji zapoznawczej w wersji Visual Studio 2019 z licencją Go Live.

W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Uruchom funkcję Snapshot Debugger z włączonym debugowaniem podróży w czasie
> * Ustawianie punktu przyciągania i zbieranie nagrania podróży w czasie
> * Rozpoczynanie debugowania rejestrowania podróży w czasie

## <a name="prerequisites"></a>Wymagania wstępne

* Debugowanie podróży w czasie dla usługi Azure Virtual Machines (VM) jest dostępne tylko dla wersji Visual Studio 2019 Enterprise lub wyższej z obciążeniem Tworzenie aplikacji **na platformie Azure.** (Na karcie **Poszczególne składniki** znajduje się ona w obszarze **Debugowanie i testowanie**  >  **Debuger migawek).**

    Jeśli nie jest jeszcze zainstalowany, zainstaluj program [Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/vs/)

* Debugowanie podróży w czasie jest dostępne dla następujących aplikacji internetowych maszyny wirtualnej platformy Azure:
  * ASP.NET (AMD64) działające w .NET Framework 4.8 lub nowszej.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Uruchom funkcję Snapshot Debugger z włączonym debugowaniem podróży w czasie

1. Otwórz projekt, dla którego chcesz zebrać nagranie podróży w czasie.

    > [!IMPORTANT]
    > Aby uruchomić TTD, musisz otworzyć tę *samą* wersję kodu źródłowego, która została opublikowana w usłudze maszyny wirtualnej platformy Azure.

1. Wybierz **pozycję Debuguj > dołącz Snapshot Debugger...**. Wybierz maszynę wirtualną platformy Azure, na których wdrożono aplikację internetową, i konto usługi Azure Storage. Wybierz opcję **Włącz debugowanie podróży w czasie (wersja** zapoznawcza), a następnie kliknij pozycję **Attach (Dołącz).**

      ![Wybieranie zasobu platformy Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Przy pierwszym wybraniu opcji **Dołącz Snapshot Debugger** maszyny wirtualnej usługi IIS zostaną automatycznie uruchomione ponownie.

    Metadane modułów **nie** są początkowo aktywowane. Przejdź do aplikacji internetowej, a następnie przycisk **Uruchom kolekcję** stanie się aktywny. Visual Studio jest teraz w trybie debugowania migawek.

   ![Tryb debugowania migawek](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Rozszerzenie Application Insights obsługuje również debugowanie migawek. Jeśli wystąpi komunikat o błędzie "Rozszerzenie lokacji jest aktualne", zobacz wskazówki dotyczące rozwiązywania problemów i znane problemy dotyczące debugowania migawek, aby [uzyskać](../debugger/debug-live-azure-apps-troubleshooting.md) szczegółowe informacje.

   Okno **Moduły** pokazuje, kiedy wszystkie moduły są ładowane dla maszyny wirtualnej platformy Azure (wybierz pozycję Debuguj moduły > **Windows > Modules,** aby otworzyć to okno).

   ![Sprawdź okno Moduły](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Ustawianie punktu przyciągania i zbieranie nagrania podróży w czasie

1. W edytorze kodu kliknij lewą rynnę w metodzie, która Cię interesuje, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który będzie wykonywany.

   ![Ustawianie punktu przyciągania](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Kliknij prawym przyciskiem myszy ikonę punktu przyciągania (ikonę piłki pustej), a następnie wybierz pozycję **Akcje**. W **oknie Ustawienia** migawki kliknij **pole wyboru** Akcja. Następnie kliknij **pole wyboru Collect a time travel trace to the end of this method** (Zbierz ślad podróży w czasie na koniec tej metody).

   ![Zbieranie śladu podróży w czasie do końca metody](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Kliknij **przycisk Start Collection** (Rozpocznij zbieranie), aby włączyć punkt przyciągania.

   ![Włączanie punktu przyciągania](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Tworzenie migawki

Gdy punkt przyciągania jest włączony, przechwytuje migawkę za każdym razem, gdy zostanie wykonany wiersz kodu, w którym znajduje się punkt przyciągania. To wykonanie może być spowodowane rzeczywistym żądaniem na serwerze. Aby wymusić trafienie punktu przyciągania, przejdź do widoku przeglądarki witryny internetowej i podjąć wszelkie wymagane działania, które powodują trafienie punktu przyciągania.

## <a name="start-debugging-a-time-travel-recording"></a>Rozpoczynanie debugowania rejestrowania podróży w czasie

1. Po trafieniu punktu przyciągania w oknie narzędzia diagnostyczne zostanie wyświetlona migawka. Aby otworzyć to okno, wybierz pozycję **Debuguj > Windows > Pokaż narzędzia diagnostyczne.**

   ![Otwieranie punktu przyciągania](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij link Wyświetl migawkę, aby otworzyć rejestrowanie podróży w czasie w edytorze kodu.
  
   Każdy wiersz kodu zarejestrowany przez TTD można wykonać przy użyciu przycisków **Kontynuuj** i **Odwróć** kontynuowanie. Ponadto paska narzędzi **Debugowanie** można użyć do pokazania następnej instrukcji **,** kroku do **,** kroku **do,** wyetapuj **,** krok do **tyłu,** krok do tyłu **,** krok **do tyłu**.

   ![Rozpocznij debugowanie](../debugger/media/time-travel-debugging-step-commands.png)

   Można również używać okien **Locals**, **Watches** i **Call Stack,** a także oceniać wyrażenia.

   ![Sprawdzanie danych migawki](../debugger/media/time-travel-debugging-start-debugging.png)

    Sama witryna internetowa nadal działa, a na użytkowników końcowych nie ma wpływu żadne kolejne działanie TTD. Domyślnie na punkt przyciągania jest przechwytywana tylko jedna migawka: po przechwyceniu migawki punkt przyciągania jest wyłączany. Jeśli chcesz przechwycić kolejną migawkę w punkcie przyciągania, możesz ponownie włączyć punkt przyciągania, klikając pozycję **Aktualizuj kolekcję**.

**Potrzebujesz pomocy?** Zobacz Rozwiązywanie [problemów i znane problemy oraz Często zadawane](../debugger/debug-live-azure-apps-troubleshooting.md) pytania dotyczące stron [debugowania migawek.](../debugger/debug-live-azure-apps-faq.yml)

## <a name="set-a-conditional-snappoint"></a>Ustawianie warunkowego punktu przyciągania

Jeśli trudno jest odtworzyć konkretny stan w aplikacji, zastanów się, czy użycie warunkowego punktu przyciągania może pomóc. Warunkowe punkty przyciągania pomagają uniknąć zbierania nagrania podróży w czasie, dopóki aplikacja nie przejdzie w żądany stan, na przykład gdy zmienna ma określoną wartość, którą chcesz sprawdzić. [Warunki można ustawiać przy użyciu wyrażeń, filtrów lub liczby trafień](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku opisano sposób zbierania nagrania podróży w czasie dla usługi Azure Virtual Machines. Możesz przeczytać więcej szczegółów na temat Snapshot Debugger.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.yml)