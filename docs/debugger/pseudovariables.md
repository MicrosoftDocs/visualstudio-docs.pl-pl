---
title: Pseudozmienne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 336d177ec939ca0f7dfdc32535e2d2e92b0f04d2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686512"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudozmienne w debugerze programu Visual Studio
Pseudozmienne są terminami używanymi do wyświetlania pewnych informacji w oknie zmiennych lub **QuickWatch** okno dialogowe. Możesz wprowadzić zmienną pseudovariable taki sam sposób, jak wprowadziłbyś normalną zmienną. Pseudozmienne to nie zmienne, a nie odpowiadają nazwom zmiennych w programie.

## <a name="example"></a>Przykład
 Załóżmy, że piszesz aplikację kodu natywnego i chcesz zobaczyć liczbę dojść przydzielanych w aplikacji. W **Obejrzyj** okna, możesz wprowadzić następujące pseudozmienne w **nazwa** kolumny, a następnie nacisnąć przycisk Powrót, aby ocenić ją:

`$handles`

 W kodzie natywnym można użyć pseudozmiennych pokazanych w następującej tabeli:

|Pseudovariable|Funkcja|
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
|`$exceptionstack`|Wyświetla ślad stosu wyjątku bieżącego środowiska wykonawczego Windows. `$ exceptionstack` działa tylko w aplikacji platformy uniwersalnej systemu Windows. `$ exceptionstack` nie jest obsługiwana dla wyjątki C++ i SEH|
|`$ReturnValue`|Wyświetla wartość zwracaną metody .NET Framework.|

 W języku C# i Visual Basic można użyć pseudozmiennych pokazanych w następującej tabeli:

|Pseudovariable|Funkcja|
|--------------------|--------------|
|`$exception`|Wyświetla informacje o ostatnim wyjątku. Jeśli wystąpił żaden wyjątek, ocena `$exception` wyświetli komunikat o błędzie.<br /><br /> W języku Visual C# tylko wtedy, gdy Asystent wyjątków jest wyłączony, `$exception` jest automatycznie dodawany do **lokalne** okna, gdy wystąpi wyjątek.|
|`$user`|Wyświetla strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje hasła nie są wyświetlane.|

 W języku Visual Basic można użyć pseudozmiennych pokazanych w następującej tabeli:

|Pseudovariable|Funkcja|
|--------------------|--------------|
|`$delete` lub `$$delete`|Usuwa zmienną niejawną, który został utworzony w **bezpośrednie** okna. Składnia jest `$delete,` *zmiennej* lub`$delete,` *zmiennej*`.`|
|`$objectids` lub `$listobjectids`|Wyświetla wszystkie aktywne identyfikatory obiektów jako elementy podrzędne określonego wyrażenia. Składnia jest `$objectid,` *wyrażenie* lub`$listobjectids,` *wyrażenia*`.`|
|`$` *N* `#`|Wyświetla obiekt z Identyfikatorem obiektu równym *N*.|
|`$dynamic`|Wyświetla specjalny **dynamiczny widok** węzła dla obiektu, który implementuje `IDynamicMetaObjectProvider`. interfejs. Składnia jest `$dynamic,` *obiektu*. Ta funkcja ma zastosowanie tylko do kodu, który używa .NET Framework w wersji 4.|

## <a name="see-also"></a>Zobacz też
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Windows zmiennej](../debugger/debugger-windows.md)