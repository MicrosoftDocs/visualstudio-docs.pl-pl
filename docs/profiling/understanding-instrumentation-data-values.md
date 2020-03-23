---
title: Opis wartości danych oprzyrządowania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778079"
---
# <a name="understand-instrumentation-data-values"></a>Opis wartości danych oprzyrządowania

Metoda profilowania *instrumentacji* programu Visual Studio rejestruje szczegółowe informacje o chronometrażu dla wywołań funkcji, wierszy i instrukcji w profilizowanej aplikacji

Metoda instrumentacji wstrzykuje kod na początku i na końcu funkcji docelowych w profilowane binarne i przed i po każdym wywołaniu przez te funkcje do innych funkcji. Wstrzyknięty kod rejestruje następujące informacje:

- Interwał między tym zdarzeniem kolekcji a poprzednim.

- Czy system operacyjny wykonał operację w tym przedziale czasu. Na przykład system operacyjny może odczytywać lub zapisywać na dysku lub przełączać się między wątkiem docelowym a innym wątkiem w innym procesie.

Dla każdego interwału analizy profilera rekonstrukcji stosu wywołań, który był obecny na końcu interwału. Stos wywołań to lista funkcji, które są aktywne na procesorze w momencie w czasie. Tylko jedna funkcja (bieżąca funkcja) wykonuje kod; inne funkcje są łańcuch wywołań funkcji, które spowodowało wywołanie bieżącej funkcji (stos wywołań).

Dla każdej funkcji na stosie wywołań podczas rejestrowania interwału analiza profilera dodaje interwał do jednej lub więcej z czterech wartości danych dla funkcji. Analiza dodaje interwał do wartości danych dla funkcji na podstawie dwóch kryteriów:

- Czy interwał wystąpił w kodzie funkcji lub w *funkcji podrzędnej* (funkcja, która została wywołana przez funkcję).

- Czy zdarzenie systemu operacyjnego wystąpiło w interwale.

Wartości danych dla interwału funkcji lub zakresu danych są nazywane Są o nazwie *Elapsed Inclusive*, *Upapsed Exclusive*, *Application Inclusive*i *Application Exclusive:*

- Wszystkie interwały funkcji są dodawane do wartości danych, które upłynęło włącznie.

- Jeśli interwał wystąpił w kodzie funkcji, a nie w funkcji podrzędnej, interwał jest dodawany do wartości danych danych, które upłynęło na wyłączność funkcji.

- Jeśli zdarzenie systemu operacyjnego nie wystąpiło w interwale, interwał jest dodawany do wartości danych włącznie z aplikacją.

- Jeśli zdarzenie systemu operacyjnego nie wystąpiło w interwale, a interwał wystąpił w bezpośrednim wykonaniu kodu funkcji (oznacza to, że nie wystąpił w funkcji podrzędnej), interwał jest dodawany do wartości danych wyłączności aplikacji.

Raporty narzędzi profilowania agregują całkowite wartości funkcji w samej sesji profilowania oraz procesy, wątki i pliki binarne sesji.

## <a name="elapsed-inclusive-values"></a>Wartości włącznie, które upłynęło

Całkowity czas spędzony na wykonywaniu funkcji i jej funkcji podrzędnych.

Wartości, które upłynęło włącznie obejmują interwały, które zostały wydane bezpośrednio na wykonanie kodu funkcji i interwały, które zostały wydane na wykonywanie funkcji podrzędnych funkcji docelowej. Interwały funkcji lub jej funkcji podrzędnych, które obejmują oczekiwanie na system operacyjny są również zawarte w wartości włącznie, które upłynęło.

## <a name="elapsed-exclusive-values"></a>Wartości wyłączne, które upłynęło

Czas spędzony na wykonywaniu funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych.

Wartości, które upłynęło na wyłączność obejmują interwały, które zostały wydane bezpośrednio na wykonanie kodu funkcji, niezależnie od tego, czy wystąpiło zdarzenie systemu operacyjnego w interwale. Wszystkie interwały spędzone w funkcjach podrzędnych, które zostały wywołane przez funkcję docelową, nie są uwzględniane w wartościach wyłącznych, które upłynęło.

## <a name="application-inclusive-values"></a>Wartości włącznie aplikacji

Czas spędzony na wykonywaniu funkcji i jej funkcji podrzędnych, z wyłączeniem czasu spędzonego na zdarzeniach systemu operacyjnego.

Wartości włącznie aplikacji nie obejmują interwałów, które zawierają zdarzenia systemu operacyjnego. Wartości włącznie aplikacji obejmują wszystkie inne interwały, które zostały wydane na wykonywanie funkcji, niezależnie od tego, czy interwał został wydany bezpośrednio na wykonanie kodu funkcji, czy został wydany w funkcjach podrzędnych funkcji docelowej.

## <a name="application-exclusive-values"></a>Wyłączne wartości aplikacji

Czas spędzony na wykonywaniu funkcji, z wyłączeniem czasu spędzonego w funkcjach podrzędnych i czasu spędzonego na zdarzeniach systemu operacyjnego.

Wyłączne wartości aplikacji nie obejmują interwałów, które zawierają zdarzenia systemu operacyjnego lub interwały, które zostały wydane na wykonywanie funkcji, które były wywoływane przez funkcję. Wyłączne wartości aplikacji obejmują tylko te interwały, które zostały wydane bezpośrednio na wykonanie kodu funkcji i które nie zawierały zdarzenia systemu operacyjnego.

## <a name="elapsed-inclusive-percent"></a>Upłynął włącznie procent

Procent całkowitych wartości włącznie, które upłynął włącznie, które zostały określone wartości włącznie funkcji, modułu, wątku lub procesu.

100 * Funkcja, która upłynęło włącznie / Sesja, która upłynęło włącznie

## <a name="elapsed-exclusive-percent"></a>Upłynął wyłączny procent

Procent całkowitych wartości włącznie, które upłynął przez sesję profilowania, które zostały określone wyłączne wartości funkcji, modułu, wątku lub procesu.

100 * Funkcja, która upłynęło exclusive / sesja, która upłynęło włącznie

## <a name="application-inclusive-percent"></a>Procent włącznie z aplikacją

Procent całkowitych wartości włącznie aplikacji sesji profilowania, które były application inclusive wartości funkcji, modułu, wątku lub procesu.

100 * Aplikacja funkcyjna Włącznie / Aplikacja sesyjna Włącznie

## <a name="application-exclusive-percent"></a>Ekskluzywny procent aplikacji

Procent całkowitych wartości włącznie aplikacji sesji profilowania, które były interwały wyłączności aplikacji funkcji, modułu, wątku lub procesu.

100 * Aplikacja funkcyjna Wyłączna / Aplikacja sesyjna Włącznie

## <a name="see-also"></a>Zobacz też

[Analizowanie danych](../profiling/analyzing-performance-tools-data.md)
narzędzi wydajności[Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md)
