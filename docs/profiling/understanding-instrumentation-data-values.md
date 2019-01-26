---
title: Zapoznanie z wartościami danych Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8131f7fecfcb28ad15fa4987767be4fa9955d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029729"
---
# <a name="understand-instrumentation-data-values"></a>Zrozumienie wartościami danych Instrumentacji

*Instrumentacji* profilowanie metody rekordy programu Visual Studio szczegółowe informacje o czasie wywołania funkcji, wierszy i zgodnie z instrukcjami w profilowanej aplikacji

Metoda Instrumentacja wprowadza kod na początku i końca funkcji docelowego profilowanych plików binarnych, a przed i po każdym wywołaniu przez te funkcje do innych funkcji. Wprowadzony kod rejestruje następujące informacje:

- Interwał między to zdarzenie kolekcji, a poprzednią.

- Czy system operacyjny wykonał operację w interwale. Na przykład system operacyjny może odczytu lub zapisu na dysku lub przełącznika między wątek docelowy i inny wątek w innym procesie.

Dla każdego interwału analizy profiler rekonstruuje stos wywołań, który nie ma pod koniec interwału. Stos wywołań znajduje się lista funkcji, które są aktywne w wyjątkach procesora w punkcie w czasie. Wykonuje kod; w tylko jednej funkcji — (bieżącej funkcji) inne funkcje są łańcuch wywołań funkcji, które wpłynęły na wywołanie funkcji bieżącej (stosu wywołań).

Dla każdej funkcji na stosie wywołań zameldowania interwał analizy profiler dodaje interwał do co najmniej jednej wartości czterech danych dla tej funkcji. Analiza dodaje interwał do wartości danych dla funkcji na podstawie dwóch kryteriów:

- Czy wystąpił interwału w kodzie, funkcji lub w *funkcji podrzędnych* (funkcja została wywołana przy użyciu funkcji).

- Czy wystąpiło zdarzenie systemu operacyjnego w interwale.

Wartości danych dla interwału zakresu funkcję lub dane są nazywane *upłynęło włącznie*, *upłynęło wyłączne*, *aplikacji włącznie*, i  *Aplikacja wyłącznie*:

- Wszystkich interwałów w funkcji są dodawane do wartości danych upłynęło włącznie.

- W przypadku interwału w kodzie funkcji i nie znajduje się w funkcji podrzędnych, interwał jest dodawany do wartość danych, który upłynął wyłączne funkcji.

- Jeśli zdarzenia systemu operacyjnego nie wystąpił w danym okresie, interwał jest dodawany do wartości danych aplikacji (włącznie).

- Jeśli zdarzenia systemu operacyjnego nie były wykonywane w zakresie, a interwał podczas bezpośrednie wykonywanie kodu funkcji (czyli go nie wystąpił w funkcji podrzędnych), interwał zostanie dodany do aplikacji wyłączne wartości danych.

Narzędzia profilowania raporty agregują sumę wartości funkcji w sesji profilowania i procesy, wątki i pliki binarne sesji.

## <a name="elapsed-inclusive-values"></a>Upłynęło włącznie wartości

Całkowity czas, który był poświęcony na wykonywanie funkcji i jej funkcji podrzędnych.

Upłynęło włącznie wartości obejmują interwałów, które spędzono bezpośrednie wykonywanie kodu funkcji i interwały spędzono w wykonywaniu funkcji podrzędnych funkcji docelowej. Interwały funkcji i jej funkcji podrzędnych, obejmujących oczekiwania dla systemu operacyjnego znajdują się również w wartości upłynęło włącznie.

## <a name="elapsed-exclusive-values"></a>Czas wyłączny wartości

Czas, jaki był poświęcony na wykonanie funkcji, z wyłączeniem czas spędzony w funkcjach podrzędnych.

Czas wyłączny wartości obejmują interwałów, które spędzono bezpośrednio wykonywania kodu funkcji, niezależnie od tego, czy wystąpiło zdarzenie systemu operacyjnego w interwale. Wszystkich interwałów w funkcji podrzędnych, które zostały wywołane przez funkcję docelowej nie są uwzględnione w wartości, który upłynął wyłączności.

## <a name="application-inclusive-values"></a>Wartości Włączne aplikacji

Czas, jaki był poświęcony na wykonywanie funkcji i jej funkcji podrzędnych, z wyłączeniem czas spędzony w zdarzeniach systemu operacyjnego.

Wartości Włączne aplikacji nie są uwzględniane interwałów, które zawiera zdarzenia systemu operacyjnego. Wartości Włączne aplikacji obejmują wszystkich interwałów, które zostały poświęcony na wykonanie funkcji, niezależnie od tego, czy interwał był poświęcony na bezpośrednie wykonywanie kodu funkcji lub był poświęcony w funkcjach podrzędnych funkcji docelowej.

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji

Czas, jaki był poświęcony na wykonanie funkcji, z wyłączeniem czasu spędzony w funkcjach podrzędnych i czas spędzony w zdarzeniach systemu operacyjnego.

Wartości wyłączne aplikacji nie dołączaj interwałów, które zawiera zdarzenia systemu operacyjnego lub interwałów, które zostały spędzony na wykonywaniu funkcji, które zostały wywołane przez funkcję. Wartości wyłączne aplikacji obejmują tylko tych odstępach czasu, spędzono bezpośrednio wykonywania kodu funkcji i nie zawiera zdarzenia systemu operacyjnego.

## <a name="elapsed-inclusive-percent"></a>Upłynęło włącznie procent

Procent całkowitej upłynęło włącznie wartości sesji profilowania, które były upłynęło włącznie wartości funkcji modułu, wątek lub procesu.

100 * funkcja upłynęło włącznie / sesji, który upłynął (włącznie)

## <a name="elapsed-exclusive-percent"></a>Czas wyłączny procent

Procent całkowitej upłynęło włącznie wartości sesji profilowania, które były upłynęło wyłączne wartości funkcji modułu, wątek lub procesu.

100 * funkcja upłynęło wyłącznie / sesji, który upłynął (włącznie)

## <a name="application-inclusive-percent"></a>Całkowity procent aplikacji

Procent aplikacji w ramach całościowych wartości sum sesji profilowania, które były aplikacji włącznie wartości funkcji modułu, wątek lub procesu.

100 * działać aplikacja włącznie / sesji aplikacji (włącznie)

## <a name="application-exclusive-percent"></a>% Wyłącznych aplikacji

Procent aplikacji w ramach całościowych wartości sum sesji profilowania, które były aplikacji wyłączne interwałów funkcji modułu, wątek lub procesu.

100 * działać aplikacja wyłącznie / sesji aplikacji (włącznie)

## <a name="see-also"></a>Zobacz także

[Analizowanie danych dotyczących narzędzi do oceny wydajności](../profiling/analyzing-performance-tools-data.md)  
[Instrukcje: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)