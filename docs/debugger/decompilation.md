---
title: Dekompilowanie kodu platformy .NET podczas debugowania | Microsoft Docs
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: ffd5f2e4bfc13f79b519fbdf9b3cf517793cd324
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091934"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generuj kod źródłowy z zestawów .NET podczas debugowania

Podczas debugowania aplikacji .NET może się okazać, że chcesz wyświetlić kod źródłowy, którego nie masz. Na przykład, przerwanie na wyjątek lub użycie stosu wywołań do przejścia do lokalizacji źródłowej.

> [!NOTE]
> * Generowanie kodu źródłowego (dekompilacja) jest dostępne tylko dla aplikacji .NET i opiera się na projekcie [ILSpy](https://github.com/icsharpcode/ILSpy) Open Source.
> * Dekompilacja jest dostępna tylko w programie Visual Studio 2019 16,5 i nowszych.

## <a name="generate-source-code"></a>Generuj kod źródłowy

Gdy debugujesz, a żaden kod źródłowy nie jest dostępny, program Visual Studio wyświetli dokument, który **nie został znaleziony** , lub jeśli nie masz symboli dla zestawu, **nie załadowano żadnych symboli** . Oba dokumenty mają opcję **dekompilowania kodu źródłowego** , która C# generuje kod dla bieżącej lokalizacji. Wygenerowany C# kod może być następnie używany podobnie jak każdy inny kod źródłowy. Można wyświetlić kod, zbadać zmienne, ustawić punkty przerwania i tak dalej.

### <a name="no-symbols-loaded"></a>Nie załadowano żadnych symboli

Poniższa ilustracja przedstawia komunikat **nie załadowano symboli** .

![Zrzut ekranu przedstawiający dokument bez symbolu załadowanego](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Nie znaleziono źródła

Poniższa ilustracja przedstawia komunikat **nie znaleziono źródła** .

![Zrzut ekranu źródła nie znaleziono dokumentu](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generowanie i osadzanie źródeł dla zestawu

Oprócz generowania kodu źródłowego dla określonej lokalizacji, można wygenerować cały kod źródłowy dla danego zestawu .NET. W tym celu przejdź do okna **moduły** i z menu kontekstowego zestawu .NET, a następnie wybierz polecenie **Dekompiluj kod źródłowy** . Program Visual Studio generuje plik symboli dla zestawu, a następnie osadza źródło w pliku symboli. W późniejszym kroku można [wyodrębnić](#extract-and-view-the-embedded-source-code) osadzony kod źródłowy.

![Zrzut ekranu przedstawiający menu kontekstowe zestawu w oknie modułów z poleceniem dekompilowania źródła.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Wyodrębnij i Wyświetl osadzony kod źródłowy

Pliki źródłowe, które są osadzone w pliku symboli, można wyodrębnić przy użyciu polecenia **Wyodrębnij kod źródłowy** z menu kontekstowego okna **moduły** .

![Zrzut ekranu przedstawiający menu kontekstowe zestawu w oknie modułów z poleceniem Wyodrębnij źródła.](media/decompilation-extract-source-code.png)

Wyodrębnione pliki źródłowe są dodawane do rozwiązania jako [różne pliki](../ide/reference/miscellaneous-files.md). Funkcja różne pliki jest domyślnie wyłączona w programie Visual Studio. Tę funkcję można włączyć z poziomu **narzędzi** > **opcje** > **środowisku** > **dokumenty** > **Pokaż różne pliki w Eksplorator rozwiązań** pole wyboru. Bez włączania tej funkcji nie będzie można otworzyć wyodrębnionego kodu źródłowego.

![Zrzut ekranu strony opcji narzędzia z włączoną opcją różne pliki.](media/decompilation-tools-options-misc-files.png)

Wyodrębnione pliki źródłowe pojawiają się w różnych plikach w **Eksplorator rozwiązań**.

![Zrzut ekranu Eksploratora rozwiązań z różnymi plikami.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Znane ograniczenia

### <a name="requires-break-mode"></a>Wymaga trybu przerwania

Generowanie kodu źródłowego przy użyciu dekompilacji jest możliwe tylko wtedy, gdy debuger jest w trybie przerwania i aplikacja jest wstrzymana. Na przykład program Visual Studio wprowadza tryb przerwania, gdy trafi do punktu przerwania lub wyjątku. Można z łatwością wyzwolić program Visual Studio do przerwania przy następnym uruchomieniu kodu przy użyciu polecenia **Break All** (![Przerwij wszystkie ikony](media/decompilation-break-all.png)).

### <a name="decompilation-limitations"></a>Ograniczenia dotyczące dekompilacji

Generowanie kodu źródłowego z formatu pośredniego (IL), który jest używany w zestawach .NET, ma pewne własne ograniczenia. W związku z tym wygenerowany kod źródłowy nie wygląda jak oryginalny kod źródłowy. Większość różnic polega na miejscach, w których informacje w oryginalnym kodzie źródłowym nie są potrzebne w czasie wykonywania. Na przykład informacje takie jak odstępy, komentarze i nazwy zmiennych lokalnych nie są potrzebne w czasie wykonywania. Zalecamy użycie generowanego źródła, aby zrozumieć, w jaki sposób program jest wykonywany, a nie jako zamiennik oryginalnego kodu źródłowego.

### <a name="debug-optimized-or-release-assemblies"></a>Debugowanie zestawów zoptymalizowanych lub wydań

Podczas debugowania kodu, który został dekompilowany z zestawu, który został skompilowany przy użyciu optymalizacji kompilatora, mogą występować następujące problemy:
- Punkty przerwania nie zawsze są powiązane z pasującą lokalizacją pochodzenia.
- Krokowe nie zawsze należy do poprawnej lokalizacji.
- Zmienne lokalne mogą nie mieć dokładnych nazw.

Więcej szczegółów można znaleźć w temacie problem z usługą GitHub: [IChsarpCompiler. dekompilator — informacje Integration w debugerze programu vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="extracted-sources"></a>Wyodrębnione źródła

Kod źródłowy wyodrębniony z zestawu ma następujące ograniczenia:
- Nazwy i lokalizacji wygenerowanych plików nie można skonfigurować.
- Pliki są tymczasowe i zostaną usunięte przez program Visual Studio.
- Pliki są umieszczane w pojedynczym folderze, a wszystkie hierarchie folderów, których oryginalne źródła nie były używane.
- Nazwa pliku dla każdego pliku zawiera skrót sumy kontrolnej pliku.

### <a name="generated-code-is-c-only"></a>Wygenerowany kod jest C# tylko
Dekompilacja generuje tylko pliki kodu źródłowego w C#programie. Nie ma możliwości generowania plików w żadnym innym języku.