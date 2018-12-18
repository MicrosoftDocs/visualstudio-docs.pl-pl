---
title: Debugowanie historyczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d43e48b67cdbfabcb38703469f8570f78336dcab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794598"
---
# <a name="historical-debugging"></a>Debugowanie historyczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie historyczne jest tryb debugowania, która jest zależna od informacji zbieranych przez IntelliTrace. Umożliwia on przenoszenie do tyłu i do przodu przez wykonanie aplikacji i sprawdzić jego stan.  
  
 Za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise (ale nie w wersjach Professional lub Community).  
  
## <a name="why-use-historical-debugging"></a>Dlaczego warto używać debugowania historycznego?  
 Ustawianie punktów przerwania, aby znaleźć błędy mogą być raczej hit-or-miss affair. Możesz ustawić punkt przerwania w pobliżu miejsca w kodzie gdzie podejrzenie błędu można, a następnie uruchom aplikację w debugera i mamy nadzieję, że odsyłania punkt przerwania, naciśnij klawisz i że to miejsce, gdzie przerywa wykonywanie może ujawnić źródła błędu. W przeciwnym razie trzeba będzie spróbować ustawić punkt przerwania w innym miejscu w kodzie i ponownie uruchom debuger, wykonywanie do kroków testu wiele razy, aż znajdziesz problem.  
  
 ![ustawienie punktu przerwania](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Możesz użyć IntelliTrace i debugowanie historyczne są przenoszone wokół w aplikacji i sprawdzić jego stan (stos wywołań i zmienne lokalne) bez konieczności ustawiania punktów przerwania, uruchom ponownie debugowanie i powtórz kroki testu. To może zaoszczędzić dużo czasu, szczególnie gdy usterka znajduje się w scenariuszu testu, który zajmuje dużo czasu, aby wykonać.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Jak uruchomić debugowania historycznego  
 Funkcja IntelliTrace jest domyślnie włączone. To wszystko, co należy zrobić, zdecyduj, które zdarzenia i wywołania funkcji Cię interesują. Aby uzyskać więcej informacji na temat definiowania mają być wyszukiwane, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md). Instrukcje krok po kroku konta debugowania za pomocą IntelliTrace, zobacz [Instruktaż: przy użyciu funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
## <a name="navigating-your-code-with-historical-debugging"></a>Poruszanie się po kodzie za pomocą debugowania historycznego  
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
  
1. W menu Narzędzia / Opcje / IntelliTrace / ogólne, upewnij się, że IntelliTrace jest włączony i wybierz zdarzenia IntelliTrace i wywołania opcji informacje. Jeśli nie zaznaczysz tej opcji, nie będzie można zobaczyć trasę nawigacji (jak wyjaśniono poniżej).  
  
2. Ustaw punkt przerwania na `Console.WriteLine(resultInt);` wiersza.  
  
3. Rozpocznij debugowanie. Kod jest wykonywany punkt przerwania. W **lokalne** okna, możesz zobaczyć, że wartość `resultInt` jest 44.  
  
4. Otwórz **narzędzia diagnostyczne** okna (**debugowanie / Pokaż narzędzia diagnostyczne**). W oknie Kod powinien wyglądać następująco:  
  
    ![Okno kodu w punkcie przerwania](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. Powinien zostać wyświetlony podwójną strzałkę obok lewy margines, tuż nad punktu przerwania. Ten obszar nosi nazwę trasę nawigacji i jest używana do debugowania historycznego. Kliknij strzałkę.  
  
    W oknie Kod powinien zostać wyświetlony, poprzedni wiersz kodu (`int resultInt = AddIterative(testInt);`) jest kolor różowy. Nad oknem powinien zostać wyświetlony komunikat, który nastąpi przekierowanie do debugowania historycznego.  
  
    W oknie kod wygląda teraz następująco:  
  
    ![Okno kodu w trybie debugowania historycznego](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. Teraz możesz wejść do `AddAll()` — metoda (**F11**, lub **Step Into** przycisk trasę nawigacji. Krok do przodu (**F10**, lub **przejdź do następnego wywołania** w trasę nawigacji. Różowa linia jest teraz dostępny w `j = AddInt(j);` wiersza. **F10** w tym przypadku nie wkracza do następnego wiersza kodu. Zamiast tego przechodzi do następnego wywołania funkcji. Debugowanie historyczne przechodzi z wywołaniami i pomija wierszy kodu, które nie obejmują wywołania funkcji.  
  
7. Teraz Wkrocz `AddInt()` metody. Powinien zostać wyświetlony błąd, w tym kodzie natychmiast.  
  
   Procedura ta po prostu rysy powierzchni co można zrobić za pomocą debugowania historycznego. Aby dowiedzieć się więcej o różnych ustawieniach i efekty różnych przycisków w trasę nawigacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).





