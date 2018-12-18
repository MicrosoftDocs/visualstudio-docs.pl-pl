---
title: Specyfikatory w języku C# formatu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 330a32b20eeab172ebf36e49f16e79aa936a1bdc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754168"
---
# <a name="format-specifiers-in-c"></a>Specyfikatory formatu w C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić format wyświetlania wartości w **Obejrzyj** okna przy użyciu specyfikatorów formatu. Możesz również użyć specyfikatorów formatu w **bezpośrednie** oknie **polecenia** okna, a nawet w oknach źródłowych. Jeśli zatrzymasz się na wyrażeniu w tych oknach, wynik pojawi się w poradzie dotyczącej danych. DataTips będzie odzwierciedlać specyfikatora formatu na wyświetlaczu DataTip.  
  
 Aby użyć specyfikatora formatu, wpisz wyrażenie rozdzielanych przecinkami. Po przecinku Dodaj specyfikator odpowiednie.  
  
## <a name="using-format-specifiers"></a>Przy użyciu specyfikatorów formatu  
 Jeśli masz następujący kod:  
  
```  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmiennej w oknie czujki (podczas debugowania, **debugowanie / Windows / Obejrzyj / obejrzeć 1**) i ustaw wyświetlania w postaci szesnastkowej (w **Obejrzyj** okna, kliknij prawym przyciskiem myszy zmienną i wybierz **Wyświetlanie szesnastkowe**). Teraz **Obejrzyj** okno pokazuje, że zawiera on wartości 0x0065. Aby zobaczyć tę wartość, wyrażone jako liczba całkowita dziesiętna zamiast Szesnastkowa liczba całkowita, w kolumnie Nazwa po nazwie zmiennej, Dodaj specyfikator formatu dziesiętnego: **, d**. Kolumna wartość wyświetla teraz wartość dziesiętną 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Specyfikatory formatu  
 W poniższej tabeli przedstawiono specyfikatory formatu C# rozpoznawanym przez debuger.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wyświetla|  
|---------------|------------|--------------------------|--------------|  
|ac|Wymuś wyniku obliczenia wyrażenia. Może to być przydatne, gdy bezwarunkowa ocena właściwości i niejawne wywołania funkcji jest wyłączone. Zobacz [efekty uboczne i wyrażenia](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Komunikat "niejawne Obliczanie funkcji zostało wyłączone przez użytkownika"|\<wartość >|  
|d|Liczba całkowita dziesiętna|0x0065|101|  
|dynamic|Wyświetla określony obiekt przy użyciu dynamicznego widoku|Wyświetla wszystkie elementy członkowskie obiektu, w tym widoku dynamicznego|Wyświetla tylko widoku dynamicznego|  
|h|Szesnastkowa liczba całkowita|61541|0x0000F065|  
|nq|ciąg znaków z nie cudzysłowów|"Mój String"|Moje ciągu|  
|hidden|Wyświetla wszystkie publiczne i niepubliczne składowe|Wyświetla publiczne elementy członkowskie|Wyświetla wszystkie elementy członkowskie|  
|nieprzetworzone|Wyświetla elementu, jak wygląda na to, w węźle pierwotne elementu. Prawidłowy tylko obiektów serwera proxy.|Słownik\<T >|Surowy widok tego słownika\<T >|  
|wyniki|Używane z zmienną typu, który implementuje interfejs IEnumerable lub typ IEnumerable\<T >, zazwyczaj wynikiem wyrażenia zapytania. Wyświetla tylko elementów członkowskich, które zawierają wyniku zapytania.|Wyświetla wszystkie elementy członkowskie.|Wyświetla elementy Członkowskie spełniają warunki zapytania.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Windows zmiennej](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





