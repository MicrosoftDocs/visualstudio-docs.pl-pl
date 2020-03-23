---
title: Widok wskaźników instrukcji (IP) — dane próbkowania pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: aa90262081a693227b4594a4e5b7fe22c8fb1627
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778664"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Widok wskaźników instrukcji ( IP) — dane próbkowania pamięci .NET
Widok adresów IP dla danych profilowania alokacji pamięci .NET, który został zebrany przy użyciu metody próbkowania zawiera listę instrukcji zestawu, które przydzielono pamięć podczas przebiegu profilowania. Kolumny widoku również lista rozmiar i liczbę alokacji.

 Wyświetlane są tylko wartości wyłączne.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) przebiegu profilowania.|
|**Nazwa procesu**|Nazwa procesu|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy zawierający instrukcję.|
|**Nazwa funkcji**|Nazwa funkcji.|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początek wiersza źródłowego**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Koniec wiersza źródłowego**|Numer wiersza końcowego w pliku źródłowym, w którym wystąpiła alokacja.|
|**Początek znaku źródłowego**|Przesunięcie znaku początkowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Źródłowy koniec znaku**|Przesunięcie znaku końcowego w wierszu pliku źródłowego, w którym wystąpiła alokacja.|
|**Adres instrukcji**|Adres instrukcji.|
|**Alokacje wyłączne**|Całkowita liczba obiektów, które zostały utworzone przez instrukcję.|
|**Alokacje wyłączne %**|Procent wszystkich obiektów, które zostały utworzone w przebiegu profilowania, które zostały przydzielone przez instrukcję.|
|**Bajty wyłączne**|Liczba bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone przez instrukcję.|
|**Bajty wyłączności %**|Procent wszystkich bajtów pamięci, które zostały przydzielone w przebiegu profilowania, które zostały przydzielone przez instrukcję.|

## <a name="see-also"></a>Zobacz też
- [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)
