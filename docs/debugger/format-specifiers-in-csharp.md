---
title: Specyfikatory formatu w debugerze (C#) | Microsoft Docs
description: Użyj specyfikatora formatu, aby zmienić format, w którym wartość jest wyświetlana w okno wyrażeń kontrolnych. Ten artykuł zawiera szczegółowe informacje dotyczące użycia.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: abc824cf5d0413f01ad5f3f4423b974aeca40b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870587"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu w języku C# w debugerze programu Visual Studio
Można zmienić format, w którym wartość jest wyświetlana w oknie **czujki** przy użyciu specyfikatorów formatu. W oknie **bezpośrednim** można także używać specyfikatorów formatu, okna **poleceń** , w [punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)i w oknach źródłowych. W przypadku wstrzymania na wyrażeniu w tych oknach wynik będzie wyświetlany w  [etykietki danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) w określonym formacie.

Aby użyć specyfikatora formatu, wprowadź wyrażenie zmiennej, po którym następuje przecinek i odpowiedni specyfikator.

## <a name="set-format-specifiers"></a>Ustaw specyfikatory formatu
Użyjemy następującego przykładowego kodu:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Dodaj `my_var1` zmienną do okna **czujki** podczas debugowania, **Debuguj**  >    >  czujkę **czujki** w systemie Windows  >  **1**. Następnie kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Wyświetlanie w formacie szesnastkowym**. Teraz okno **czujki** pokazuje wartość 0x0065. Aby wyświetlić tę wartość jako liczbę całkowitą dziesiętną, a nie szesnastkową liczbą całkowitą, Dodaj specyfikator formatu dziesiętnego **, d** w kolumnie **Nazwa** po nazwie zmiennej. Kolumna **wartość** zawiera teraz **101**.

![Zrzut ekranu programu Visual Studio okno wyrażeń kontrolnych z jednym wierszem, który pokazuje my_var1, d o wartości 101 i typie int.](../debugger/media/watchformatcsharp.png)

::: moniker range=">= vs-2019" 

Można wyświetlić i wybrać listę dostępnych specyfikatorów formatu, dołączając przecinek (,) do wartości w oknie **czujki** . 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>Specyfikatory formatu
W poniższej tabeli opisano specyfikatory formatu w języku C# dla debugera programu Visual Studio.

|Specyfikator|Format|Oryginalna wartość czujki|Listę|
|---------------|------------|--------------------------|--------------|
|Napięcie|Wymuszanie oceny wyrażenia, które może być przydatne, gdy niejawna Ocena właściwości i niejawne wywołania funkcji jest wyłączona.|Komunikat "niejawna Ocena funkcji jest wyłączona przez użytkownika"|\<value>|
|d|Liczba całkowita dziesiętna|0x0065|101|
|dynamiczna|Wyświetla określony obiekt za pomocą widoku dynamicznego|Wyświetla wszystkie elementy członkowskie obiektu, w tym Widok dynamiczny|Wyświetla tylko Widok dynamiczny|
|h|Szesnastkowa liczba całkowita|61541|0x0000F065|
|nq|ciąg bez cudzysłowów|"Mój ciąg"|Mój ciąg|
|nse|Określa zachowanie, nie format. Oblicza wyrażenie ze znakiem "bez efektów ubocznych". Jeśli wyrażenie nie może być interpretowane i może zostać rozpoznane tylko przez oszacowanie (takie jak wywołanie funkcji), zamiast tego zobaczysz błąd.|NIE DOTYCZY|NIE DOTYCZY|
|hidden|Wyświetla wszystkie publiczne i niepubliczne składowe|Wyświetla publiczne elementy członkowskie|Wyświetla wszystkie elementy członkowskie|
|surowców|Wyświetla element, który pojawia się w węźle nieprzetworzonych elementów. Prawidłowy tylko w obiektach proxy.|Słownik\<T>|Nieprzetworzony widok słownika\<T>|
|wyniki|Używany ze zmienną typu, który implementuje interfejs IEnumerable lub IEnumerable \<T> , zazwyczaj wynik wyrażenia zapytania. Wyświetla tylko elementy członkowskie, które zawierają wynik zapytania.|Wyświetla wszystkie elementy członkowskie|Wyświetla elementy członkowskie spełniające warunki zapytania|

## <a name="see-also"></a>Zobacz też
- [Oglądaj i QuickWatch okna](../debugger/watch-and-quickwatch-windows.md)
- [Okna zmiennych i okien lokalnych](../debugger/autos-and-locals-windows.md)
