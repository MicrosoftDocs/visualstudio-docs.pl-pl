---
title: Debuguj zoptymalizowany kod | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: da0a9c40a2c4887b2798e908ad0c12d6c9a85b32
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852390"
---
# <a name="how-to-debug-optimized-code"></a>Porady: debugowanie zoptymalizowanego kodu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

> [!NOTE]
> Opcja kompilatora [/zo (rozszerzanie zoptymalizowanego debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging)(wprowadzona w Visual Studio Update 3) generuje bogatsze informacje debugowania dla zoptymalizowanego kodu (projekty, które nie zostały skompilowane przy użyciu opcji kompilatora **/od** ). Zobacz [/O opcje (Optymalizuj kod)](/cpp/build/reference/o-options-optimize-code)). Obejmuje to ulepszoną obsługę debugowania zmiennych lokalnych i funkcji w wierszu.
>
> Polecenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md) jest wyłączone, gdy jest używana opcja **/zo** ocompiler.

 Gdy kompilator optymalizuje kod, zmienia położenie i Reorganizuje instrukcje. Powoduje to bardziej wydajne skompilowane kod. Ze względu na to ponowne rozmieszczenie debuger nie zawsze identyfikuje kod źródłowy, który odpowiada zestawowi instrukcji.

 Optymalizacja może mieć wpływ na:

- Zmienne lokalne, które mogą zostać usunięte przez optymalizator lub przeniesione do lokalizacji debuger nie rozpoznaje.

- Położenie wewnątrz funkcji, które są zmieniane, gdy optymalizator Scala bloki kodu.

- Nazwy funkcji dla ramek na stosie wywołań, które mogą być nieprawidłowe, jeśli optymalizator Scala dwie funkcje.

  Ramki widoczne na stosie wywołań są prawie zawsze poprawiane, jednak przy założeniu, że masz symbole dla wszystkich ramek. Ramki na stosie wywołań będą niewłaściwe w przypadku uszkodzenia stosu, jeśli masz funkcje w języku zestawu lub jeśli istnieją ramki systemu operacyjnego bez pasujących symboli w stosie wywołań.

  Zmienne globalne i statyczne są zawsze wyświetlane poprawnie. Tak więc jest układ struktury. Jeśli masz wskaźnik do struktury i wartość wskaźnika jest poprawna, Każda zmienna elementu członkowskiego struktury będzie zawierać poprawną wartość.

  Ze względu na te ograniczenia należy debugować przy użyciu niezoptymalizowanej wersji programu, jeśli jest to możliwe. Domyślnie optymalizacja jest wyłączona w konfiguracji debugowania programu C++ i włączona w konfiguracji wydania.

  Usterka może jednak wystąpić tylko w zoptymalizowanej wersji programu. W takim przypadku należy debugować zoptymalizowany kod.

## <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Aby włączyć optymalizację w konfiguracji kompilacji debugowania

1. Podczas tworzenia nowego projektu, wybierz `Win32 Debug` element docelowy. Użyj `Win32``Debug` elementu docelowego do momentu, gdy program jest w pełni debugowany i wszystko jest gotowe do skompilowania `Win32 Release` celu. Kompilator nie optymalizuje `Win32 Debug` elementu docelowego.

2. Wybierz projekt w Eksplorator rozwiązań.

3. W menu **Widok** kliknij polecenie **strony właściwości**.

4. Na **stronie właściwości** okno dialogowe, upewnij się, że `Debug` jest zaznaczone na liście rozwijanej **Konfiguracja** .

5. W widoku folderu po lewej stronie Wybierz folder **C/C++** .

6. W folderze **C++** wybierz opcję `Optimization` .

7. Na liście właściwości po prawej stronie Znajdź `Optimization` . Obok tego ustawienia prawdopodobnie widnieje `Disabled (` [/od](/cpp/build/reference/od-disable-debug) `)` . Wybierz jedną z innych opcji ( `Minimum Size``(` [/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed) `)` , `Full Optimization``(` [/OX](/cpp/build/reference/ox-full-optimization) `)` lub `Custom` ).

8. W przypadku wybrania `Custom` opcji dla `Optimization` , można teraz ustawić opcje dla każdej z pozostałych właściwości wyświetlanych na liście właściwości.

9. Wybierz właściwości konfiguracji, C/C++, węzeł wiersza polecenia na stronie właściwości projektu i Dodaj `(` [/zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` do pola tekstowego **Opcje dodatkowe** .

    > [!WARNING]
    > `/Zo` wymaga Visual Studio 2013 Update 3 lub nowszą wersję.
    >
    >  Dodanie `/Zo` spowoduje wyłączenie [Edytuj i Kontynuuj](../debugger/edit-and-continue-visual-csharp.md).

   Podczas debugowania zoptymalizowanego kodu Użyj okna **demontażu** , aby zobaczyć, jakie instrukcje są w rzeczywistości tworzone i wykonywane. Po ustawieniu punktów przerwania należy się dowiedzieć, że punkt przerwania może zostać przesunięty razem z instrukcją. Rozważmy na przykład następujący kod:

```cpp
for (x=0; x<10; x++)
```

 Załóżmy, że ustawisz punkt przerwania w tym wierszu. Może oczekiwać, że punkt przerwania zostanie osiągnięty 10 razy, ale jeśli kod jest zoptymalizowany, punkt przerwania zostanie trafiony tylko raz. Oznacza to, że pierwsza instrukcja ustawia wartość `x` na 0. Kompilator rozpoznaje, że tylko raz i przenosi go z pętli. Punkt przerwania jest przenoszony razem z nim. Instrukcje, które porównują i zwiększają, `x` pozostają wewnątrz pętli. Po wyświetleniu okna **demontażu** [Jednostka kroku](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) jest automatycznie ustawiana na instrukcje w celu uzyskania większej kontroli, co jest przydatne w przypadku przechodzenia przez zoptymalizowany kod.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)