---
title: Widok alokacji pamięci platformy .NET | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74777380"
---
# <a name="net-memory-allocations-view"></a>.NET Widok alokacji pamięci
Widok alokacje zawiera listę typów, które zostały utworzone podczas przebiegu profilowania. Każdy typ jest węzłem głównym drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowały alokacje typu.

 Dane w wierszu typu przedstawiają łączną liczbę obiektów typu, które zostały utworzone w ramach uruchomienia profilowania i łączną liczbę bajtów przydzieloną dla obiektów tego typu. Wartości włączne i wyłączne dla typu są zawsze takie same.

- Wartości włącznie są dla obiektów utworzonych w wystąpieniach funkcji i jej funkcji podrzędnych, które zostały wywołane przez funkcję nadrzędną w drzewie wywołań.

- Wartości wyłączne są dla obiektów, które zostały utworzone bezpośrednio przez funkcję, gdy zostały wywołane przez funkcję nadrzędną. Obiekty utworzone w funkcjach podrzędnych nie są uwzględniane.

  Dane dla funkcji wyświetlają liczbę utworzonych obiektów i liczbę bajtów przydzieloną dla obiektów typu nadrzędnego.

## <a name="highlight-the-execution-hot-path"></a>Wyróżnij gorącą ścieżkę wykonywania
 Można znaleźć ścieżkę wykonywania drzewa wywołań, która utworzyła większość obiektów typu nadrzędnego.

- Aby wyświetlić najbardziej aktywną ścieżkę, kliknij prawym przyciskiem myszy typ lub funkcję, a następnie kliknij przycisk **Rozwiń ścieżkę gorącą**.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa przydzielonych typów lub funkcji.|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera typ lub funkcję.|
|**Ścieżka modułu**|Ścieżka modułu zawierającego typ lub funkcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla typu lub funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej definicji typu lub funkcji w pliku źródłowym.|
|**Poziomie**|Wskazuje, czy dane są dla typu, czy funkcji.|
|**Przydziały włączne**|-Dla funkcji — całkowita liczba obiektów typu nadrzędnego, które zostały utworzone przez funkcję. Ta liczba obejmuje obiekty utworzone w funkcjach podrzędnych.<br />-Dla typu, Łączna liczba wystąpień tego typu, które zostały utworzone.|
|**% Przydziałów włącznych**|-Dla funkcji, procent wszystkich obiektów utworzonych w ramach uruchomienia profilowania, które były przydzielone do alokacji typu nadrzędnego przez funkcję.<br />-Dla typu, procent łącznej liczby obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były wystąpieniami tego typu.|
|**Alokacje wyłączne**|-Dla funkcji, liczba obiektów, które zostały utworzone podczas wykonywania funkcji bezpośrednio w górnej części stosu wywołań. Ta liczba nie obejmuje obiektów utworzonych w funkcjach podrzędnych.<br />-Dla typu, Łączna liczba wystąpień tego typu, które zostały utworzone.|
|**% Przydziałów wyłącznych**|-Dla funkcji, procent wszystkich obiektów utworzonych w ramach uruchomienia profilowania, które były wyłącznych alokacji typu nadrzędnego przez funkcję.<br />-Dla typu, procent łącznej liczby obiektów, które zostały utworzone w ramach uruchomienia profilowania, które były wystąpieniami tego typu.|
|**Bajty włączne**|-Dla funkcji, liczba bajtów pamięci przydzielonej przez funkcję dla obiektów typu nadrzędnego. Ta liczba obejmuje pamięć, która została przypisana przez funkcje podrzędne.<br />-Dla typu, Łączna liczba bajtów, które zostały przydzieloną w profilowania w ramach uruchomienia dla wystąpień typu.|
|**% Bajtów włącznych**|-Dla funkcji — wartość procentowa całej pamięci przydzielonej w ramach uruchomienia profilowania, która obejmuje przydziały dla typu nadrzędnego przez funkcję.<br />-Dla typu, wartość procentowa całej pamięci przydzieloną w ramach uruchomienia profilowania, która została przypisana dla wystąpień typu.|
|**Bajty wyłączne**|-Dla funkcji, liczba bajtów pamięci przydzielonej przez funkcję dla obiektów typu nadrzędnego. Ta liczba nie obejmuje pamięci, która została przypisana przez jej funkcje podrzędne.<br />-Dla typu, Łączna liczba bajtów, które zostały przydzieloną w profilowania, dla wystąpień typu.|
|**% Bajtów wyłącznych**|-Dla funkcji, procent całej pamięci przydzielonej w ramach uruchomienia profilowania, który miał wyłączne alokacje typu nadrzędnego przez funkcję.<br />-Dla typu, wartość procentowa całej pamięci przydzieloną w ramach uruchomienia profilowania, która została przypisana dla wystąpień typu.|
