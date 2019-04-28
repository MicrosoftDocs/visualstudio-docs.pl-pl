---
title: Ładowanie podzestaw projektów
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2612770b760bec70ec9ee6c679c47804d4e69f42
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439852"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrowane rozwiązań w programie Visual Studio

Duże zespoły programistów często współpracować przy użyciu jednego rozwiązania dużych z wielu projektów. Jednak indywidualni Deweloperzy zazwyczaj działa na mały podzbiór tych projektów. W celu poprawy wydajności podczas otwierania dużych rozwiązań programu Visual Studio 2019 wprowadzone *filtrowanie rozwiązań*. Rozwiązanie Filtrowanie umożliwia otwarciu rozwiązania przy użyciu tylko selektywne projektów możliwych do przeanalizowania. Trwa ładowanie podzestaw projektów w rozwiązaniu zmniejsza ładowania rozwiązań, kompilacji i testowania, w czasie wykonywania i umożliwia bardziej ukierunkowane przeglądu.

Dostępne są następujące funkcje:

- Możesz uzyskać kod szybciej, otwierając rozwiązanie bez ładowania jeden z jego projektów. Po otwarciu rozwiązania można selektywnie wskazać projektów do załadowania.

- Po ponownym otwarciu rozwiązania Visual Studio zapamiętuje, które projekty zostały załadowane w poprzedniej sesji i ładowane są tylko te projekty.

- Można utworzyć pliku filtru rozwiązania, aby zapisać co najmniej jedna konfiguracja ładowanie projektu lub mają taką konfigurację z członkami zespołu.

## <a name="open-a-filtered-solution"></a>Otwórz rozwiązanie filtrowane

Można otworzyć rozwiązanie bez ładowania jeden z jego projektów bezpośrednio z **Otwórz projekt** okna dialogowego lub za pomocą [wiersza polecenia](#command-line).

### <a name="open-project-dialog"></a>Otwórz okno dialogowe projektu

Aby otworzyć rozwiązanie bez ładowania jeden z jego projektów za pomocą **Otwórz projekt** okno dialogowe:

1. Wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie** z paska menu.

2. W **Otwórz projekt** okno dialogowe, wybierz rozwiązanie, a następnie wybierz **projekty nie są ładowane**.

   ![Visual Studio Otwórz okno dialogowe projektu za pomocą nie są ładowane projekty zaznaczone](media/filtered-solutions/do-not-load-projects.png)

3. Wybierz **Otwórz**.

   Otwiera rozwiązanie ze wszystkimi jego projekty pozostaną niezaładowane.

4. W **Eksploratora rozwiązań**, wybierz projekty do załadowania (naciśnij klawisz **Ctrl** podczas klikania, aby wybrać więcej niż jeden projekt), a następnie kliknij prawym przyciskiem myszy nad projektem i wybierz **Załaduj ponownie projekt** .

   ![Załaduj ponownie wielu projektów w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/reload-project.png)

   Program Visual Studio zapamiętuje, projekty, które są ładowane przy następnym otwarciu rozwiązania lokalnie.

### <a name="command-line"></a>Wiersz polecenia

(Nowość w programie Visual Studio 2019 wersji 16.1.)

Aby otworzyć rozwiązanie bez ładowania jeden z jego projektów z wiersza polecenia, należy użyć [ `/donotloadprojects` ](../ide/reference/donotloadprojects-devenv-exe.md) przełącznika, jak pokazano w poniższym przykładzie:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Przełącz widoczność zwolnionego projektu

Można wybrać wyświetlić wszystkie projekty w rozwiązaniu albo tylko tych załadowany przy użyciu jednej z następujących opcji w **Eksploratora rozwiązań**:

- Kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Pokaż zwolnione projektów** lub **Ukryj zwolnione projektów**.

- Wybierz węzeł rozwiązania, aby umożliwić **Pokaż wszystkie pliki** przycisk; następnie kliknij przycisk, aby przełączyć widoczność zwolnione projektów.

   ![Pokaż wszystkie pliki w Eksploratorze rozwiązań w usłudze Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Ładowanie zależności projektu

W ramach rozwiązania, gdy są ładowane tylko wybrane projekty nie masz wszystkie zależności projektu projektów załadowanych. Użyj **załadować zależności projektu** opcję menu, aby upewnić się, że wszystkie projekty, które zależy od projektu również są ładowane. Kliknij prawym przyciskiem myszy na co najmniej jeden projekt załadowany w **Eksploratora rozwiązań** i wybierz polecenie **załadować zależności projektu**.

![Ładowanie zależności projektu w programie Visual Studio 2019 r.](media/filtered-solutions/load-project-dependencies.png)

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
