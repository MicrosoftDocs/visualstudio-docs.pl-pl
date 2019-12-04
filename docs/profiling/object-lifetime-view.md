---
title: Widok okresu istnienia obiektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d4ea486930d0ea9f266b4ee57b69a50f7c570651
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772627"
---
# <a name="object-lifetime-view"></a>Widok okresu istnienia obiektu
Widok okresu istnienia obiektu jest dostępny, gdy **zbieranie danych o okresie istnienia obiektu .NET** jest sprawdzane na stronach właściwości **sesji wydajności** .

 Moduł wyrzucania elementów bezużytecznych .NET Framework zarządza alokacją i ilością pamięci dla aplikacji. Aby zoptymalizować wydajność modułu wyrzucania elementów bezużytecznych, sterta zarządzana jest dzielona na trzy generacje: 0, 1 i 2. Moduł wyrzucania elementów bezużytecznych w środowisku uruchomieniowym przechowuje nowe obiekty w generacji 0. Obiekty, które przeżyły kolekcje, są promowane i przechowywane w generacjach 1 i 2.

 Moduł zbierający elementy bezużyteczne odzyskuje pamięć przez cofnięcie przydziału całej generacji obiektów. W przypadku obiektów utworzonych przez profilowaną aplikację widok okres istnienia obiektu przedstawia liczbę i rozmiar obiektów oraz generację, w których są odzyskiwane.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa klasy**|Nazwa klasy przydzielonych typów.|
|**Identyfikator procesu**|Identyfikator procesu uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|

## <a name="instance-data"></a>Dane wystąpienia
 Dane wystąpienia wskazuje liczbę obiektów typu, które zostały utworzone w ramach uruchomienia profilowania, oraz generację, w których obiekty zostały cofnięte alokacja przez moduł wyrzucania elementów bezużytecznych.

|Kolumna|Opis|
|------------|-----------------|
|**Wystąpienia**|Liczba alokacji obiektów tego typu.|
|**Łączna liczba wystąpień%**|Wartość procentowa łącznej liczby przydziałów, które zostały wykonane w ramach uruchomienia profilowania.|
|**Zebrane wystąpienia generacji 0**|Liczba wystąpień typu, które zostały cofnięte w generacji 0 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane wystąpienia generacji 1**|Liczba wystąpień typu, które zostały cofnięte w generacji 1 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane wystąpienia generacji 2**|Liczba wystąpień typu, które zostały cofnięte w generacji 2 algorytmu wyrzucania elementów bezużytecznych.|
|**Wystąpienia aktywne na końcu**|Liczba wystąpień typu, które nie zostały cofnięte do końca uruchomienia profilowania.|

## <a name="size-byte-data"></a>Dane rozmiaru (bajtu)
 Wartość rozmiar (bajt) wskazuje rozmiar obiektów typu, które zostały utworzone w ramach uruchomienia profilowania, i ilość pamięci, która została odtworzona w każdej generacji, w której cofnięto alokację obiektów.

|Kolumna|Opis|
|------------|-----------------|
|**Łączna liczba przydzieloną bajtów**|Całkowita liczba bajtów dla wszystkich wystąpień typu.|
|**Łączna liczba bajtów%**|Wartość procentowa łącznej liczby przyznanych bajtów w przebiegu profilowania, które zostały przydzieloną dla wystąpień tego typu.|
|**Zebrane bajty generacji 0**|Rozmiar wystąpień typu, które zostały cofnięte w generacji 0 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane bajty generacji 1**|Rozmiar wystąpień typu, które zostały cofnięte w generacji 1 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane bajty generacji 2**|Rozmiar wystąpień typu, które zostały cofnięte w generacji 2 algorytmu wyrzucania elementów bezużytecznych.|

## <a name="large-object-heap-data"></a>Dane sterty dużych obiektów
 Program przydzielający pamięć .NET zarządza bardzo dużymi obiektami w lokalizacji, która jest oddzielona od standardowej sterty zarządzanej. Dane sterty dużego obiektu wskazują liczbę i rozmiar obiektów typu, które były zarządzane w tej lokalizacji.

|Kolumna|Opis|
|------------|-----------------|
|**Zebrano wystąpienia sterty dużych obiektów**|Liczba wystąpień tego typu, które znajdowały się w stercie dużego obiektu i zostały zebrane w ramach uruchomienia profilowania.|
|**Zebrane bajty sterty dużych obiektów**|Rozmiar (w bajtach) wystąpień tego typu, które znajdowały się w stercie dużych obiektów i zostały zebrane w ramach uruchomienia profilowania.|

## <a name="see-also"></a>Zobacz także
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
