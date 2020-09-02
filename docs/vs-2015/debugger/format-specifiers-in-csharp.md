---
title: Specyfikatory formatu w języku C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6085ba95d3880417e517530069734052741113e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682483"
---
# <a name="format-specifiers-in-c"></a>Specyfikatory formatu w języku C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić format, w którym wartość jest wyświetlana w oknie **czujki** przy użyciu specyfikatorów formatu. Można również użyć specyfikatorów formatu w oknie **bezpośrednim** , oknie **polecenia** , a nawet w oknach źródłowych. W przypadku wstrzymania na wyrażeniu w tych oknach wynik zostanie wyświetlony w etykietki danych. Etykietki danych odzwierciedlają specyfikator formatu na ekranie etykietki danych.

Aby użyć specyfikatora formatu, wpisz wyrażenie, po którym następuje przecinek. Po przecinku Dodaj odpowiedni specyfikator.

## <a name="using-format-specifiers"></a>Używanie specyfikatorów formatu

Jeśli masz następujący kod:

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Dodaj `my_var1` zmienną do okno wyrażeń kontrolnych (podczas debugowania, **Debuguj/Windows/Watch/Watch 1**) i ustaw wartość wyświetlaną w formacie szesnastkowym (w oknie **czujka** , kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Wyświetlanie szesnastkowe**). Teraz okno **czujki** pokazuje, że zawiera on wartość 0x0065. Aby wyświetlić tę wartość wyrażoną jako dziesiętną liczbę całkowitą zamiast szesnastkowej liczby całkowitej, w kolumnie Nazwa po nazwie zmiennej Dodaj specyfikator formatu dziesiętnego: **, d**. W kolumnie wartość zostanie wyświetlona wartość dziesiętna 101

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

## <a name="format-specifiers"></a>Specyfikatory formatu

W poniższej tabeli przedstawiono specyfikatory formatu w języku C# rozpoznawane przez debuger.

|Specyfikator|Format|Oryginalna wartość czujki|Listę|
|---------------|------------|--------------------------|--------------|
|Napięcie|Wymuś Obliczanie wyrażenia. Może to być przydatne w przypadku wyłączenia niejawnej oceny właściwości i niejawnych wywołań funkcji. Zobacz [efekty uboczne i wyrażenia](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).|Komunikat "niejawna Ocena funkcji jest wyłączona przez użytkownika"|\<value>|
|d|Liczba całkowita dziesiętna|0x0065|101|
|dynamiczna|Wyświetla określony obiekt za pomocą widoku dynamicznego|Wyświetla wszystkie elementy członkowskie obiektu, w tym Widok dynamiczny|Wyświetla tylko Widok dynamiczny|
|h|Szesnastkowa liczba całkowita|61541|0x0000F065|
|nq|ciąg bez cudzysłowów|"Mój ciąg"|Mój ciąg|
|hidden|Wyświetla wszystkie publiczne i niepubliczne składowe|Wyświetla publiczne elementy członkowskie|Wyświetla wszystkie elementy członkowskie|
|surowców|Wyświetla element, który pojawia się w węźle nieprzetworzonych elementów. Prawidłowy tylko w obiektach proxy.|Słownik\<T>|Nieprzetworzony widok słownika\<T>|
|wyniki|Używany ze zmienną typu, który implementuje interfejs IEnumerable lub IEnumerable \<T> , zazwyczaj wynik wyrażenia zapytania. Wyświetla tylko elementy członkowskie, które zawierają wynik zapytania.|Wyświetla wszystkie elementy członkowskie.|Wyświetla elementy członkowskie spełniające warunki zapytania.|

## <a name="see-also"></a>Zobacz też

- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Zmienne okna](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
