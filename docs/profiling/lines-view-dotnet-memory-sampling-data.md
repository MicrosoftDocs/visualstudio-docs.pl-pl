---
title: Widok linii — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774083"
---
# <a name="lines-view---net-memory-sampling-data"></a>Widok linii — dane próbkowania pamięci .NET
Widok Linie dla danych profilowania alokacji pamięci .NET, który używa metody próbkowania, zawiera listę instrukcji, które przydzielono pamięć podczas przebiegu profilowania. Kolumny zawierają również rozmiar i liczbę alokacji.

 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.

 Oświadczenie jest identyfikowane przez następujące:

- Plik źródłowy zawierający instrukcję funkcji.

- Funkcja, która zawiera instrukcję.

- Wiersz źródłowy, od którego rozpoczyna się instrukcja.

- Znak w wierszu źródłowym, od którego rozpoczyna się instrukcja.

- Wiersz źródłowy, w którym kończy się instrukcja.

- Znak w wierszu źródłowym, w którym kończy się instrukcja.

  Kolumna Nazwa wiersza zawiera sortowalne łączenia danych identyfikatorów.

  Z definicji instrukcja nie wywoływać inne funkcje. W związku z tym wyświetlane są tylko wartości wyłączne.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy zawierający instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Koniec wiersza źródłowego**|Numer wiersza końcowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Źródłowy koniec znaku**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Nazwa wiersza**|Wygenerowany przez profiler identyfikator wiersza o następującej`Source File`składni:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number Start,Character Start`**]**|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone w tym wierszu.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które zostały przydzielone w tym wierszu.|
|**Bajty wyłączne**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone w tym wierszu.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone w tym wierszu.|

## <a name="see-also"></a>Zobacz też
- [Widok linii](../profiling/lines-view-sampling-data.md)
