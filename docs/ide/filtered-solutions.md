---
title: Ładowanie podzbioru projektów
ms.date: 04/22/2019
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: jillre
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4c44d267ef5686d04e9549601e05866aabbfb62d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72650835"
---
# <a name="filtered-solutions-in-visual-studio"></a>Filtrowane rozwiązania w programie Visual Studio

Duże zespoły programistyczne często współpracują przy użyciu jednego dużego rozwiązania z wieloma projektami. Jednak poszczególnych deweloperów zazwyczaj pracują nad małym podzbiorem tych projektów. Aby zwiększyć wydajność podczas otwierania dużych rozwiązań, program Visual Studio 2019 wprowadził *filtrowanie rozwiązań.* Filtrowanie rozwiązań umożliwia otwieranie rozwiązania z załadowanymi tylko selektywnymi projektami. Ładowanie podzbioru projektów w rozwiązaniu zmniejsza obciążenie rozwiązania, kompilacji i czasu wykonywania testów i umożliwia bardziej skoncentrowany przegląd.

Dostępne są następujące funkcje:

- Możesz szybciej uzyskać kod, otwierając rozwiązanie bez ładowania żadnego z jego projektów. Po otwarciu rozwiązania można selektywnie wybrać projekty, które mają być ładowane.

- Po ponownym otwarciu rozwiązania visual studio zapamiętuje, które projekty zostały załadowane w poprzedniej sesji i ładuje tylko te projekty.

- Można utworzyć plik filtru rozwiązania, aby zapisać jedną lub więcej konfiguracji obciążenia projektu lub udostępnić konfigurację kolegom z zespołu.

## <a name="open-a-filtered-solution"></a>Otwieranie filtrowanego rozwiązania

Rozwiązanie można otworzyć bez ładowania któregokolwiek z jego projektów bezpośrednio z okna dialogowego **Otwórz projekt** lub za pośrednictwem [wiersza polecenia](#command-line).

### <a name="open-project-dialog"></a>Okno dialogowe Otwórz projekt

Aby otworzyć rozwiązanie bez ładowania żadnego z jego projektów przy użyciu okna dialogowego **Otwórz projekt:**

1. Z paska menu **wybierz polecenie** > **Otwórz** > **plik projektu/rozwiązania.**

2. W oknie dialogowym **Otwórz projekt** wybierz rozwiązanie, a następnie wybierz pozycję **Nie ładuj projektów**.

   ![Okno dialogowe Otwórz projekt programu Visual Studio z zaznaczonymi nieczyszczaj projektów](media/filtered-solutions/do-not-load-projects.png)

3. Wybierz **pozycję Otwórz**.

   Rozwiązanie otwiera się z wszystkich jego projektów wyładowane.

4. W **Eksploratorze rozwiązań**wybierz projekty, które chcesz załadować (naciśnij klawisz **Ctrl,** klikając przycisk, aby zaznaczyć więcej niż jeden projekt), a następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Przeładuj ponownie projekt**.

   ![Ponowne ładowanie wielu projektów w Eksploratorze rozwiązań programu Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio zapamięta, które projekty są ładowane przy następnym otwarciu rozwiązania lokalnie.

### <a name="command-line"></a>Wiersz polecenia

(Nowość w programie Visual Studio 2019 w wersji 16.1.

Aby otworzyć rozwiązanie bez ładowania żadnego z jego [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) projektów z wiersza polecenia, użyj przełącznika, jak pokazano w poniższym przykładzie:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Przełączanie widoczność projektu niezaładowanych

Możesz wybrać, aby wyświetlić wszystkie projekty w rozwiązaniu lub tylko te załadowane przy użyciu jednej z następujących opcji w **Eksploratorze rozwiązań:**

- Kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Pokaż nieobciążone projekty** lub **Ukryj niezaładowane projekty**.

- Wybierz węzeł rozwiązania, aby włączyć przycisk **Pokaż wszystkie pliki;** następnie kliknij przycisk, aby przełączyć widoczność nieobciążonych projektów.

   ![Przycisk Pokaż wszystkie pliki w Eksploratorze rozwiązań programu Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Załaduj zależności projektu

W rozwiązaniu, w którym są ładowane tylko wybrane projekty, nie można załadować wszystkich zależności projektu projektu. Użyj opcji menu **Załaduj zależności projektu,** aby upewnić się, że wszystkie projekty, od których zależy projekt, są również ładowane. Kliknij prawym przyciskiem myszy jeden lub więcej załadowanych projektów w **Eksploratorze rozwiązań** i wybierz pozycję **Załaduj zależności projektu**.

![Ładowanie zależności projektu w programie Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Pliki filtrów rozwiązania

Jeśli chcesz udostępnić konfigurację obciążenia projektu lub zatwierdzić ją do kontroli źródła, możesz utworzyć plik filtru rozwiązania (ma rozszerzenie *.slnf*). Po otwarciu pliku filtru rozwiązania rozwiązanie zostanie otwarte w programie Visual Studio z załadowanymi określonymi projektami i ukrytymi wszystkimi niezaładowanymi projektami. Można [przełączyć, aby](#toggle-unloaded-project-visibility) wyświetlić niezaładowane projekty.

Pliki filtrów rozwiązań są wizualnie odróżniane od zwykłych plików rozwiązań przez dodatkowy glif lejka w ikonie obok rozwiązania w **Eksploratorze rozwiązań**. Obok nazwy rozwiązania wyświetlana jest również nazwa filtru i liczba załadowanych projektów.

![Otwarty plik filtru rozwiązania w Eksploratorze rozwiązań programu Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Jeśli nowe projekty zostaną dodane do oryginalnego rozwiązania po utworzeniu pliku filtru rozwiązania, są one wyświetlane jako projekty nierozładowane w **Eksploratorze rozwiązań**.

### <a name="create-a-solution-filter-file"></a>Tworzenie pliku filtru rozwiązania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz opcję **Zapisz jako filtr rozwiązania**.

   ![Menu Zapisz jako filtr rozwiązania w Eksploratorze rozwiązań programu Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Wybierz nazwę i lokalizację pliku filtru rozwiązania.

Po utworzeniu pliku filtru rozwiązania jest on dodawany do listy **Ostatnie projekty i rozwiązania** w celu ułatwienia dostępu:

![Otwórz ostatnio w programie Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie zagnieżdżania plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md)
- [Optymalizowanie wydajności programu Visual Studio](optimize-visual-studio-performance.md)
