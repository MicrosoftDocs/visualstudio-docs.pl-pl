---
title: Informacje o wartościach danych Instrumentacji | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3dace7b13816c63664ccb4dabfed52d1c5fb7523
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778079"
---
# <a name="understand-instrumentation-data-values"></a>Opis wartości danych Instrumentacji

Metoda profilowania *Instrumentacji* programu Visual Studio rejestruje szczegółowe informacje o chronometrażu dla wywołań funkcji, wierszy i instrukcji w profilowanej aplikacji

Metoda Instrumentacji wprowadza kod na początku i na końcu funkcji docelowych w profilowanym pliku binarnym oraz przed i po każdym wywołaniu przez te funkcje do innych funkcji. Wprowadzony kod rejestruje następujące informacje:

- Interwał między tym zdarzeniem kolekcji a poprzednim.

- Czy system operacyjny wykonał operację w trakcie interwału. Na przykład system operacyjny może odczytywać lub zapisywać dane na dysku lub przełączać się między wątkiem docelowym a innym wątkiem w innym procesie.

Dla każdego interwału analiza profilera odbudowy stosu wywołań, który był obecny na końcu interwału. Stos wywołań jest listą funkcji, które są aktywne w procesorze w danym momencie. Tylko jedna funkcja (bieżąca funkcja) wykonuje kod; inne funkcje to łańcuch wywołań funkcji, które spowodowały wywołanie bieżącej funkcji (stos wywołań).

Dla każdej funkcji na stosie wywołań podczas rejestrowania interwału analiza profilera dodaje interwał do co najmniej jednej z czterech wartości danych dla tej funkcji. Analiza dodaje interwał do wartości danych dla funkcji na podstawie dwóch kryteriów:

- Określa, czy interwał wystąpił w kodzie funkcji, czy w *funkcji podrzędnej* (funkcja, która została wywołana przez funkcję).

- Czy w interwale wystąpi zdarzenie systemu operacyjnego.

Wartości danych dla interwału funkcji lub zakresu danych są nazywane *włącznie* *, bez*wykluczeń, *aplikacji włącznie*i *aplikacji na wyłączność*:

- Wszystkie interwały funkcji są dodawane do wartości danych włącznie.

- Jeśli interwał wystąpi w kodzie funkcji, a nie w funkcji podrzędnej, interwał jest dodawany do wartości danych wyłącznego, który upłynął.

- Jeśli w interwale nie wystąpi zdarzenie systemu operacyjnego, interwał jest dodawany do wartości danych w ramach aplikacji.

- Jeśli zdarzenie systemu operacyjnego nie wystąpi w interwale, a interwał wystąpił w bezpośrednim wykonaniu kodu funkcji (to oznacza, że nie wystąpił w funkcji podrzędnej), interwał jest dodawany do wartości danych wyłącznego aplikacji.

Raporty narzędzia profilowania agregują łączne wartości funkcji w samej sesji profilowania oraz procesów, wątków i plików binarnych sesji.

## <a name="elapsed-inclusive-values"></a>Wartości włączne, które upłynęły

Łączny czas spędzony na wykonywaniu funkcji i jej funkcji podrzędnych.

Wartości włączne (włącznie) obejmują przedziały, które były poświęcone bezpośrednio na wykonywanie kodu funkcji i przedziały czasu, w których wystąpiły wykonywanie funkcji podrzędnych funkcji docelowej. Interwały funkcji lub jej funkcji podrzędnych, które obejmują oczekiwanie na system operacyjny, również są uwzględniane w wartościach, które upłynęły.

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęły

Czas spędzony na wykonywaniu funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych.

Wykluczone wartości obejmują przedziały, które były poświęcone bezpośrednio na wykonywanie kodu funkcji, niezależnie od tego, czy w interwale wystąpi zdarzenie systemu operacyjnego. Wszystkie interwały w funkcjach podrzędnych, które zostały wywołane przez funkcję docelową, nie są uwzględniane w wartościach, których nie upłynął.

## <a name="application-inclusive-values"></a>Wartości włączne aplikacji

Czas spędzony na wykonywaniu funkcji i jej funkcji podrzędnych, z wyłączeniem czasu spędzonego na zdarzeniach systemu operacyjnego.

Wartości włącznie z aplikacją nie obejmują interwałów, które zawierają zdarzenia systemu operacyjnego. Wartości włącznie obejmują wszystkie inne interwały, w których wykorzystano funkcję, bez względu na to, czy przedziały bezpośrednio wykonywały kod funkcji, czy zostały wykorzystane w funkcjach podrzędnych funkcji docelowej.

## <a name="application-exclusive-values"></a>Wartości wyłączne aplikacji

Czas spędzony na wykonywaniu funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych oraz czasu spędzonego w zdarzeniach systemu operacyjnego.

Wartości wyłączne aplikacji nie obejmują interwałów, które zawierają zdarzenia lub interwały systemu operacyjnego, które były używane do wykonywania funkcji, które zostały wywołane przez funkcję. Wartości wyłączne aplikacji obejmują tylko te interwały, które były poświęcone bezpośrednio na wykonywanie kodu funkcji i nie zawierają zdarzenia systemu operacyjnego.

## <a name="elapsed-inclusive-percent"></a>Procent łączny, który upłynął

Wartość procentowa łącznej liczby włączonych wartości w sesji profilowania, które upłynęły łącznie do wartości funkcji, modułu, wątku lub procesu.

100 * funkcja, która upłynęła włącznie/sesja

## <a name="elapsed-exclusive-percent"></a>Procent wyłącznych

Wartość procentowa łącznej liczby włączonych wartości w sesji profilowania, które upłynęły od wyłącznej wartości funkcji, modułu, wątku lub procesu.

100 * funkcja, która upłynęła z wyłączeniem/sesją

## <a name="application-inclusive-percent"></a>Wartość procentowa włącznie

Wartość procentowa łącznej liczby wartości obejmujących sesję profilowania, w których były zawarte w aplikacji wartości, moduł, wątek lub proces.

100 * aplikacja funkcji włącznie/aplikacja do sesji włącznie

## <a name="application-exclusive-percent"></a>Procent wyłączny aplikacji

Wartość procentowa łącznej liczby wartości obejmujących sesję profilowania, które były wyłącznymi interwałami aplikacji, modułu, wątku lub procesu.

100 * aplikacja funkcji na wyłączność/sesja, włącznie

## <a name="see-also"></a>Zobacz także

[Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)
[: wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)
