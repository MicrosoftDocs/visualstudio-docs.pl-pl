---
title: Specyfikatory w debugerze formatu (C#) | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f01951a45a2e50f6dac093924627fe178011c9f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899017"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu C# w debugerze programu Visual Studio
Można zmienić format wyświetlania wartości w **Obejrzyj** okna przy użyciu specyfikatorów formatu. Możesz również użyć specyfikatorów formatu w **bezpośrednie** oknie **polecenia** okna w [punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)i w oknach źródłowych. Jeśli zatrzymasz się na wyrażeniu w tych oknach, wynik pojawi się w [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) wyświetlania określonego formatu.  
  
 Aby użyć specyfikatora formatu, wprowadź wyrażenie zmienne, a następnie przecinek i odpowiednie specyfikator.  
  
## <a name="set-format-specifiers"></a>Zestaw specyfikatorów formatu  
Użyjemy poniższy przykład kodu:   
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmienną **Obejrzyj** okna podczas debugowania, **debugowania** > **Windows** > **Obejrzyj**  >  **Obejrzeć 1**. Następnie kliknij prawym przyciskiem myszy zmienną i wybierz **wyświetlanie szesnastkowe**. Teraz **Obejrzyj** okno pokazuje wartość 0x0065. Aby wyświetlić tę wartość jako dziesiętna liczba całkowita, a nie jako szesnastkowa liczba całkowita, Dodaj specyfikator formatu dziesiętnego **, d** w **nazwa** kolumn po nazwie zmiennej. **Wartość** zawiera obecnie kolumnę **101**.   
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Specyfikatory formatu  
 W poniższej tabeli opisano C# formatowania specyfikatory dla debugera programu Visual Studio.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wyświetla|  
|---------------|------------|--------------------------|--------------|  
|ac|Wymuszenie obliczenia wyrażenia, które mogą być przydatne, gdy bezwarunkowa ocena właściwości i niejawne wywołania funkcji jest wyłączone.|Komunikat "niejawne Obliczanie funkcji zostało wyłączone przez użytkownika"|\<wartość >|  
|d|Liczba całkowita dziesiętna|0x0065|101|  
|dynamic|Wyświetla określony obiekt przy użyciu dynamicznego widoku|Wyświetla wszystkie elementy członkowskie obiektu, w tym widoku dynamicznego|Wyświetla tylko widoku dynamicznego|  
|h|Szesnastkowa liczba całkowita|61541|0x0000F065|  
|nq|ciąg znaków z nie cudzysłowów|"Mój String"|Moje ciągu|  
|nse|Określa zachowanie, nie formatu. Oblicza wyrażenie za pomocą "Żadnych efektów ubocznych". Jeśli wyrażenie nie mogą być interpretowane a tylko można rozwiązać poprzez ocenę (takie jak wywołania funkcji), zamiast tego zostanie wyświetlony błąd.|Brak|Brak|
|hidden|Wyświetla wszystkie publiczne i niepubliczne składowe|Wyświetla publiczne elementy członkowskie|Wyświetla wszystkie elementy członkowskie|  
|nieprzetworzone|Wyświetla elementu, jak wygląda na to, w węźle pierwotne elementu. Prawidłowy tylko obiektów serwera proxy.|Słownik\<T >|Surowy widok tego słownika\<T >|  
|wyniki|Używane z zmienną typu, który implementuje interfejs IEnumerable lub typ IEnumerable\<T >, zazwyczaj wynikiem wyrażenia zapytania. Wyświetla tylko elementów członkowskich, które zawierają wyniku zapytania.|Wyświetla wszystkie elementy członkowskie|Wyświetla elementy Członkowskie spełniają warunki zapytania|  
  
## <a name="see-also"></a>Zobacz także  
 [Oknach wyrażenie kontrolne i QuickWatch](../debugger/watch-and-quickwatch-windows.md)   
 [Okien zmiennych automatycznych i zmiennych lokalnych](../debugger/autos-and-locals-windows.md)
