---
title: Dekompilowanie kodu .NET podczas debugowania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508748"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generowanie kodu źródłowego z zestawów .NET podczas debugowania

Podczas debugowania aplikacji .NET może się okazać, że chcesz wyświetlić kod źródłowy, który nie masz. Na przykład podział na wyjątek lub za pomocą stosu wywołań, aby przejść do lokalizacji źródłowej.

> [!NOTE]
> * Generowanie kodu źródłowego (dekompilacja) jest dostępne tylko dla aplikacji .NET i jest oparte na projekcie [ILSpy](https://github.com/icsharpcode/ILSpy) open source.
> * Dekompilacja jest dostępna tylko w programie Visual Studio 2019 16.5 i nowszych.
> * Zastosowanie [atrybutu SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) do zestawu lub modułu uniemożliwia programowi Visual Studio podejmowanie próby dekompilacji.

## <a name="generate-source-code"></a>Generowanie kodu źródłowego

Podczas debugowania i nie jest dostępny kod źródłowy, Visual Studio pokazuje **źródło nie znaleziono** dokumentu lub jeśli nie masz symboli dla zestawu, Nie **symbole załadowany** dokument. Oba dokumenty mają **dekompilowany kod źródłowy** opcja, która generuje kod C# dla bieżącej lokalizacji. Wygenerowany kod Języka C# może być następnie używany tak samo, jak każdy inny kod źródłowy. Można wyświetlić kod, sprawdzić zmienne, ustawić punkty przerwania i tak dalej.

### <a name="no-symbols-loaded"></a>Brak załadowanych symboli

Na poniższej ilustracji przedstawiono komunikat **Brak załadowanych symboli.**

![Zrzut ekranu przedstawiający brak załadowanego dokumentu bez symbolu](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Nie znaleziono źródła

Na poniższej ilustracji przedstawiono komunikat **Nie znaleziono źródła.**

![Zrzut ekranu przedstawiający nieotworzę nie znaleziony dokument źródłowy](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generowanie i osadzanie źródeł dla złożenia

Oprócz generowania kodu źródłowego dla określonej lokalizacji, można wygenerować cały kod źródłowy dla danego zestawu .NET. Aby to zrobić, przejdź do okna **Moduły** i z menu kontekstowego zestawu .NET, a następnie wybierz polecenie **Decompile kod źródłowy.** Visual Studio generuje plik symbolu dla zestawu, a następnie osadza źródło w pliku symbolu. W późniejszym kroku można [wyodrębnić](#extract-and-view-the-embedded-source-code) osadzony kod źródłowy.

![Zrzut ekranu przedstawiający menu kontekstowe zestawu w oknie modułów z poleceniem dekompilacyjnym źródłowym.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Wyodrębnianie i wyświetlanie osadzonego kodu źródłowego

Można wyodrębnić pliki źródłowe, które są osadzone w pliku symbolu za pomocą polecenia **Wyodrębnij kod źródłowy** w menu kontekstowym okna **Moduły.**

![Zrzut ekranu przedstawiający menu kontekstowe zestawu w oknie modułów z poleceniem wyodrębnij źródła.](media/decompilation-extract-source-code.png)

Wyodrębnione pliki źródłowe są dodawane do rozwiązania jako [różne pliki](../ide/reference/miscellaneous-files.md). Funkcja różnych plików jest domyślnie wyłączona w programie Visual Studio. Tę funkcję można włączyć w menu wyboru **Opcje narzędzi** > **Options** > **Dokumenty** > **środowiska** > Pokaż różne**pliki w Eksploratorze rozwiązań.** Bez włączenia tej funkcji nie będzie można otworzyć wyodrębnionego kodu źródłowego.

![Zrzut ekranu przedstawiający stronę opcji narzędzi z włączoną opcją różnych plików.](media/decompilation-tools-options-misc-files.png)

Wyodrębnione pliki źródłowe pojawiają się w różnych plikach w **Eksploratorze rozwiązań**.

![Zrzut ekranu przedstawiający Eksploratora rozwiązań z różnymi plikami.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Znane ograniczenia

### <a name="requires-break-mode"></a>Wymaga trybu przerwania

Generowanie kodu źródłowego przy użyciu dekompilacji jest możliwe tylko wtedy, gdy debuger jest w trybie przerwania, a aplikacja jest wstrzymana. Na przykład Visual Studio wchodzi w tryb przerwania, gdy trafi punkt przerwania lub wyjątek. Program Visual Studio można łatwo wyzwolić, aby przerwać następnym![uruchomieniu kodu](media/decompilation-break-all.png)przy użyciu polecenia **Podziel wszystko** (Przerwij wszystkie ikony).

### <a name="decompilation-limitations"></a>Ograniczenia dekompilacji

Generowanie kodu źródłowego z formatu pośredniego (IL), który jest używany w zestawach .NET ma pewne nieodłączne ograniczenia. W związku z tym wygenerowany kod źródłowy nie wygląda jak oryginalny kod źródłowy. Większość różnic są w miejscach, w których informacje w oryginalnym kodzie źródłowym nie jest potrzebne w czasie wykonywania. Na przykład informacje, takie jak odstępy, komentarze i nazwy zmiennych lokalnych nie są potrzebne w czasie wykonywania. Zaleca się użycie wygenerowanego źródła, aby zrozumieć, jak program jest wykonywany, a nie jako zamiennik oryginalnego kodu źródłowego.

### <a name="debug-optimized-or-release-assemblies"></a>Zestawy zoptymalizowane pod kątem debugowania lub zwalniania

Podczas debugowania kodu, który został dekompilowany z zestawu, który został skompilowany przy użyciu optymalizacji kompilatora, można natknąć się na następujące problemy:
- Punkty przerwania nie zawsze mogą być powiązane z pasującą lokalizacją zaopatrzenia.
- Stepping nie zawsze krok do właściwej lokalizacji.
- Zmienne lokalne mogą nie mieć dokładnych nazw.
- Niektóre zmienne mogą nie być dostępne do oceny.

Więcej szczegółów można znaleźć w problemie z gitHubem: [integracja ICSharpCode.Decompiler z debugerem VS](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Niezawodność dekompilacji

Stosunkowo niewielki procent prób dekompilacji może spowodować niepowodzenie. Jest to spowodowane błędem odwołania do wartości null punktu sekwencji w ILSpy.  Złagodziliśmy niepowodzenie, łapiąc te problemy i z wdziękiem nie udając się próba dekompilacji.

Więcej szczegółów można znaleźć w problemie z gitHubem: [integracja ICSharpCode.Decompiler z debugerem VS](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Ograniczenia z kodem asynchronizowym

Wyniki z dekompilacji modułów z wzorcami kodu asynchronicznie/await mogą być niekompletne lub całkowicie nie. Implementacja ILSpy asynchronii/await i wydajność maszyn stanowych jest tylko częściowo zaimplementowana. 

Więcej szczegółów można znaleźć w problemie z gitHub: [Status generatora PDB](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Tylko mój kod

Ustawienia [Just My Code (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) umożliwia visual studio krok przez system, struktury, biblioteki i innych wywołań innych użytkowników. Podczas sesji debugowania okna **Moduły** pokazuje, które moduły kodu debugera traktuje jako Mój kod (kod użytkownika).

Dekompilacja zoptymalizowanych lub zwolnionych modułów tworzy kod niebędący użytkownikiem. Jeśli debuger przerwy w dekompilowanym kodzie nie-użytkownik, na przykład pojawi się okno **Brak źródła.** Aby wyłączyć tylko mój kod, przejdź do**opcji** **narzędzi** > (lub**opcji** **debugowania)** > > **Debugowanie** > **ogólne**, a następnie usuń zaznaczenie opcji Włącz tylko **mój kod**.

### <a name="extracted-sources"></a>Źródła wyodrębnione

Kod źródłowy wyodrębniony z zestawu ma następujące ograniczenia:
- Nazwa i lokalizacja wygenerowanych plików nie można skonfigurować.
- Pliki są tymczasowe i zostaną usunięte przez program Visual Studio.
- Pliki są umieszczane w jednym folderze, a żadna hierarchia folderów, które oryginalne źródła nie jest używany.
- Nazwa pliku dla każdego pliku zawiera skrót sumy kontrolnej pliku.

### <a name="generated-code-is-c-only"></a>Wygenerowany kod jest tylko C#
Dekompilacja generuje tylko pliki kodu źródłowego w języku C#. Nie ma opcji generowania plików w innym języku.
