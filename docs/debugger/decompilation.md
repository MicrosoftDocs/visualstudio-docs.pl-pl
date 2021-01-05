---
title: Dekompilowanie kodu platformy .NET podczas debugowania | Microsoft Docs
description: Generuj i osadzaj kod źródłowy z zestawów .NET podczas debugowania w programie Visual Studio. Wyodrębnij i Wyświetl osadzony kod źródłowy.
ms.custom: SEO-VS-2020
ms.date: 2/2/2020
ms.topic: how-to
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
ms.openlocfilehash: 8ad919b14642dff98746c194ad8c05bbb3aea529
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726738"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generuj kod źródłowy z zestawów .NET podczas debugowania

Podczas debugowania aplikacji .NET może się okazać, że chcesz wyświetlić kod źródłowy, którego nie masz. Na przykład, przerwanie na wyjątek lub użycie stosu wywołań do przejścia do lokalizacji źródłowej.

> [!NOTE]
> * Generowanie kodu źródłowego (dekompilacja) jest dostępne tylko dla aplikacji .NET i opiera się na projekcie [ILSpy](https://github.com/icsharpcode/ILSpy) Open Source.
> * Dekompilacja jest dostępna tylko w programie Visual Studio 2019 16,5 i nowszych.
> * Zastosowanie atrybutu [SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) do zestawu lub modułu uniemożliwia programowi Visual Studio podjęcie próby dekompilacji.

## <a name="generate-source-code"></a>Generuj kod źródłowy

Gdy debugujesz, a żaden kod źródłowy nie jest dostępny, program Visual Studio wyświetli dokument, który **nie został znaleziony** , lub jeśli nie masz symboli dla zestawu, **nie załadowano żadnych symboli** . Oba dokumenty mają opcję **dekompilowania kodu źródłowego** , która generuje kod C# dla bieżącej lokalizacji. Wygenerowany kod C# można następnie użyć podobnie jak każdy inny kod źródłowy. Można wyświetlić kod, zbadać zmienne, ustawić punkty przerwania i tak dalej.

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

Wyodrębnione pliki źródłowe są dodawane do rozwiązania jako [różne pliki](../ide/reference/miscellaneous-files.md). Funkcja różne pliki jest domyślnie wyłączona w programie Visual Studio. Tę funkcję można włączyć z poziomu opcji **Narzędzia**  >    >    >  **dokumenty** środowiska  >  **Pokaż różne pliki w Eksplorator rozwiązań** pole wyboru. Bez włączania tej funkcji nie będzie można otworzyć wyodrębnionego kodu źródłowego.

![Zrzut ekranu strony opcji narzędzia z włączoną opcją różne pliki.](media/decompilation-tools-options-misc-files.png)

Wyodrębnione pliki źródłowe pojawiają się w różnych plikach w **Eksplorator rozwiązań**.

![Zrzut ekranu Eksploratora rozwiązań z różnymi plikami.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Znane ograniczenia

### <a name="requires-break-mode"></a>Wymaga trybu przerwania

Generowanie kodu źródłowego przy użyciu dekompilacji jest możliwe tylko wtedy, gdy debuger jest w trybie przerwania i aplikacja jest wstrzymana. Na przykład program Visual Studio wprowadza tryb przerwania, gdy trafi do punktu przerwania lub wyjątku. Możesz łatwo wyzwolić program Visual Studio, aby przerwać przy następnym uruchomieniu kodu przy użyciu polecenia **Break All** ( ![ Przerwij wszystko ](media/decompilation-break-all.png) ).

### <a name="decompilation-limitations"></a>Ograniczenia dotyczące dekompilacji

Generowanie kodu źródłowego z formatu pośredniego (IL), który jest używany w zestawach .NET, ma pewne własne ograniczenia. W związku z tym wygenerowany kod źródłowy nie wygląda jak oryginalny kod źródłowy. Większość różnic polega na miejscach, w których informacje w oryginalnym kodzie źródłowym nie są potrzebne w czasie wykonywania. Na przykład informacje takie jak odstępy, komentarze i nazwy zmiennych lokalnych nie są potrzebne w czasie wykonywania. Zalecamy użycie generowanego źródła, aby zrozumieć, w jaki sposób program jest wykonywany, a nie jako zamiennik oryginalnego kodu źródłowego.

### <a name="debug-optimized-or-release-assemblies"></a>Debugowanie zestawów zoptymalizowanych lub wydań

Podczas debugowania kodu, który został dekompilowany z zestawu, który został skompilowany przy użyciu optymalizacji kompilatora, mogą występować następujące problemy:
- Punkty przerwania nie zawsze są powiązane z pasującą lokalizacją pochodzenia.
- Krokowe nie zawsze należy do poprawnej lokalizacji.
- Zmienne lokalne mogą nie mieć dokładnych nazw.
- Niektóre zmienne mogą nie być dostępne do oceny.

Więcej szczegółów można znaleźć w temacie problem z usługą GitHub: [ICSharpCode. dekompilator — informacje Integration w debugerze programu vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Niezawodność dekompilacji

Stosunkowo niewielki procent prób dekompilacji może skutkować niepowodzeniem. Jest to spowodowane błędem odwołania o wartości null punktu sekwencji w ILSpy.  Wyeliminowano błąd, przechwytując te problemy i łagodnie kończy się niepowodzeniem podczas próby dekompilacji.

Więcej szczegółów można znaleźć w temacie problem z usługą GitHub: [ICSharpCode. dekompilator — informacje Integration w debugerze programu vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Ograniczenia związane z kodem asynchronicznym

Wyniki z dekompilowania modułów z wzorcem kodu Async/await mogą być niekompletne lub w całości kończyć się niepowodzeniem. ILSpy implementacja Async/await i Yield State-Machines jest tylko częściowo zaimplementowana. 

Więcej szczegółów można znaleźć w temacie problem z usługą plików [PDB](https://github.com/icsharpcode/ILSpy/issues/1422):.

### <a name="just-my-code"></a>Tylko mój kod

Ustawienia [tylko mój kod (JMC)](./just-my-code.md) pozwalają programowi Visual Studio na przechodzenie przez system, strukturę, bibliotekę i inne wywołania niebędące użytkownikami. Podczas sesji debugowania w oknie **moduły** są wyświetlane moduły kodu, które debuger jest traktowany jako mój kod (kod użytkownika).

Dekompilacja modułów zoptymalizowanych lub wydań generuje kod niebędący użytkownikiem. Jeśli debuger przerwie w nieskompilowanym kodzie nieużywanym przez użytkownika, na przykład okno **nie** zostanie wyświetlone. Aby wyłączyć tylko mój kod, przejdź do   >  **opcji** narzędzia (lub   >  **Opcje** debugowania) > **debugowania**  >  **Ogólne**, a następnie usuń zaznaczenie opcji **Włącz tylko mój kod**.

### <a name="extracted-sources"></a>Wyodrębnione źródła

Kod źródłowy wyodrębniony z zestawu ma następujące ograniczenia:
- Nazwy i lokalizacji wygenerowanych plików nie można skonfigurować.
- Pliki są tymczasowe i zostaną usunięte przez program Visual Studio.
- Pliki są umieszczane w pojedynczym folderze, a wszystkie hierarchie folderów, których oryginalne źródła nie były używane.
- Nazwa pliku dla każdego pliku zawiera skrót sumy kontrolnej pliku.

### <a name="generated-code-is-c-only"></a>Wygenerowany kod jest tylko w języku C#
Dekompilacja generuje tylko pliki kodu źródłowego w języku C#. Nie ma możliwości generowania plików w żadnym innym języku.