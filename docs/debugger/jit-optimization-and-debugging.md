---
title: JIT Optymalizacja i debugowanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7346b6fd8fbd483021437638f9e134ead88a0b93
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699148"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
**Optymalizacje działania na platformie .NET:** Jeśli chcesz debugować kod, łatwiej gdy kod jest **nie** zoptymalizowane pod kątem. To dlatego, gdy kod jest zoptymalizowany, kompilatora i środowiska uruchomieniowego dokonać zmian emitowany kod procesora CPU, aby działa szybciej, ale jest mniej bezpośrednie mapowanie do oryginalnego kodu źródłowego. Oznacza to, że debugery są często nie może poinformować Cię, wartości lokalnych zmiennych i kodu, przechodzenie krok po kroku, a punkty przerwania mogą nie działać zgodnie z oczekiwaniami.

Zwykle Konfiguracja kompilacji wydania tworzy zoptymalizowany kod i nie obsługuje konfiguracji kompilacji debugowania. `Optimize` Właściwość MSBuild Określa, czy kompilator jest poinformował do optymalizacji kodu.

Należący do ekosystemu .NET kodu jest włączone ze źródła do instrukcji procesora CPU w dwuetapowy proces: po pierwsze, C# kompilator konwertuje można wpisać tekst w celu pośrednich formy binarnej o nazwie MSIL i zapisuje ten pliki .dll. Później środowisko uruchomieniowe platformy .NET konwertuje ten MSIL instrukcje procesora CPU. Oba kroki można zoptymalizować w pewnym stopniu, ale drugi etap wykonywane przez środowisko uruchomieniowe platformy .NET wykonuje bardziej znaczące optymalizacje.

**Opcja "Pomijaj optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)".** Debuger ujawnia kontrolować, co się dzieje podczas ładowania biblioteki DLL, który został skompilowany z włączonymi optymalizacjami, wewnątrz procesu docelowego. Jeśli ta opcja nie jest zaznaczone (domyślny stan), a następnie, gdy środowisko uruchomieniowe platformy .NET kompiluje kod MSIL kod procesora CPU, instalacja pozostawia włączonymi optymalizacjami. Jeśli opcja zostanie zaznaczona, debuger żądań wyłączone optymalizacje.

Aby znaleźć **Pomijaj optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)** wybierz **narzędzia** > **opcje**, a następnie wybierz pozycję  **Ogólne** strony w obszarze **debugowanie** węzła.

**Gdy ta opcja powinien sprawdzić:** Zaznacz tę opcję, gdy został pobrany z innego źródła, takich jak pakiet nuget, biblioteki dll i chcesz debugować kod w tej biblioteki DLL. Aby to zrobić można również znaleźć pliku symboli (.pdb) dla tej biblioteki DLL.

Jeśli interesuje Cię tylko podczas debugowania kodu, które tworzysz, lokalnie, najlepiej zaznaczaj tej opcji, ponieważ w niektórych przypadkach włączenie tej opcji będzie znacznie spowolnić debugowania. Istnieją dwa przyczyna to spowolnić:

* Zoptymalizowany kod działa szybciej. Jeśli są wyłączenie optymalizacji dla części kodu, jego wpływ na wydajność możliwe jest dodanie.
* Jeśli masz włączoną opcję tylko mój kod, debuger nawet spróbuj i załadować symbole dla bibliotek DLL, które są zoptymalizowane. Znajdowanie symboli może potrwać dłuższy czas.

**Ograniczenia tej opcji:** Istnieją dwie sytuacje, gdy ta opcja spowoduje **nie** pracy:

1. W sytuacjach, w którym są dołączanie debugera do już uruchomionego procesu ta opcja nie wpłyną na moduły, które zostały już załadowane w czasie, który debuger został dołączony.
2. Ta opcja nie ma wpływu na bibliotek DLL, które zostały wstępnie skompilowane (nazywane również przetworzone przez program ngen) do kodu natywnego. Jednak użycie wstępnie skompilowany kod można wyłączyć przez uruchomienie procesu ze środowiskiem, zmiennej COMPlus_ZapDisable ustawiony na "1".

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proces zarządzanego wykonania](/dotnet/standard/managed-execution-process)
