---
title: Ładowanie podzestaw projektów
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: visual-studio-dev16
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 1ce2c3fbb8386cb58e096e526dc27b03d16e428e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972563"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrowane rozwiązań w programie Visual Studio

**Nowość w programie Visual Studio 2019 Preview 1**

Duże zespoły programistów często współpracować przy użyciu jednego rozwiązania dużych z wielu projektów. Jednak indywidualni Deweloperzy zazwyczaj działa na mały podzbiór tych projektów. W celu poprawy wydajności podczas otwierania dużych rozwiązań programu Visual Studio 2019 r w wersji zapoznawczej 1 wprowadzono *filtrowanie rozwiązań*. Rozwiązanie Filtrowanie umożliwia otwarciu rozwiązania przy użyciu tylko selektywne projektów możliwych do przeanalizowania. Trwa ładowanie podzestaw projektów w rozwiązaniu zmniejsza ładowania rozwiązań, kompilacji i testowania, w czasie wykonywania i umożliwia bardziej ukierunkowane przeglądu.

Dostępne są następujące funkcje:

- Możesz uzyskać kod szybciej, otwierając rozwiązanie bez ładowania jeden z jego projektów. Po otwarciu rozwiązania można selektywnie wskazać projektów do załadowania.

- Po ponownym otwarciu rozwiązania Visual Studio zapamiętuje, które projekty zostały załadowane w poprzedniej sesji i ładowane są tylko te projekty.

- Można utworzyć pliku filtru rozwiązania, aby zapisać co najmniej jedna konfiguracja ładowanie projektu lub mają taką konfigurację z członkami zespołu.

## <a name="open-a-filtered-solution"></a>Otwórz rozwiązanie filtrowane

Aby otworzyć rozwiązanie z tylko niektóre z jego projektów, wykonaj następujące kroki:

1. Wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie** z paska menu.

2. W **nowy projekt** okno dialogowe, wybierz rozwiązanie, a następnie wybierz **projekty nie są ładowane**.

   ![Visual Studio Otwórz okno dialogowe projektu za pomocą nie są ładowane projekty zaznaczone](media/filtered-solutions/do-not-load-projects.png)

3. Wybierz **Otwórz**.

   Otwiera rozwiązanie ze wszystkimi jego projekty pozostaną niezaładowane.

4. W **Eksploratora rozwiązań**, wybierz projekty do załadowania (naciśnij klawisz **Ctrl** podczas klikania, aby wybrać więcej niż jeden projekt), a następnie kliknij prawym przyciskiem myszy nad projektem i wybierz **Załaduj ponownie projekt** .

   ![Załaduj ponownie wielu projektów w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/reload-project.png)

   Program Visual Studio zapamiętuje, projekty, które są ładowane przy następnym otwarciu rozwiązania lokalnie.

## <a name="toggle-unloaded-project-visibility"></a>Przełącz widoczność zwolnionego projektu

Można wybrać wyświetlić wszystkie projekty w rozwiązaniu albo tylko tych załadowany przy użyciu jednej z następujących opcji w **Eksploratora rozwiązań**:

- Kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Pokaż zwolnione projektów** lub **Ukryj zwolnione projektów**.

- Wybierz **Pokaż wszystkie pliki** przycisk, aby przełączyć widoczność zwolnione projektów.

   ![Pokaż wszystkie pliki w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>Pliki filtrów rozwiązania

Jeśli chcesz udostępnić konfigurację ładowania projektu lub przekazać go do kontroli źródła, można utworzyć pliku rozwiązania filtru (ma rozszerzenie *.slnf*). Po otwarciu pliku filtru rozwiązania, rozwiązanie zostanie otwarty w programie Visual Studio przy użyciu określonych projektów, które są ładowane i wszystkie projekty zwolnione ukryte. Możesz [Przełącz](#toggle-unloaded-project-visibility) do wyświetlania projektów zwolniony.

Pliki filtr rozwiązania wizualnie różnią się od plików rozwiązania regularne przez symbol dodatkowe lejka ikona obok rozwiązania w **Eksploratora rozwiązań**. Nazwa filtru i liczbę ładowanych projektów są także wyświetlane obok nazwy rozwiązania.

![Plik filtru rozwiązania Otwórz w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Jeśli nowe projekty zostaną dodane do oryginalnego rozwiązania, po utworzeniu pliku filtru rozwiązania, pojawiają się jako zwolniony projektów w **Eksploratora rozwiązań**.

### <a name="create-a-solution-filter-file"></a>Utworzenie pliku filtru rozwiązania

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Zapisz jako filtr rozwiązania**.

   ![Menu Zapisz jako filtr rozwiązania w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Wybierz nazwę i lokalizację pliku filtru rozwiązania.

Po utworzeniu pliku rozwiązania filtr zostanie dodany do Twojego **niedawne projekty i rozwiązania** listy, aby mieć łatwy dostęp:

![Otwórz ostatnio używane w programie Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie zagnieżdżanie plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md)
- [Optymalizacja wydajności programu Visual Studio](optimize-visual-studio-performance.md)