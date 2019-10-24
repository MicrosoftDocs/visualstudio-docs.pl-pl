---
title: Optymalizacja i debugowanie JIT | Microsoft Docs
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
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731619"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
**Jak działa Optymalizacja w programie .NET:** Jeśli próbujesz debugować kod, łatwiej jest, gdy ten kod **nie** jest zoptymalizowany. Jest to spowodowane tym, że gdy kod jest zoptymalizowany, kompilator i środowisko uruchomieniowe wprowadzają zmiany w wyemitowanym kodzie procesora, dzięki czemu będzie działać szybciej, ale ma mniej bezpośrednie mapowanie na oryginalny kod źródłowy. Oznacza to, że debugery często nie są w stanie stwierdzić wartości zmiennych lokalnych, a taktowanie kodu i punkty przerwania mogą nie zadziałały zgodnie z oczekiwaniami.

Zwykle konfiguracja kompilacji wydania tworzy zoptymalizowany kod, a konfiguracja kompilacji debugowania nie. Właściwość programu MSBuild `Optimize` określa, czy kompilator ma być powiadamiany o optymalizacji kodu.

W ekosystemie .NET kod jest przełączany ze źródła do instrukcji procesora CPU w procesie dwuetapowym: najpierw C# kompilator konwertuje wpisany tekst na pośredni formularz binarny o nazwie MSIL i zapisuje je w plikach dll. Później środowisko uruchomieniowe platformy .NET konwertuje te MSIL na instrukcje procesora CPU. Obie kroki można zoptymalizować do pewnego stopnia, ale drugi krok wykonywany przez środowisko uruchomieniowe platformy .NET wykonuje bardziej znaczące optymalizacje.

**Opcja "Pomiń optymalizację JIT podczas ładowania modułu (tylko zarządzany)":** Debuger uwidacznia opcję, która ma wpływ na to, co się dzieje, gdy biblioteka DLL, która jest kompilowana z włączonymi optymalizacjami, jest ładowana w procesie docelowym. Jeśli ta opcja nie jest zaznaczona (stan domyślny), gdy środowisko uruchomieniowe platformy .NET kompiluje kod MSIL w kodzie procesora, pozostawia optymalizacje włączone. Jeśli opcja jest zaznaczona, debuger żąda wyłączenia optymalizacji.

Aby znaleźć opcję **Pomiń optymalizację JIT podczas ładowania modułu (tylko zarządzany)** , wybierz pozycję **Narzędzia**  > **Opcje**, a następnie wybierz stronę **Ogólne** w węźle **debugowanie** .

**Kiedy należy zaznaczyć tę opcję:** Zaznacz tę opcję, jeśli pobrane biblioteki DLL pochodzą z innego źródła, takiego jak pakiet NuGet, i chcesz debugować kod w tej bibliotece DLL. Aby ta wartość działała, należy również znaleźć plik symboli (. pdb) dla tej biblioteki DLL.

Jeśli interesuje Cię tylko Debugowanie kodu, który tworzysz lokalnie, najlepszym rozwiązaniem jest pozostawienie tej opcji niezaznaczone, ponieważ w niektórych przypadkach włączenie tej opcji spowoduje znaczne spowolnienie debugowania. Istnieją dwie przyczyny tego spowolnienia:

* Zoptymalizowany kod działa szybciej. Jeśli wyłączysz optymalizacje dla wielu kodów, wpływ na wydajność może zostać dodany.
* Jeśli włączono Tylko mój kod, debuger nie będzie musiał jeszcze próbować i ładować symboli dla bibliotek DLL, które są zoptymalizowane. Znajdowanie symboli może zająć dużo czasu.

**Ograniczenia tej opcji:** Istnieją dwie sytuacje, w których ta opcja **nie** będzie działała:

1. W sytuacjach, gdy dołączysz debuger do już uruchomionego procesu, ta opcja nie będzie miała wpływu na moduły, które zostały już załadowane w momencie dołączenia debugera.
2. Ta opcja nie ma wpływu na biblioteki DLL, które zostały wstępnie skompilowane (a. k. a ngen'ed) do kodu natywnego. Można jednak wyłączyć użycie wstępnie skompilowanego kodu przez uruchomienie procesu ze zmienną środowiskową "COMPlus_ZapDisable" ustawioną na wartość "1".

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proces zarządzanego wykonania](/dotnet/standard/managed-execution-process)
