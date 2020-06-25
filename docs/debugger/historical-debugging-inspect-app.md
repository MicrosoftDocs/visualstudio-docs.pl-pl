---
title: Zbadaj aplikację za pomocą debugowania historycznego | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efabc8cd185daed4f018e3e4209e391b5bc39f44
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350449"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Sprawdzanie aplikacji za pomocą debugowania historycznego IntelliTrace w programie Visual Studio (C#, Visual Basic, C++)

Możesz użyć [debugowania historycznego](../debugger/historical-debugging.md) , aby przejść do tyłu i do przodu przez wykonanie aplikacji i sprawdzić jej stan.

Możesz użyć IntelliTrace w wersji Visual Studio Enterprise, ale nie wersji Professional ani Community.

## <a name="navigate-your-code-with-historical-debugging"></a>Nawigowanie po kodzie za pomocą debugowania historycznego

Zacznijmy od prostego programu, który ma usterkę. W aplikacji konsolowej C# Dodaj następujący kod:

```csharp
static void Main(string[] args)
{
    int testInt = 0;
    int resultInt = AddAll(testInt);
    Console.WriteLine(resultInt);
}
private static int AddAll(int j)
{
    for (int i = 0; i < 20; i++)
    {
        j = AddInt(j);
    }
    return j;
}

private static int AddInt(int add)
{
    if (add == 10)
    {
        return add += 25;
    }
    return ++add;
}
```

Przyjęto założenie, że oczekiwana wartość `resultInt` po wywołaniu `AddAll()` to 20 (wynik zwiększania `testInt` 20 razy). (Założono również, że błąd nie jest widoczny w programie `AddInt()` ). Jednak wynik jest w rzeczywistości 44. Jak można znaleźć usterkę bez przechodzenia przez `AddAll()` 10 razy? Możemy użyć debugowania historycznego, aby szybciej i łatwiej znaleźć usterkę. Oto kroki tej procedury:

1. W obszarze **narzędzia > opcje > IntelliTrace > ogólne**upewnij się, że IntelliTrace jest włączona, a następnie wybierz pozycję **zdarzenia IntelliTrace i informacje o wywołaniu**. Jeśli nie wybierzesz tej opcji, nie będzie można zobaczyć odstępu nawigacyjnego (jak wyjaśniono poniżej).

2. Ustaw punkt przerwania w `Console.WriteLine(resultInt);` wierszu.

3. Rozpocznij debugowanie. Kod jest wykonywany w punkcie przerwania. W oknie zmienne **lokalne** można zobaczyć, że wartość `resultInt` to 44.

4. Otwórz okno **Narzędzia diagnostyczne** (**debuguj > Pokaż narzędzia diagnostyczne**). Okno kod powinno wyglądać następująco:

    ![Okno kodu w punkcie przerwania](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Powinna zostać wyświetlona podwójna strzałka obok lewego marginesu, tuż nad punktem przerwania. Ten obszar jest nazywany marginesem nawigacyjnym i służy do debugowania historycznego. Kliknij strzałkę.

    W oknie Kod należy zobaczyć, że poprzedni wiersz kodu ( `int resultInt = AddIterative(testInt);` ) jest kolorem różowym. Nad oknem powinien pojawić się komunikat, że teraz zawarto debugowanie historyczne.

    Okno kod wygląda teraz następująco:

    ![okno kodu w trybie debugowania historycznego](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Teraz możesz przejść do `AddAll()` metody (**F11**lub **Wkrocz do** przycisku na marginesie nawigacyjnym). Krok do przodu (**F10**lub **Przejdź do następnego wywołania** na marginesie nawigacyjnym. Różowa linia znajduje się teraz w `j = AddInt(j);` wierszu. W tym przypadku **F10** nie przechodzi do następnego wiersza kodu. Zamiast tego należy wykonać kroki do następnego wywołania funkcji. Debugowanie historyczne prowadzi od wywołania wywołania i pomija wiersze kodu, które nie zawierają wywołania funkcji.

7. Teraz przejdź do `AddInt()` metody. Usterka powinna być natychmiast widoczna w tym kodzie.

## <a name="next-steps"></a>Następne kroki

Ta procedura właśnie zakreśla powierzchnię tego, co można zrobić za pomocą debugowania historycznego.

- Aby wyświetlić migawki podczas debugowania, zobacz [Sprawdzanie poprzedniego stanu aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md).
- Aby dowiedzieć się więcej o różnych ustawieniach i efektach różnych przycisków na marginesie nawigacyjnym, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).
