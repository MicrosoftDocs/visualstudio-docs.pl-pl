---
title: Sprawdzanie aplikacji za pomocą debugowania historycznego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 998b94a13f3650446f9f791ffc29c7c863f9df89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968634"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Sprawdzanie aplikacji z programem IntelliTrace historical debugowania w programie Visual Studio
Możesz użyć [debugowania historycznego](../debugger/historical-debugging.md) do tyłu i do przodu przez wykonanie aplikacji i sprawdzić jego stan.  
  
Za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise, ale nie w wersjach Professional lub Community.  
  
## <a name="navigate-your-code-with-historical-debugging"></a>Nawiguj po kodzie za pomocą debugowania historycznego  
 Zacznijmy od prosty program, który zawiera błąd. W aplikacji konsolowej C# Dodaj następujący kod:  
  
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
  
 Firma Microsoft będzie przyjęto założenie, że oczekiwana wartość `resultInt` po wywołaniu `AddAll()` wynosi 20 (zwiększanie wyniku `testInt` 20 razy). (Przyjmiemy również, że nie widzisz usterkę w `AddInt()`). Jednak wynik jest faktycznie 44. Jak możemy znaleźć usterki bez krokowe `AddAll()` 10 razy? Możemy użyć debugowania historycznego, aby znaleźć usterki szybciej i łatwiej. Oto jak:  
  
1.  W **Narzędzia > Opcje > IntelliTrace > Ogólne**, upewnij się, że IntelliTrace jest włączony i wybierz **zdarzenia IntelliTrace i wywołania informacji**. Jeśli nie zaznaczysz tej opcji, nie będzie można zobaczyć trasę nawigacji (jak wyjaśniono poniżej).  
  
2.  Ustaw punkt przerwania na `Console.WriteLine(resultInt);` wiersza.  
  
3.  Rozpocznij debugowanie. Kod jest wykonywany punkt przerwania. W **lokalne** okna, możesz zobaczyć, że wartość `resultInt` jest 44.  
  
4.  Otwórz **narzędzia diagnostyczne** okna (**Debuguj > Pokaż narzędzia diagnostyczne**). W oknie Kod powinien wyglądać następująco:  
  
     ![Okno kodu w punkcie przerwania](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  Powinien zostać wyświetlony podwójną strzałkę obok lewy margines, tuż nad punktu przerwania. Ten obszar nosi nazwę trasę nawigacji i jest używana do debugowania historycznego. Kliknij strzałkę.  
  
     W oknie Kod powinien zostać wyświetlony, poprzedni wiersz kodu (`int resultInt = AddIterative(testInt);`) jest kolor różowy. Nad oknem powinien zostać wyświetlony komunikat, który nastąpi przekierowanie do debugowania historycznego.  
  
     W oknie kod wygląda teraz następująco:  
  
     ![Okno kodu w trybie debugowania historycznego](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  Teraz możesz wejść do `AddAll()` — metoda (**F11**, lub **Step Into** przycisk trasę nawigacji. Krok do przodu (**F10**, lub **przejdź do następnego wywołania** w trasę nawigacji. Różowa linia jest teraz dostępny w `j = AddInt(j);` wiersza. **F10** w tym przypadku nie wkracza do następnego wiersza kodu. Zamiast tego przechodzi do następnego wywołania funkcji. Debugowanie historyczne przechodzi z wywołaniami i pomija wierszy kodu, które nie obejmują wywołania funkcji.  
  
7.  Teraz Wkrocz `AddInt()` metody. Powinien zostać wyświetlony błąd, w tym kodzie natychmiast.  

## <a name="next-steps"></a>Następne kroki

Procedura ta po prostu rysy powierzchni co można zrobić za pomocą debugowania historycznego.

- Aby wyświetlić migawki podczas debugowania, zobacz [Sprawdź poprzednie Stany aplikacji za pomocą funkcji IntelliTrace](../debugger/view-historical-application-state.md).
- Aby dowiedzieć się więcej o różnych ustawieniach i efekty różnych przycisków w trasę nawigacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).