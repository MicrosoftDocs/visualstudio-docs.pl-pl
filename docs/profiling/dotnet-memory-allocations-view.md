---
title: Widok alokacji pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.allocation
helpviewer_keywords:
- performance reports, allocation view
- Allocations view
- profiling tools, Allocation view
- profiling tools reports, Allocation view
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce16f65947fd69b5a54e564ba6bec061bc68e328
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777380"
---
# <a name="net-memory-allocations-view"></a>.NET Widok alokacji pamięci
Widok Alokacje zawiera listę typów, które zostały utworzone podczas przebiegu profilowania. Każdy typ jest węzłem głównym drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowało alokacje typu.

 Dane w wierszu typu wyświetlają całkowitą liczbę obiektów typu, które zostały utworzone w przebiegu profilowania oraz całkowitą liczbę bajtów przydzielonych dla obiektów tego typu. Wartości włączające i wyłączne dla typu są zawsze takie same.

- Wartości włącznie są dla obiektów utworzonych w wystąpieniach funkcji i jej funkcji podrzędnych, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.

- Wyłączne wartości są dla obiektów, które zostały utworzone bezpośrednio przez funkcję, gdy były wywoływane przez funkcję nadrzędną. Obiekty utworzone w funkcjach podrzędnych nie są uwzględniane.

  Dane funkcji są wyświetlane pod względem liczby utworzonych obiektów oraz liczby bajtów przydzielonych dla obiektów typu nadrzędnego.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnianie ścieżki aktywnej wykonania
 Można znaleźć ścieżkę wykonywania drzewa wywołań, który utworzył najwięcej obiektów typu nadrzędnego.

- Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy tekst lub funkcję, a następnie kliknij polecenie **Rozwiń ścieżkę gorącą**.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa przydzielonego typu lub funkcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera typ lub funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera typ lub funkcję.|
|**Plik źródłowy**|Plik źródłowy zawierający definicję typu lub funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku definicji tego typu lub funkcji w pliku źródłowym.|
|**Poziom**|Wskazuje, czy dane są dla typu lub funkcji.|
|**Alokacje włącznie**|- Dla funkcji całkowita liczba obiektów typu nadrzędnego, które zostały utworzone przez funkcję. Liczba ta obejmuje obiekty utworzone w funkcjach podrzędnych.<br />- Dla typu całkowita liczba wystąpień tego typu, które zostały utworzone.|
|**Alokacje włącznie %**|- Dla funkcji procent wszystkich obiektów utworzonych w przebiegu profilowania, które były alokacje włącznie typu nadrzędnego przez funkcję.<br />- Dla typu procent całkowitej liczby obiektów, które zostały utworzone w przebiegu profilowania, które były wystąpienia typu.|
|**Alokacje wyłączne**|- Dla funkcji liczba obiektów, które zostały utworzone, gdy funkcja była wykonywana bezpośrednio w górnej części stosu wywołań. Liczba ta nie obejmuje obiektów utworzonych w funkcjach podrzędnych.<br />- Dla typu całkowita liczba wystąpień tego typu, które zostały utworzone.|
|**Alokacje wyłączne %**|- Dla funkcji procent wszystkich obiektów utworzonych w przebiegu profilowania, które były wyłączne alokacje typu nadrzędnego przez funkcję.<br />- Dla typu procent całkowitej liczby obiektów, które zostały utworzone w przebiegu profilowania, które były wystąpienia typu.|
|**Bajty włącznie**|- Dla funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Liczba ta obejmuje pamięć, która została przydzielona przez jego funkcje podrzędne.<br />- Dla typu całkowita liczba bajtów, które zostały przydzielone w przebiegu profilowania dla wystąpień typu.|
|**Bajty włącznie %**|- Dla funkcji procent całej pamięci przydzielonej w przebiegu profilowania, który był włącznie alokacji typu nadrzędnego przez funkcję.<br />- Dla typu procent całej pamięci przydzielonej w przebiegu profilowania, który został przydzielony dla wystąpień typu.|
|**Bajty wyłączne**|- Dla funkcji liczba bajtów pamięci, które zostały przydzielone przez funkcję dla obiektów typu nadrzędnego. Liczba ta nie obejmuje pamięci, która została przydzielona przez jego funkcje podrzędne.<br />- Dla typu całkowita liczba bajtów, które zostały przydzielone w przebiegu profilowania dla wystąpień typu.|
|**Bajty wyłączności %**|- Dla funkcji procent wszystkich pamięci przydzielonych w przebiegu profilowania, który był wyłączne alokacje typu nadrzędnego przez funkcję.<br />- Dla typu procent całej pamięci przydzielonej w przebiegu profilowania, który został przydzielony dla wystąpień typu.|
