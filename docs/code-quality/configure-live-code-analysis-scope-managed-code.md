---
title: Konfigurowanie zakresu analizy kodu na żywo dla platformy .NET
ms.date: 09/01/2020
description: Dowiedz się więcej na temat analizy w tle w programie Visual Studio. Zobacz, jak ograniczyć analizę do widocznego dokumentu, wszystkie otwarte dokumenty lub wszystkie pliki i projekty.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7a6a7253d4104fbcde09b96b86f5f83a864677cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860402"
---
# <a name="configure-live-code-analysis-for-net"></a>Konfigurowanie analizy kodu na żywo dla platformy .NET

Program Visual Studio wykonuje wiele analiz kodu na żywo, nazywanych również *analizą w tle*, podczas edytowania plików źródłowych w edytorze. Niektóre z nich są wymagane do minimalnej analizy dla akceptowalnego środowiska edytowania środowiska IDE programu Visual Studio. Niektóre z nich mają na celu zwiększenie czasu odpowiedzi dla funkcji środowiska IDE. Niektóre z nich umożliwiają włączenie dodatkowych funkcji środowiska IDE, takich jak diagnostyka i poprawki kodu z analizatorów Roslyn. W oparciu o funkcje te analizy można grupować w następujący sposób:

- **Obliczanie danych diagnostycznych w tle**: Analiza błędów, ostrzeżeń i sugestii w plikach źródłowych. Te diagnostyki są wyświetlane jako wpisy na liście błędów i w edytorze. Mogą być klasyfikowane do dwóch kategorii:
  - Diagnostyka kompilatora C# i Visual Basic
  - Diagnostyka analizatora Roslyn, która obejmuje:

    - Wbudowane analizatory środowiska IDE na potrzeby sugestii dotyczących stylu kodu
    - Wbudowane analizatory urzędów certyfikacji dla sugestii dotyczących jakości kodu
    - Pakiety analizatora innych firm [zainstalowane](./install-roslyn-analyzers.md) dla projektów w bieżącym rozwiązaniu.

- **Inne analizy w tle**: Analiza w celu poprawy czasu reakcji i interakcji z programu Visual Studio na potrzeby funkcji środowiska IDE. Przykłady takich analiz są następujące:
  - Analiza otwartych plików w tle.
  - Kompilacja w tle projektów z otwartymi plikami w celu zrealizowania symboli w celu uzyskania ulepszonej reakcji niektórych funkcji środowiska IDE.
  - Tworzenie składni i pamięci podręcznych symboli.
  - Wykrywanie skojarzenia projektanta dla plików źródłowych, takich jak formularze, kontrolki itp.

## <a name="default-analysis-scope"></a>Domyślny zakres analizy

Domyślnie Analiza kodu na żywo dla obliczeń w tle jest wykonywana dla wszystkich plików, które są _otwarte_ w programie Visual Studio. Niektóre _inne analizy w tle_ wymienione powyżej zostały wykonane dla wszystkich projektów, które mają co najmniej jeden otwarty plik. Chociaż kilka analiz w tle jest wykonywanych dla całego rozwiązania.

## <a name="custom-analysis-scope"></a>Zakres analizy niestandardowej

Domyślny zakres każdej analizy w tle został dostrojony, aby zapewnić optymalne środowisko użytkownika, funkcjonalność i wydajność większości scenariuszy i rozwiązań klientów. Istnieją jednak przypadki, w których klienci mogą chcieć dostosować ten zakres, aby zmniejszyć lub zwiększyć analizę w tle. Na przykład:

- Tryb oszczędzania energii: Użytkownicy korzystający z baterii laptop mogą chcieć zminimalizować zużycie energii, aby wydłużyć czas pracy baterii. W tym scenariuszu chcą zminimalizować analizę w tle.
- Analiza kodu na żądanie: Jeśli użytkownicy wolą wyłączać wykonywanie usługi Live Analyzer i ręcznie przeprowadzać analizę kodu na żądanie, chcą zminimalizować analizę w tle. Zobacz [jak: ręczne przeprowadzanie analizy kodu na żądanie](./how-to-run-code-analysis-manually-for-managed-code.md).
- Pełna analiza rozwiązań: Jeśli użytkownicy chcą zawsze widzieć całą diagnostykę we wszystkich plikach w rozwiązaniu, niezależnie od tego, czy są otwarte w edytorze, czy nie. W tym scenariuszu chcą maksymalizować zakres analizy w tle do całego rozwiązania.

Począwszy od programu Visual Studio 2019 w wersji 16,5, użytkownicy mogą jawnie dostosowywać zakres wszystkich analiz kodu na żywo, w tym obliczeń diagnostycznych, dla projektów C# i Visual Basic. Dostępne zakresy analiz to:

- **Bieżący dokument**: minimalizuje zakres analizy kodu na żywo, aby można było wykonać tylko bieżący lub widoczny plik w edytorze.
- **Otwórz dokumenty**: domyślny zakres analizy kodu na żywo, zgodnie z opisem w powyższej sekcji.
- **Całe rozwiązanie**: maksymalizuje zakres analizy kodu na żywo do wykonania dla wszystkich plików i projektów w całym rozwiązaniu.

W oknie dialogowym Opcje narzędzi można wybrać jeden z powyższych zakresów analizy niestandardowej, wykonując następujące czynności:

1. Aby otworzyć okno dialogowe **Opcje** , na pasku menu w programie Visual Studio wybierz pozycję **Narzędzia**  >  **Opcje**.

2. W oknie dialogowym **Opcje** wybierz **Edytor tekstu**  >  **C#** lub **Basic**  >  **Advanced**.

3. Wybierz żądany **zakres analizy w tle** , aby dostosować zakres analizy. Po zakończeniu wybierz **przycisk OK** .

![Zakres analizy.](./media/background-analysis-scope.png)

> [!NOTE]
> W starszych wersjach programu Visual Studio 2019 w wersji 16,5 Użytkownicy mogą dostosować zakres analizy dla obliczeń diagnostycznych do całego rozwiązania przy użyciu pola wyboru **Włącz analizę pełnej rozwiązań** z opcji **Narzędzia**  >    >  **Edytor tekstu**  >  **C#** lub **podstawowa**  >  karta **Zaawansowane** . W poprzednich wersjach programu Visual Studio nie jest obsługiwane minimalizowanie zakresu analizy w tle.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Automatycznie Minimalizuj zakres analizy kodu na żywo

Jeśli program Visual Studio wykryje, że dostępna jest 200 MB lub mniej pamięci systemowej, automatycznie minimalizuje zakres analizy kodu na żywo do "bieżącego dokumentu". W takim przypadku zostanie wyświetlony alert informujący o tym, że program Visual Studio wyłączył niektóre funkcje. Przycisk umożliwia przełączenie z powrotem do wcześniejszego zakresu analizy, jeśli chcesz.

![Zakres analizy minimalizowania tekstu alertu](./media/fsa_alert.png)

## <a name="see-also"></a>Zobacz też

- [Automatyczne wstrzymanie funkcji](./automatic-feature-suspension.md)
- [Żądanie funkcji trybu oszczędzania w trybie oszczędzania](https://github.com/dotnet/roslyn/issues/38429)
