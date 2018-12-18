---
title: Pseudozmienne | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79d2f47acfbd5a4b6adf6d5f679fb3b514679dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789502"
---
# <a name="pseudovariables"></a>Pseudozmienne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pseudozmienne są terminami używanymi do wyświetlania pewnych informacji w oknie zmiennych lub **QuickWatch** okno dialogowe. Możesz wprowadzić zmienną pseudovariable taki sam sposób, jak wprowadziłbyś normalną zmienną. Pseudozmienne to nie zmienne, a nie odpowiadają nazwom zmiennych w programie.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że piszesz aplikację kodu natywnego i chcesz zobaczyć liczbę dojść przydzielanych w aplikacji. W **Obejrzyj** okna, możesz wprowadzić następujące pseudozmienne w **nazwa** kolumny, a następnie nacisnąć przycisk Powrót, aby ocenić ją:  
  
```  
$handles  
```  
  
 W kodzie natywnym można użyć pseudozmiennych pokazanych w następującej tabeli:  
  
|Pseudozmienne|Funkcja|  
|--------------------|--------------|  
|`$err`|Wyświetla zestaw wartości ostatniego błędu z funkcji SetLastError. Wartość, która jest wyświetlana reprezentuje co zostałaby zwrócone przez funkcję GetLastError.<br /><br /> Użyj `$err,hr` aby zobaczyć zdekodowaną postać tej wartości. Na przykład jeśli ostatnim błędem było 3 `$err,hr` zostanie wyświetlony `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Wyświetla liczbę dojść przydzielanych w aplikacji.|  
|`$vframe`|Wyświetla adres bieżącej ramki stosu.|  
|`$tid`|Wyświetla identyfikator wątku dla bieżącego wątku.|  
|`$env`|Wyświetla blok środowiska w podglądzie ciąg.|  
|`$cmdline`|Wyświetla ciąg wiersza polecenia, który uruchamiany program.|  
|`$pid`|Wyświetla identyfikator procesu.|  
|`$` *registername —*<br /><br /> lub<br /><br /> `@` *registername —*|Wyświetla zawartość rejestru *registername —*.<br /><br /> Zazwyczaj można wyświetlać zawartość rejestru poprzez samo podanie nazwy rejestru. Jedyną sytuacją, należy użyć tej składni jest, gdy nazwa rejestru przeciąża nazwę zmiennej. Jeśli nazwa rejestru jest taka sama jak nazwa zmiennej w bieżącym zakresie, debuger interpretuje nazwę jako nazwę zmiennej. Gdy `$` *registername —* lub `@` *registername —* przydatność.|  
|`$clk`|Wyświetla godzinę w cyklach zegara.|  
|`$user`|Wyświetla strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje hasła nie są wyświetlane.|  
|`$exceptionstack`|Wyświetla ślad stosu wyjątku bieżącego środowiska wykonawczego Windows. `$ exceptionstack` działa tylko w aplikacji Store, które są uruchomione na Windows 8.1 lub nowszym. `$ exceptionstack` nie jest obsługiwana dla języka C++ i wyjątki|  
|`$ReturnValue`|Wyświetla wartość zwracaną metody .NET Framework. Zobacz [Sprawdź wartości zwracanych z wywołań metod](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 W języku C# i Visual Basic można użyć pseudozmiennych pokazanych w następującej tabeli:  
  
|Pseudozmienne|Funkcja|  
|--------------------|--------------|  
|`$exception`|Wyświetla informacje o ostatnim wyjątku. Jeśli wystąpił żaden wyjątek, ocena `$exception` wyświetli komunikat o błędzie.<br /><br /> W języku Visual C# tylko wtedy, gdy Asystent wyjątków jest wyłączony, `$exception` jest automatycznie dodawany do **lokalne** okna, gdy wystąpi wyjątek.|  
|`$user`|Wyświetla strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje hasła nie są wyświetlane.|  
  
 W języku Visual Basic można użyć pseudozmiennych pokazanych w następującej tabeli:  
  
|Pseudozmienne|Funkcja|  
|--------------------|--------------|  
|`$delete` lub `$$delete`|Usuwa zmienną niejawną, który został utworzony w **bezpośrednie** okna. Składnia jest `$delete,` *zmiennej* lub`$delete,` *zmiennej*`.`|  
|`$objectids` lub `$listobjectids`|Wyświetla wszystkie aktywne identyfikatory obiektów jako elementy podrzędne określonego wyrażenia. Składnia jest `$objectid,` *wyrażenie* lub`$listobjectids,` *wyrażenia*`.`|  
|`$` *N* `#`|Wyświetla obiekt z Identyfikatorem obiektu równym *N*.|  
|`$dynamic`|Wyświetla specjalny **dynamiczny widok** węzła dla obiektu, który implementuje `IDynamicMetaObjectProvider`. interfejs. Składnia jest `$dynamic,` *obiektu*. Ta funkcja ma zastosowanie tylko do kodu, który używa .NET Framework w wersji 4. Zobacz [dynamiczny widok](http://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Windows zmiennej](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





