---
title: Widok okresu istnienia obiektu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772627"
---
# <a name="object-lifetime-view"></a>Widok okresu istnienia obiektu
Widok Okres istnienia obiektu jest dostępny, gdy **dane okresu istnienia obiektu .NET są** sprawdzane na stronach właściwości Sesja **wydajności.**

 Moduł zbierający elementy bezużyteczne programu .NET Framework zarządza alokacją i wydaniem pamięci dla aplikacji. Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, zarządzany stos jest podzielony na trzy generacje: 0, 1 i 2. Moduł zbierający elementy bezużyteczne środowiska wykonawczego przechowuje nowe obiekty w generacji 0. Obiekty, które przetrwają kolekcje są promowane i przechowywane w pokoleniach 1 i 2.

 Moduł zbierający elementy bezużyteczne odzyskuje pamięć przez rozdzielenie alokacji całej generacji obiektów. Dla obiektów, które zostały utworzone przez profilowane aplikacji, Widok Okres istnienia obiektu wyświetla liczbę i rozmiar obiektów i generowania, w którym są one odzyskane.

## <a name="general"></a>Ogólne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa klasy**|Nazwa klasy przydzielonego typu.|
|**Identyfikator procesu**|Identyfikator procesu przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|

## <a name="instance-data"></a>Dane wystąpienia
 Dane wystąpienia wskazuje liczbę obiektów typu, które zostały utworzone w przebiegu profilowania i generowania, w którym obiekty zostały cofnięte przez moduł zbierający elementy bezużyteczne.

|Kolumna|Opis|
|------------|-----------------|
|**Wystąpienia**|Liczba alokacji obiektów tego typu.|
|**Łączna liczba wystąpień %**|Procent całkowitej liczby alokacji, które zostały wykonane w przebiegu profilowania.|
|**Zebrane wystąpienia gen 0**|Liczba wystąpień typu, które zostały cofnięte alokacji w generacji 0 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane wystąpienia gen 1**|Liczba wystąpień typu, które zostały cofnięte alokacji w generacji 1 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane wystąpienia gen 2**|Liczba wystąpień typu, które zostały cofnięte alokacji w generacji 2 algorytmu wyrzucania elementów bezużytecznych.|
|**Instancje przy życiu na końcu**|Liczba wystąpień typu, które nie zostały cofnięte alokacji do końca przebiegu profilowania.|

## <a name="size-byte-data"></a>Rozmiar (bajt) dane
 Rozmiar (bajt) dane wskazuje rozmiar obiektów typu, które zostały utworzone w przebiegu profilowania i ilość pamięci, która została odzyskana w każdej generacji, w którym obiekty zostały cofnięte.

|Kolumna|Opis|
|------------|-----------------|
|**Łączna liczba przydzielonych bajtów**|Całkowita liczba bajtów dla wszystkich wystąpień typu.|
|**Całkowita liczba bajtów %**|Procent całkowitej liczby przydzielonych bajtów w przebiegu profilowania, które zostały przydzielone dla wystąpień tego typu.|
|**Gen 0 Bajty zebrane**|Rozmiar wystąpień typu, które zostały cofnięte alokacji w generacji 0 algorytmu wyrzucania elementów bezużytecznych.|
|**Zebrane bajty gen 1**|Rozmiar wystąpień typu, które zostały cofnięte alokacji w generacji 1 algorytmu wyrzucania elementów bezużytecznych.|
|**Gen 2 Bajty zebrane**|Rozmiar wystąpień typu, które zostały cofnięte alokacji w generacji 2 algorytmu wyrzucania elementów bezużytecznych.|

## <a name="large-object-heap-data"></a>Dane sterty dużych obiektów
 Alokator pamięci .NET zarządza bardzo dużymi obiektami w lokalizacji, która jest oddzielona od standardowego zarządzanego stosu. Dane sterty dużych obiektów wskazują liczbę i rozmiar obiektów typu, które były zarządzane w tej lokalizacji.

|Kolumna|Opis|
|------------|-----------------|
|**Zebrane wystąpienia sterty dużych obiektów**|Liczba wystąpień tego typu, które znajdowały się w stercie dużych obiektów i które zostały zebrane w przebiegu profilowania.|
|**Zbierane bajty sterty dużych obiektów**|Rozmiar w bajtach wystąpień tego typu, które znajdowały się w stercie dużych obiektów i które zostały zebrane w przebiegu profilowania.|

## <a name="see-also"></a>Zobacz też
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
