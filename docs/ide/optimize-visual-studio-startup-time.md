---
title: Poprawić czas uruchamiania
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 62f6316332ce74ddcd291612524cab2b2019606d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954481"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizowanie czasu uruchamiania programu Visual Studio

Program Visual Studio jest przeznaczony do uruchamiania tak szybko i skutecznie, jak to możliwe. Jednak niektóre rozszerzenia programu Visual Studio i okien narzędzi może niekorzystnie wpłynąć na czas uruchamiania, gdy są ładowane. Można kontrolować zachowanie rozszerzeń powolne i okien narzędzi w **zarządzanie wydajnością programu Visual Studio** okno dialogowe. Aby uzyskać bardziej ogólne porady dotyczące poprawy wydajności, zobacz [i porady dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Zachowanie podczas uruchamiania

Aby uniknąć rozszerzanie czas uruchamiania, Visual Studio 2017 ładuje rozszerzeń przy użyciu _na żądanie_ podejście. To zachowanie oznacza, że rozszerzenia nie otwieraj natychmiast po uruchomieniu programu Visual Studio, ale na zgodnie z potrzebami. Ponadto ponieważ okien narzędzi pozostawione otwarte w poprzedniej sesji programu Visual Studio może zmniejszyć czas uruchamiania, Visual Studio otwiera okien narzędzi w sposób bardziej inteligentne, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje powolne uruchamiania, pojawi się komunikat podręczny, wysyłać alerty o oknie rozszerzenia lub narzędzia, które jest przyczyną spowolnienia. Wiadomość z linkiem do **zarządzanie wydajnością programu Visual Studio** okno dialogowe. Można również otworzyć to okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** z paska menu.

![Zarządzanie wydajnością programu Visual Studio — okno podręczne odczytywanie "Zauważyliśmy tego rozszerzenia... spowalnia program Visual Studio"](../ide/media/vside_perfdialog_popup.png)

Okno dialogowe wyświetla okna narzędzia i rozszerzenia, które mają wpływ na wydajność uruchamiania. Możesz zmienić narzędzia i rozszerzenia ustawień okna, aby zwiększyć wydajność uruchamiania.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Aby zmienić ustawienia rozszerzenia w celu uruchamiania, ładowanie rozwiązania i wpisując wydajności

1. Otwórz **zarządzanie wydajnością programu Visual Studio** okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** z paska menu.

    Jeśli rozszerzenie spowalnia uruchamiania programu Visual Studio, ładowania, rozwiązania lub pisania, rozszerzenia pojawia się w **zarządzanie wydajnością programu Visual Studio** okno dialogowe, w obszarze **rozszerzenia**  >   **Uruchamianie** (lub **ładowania rozwiązań** lub **wpisując**).

    ![Zarządzanie wydajnością programu Visual Studio — widok rozszerzenia](../ide/media/vside_perfdialog_extensions.png)

2. Wybierz rozszerzenie, aby wyłączyć, a następnie wybierz **wyłączyć** przycisku.

Można zawsze ponownie włączyć rozszerzenie dla przyszłych sesji przy użyciu **Menedżera rozszerzeń** lub **zarządzanie wydajnością programu Visual Studio** okno dialogowe.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Aby zmienić ustawienia okna narzędzia, aby poprawić czas uruchamiania

1. Otwórz **zarządzanie wydajnością programu Visual Studio** okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** z paska menu.

    Jeśli okno narzędzia spowalnia uruchamiania programu Visual Studio, okno narzędzia pojawi się w **zarządzanie wydajnością programu Visual Studio** okno dialogowe, w obszarze **narzędzie Windows** > **uruchamiania**.

2. Wybierz okno narzędzia, aby zmienić zachowanie.

3. Wybierz jedną z następujących trzech opcji:

   - **Użyj zachowania domyślnego:** Domyślne zachowanie okna narzędzia. Utrzymywanie wybrania tej opcji nie poprawi wydajność uruchamiania.

   - **Nie pokazuj okna przy uruchamianiu:** W oknie określonego narzędzia jest zawsze zamknięte po otwarciu programu Visual Studio, nawet wtedy, gdy zostanie on otwarty w poprzedniej sesji. Możesz otworzyć okno narzędzia menu odpowiednie, gdy będą potrzebne.

   - **Automatycznie Ukryj okno przy uruchamianiu:** Jeśli okno narzędzia zostało pozostawione otwarte w poprzedniej sesji, ta opcja powoduje grupy okna narzędzi przy uruchamianiu w celu uniknięcia Inicjowanie okna narzędzia. Ta opcja jest dobrym rozwiązaniem, jeśli często używane okna narzędzi. Okna narzędzi jest nadal dostępna, ale nie będzie miało negatywny wpływ na czas uruchamiania programu Visual Studio.

     ![Zarządzanie wydajnością programu Visual Studio — wyświetlanie okien narzędzi](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Niektóre starsze wersje programu Visual Studio 2017 ma funkcję o nazwie **uproszczone ładowanie rozwiązań**. Ta funkcja nie jest już dostępne w programie Visual Studio 2017 w wersji 15.5 i nowszych wersjach. W programie Visual Studio 2017 w wersji 15.5 i nowszych dużych rozwiązań, które zawierają zarządzany kod obciążenia znacznie szybciej niż wcześniej, nawet bez uproszczone ładowanie rozwiązań.

## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Porady dotyczące wydajności programu Visual Studio i wskazówki](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog Visual Studio — rozwiązania obciążenia szybciej za pomocą programu Visual Studio 2017 w wersji 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)