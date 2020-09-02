---
title: Pseudozmiennych pokazanych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693763"
---
# <a name="pseudovariables"></a>Pseudozmienne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudozmiennych pokazanych są terminami używanymi do wyświetlania pewnych informacji w oknie zmiennych lub oknie dialogowym **QuickWatch** . Możesz wprowadzić pseudozmienna w taki sam sposób, jak w przypadku wprowadzenia zmiennej normalnej. Pseudozmiennych pokazanych nie są zmienne, ale nie odpowiadają nazwom zmiennych w programie.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że piszesz natywną aplikację kodu i chcesz zobaczyć liczbę dojść przyznanych w aplikacji. W oknie **czujki** możesz wprowadzić następujące pseudozmienna w kolumnie **Nazwa** , a następnie nacisnąć klawisz Return, aby ją oszacować:  
  
```  
$handles  
```  
  
 W kodzie natywnym można użyć pseudozmiennych pokazanych pokazanego w tej tabeli:  
  
|Pseudozmienna|Funkcja|  
|--------------------|--------------|  
|`$err`|Wyświetla wartość ostatniego błędu ustawioną przy użyciu funkcji SetLastError. Wyświetlana wartość reprezentuje element zwracany przez funkcję GetLastError.<br /><br /> Użyj `$err,hr` , aby zobaczyć zdekodowaną postać tej wartości. Na przykład jeśli ostatni błąd to 3, `$err,hr` zostanie wyświetlony komunikat `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Wyświetla liczbę dojść przyznanych w aplikacji.|  
|`$vframe`|Wyświetla adres bieżącej ramki stosu.|  
|`$tid`|Wyświetla identyfikator wątku dla bieżącego wątku.|  
|`$env`|Wyświetla blok środowiska w podglądzie ciągów.|  
|`$cmdline`|Wyświetla ciąg wiersza polecenia, który uruchomił program.|  
|`$pid`|Wyświetla identyfikator procesu.|  
|`$`*zarejestrujname*<br /><br /> lub<br /><br /> `@`*zarejestrujname*|Wyświetla zawartość *rejestru RegisterName.*<br /><br /> Zwykle można wyświetlić zawartość rejestru, wprowadzając nazwę rejestru. Jedyną potrzebą jest użycie tej składni, gdy nazwa rejestru przeciąża nazwę zmiennej. Jeśli nazwa rejestru jest taka sama jak nazwa zmiennej w bieżącym zakresie, debuger interpretuje nazwę jako nazwę zmiennej. Jest to przydatne, gdy `$` w programie *RegisterName* lub `@` *RegisterName* jest dostępna.|  
|`$clk`|Wyświetla godzinę w cyklach zegara.|  
|`$user`|Przedstawia strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje o haśle nie są wyświetlane.|  
|`$exceptionstack`|Wyświetla ślad stosu bieżącego wyjątku środowisko wykonawcze systemu Windows. `$ exceptionstack` działa tylko w aplikacjach ze sklepu, które działają w systemie Windows 8.1 lub nowszym. `$ exceptionstack` nie jest obsługiwany w przypadku języka C++ i wyjątków|  
|`$ReturnValue`|Wyświetla wartość zwracaną metody .NET Framework. Zobacz [Badanie zwracanych wartości wywołań metod](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 W językach C# i Visual Basic można użyć pseudozmiennych pokazanych pokazanej w tej tabeli:  
  
|Pseudozmienna|Funkcja|  
|--------------------|--------------|  
|`$exception`|Wyświetla informacje o ostatnim wyjątku. Jeśli nie wystąpił żaden wyjątek, Ocena `$exception` wyświetla komunikat o błędzie.<br /><br /> Tylko w języku Visual C#, gdy Asystent wyjątków jest wyłączony, `$exception` jest automatycznie dodawany do okna **zmiennych lokalnych** , gdy wystąpi wyjątek.|  
|`$user`|Przedstawia strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje o haśle nie są wyświetlane.|  
  
 W Visual Basic można użyć pseudozmiennych pokazanych pokazanej w poniższej tabeli:  
  
|Pseudozmienna|Funkcja|  
|--------------------|--------------|  
|`$delete` lub `$$delete`|Usuwa zmienną niejawną, która została utworzona w oknie **bezpośrednim** . Składnia jest `$delete,` *zmienna* lub `$delete,` *zmienna*`.`|  
|`$objectids` lub `$listobjectids`|Wyświetla wszystkie aktywne identyfikatory obiektów jako elementy podrzędne określonego wyrażenia. Składnia jest `$objectid,` *wyrażeniem* lub `$listobjectids,` *wyrażeniem*`.`|  
|`$` *N* `#`|Wyświetla obiekt z IDENTYFIKATORem obiektu równy *N*.|  
|`$dynamic`|Wyświetla specjalny węzeł **widoku dynamicznego** dla obiektu, który implementuje `IDynamicMetaObjectProvider` . Interfejsu. Składnia jest `$dynamic,` *obiektem*. Ta funkcja ma zastosowanie tylko do kodu, który używa .NET Framework w wersji 4. Zobacz [Widok dynamiczny](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Zobacz też  
 [Oglądaj i QuickWatch okna](../debugger/watch-and-quickwatch-windows.md)   
 [Zmienne okna](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
