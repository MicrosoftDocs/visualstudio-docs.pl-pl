---
title: Debugowanie historyczne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192187"
---
# <a name="historical-debugging"></a>Debugowanie historyczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie historyczne jest trybem debugowania, który zależy od informacji zbieranych przez IntelliTrace. Umożliwia przejście do tyłu i do przodu przez wykonanie aplikacji i sprawdzenie jej stanu.  
  
 Możesz użyć IntelliTrace w wersji Visual Studio Enterprise (ale nie wersji Professional lub Community).  
  
## <a name="why-use-historical-debugging"></a>Dlaczego warto używać debugowania historycznego?  
 Ustawienie punktów przerwania w celu znalezienia usterek może być Affair trafień lub chybień. Punkt przerwania jest ustawiany blisko miejsca w kodzie, w którym podejrzewasz, że usterka jest uruchamiana, a następnie uruchom aplikację w debugerze i polubisz, że punkt przerwania zostanie osiągnięty, i że miejsce, gdzie wykonywanie przerw w działaniu może ujawnić Źródło błędu. W przeciwnym razie trzeba będzie spróbować ustawić punkt przerwania w innym miejscu kodu i ponownie uruchomić debuger, wykonując kroki testu w trybie failover i aż do momentu znalezienia problemu.  
  
 ![Ustawianie punktu przerwania](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Można użyć IntelliTrace i debugowania historycznego, aby poruszać się w aplikacji i sprawdzać stan (stos wywołań i zmienne lokalne) bez konieczności ustawiania punktów przerwania, ponownego uruchomienia debugowania i powtarzania kroków testu. Pozwala to zaoszczędzić dużo czasu, szczególnie w przypadku, gdy błąd znajduje się w scenariuszu testowym, który zajmuje dużo czasu na wykonanie.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Jak mogę rozpocząć korzystanie z debugowania historycznego?  
 IntelliTrace jest domyślnie włączona. Wszystko, co musisz zrobić, decyduje o tym, które zdarzenia i wywołania funkcji są interesujące dla użytkownika. Aby uzyskać więcej informacji na temat definiowania elementów, które chcesz wyszukać, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md). Aby zapoznać się z kontem krok po kroku debugowania z usługą IntelliTrace, zobacz [Przewodnik: korzystanie z IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Nawigowanie po kodzie za pomocą debugowania historycznego  
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
  
 Przyjęto założenie, że oczekiwana wartość `resultInt` po wywołaniu `AddAll()` to 20 (wynik zwiększania `testInt` 20 razy). (Założono również, że błąd nie jest widoczny w programie `AddInt()` ). Jednak wynik jest w rzeczywistości 44. Jak można znaleźć usterkę bez przechodzenia przez `AddAll()` 10 razy? Możemy użyć debugowania historycznego, aby szybciej i łatwiej znaleźć usterkę. Aby to zrobić:  
  
1. W obszarze Narzędzia/Opcje/IntelliTrace/ogólne upewnij się, że IntelliTrace jest włączona, a następnie wybierz opcję zdarzenia IntelliTrace i informacje o wywołaniu. Jeśli nie wybierzesz tej opcji, nie będzie można zobaczyć odstępu nawigacyjnego (jak wyjaśniono poniżej).  
  
2. Ustaw punkt przerwania w `Console.WriteLine(resultInt);` wierszu.  
  
3. Uruchom debugowanie. Kod jest wykonywany w punkcie przerwania. W oknie zmienne **lokalne** można zobaczyć, że wartość `resultInt` to 44.  
  
4. Otwórz okno **Narzędzia diagnostyczne** (**debuguj/Pokaż narzędzia diagnostyczne**). Okno kod powinno wyglądać następująco:  
  
    ![Okno kodu w punkcie przerwania](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Powinna zostać wyświetlona podwójna strzałka obok lewego marginesu, tuż nad punktem przerwania. Ten obszar jest nazywany marginesem nawigacyjnym i służy do debugowania historycznego. Kliknij strzałkę.  
  
    W oknie Kod należy zobaczyć, że poprzedni wiersz kodu ( `int resultInt = AddIterative(testInt);` ) jest kolorem różowym. Nad oknem powinien pojawić się komunikat, że teraz zawarto debugowanie historyczne.  
  
    Okno kod wygląda teraz następująco:  
  
    ![okno kodu w trybie debugowania historycznego](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Teraz możesz przejść do `AddAll()` metody (**F11**lub **Wkrocz do** przycisku na marginesie nawigacyjnym). Krok do przodu (**F10**lub **Przejdź do następnego wywołania** na marginesie nawigacyjnym. Różowa linia znajduje się teraz w `j = AddInt(j);` wierszu. W tym przypadku **F10** nie przechodzi do następnego wiersza kodu. Zamiast tego należy wykonać kroki do następnego wywołania funkcji. Debugowanie historyczne prowadzi od wywołania wywołania i pomija wiersze kodu, które nie zawierają wywołania funkcji.  
  
7. Teraz przejdź do `AddInt()` metody. Usterka powinna być natychmiast widoczna w tym kodzie.  
  
   Ta procedura właśnie zakreśla powierzchnię tego, co można zrobić za pomocą debugowania historycznego. Aby dowiedzieć się więcej o różnych ustawieniach i efektach różnych przycisków na marginesie nawigacyjnym, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).
