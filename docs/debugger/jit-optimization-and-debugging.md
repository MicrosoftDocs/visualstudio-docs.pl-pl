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
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916220"
---
# <a name="jit-optimization-and-debugging"></a>Optymalizacja i debugowanie JIT
Jeśli próbujesz debugować kod, łatwiej jest, gdy ten kod **nie** jest zoptymalizowany. Gdy kod jest zoptymalizowany, kompilator i środowisko uruchomieniowe wprowadzają zmiany w emitowanym kodzie procesora CPU, dzięki czemu będzie działać szybciej, ale ma mniej bezpośrednie mapowanie na oryginalny kod źródłowy. Jeśli mapowanie jest mniej bezpośrednie, debugery często nie mogą określić wartości zmiennych lokalnych, a taktowanie kodu i punkty przerwania mogą nie zadziałać zgodnie z oczekiwaniami.

> [!NOTE]
> Aby uzyskać więcej informacji na temat debugowania JIT (just in Time), zapoznaj się z [tą dokumentacją](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Jak działa Optymalizacja w środowisku .NET 
Zwykle konfiguracja kompilacji wydania tworzy zoptymalizowany kod, a konfiguracja kompilacji debugowania nie. Właściwość programu MSBuild `Optimize` określa, czy kompilator ma być powiadamiany o optymalizacji kodu.

W ekosystemie .NET kod jest przełączany ze źródła do instrukcji procesora w procesie dwuetapowym: najpierw C# kompilator konwertuje wpisany tekst na pośredni formularz binarny o nazwie MSIL i zapisuje pliki MSIL do. dll. Później środowisko uruchomieniowe platformy .NET konwertuje te MSIL na instrukcje procesora CPU. Obie kroki można zoptymalizować do pewnego stopnia, ale drugi krok wykonywany przez środowisko uruchomieniowe platformy .NET wykonuje bardziej znaczące optymalizacje.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>Opcja "Pomiń optymalizację JIT podczas ładowania modułu (tylko zarządzany)"
Debuger uwidacznia opcję, która ma wpływ na to, co się dzieje, gdy biblioteka DLL, która jest kompilowana z włączonymi optymalizacjami, jest ładowana w procesie docelowym. Jeśli ta opcja nie jest zaznaczona (stan domyślny), gdy środowisko uruchomieniowe platformy .NET kompiluje kod MSIL w kodzie procesora, pozostawia optymalizacje włączone. Jeśli opcja jest zaznaczona, debuger żąda wyłączenia optymalizacji.

Aby znaleźć opcję **Pomiń optymalizację JIT podczas ładowania modułu (tylko zarządzany)** , wybierz pozycję **Narzędzia** > **Opcje**, a następnie wybierz stronę **Ogólne** w węźle **debugowanie** .

![Pomiń optymalizację JIT](../debugger/media/suppress-jit-tool-options.png "Pomiń optymalizację JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Kiedy należy zaznaczyć opcję "Pomiń optymalizację JIT"?
Zaznacz tę opcję, jeśli pobrane biblioteki DLL pochodzą z innego źródła, takiego jak pakiet NuGet, i chcesz debugować kod w tej bibliotece DLL. Aby pominięcie działało, należy również znaleźć plik symbolu (. pdb) dla tej biblioteki DLL.

Jeśli interesuje Cię tylko Debugowanie kodu, który tworzysz lokalnie, najlepszym rozwiązaniem jest pozostawienie tej opcji niezaznaczone, ponieważ w niektórych przypadkach włączenie tej opcji spowoduje znaczne spowolnienie debugowania. Istnieją dwie przyczyny tego spowolnienia:

* Zoptymalizowany kod działa szybciej. Jeśli wyłączysz optymalizacje dla wielu kodów, wpływ na wydajność może zostać dodany.
* Jeśli włączono Tylko mój kod, debuger nie będzie jeszcze próbować ładować symboli dla bibliotek DLL, które są zoptymalizowane. Znajdowanie symboli może zająć dużo czasu.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Ograniczenia opcji pomijania optymalizacji JIT 
Istnieją dwie sytuacje, w których ta opcja **nie** będzie działała:

1. W sytuacjach, gdy dołączysz debuger do już uruchomionego procesu, ta opcja nie będzie miała wpływu na moduły, które zostały już załadowane w momencie dołączenia debugera.
2. Ta opcja nie ma wpływu na biblioteki DLL, które zostały wstępnie skompilowane (a. k. a ngen'ed) do kodu natywnego. Można jednak wyłączyć użycie wstępnie skompilowanego kodu, uruchamiając proces ze zmienną środowiskową **"COMPlus_ReadyToRun"** ustawioną na **wartość "0"** . Poinformuje środowisko uruchomieniowe platformy .NET Core, aby wyłączyć korzystanie z wstępnie skompilowanych obrazów, wymuszając środowisko uruchomieniowe do kompilowania kodu struktury. 

    > [!IMPORTANT]
    > Jeśli celem jest .NET Framework lub starsza wersja programu .NET Core (2. x lub niższa), należy również dodać zmienną środowiskową "COMPlus_ZapDisable" i ustawić ją na wartość "1".

    **Aby ustawić zmienną środowiskową dla projektu .NET Core w programie Visual Studio:**
    1. W **Eksplorator rozwiązań** **kliknij prawym przyciskiem myszy** plik projektu i wybierz polecenie **Właściwości**.
    2. Przejdź do karty **debugowanie** i w obszarze **zmienne środowiskowe**kliknij przycisk **Dodaj** .
    3. Ustaw nazwę (klucz) na **COMPlus_ReadyToRun** i ustaw wartość **0**.

    ![Ustaw zmienną środowiskową COMPlus_ReadyToRun](../debugger/media/environment-variables-debug-menu.png "Ustaw zmienną środowiskową COMPlus_ReadyToRun")

## <a name="see-also"></a>Zobacz także
- [Jak debugować Źródło struktury dotnet](../debugger/how-to-debug-dotnet-framework-source.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)
- [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Proces zarządzanego wykonania](/dotnet/standard/managed-execution-process)
