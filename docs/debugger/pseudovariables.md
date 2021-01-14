---
title: Pseudozmiennych pokazanych | Microsoft Docs
description: Przejrzyj pseudozmiennych pokazanych w debugerze programu Visual Studio. Pseudozmiennych pokazanych są terminami używanymi do wyświetlania określonych danych w oknie zmiennych lub oknie dialogowym QuickWatch.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c5a76bf799eabd29b778c2dec867cc7e50aa45ee
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205531"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudozmiennych pokazanych w debugerze programu Visual Studio
Pseudozmiennych pokazanych są terminami używanymi do wyświetlania pewnych informacji w oknie zmiennych lub oknie dialogowym **QuickWatch** . Możesz wprowadzić pseudozmienna w taki sam sposób, jak w przypadku wprowadzenia zmiennej normalnej. Pseudozmiennych pokazanych nie są zmienne, ale nie odpowiadają nazwom zmiennych w programie.

## <a name="example"></a>Przykład
 Załóżmy, że piszesz natywną aplikację kodu i chcesz zobaczyć liczbę dojść przyznanych w aplikacji. W oknie **czujki** możesz wprowadzić następujące pseudozmienna w kolumnie **Nazwa** , a następnie nacisnąć klawisz Return, aby ją oszacować:

`$handles`

 W kodzie natywnym można użyć pseudozmiennych pokazanych pokazanego w poniższej tabeli:

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
|`$exceptionstack`|Wyświetla ślad stosu bieżącego wyjątku środowisko wykonawcze systemu Windows. `$ exceptionstack` działa tylko w aplikacjach platformy UWP. `$ exceptionstack` nie jest obsługiwane w przypadku wyjątków C++ i SEH|
|`$returnvalue`|Wyświetla wartość zwracaną przez metodę.|

 W języku C# można użyć pseudozmiennych pokazanych pokazanych w poniższej tabeli:

|Pseudozmienna|Funkcja|
|--------------------|--------------|
|`$exception`|Wyświetla informacje o ostatnim wyjątku. Jeśli nie wystąpił żaden wyjątek, Ocena `$exception` wyświetla komunikat o błędzie.<br /><br /> Gdy Asystent wyjątków jest wyłączony, `$exception` jest automatycznie dodawany do okna **zmiennych lokalnych** , gdy wystąpi wyjątek.|
|`$user`|Przedstawia strukturę z informacjami o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje o haśle nie są wyświetlane.|
|`$returnvalue`|Wyświetla wartość zwracaną przez metodę .NET.|

 W Visual Basic można użyć pseudozmiennych pokazanych pokazanej w poniższej tabeli:

|Pseudozmienna|Funkcja|
|--------------------|--------------|
|`$exception`|Wyświetla informacje o ostatnim wyjątku. Jeśli nie wystąpił żaden wyjątek, Ocena `$exception` wyświetla komunikat o błędzie.|
|`$delete` lub `$$delete`|Usuwa zmienną niejawną, która została utworzona w oknie **bezpośrednim** . Składnia jest `$delete,` *zmienna* lub `$delete,` *zmienna*`.`|
|`$objectids` lub `$listobjectids`|Wyświetla wszystkie aktywne identyfikatory obiektów jako elementy podrzędne określonego wyrażenia. Składnia jest `$objectid,` *wyrażeniem* lub `$listobjectids,` *wyrażeniem*`.`|
|`$`*N*`#`|Wyświetla obiekt z IDENTYFIKATORem obiektu równy *N*.|
|`$dynamic`|Wyświetla specjalny węzeł **widoku dynamicznego** dla obiektu, który implementuje `IDynamicMetaObjectProvider` . Interfejsu. Składnia jest `$dynamic,` *obiektem*. Ta funkcja ma zastosowanie tylko do kodu, który używa .NET Framework w wersji 4 lub nowszej.|

## <a name="see-also"></a>Zobacz też
- [Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych](../debugger/watch-and-quickwatch-windows.md)
- [Zmienne okna](../debugger/debugger-windows.md)
