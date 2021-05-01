---
title: Ładowanie podzestawu projektów
description: Dowiedz się więcej na temat filtrowania rozwiązań i sposobu, w jaki umożliwia ono szybkie ładowanie podzestawu projektów w rozwiązaniu.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: ea30edbaac7248af8e1a58b76aebd66cf44befba
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298733"
---
# <a name="filtered-solutions-in-visual-studio"></a>Odfiltrowane rozwiązania w Visual Studio

Duże zespoły programowe często współpracują przy użyciu jednego dużego rozwiązania z wieloma projektami. Jednak poszczegnieni deweloperzy zwykle pracują nad niewielkim podzbiorem tych projektów. Aby zwiększyć wydajność podczas otwierania dużych rozwiązań, Visual Studio 2019 r. *wprowadzono filtrowanie rozwiązań.* Filtrowanie rozwiązań umożliwia otwarcie rozwiązania z załadowanym tylko projektami selektywnym. Ładowanie podzestawu projektów w rozwiązaniu zmniejsza obciążenie rozwiązania, kompilowanie i testowanie czasu działania oraz umożliwia bardziej skoncentrowany przegląd.

Dostępne są następujące funkcje:

- Kod można uzyskać szybciej, otwierając rozwiązanie bez ładowania żadnego z jego projektów. Po otworeniu rozwiązania możesz selektywnie wybrać projekty do załadowania.

- Po ponownym otwarciu rozwiązania program Visual Studio, które projekty zostały załadowane w poprzedniej sesji, i ładuje tylko te projekty.

- Możesz utworzyć plik filtru rozwiązania, aby zapisać co najmniej jedną konfigurację ładowania projektu lub udostępnić konfigurację innym zespołom.

> [!NOTE]
> Ten temat dotyczy Visual Studio w systemie Windows.

## <a name="open-a-filtered-solution"></a>Otwieranie filtrowanych rozwiązań

Rozwiązanie można otworzyć bez ładowania żadnego z  jego projektów bezpośrednio z okna dialogowego Otwieranie projektu lub za pośrednictwem [wiersza polecenia](#command-line).

### <a name="open-project-dialog"></a>Okno dialogowe Otwieranie projektu

Aby otworzyć rozwiązanie bez ładowania żadnego z jego projektów przy użyciu okna **dialogowego Otwieranie** projektu:

1. Wybierz **pozycję Plik**  >  **Otwórz**  >  **projekt/rozwiązanie** na pasku menu.

2. W **oknie dialogowym Otwieranie** projektu wybierz rozwiązanie, a następnie wybierz pozycję **Nie ładuj projektów.**

   ![Visual Studio Otwieranie projektu z zaznaczoną oknie dialogowym Nie ładuj projektów](media/filtered-solutions/do-not-load-projects.png)

3. Wybierz **pozycję Otwórz.**

   Rozwiązanie zostanie otwarte z zwolnionymi wszystkimi swoimi projektami.

4. W **Eksplorator rozwiązań** projektu wybierz projekty, które chcesz załadować (naciśnij **klawisz Ctrl** podczas klikania, aby wybrać więcej niż jeden projekt), a następnie kliknij prawym przyciskiem myszy projekt i wybierz polecenie Załaduj **ponownie projekt.**

   ![Załaduj ponownie wiele projektów w Visual Studio Eksplorator rozwiązań](media/filtered-solutions/reload-project.png)

   Visual Studio zapamięta, które projekty zostaną załadowane przy następnym otwarciu rozwiązania lokalnie.

### <a name="command-line"></a>Wiersz polecenia

(Nowość w Visual Studio 2019 r. w wersji 16.1).

Aby otworzyć rozwiązanie bez ładowania żadnego z jego projektów z wiersza polecenia, użyj przełącznika , [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) jak pokazano w poniższym przykładzie:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Przełącz niezaładowany wgląd w projekt

Możesz wyświetlić wszystkie projekty w rozwiązaniu lub tylko te załadowane, korzystając z jednej z następujących opcji w **Eksplorator rozwiązań**:

- Kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Pokaż niezaładowane projekty** lub **Ukryj niezaładowane projekty.**

- Wybierz węzeł rozwiązania, aby włączyć **przycisk Pokaż wszystkie** pliki. Następnie kliknij przycisk , aby przełączać widoczność niezaładowanych projektów.

   ![Przycisk Pokaż wszystkie pliki w Visual Studio Eksplorator rozwiązań](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Ładowanie zależności projektu

W rozwiązaniu, w którym ładowane są tylko wybrane projekty, mogą nie być załadowane wszystkie zależności projektu. Użyj opcji menu **Załaduj zależności** projektu, aby upewnić się, że wszystkie projekty, od których zależy projekt, również zostaną załadowane. Kliknij prawym przyciskiem myszy co najmniej jeden załadowany projekt **w programie Eksplorator rozwiązań** a następnie wybierz **pozycję Załaduj zależności projektu.**

![Ładowanie zależności projektu w programie Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

## <a name="solution-filter-files"></a>Pliki filtru rozwiązania

Jeśli chcesz udostępnić konfigurację ładowania projektu lub zatwierdzić ją w kontroli źródła, możesz utworzyć plik filtru rozwiązania (ma rozszerzenie *slnf*). Po otwarciu pliku filtru rozwiązania rozwiązanie zostanie otwarte w skrypcie Visual Studio z załadowanym określonymi projektami i ukryciem wszystkich niezaładowanych projektów. Możesz [przełączyć się,](#toggle-unloaded-project-visibility) aby wyświetlić niezaładowane projekty.

Pliki filtru rozwiązania są wizualnie odróżnione od zwykłych plików rozwiązań za pomocą dodatkowego symbolu lejka na ikonie obok rozwiązania w **Eksplorator rozwiązań**. Nazwa filtru i liczba załadowanych projektów są również wyświetlane obok nazwy rozwiązania.

![Plik filtru rozwiązania otwarty w Visual Studio Eksplorator rozwiązań](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Jeśli nowe projekty zostaną dodane do oryginalnego rozwiązania po utworzeniu pliku filtru rozwiązania, będą one wyświetlane jako niezaładowane projekty w **Eksplorator rozwiązań**.

### <a name="create-a-solution-filter-file"></a>Tworzenie pliku filtru rozwiązania

1. W **Eksplorator rozwiązań** kliknij rozwiązanie prawym przyciskiem myszy i wybierz **pozycję Zapisz jako filtr rozwiązania.**

   ![Menu Filtr rozwiązania Zapisz jako w Visual Studio Eksplorator rozwiązań](media/filtered-solutions/save-as-solution-filter.png)

2. Wybierz nazwę i lokalizację pliku filtru rozwiązania.

Po utworzeniu pliku filtru rozwiązania zostanie on dodany do listy **Ostatnie** projekty i rozwiązania w celu uzyskania łatwego dostępu:

![Otwórz ostatnio w programie Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie zagnieżdżania plików w Eksploratorze rozwiązań](file-nesting-solution-explorer.md)
- [Optymalizowanie wydajności programu Visual Studio](optimize-visual-studio-performance.md)
