---
title: Widok linii — dane próbkowania pamięci platformy .NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 503b3753f4f4fdc98f39804ec767277d7685d0d7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774083"
---
# <a name="lines-view---net-memory-sampling-data"></a>Widok linii — dane próbkowania pamięci platformy .NET
Widok linie dla danych profilowania przydziału pamięci platformy .NET, które używają metody próbkowania, zawiera listę instrukcji, które przydzieliły pamięć podczas przebiegu profilowania. Kolumny obejmują również rozmiar i liczbę alokacji.

 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Instrukcja jest identyfikowana przez następujące elementy:

- Plik źródłowy, który zawiera instrukcję Function.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, w którym rozpocznie się wykonywanie instrukcji.

- Znak w wierszu źródłowym, w którym rozpocznie się wykonywanie instrukcji.

- Wiersz źródłowy, w którym zostanie zakończona instrukcja.

- Znak w wierszu źródłowym, w którym następuje zakończenie instrukcji.

  Kolumna Nazwa wiersza zawiera konkatenację łączenia danych identyfikatora.

  Zgodnie z definicją instrukcja nie wywołuje innych funkcji. W związku z tym wyświetlane są tylko wartości wykluczane.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początek linii źródłowej**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Koniec linii źródłowej**|Numer wiersza końcowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Końcowy znak źródłowy**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Nazwa wiersza**|Wygenerowany przez profiler Identyfikator wiersza z następującą składnią:`Source File` **; [** `Line Number Start` **,** `Character Start` **]->; [** `Line Number Start,Character Start` **]**|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone w tym wierszu.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w ramach uruchomienia profilowania, które zostały przydzieloną w tym wierszu.|
|**Bajty wyłączne**|Wartość procentowa wszystkich bajtów pamięci przydzieloną w ramach uruchomienia profilowania, która została przypisana w tym wierszu.|
|**% Bajtów wyłącznych**|Wartość procentowa wszystkich bajtów pamięci przydzieloną w ramach uruchomienia profilowania, która została przypisana w tym wierszu.|

## <a name="see-also"></a>Zobacz także
- [Widok linii](../profiling/lines-view-sampling-data.md)
