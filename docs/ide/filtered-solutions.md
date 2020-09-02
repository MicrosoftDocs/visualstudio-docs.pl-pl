---
title: Załaduj podzestaw projektów
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650835"
---
# <a name="filtered-solutions-in-visual-studio"></a>Rozwiązania filtrowane w programie Visual Studio

Duże zespoły programistyczne często współpracują z wykorzystaniem jednego dużego rozwiązania z wieloma projektami. Jednak Indywidualni deweloperzy zazwyczaj pracują nad małym podzbiorem tych projektów. Aby zwiększyć wydajność podczas otwierania dużych rozwiązań, program Visual Studio 2019 wprowadził *filtrowanie rozwiązań*. Filtrowanie rozwiązań pozwala otworzyć rozwiązanie z załadowanymi tylko projektami selektywnymi. Ładowanie podzestawu projektów w rozwiązaniu zmniejsza obciążenie, kompilację i czas wykonywania testu oraz umożliwia dokładniejsze przegląd.

Dostępne są następujące funkcje:

- Możesz szybciej uzyskać kod, otwierając rozwiązanie bez ładowania żadnego z jego projektów. Po otwarciu rozwiązania można wybiórczo wybierać projekty do załadowania.

- Po ponownym otwarciu rozwiązania program Visual Studio zapamiętuje projekty, które zostały załadowane w poprzedniej sesji i ładuje tylko te projekty.

- Można utworzyć plik filtru rozwiązania, aby zapisać co najmniej jedną konfigurację ładowania projektu lub udostępnić konfigurację członkom zespołu.

## <a name="open-a-filtered-solution"></a>Otwórz filtrowane rozwiązanie

Możesz otworzyć rozwiązanie bez ładowania żadnego z jego projektów bezpośrednio z okna dialogowego **Otwórz projekt** lub [wiersza polecenia](#command-line).

### <a name="open-project-dialog"></a>Otwórz okno dialogowe projektu

Aby otworzyć rozwiązanie bez ładowania żadnego z jego projektów przy użyciu okna dialogowego **Otwórz projekt** :

1. Wybierz pozycję **plik**  >  **Otwórz**  >  **projekt/rozwiązanie** z paska menu.

2. W oknie dialogowym **Otwórz projekt** wybierz rozwiązanie, a następnie wybierz pozycję nie **Ładuj projektów**.

   ![Okno dialogowe otwierania projektu programu Visual Studio z zaznaczoną opcją nie Ładuj projektów](media/filtered-solutions/do-not-load-projects.png)

3. Wybierz pozycję **Otwórz**.

   Zostanie otwarte rozwiązanie ze wszystkimi niezaładowanymi swoimi projektami.

4. W **Eksplorator rozwiązań**wybierz projekty, które chcesz załadować (naciśnij klawisz **Ctrl** podczas klikania, aby zaznaczyć więcej niż jeden projekt), a następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Załaduj ponownie projekt**.

   ![Załaduj ponownie wiele projektów w programie Visual Studio Eksplorator rozwiązań](media/filtered-solutions/reload-project.png)

   Program Visual Studio będzie pamiętać, które projekty są ładowane przy następnym otwarciu rozwiązania lokalnie.

### <a name="command-line"></a>Wiersz polecenia

(Nowość w programie Visual Studio 2019 w wersji 16,1).

Aby otworzyć rozwiązanie bez ładowania żadnego z jego projektów z wiersza polecenia, należy użyć przełącznika, [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) jak pokazano w następującym przykładzie:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Przełącz widoczność niezaładowanych projektów

Możesz wyświetlić wszystkie projekty w rozwiązaniu lub tylko te, które zostały załadowane, korzystając z jednej z następujących opcji w **Eksplorator rozwiązań**:

- Kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Pokaż niezaładowane projekty** lub **Ukryj niezaładowane projekty**.

- Wybierz węzeł rozwiązania, aby włączyć przycisk **Pokaż wszystkie pliki** ; następnie kliknij przycisk, aby przełączyć widoczność niezaładowanych projektów.

   ![Przycisk Pokaż wszystkie pliki w programie Visual Studio Eksplorator rozwiązań](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Załaduj zależności projektu

W rozwiązaniu, w którym załadowano tylko wybrane projekty, nie można załadować wszystkich zależności projektu projektu. Użyj opcji menu **Załaduj zależności projektu** , aby upewnić się, że wszystkie projekty, od których zależy projekt, są również ładowane. Kliknij prawym przyciskiem myszy jeden lub więcej załadowanych projektów w **Eksplorator rozwiązań** i wybierz pozycję **Załaduj zależności projektu**.

![Załaduj zależności projektu w programie Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Pliki filtrów rozwiązań

Jeśli chcesz udostępnić konfigurację ładowania projektu lub zatwierdzić ją w kontroli źródła, możesz utworzyć plik filtru rozwiązania (ma rozszerzenie *. slnf*). Po otwarciu pliku filtru rozwiązania rozwiązanie otwiera się w programie Visual Studio z załadowanymi określonymi projektami i wszystkimi niezaładowanymi projektami. Można [przełączyć](#toggle-unloaded-project-visibility) , aby wyświetlić niezaładowane projekty.

Pliki filtrów rozwiązań są wizualnie odróżniane od zwykłych plików rozwiązania przez dodatkowy symbol lejka w ikonie obok rozwiązania w **Eksplorator rozwiązań**. Nazwa filtru i liczba załadowanych projektów są również wyświetlane obok nazwy rozwiązania.

![Plik filtru rozwiązania otwarty w programie Visual Studio Eksplorator rozwiązań](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Jeśli nowe projekty zostaną dodane do oryginalnego rozwiązania po utworzeniu pliku filtru rozwiązania, są one wyświetlane jako niezaładowane projekty w **Eksplorator rozwiązań**.

### <a name="create-a-solution-filter-file"></a>Utwórz plik filtru rozwiązania

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Zapisz jako filtr rozwiązania**.

   ![Menu filtrowania rozwiązań w programie Visual Studio Eksplorator rozwiązań](media/filtered-solutions/save-as-solution-filter.png)

2. Wybierz nazwę i lokalizację pliku filtru rozwiązania.

Po utworzeniu pliku filtru rozwiązania zostanie on dodany do listy **ostatnio używanych projektów i rozwiązań** w celu ułatwienia dostępu:

![Otwórz ostatnie w programie Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie zagnieżdżania plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md)
- [Optymalizowanie wydajności programu Visual Studio](optimize-visual-studio-performance.md)
