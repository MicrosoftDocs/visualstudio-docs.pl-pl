---
title: 'Instrukcje: Debugowanie zoptymalizowanego kodu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 756b8859c2f13c53eb46a0d9ae9d32836997f70f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035929"
---
# <a name="how-to-debug-optimized-code"></a>Instrukcje: Debugowanie zoptymalizowanego kodu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> [/Zo (Rozszerzanie zoptymalizowane pod kątem debugowanie)](/cpp/build/reference/zo-enhance-optimized-debugging)(zostanie wprowadzony w programie Visual Studio Update 3) — opcja kompilatora generuje bogatsze informacje debugowania dla zoptymalizowanego kodu (projekty, które nie są tworzone za pomocą **/Od** — Opcja kompilatora. Zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code)). W tym Ulepszona obsługa debugowania zmienne lokalne i funkcje śródwierszowe.
>
> [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md) jest wyłączona, gdy **/Zo** ocompiler opcja jest używana.

 Gdy kompilator optymalizuje kod, powoduje przeniesienie i Reorganizuje instrukcje. Skutkuje to bardziej wydajne skompilowanego kodu. Z powodu ta zmiana położenia debuger zawsze nie może zidentyfikować kod źródłowy, który odnosi się do zestawu instrukcji.

 Optymalizacja może mieć wpływ na:

- Zmienne lokalne, które mogą zostać usunięte przez optymalizator lub przeniesiony do lokalizacji, których nie rozumie debugera.

- Położenie wewnątrz funkcji, które są zmieniane, gdy Optymalizator scala bloków kodu.

- Nazwy funkcji ramek na stosie wywołań, która może być nieprawidłowy, jeśli Optymalizator scala dwie funkcje.

  Klatek, które widać w stosie wywołań są prawie zawsze poprawna, jednak przy założeniu, że symbole dla wszystkich ramek. Ramek na stosie wywołań będą nieprawidłowe, jeśli masz uszkodzenie stosu, jeśli masz functions napisanej w języku zestawu lub w przypadku ramek systemu operacyjnego bez pasującego symboli w stosie wywołań.

  Zmiennych globalnych i statycznych są zawsze wyświetlane prawidłowo. Więc układ struktury. Jeśli masz wskaźnik do struktury, a wartość wskaźnika jest poprawna, co zmiennej składowej struktury pokaże poprawnej wartości.

  Ze względu na ograniczenia te powinny debugowania, jeśli to możliwe przy użyciu niezoptymalizowanym wersji programu. Domyślnie Optymalizacja jest wyłączone w konfiguracji debugowania programu Visual C++ i włączone w konfiguracji wydania.

  Jednak błąd może pojawić się tylko w przypadku zoptymalizowanych wersję programu. W takim przypadku należy debugować zoptymalizowany kod.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Aby włączyć optymalizację podczas debugowania Konfiguracja kompilacji

1. Podczas tworzenia nowego projektu wybierz `Win32 Debug` docelowej. Użyj `Win32``Debug` docelowe, dopóki program pełni debugowania i można przystąpić do tworzenia `Win32 Release` docelowej. Kompilator nie optymalizuje `Win32 Debug` docelowej.

2. Wybierz projekt w Eksploratorze rozwiązań.

3. Na **widoku** menu, kliknij przycisk **stron właściwości**.

4. W **stron właściwości** okna dialogowego pole, upewnij się, `Debug` wybrano **konfiguracji** listy rozwijanej.

5. W widoku folderu po lewej stronie wybierz **C/C++** folderu.

6. W obszarze **C++** folderu, wybierz `Optimization`.

7. Na liście właściwości po prawej stronie Znajdź `Optimization`. Prawdopodobnie wynika z ustawieniem obok niego `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Wybierz jedną z opcji (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [ox](/cpp/build/reference/ox-full-optimization) `)`, lub `Custom`).

8. Jeśli została wybrana opcja `Custom` opcja dla `Optimization`, można teraz ustawić opcje dla każdego z pozostałych właściwości wyświetlane na liście właściwości.

9. Wybierz właściwości konfiguracji, C/C++, węzeł wiersza polecenia na stronie właściwości projektu i Dodaj `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` do **dodatkowe opcje** pola tekstowego.

    > [!WARNING]
    >  `/Zo` wymaga programu Visual Studio 2013 Update 3 lub nowszej wersji.
    >
    >  Dodawanie `/Zo` spowoduje wyłączenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md).

   Podczas debugowania zoptymalizowanego kodu, należy użyć **dezasemblacji** okna, aby zobaczyć, jakie instrukcje są faktycznie utworzone i są stosowane. Podczas ustawiania punktów przerwania, musisz wiedzieć, że punkt przerwania może przenieść wraz z instrukcji. Na przykład rozważmy następujący kod:

```cpp
for (x=0; x<10; x++)
```

 Załóżmy, że Ustaw punkt przerwania w tym wierszu. Można by oczekiwać punkt przerwania zostanie osiągnięty 10 razy, ale jeśli kod jest zoptymalizowany, punkt przerwania zostaje trafiony tylko jeden raz. Wynika to pierwsza instrukcja ustawia wartość `x` na 0. Kompilator rozpoznaje, że to tylko należy wykonać jeden raz i przenosi ją wyjścia z pętli. Przenosi punkt przerwania z nim. Instrukcje, które porównania i zwiększ `x` pozostają wewnątrz pętli. Po wyświetleniu **dezasemblacji** oknie [jednostka kroku](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) jest automatycznie ustawiana na instrukcji lepszą kontrolę, co jest przydatne, jeśli krok po kroku przez zoptymalizowany kod.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)