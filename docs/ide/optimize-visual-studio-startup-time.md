---
title: Zwiększ czas uruchamiania
description: Dowiedz się, jak kontrolować ustawienia rozszerzeń i okien narzędzi w oknie dialogowym Zarządzanie wydajnością programu Visual Studio w celu usprawnienia czasu uruchamiania programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/15/2017
ms.topic: how-to
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: c409ad35b3d9c09a5dbe574d00a24d1f2bcb8370
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479956"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizuj czas uruchamiania programu Visual Studio

Program Visual Studio został zaprojektowany tak, aby można go było szybko i wydajnie uruchamiać. Jednak niektóre rozszerzenia programu Visual Studio i okna narzędzi mogą niekorzystnie wpłynąć na czas uruchamiania podczas ładowania. Możesz kontrolować zachowanie wolnych rozszerzeń i okien narzędzi w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** . Aby uzyskać bardziej ogólne porady dotyczące poprawy wydajności, zobacz [porady i wskazówki dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Zachowanie podczas uruchamiania

Aby uniknąć wydłużenia czasu uruchamiania, program Visual Studio ładuje rozszerzenia przy użyciu podejścia _na żądanie_ . To zachowanie oznacza, że rozszerzenia nie otwierają się natychmiast po uruchomieniu programu Visual Studio, ale zgodnie z potrzebami. Ponadto, ponieważ okna narzędzi otwierane w poprzedniej sesji programu Visual Studio mogą spowalniać uruchamianie, program Visual Studio otwiera okna narzędzi w bardziej inteligentny sposób, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje wolne uruchomienie, zostanie wyświetlony komunikat podręczny z powiadomieniem o rozszerzeniu lub oknie narzędzi, które powoduje spowolnienie. Komunikat zawiera link do okna dialogowego **Zarządzanie wydajnością programu Visual Studio** . Możesz również uzyskać dostęp do tego okna dialogowego, wybierając pozycję **Pomoc**  >  **Zarządzanie wydajnością programu Visual Studio** z paska menu.

![Zarządzanie wydajnością programu Visual Studio — odczyt podręczny "Zauważyliśmy, że rozszerzenie... spowalnia program Visual Studio "](../ide/media/vside_perfdialog_popup.png)

Okno dialogowe zawiera listę rozszerzeń i narzędzi, które mają wpływ na wydajność uruchamiania. Można zmienić rozszerzenie i ustawienia okna narzędzi, aby zwiększyć wydajność uruchamiania.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Aby zmienić ustawienia rozszerzenia w celu usprawnienia uruchamiania, ładowania rozwiązań i pisania wydajności

1. Otwórz okno dialogowe **Zarządzanie wydajnością programu Visual Studio** , wybierając pozycję **Pomoc**  >  **Zarządzanie wydajnością programu Visual Studio** z paska menu.

    Jeśli rozszerzenie spowalnia Uruchamianie programu Visual Studio, ładowanie rozwiązania lub wpisywanie, rozszerzenie pojawia się w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** w obszarze **Extensions**  >  **Uruchamianie** rozszerzeń (lub **ładowanie rozwiązania** lub **wpisywanie**).

    ![Zarządzanie wydajnością programu Visual Studio — widok rozszerzeń](../ide/media/vside_perfdialog_extensions.png)

2. Wybierz rozszerzenie, które chcesz wyłączyć, a następnie wybierz przycisk **Wyłącz** .

Można zawsze ponownie włączyć rozszerzenie dla przyszłych sesji za pomocą **Menedżera rozszerzeń** lub okna dialogowego **Zarządzanie wydajnością programu Visual Studio** .

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Aby zmienić ustawienia okna narzędzi w celu usprawnienia czasu uruchamiania

1. Otwórz okno dialogowe **Zarządzanie wydajnością programu Visual Studio** , wybierając pozycję **Pomoc**  >  **Zarządzanie wydajnością programu Visual Studio** z paska menu.

    Jeśli okno narzędzia spowalnia Uruchamianie programu Visual Studio, okno narzędzia pojawia się w oknie dialogowym **Zarządzanie wydajnością programu Visual Studio** w obszarze narzędzia uruchamianie **systemu Windows**  >  **Startup**.

2. Wybierz okno narzędzi, dla którego chcesz zmienić zachowanie.

3. Wybierz jedną z następujących trzech opcji:

   - **Użyj zachowania domyślnego:** Domyślne zachowanie okna narzędzi. Pozostawienie wybranej opcji nie spowoduje zwiększenia wydajności uruchamiania.

   - **Nie pokazuj okna przy uruchamianiu:** Określone okno narzędzi jest zawsze zamknięte po otwarciu programu Visual Studio, nawet jeśli zostało ono otwarte w poprzedniej sesji. Możesz otworzyć okno narzędzi z odpowiedniego menu, gdy będzie to potrzebne.

   - **Automatycznie Ukryj okno przy uruchamianiu:** Jeśli okno narzędzi zostało otwarte w poprzedniej sesji, ta opcja Zwija grupę okna narzędzia przy uruchamianiu, aby uniknąć inicjalizacji okna narzędzi. Ta opcja jest dobrym rozwiązaniem w przypadku częstego używania okna narzędzi. Okno narzędzi jest nadal dostępne, ale nie ma już negatywnego wpływu na czas uruchamiania programu Visual Studio.

     ![Zarządzanie wydajnością programu Visual Studio — widok systemu Windows](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Niektóre starsze wersje programu Visual Studio 2017 miały funkcję o nazwie **uproszczone ładowanie rozwiązań**. W bieżących wersjach, duże rozwiązania zawierające kod zarządzany znacznie szybciej niż wcześniej, nawet bez uproszczonego ładowania rozwiązania.

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Porady i wskazówki dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Rozwiązania do ładowania blogów z programu Visual Studio szybciej dzięki programowi Visual Studio 2017 w wersji 15,6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
