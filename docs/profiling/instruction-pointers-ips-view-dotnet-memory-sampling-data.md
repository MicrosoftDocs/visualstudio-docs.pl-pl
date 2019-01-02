---
title: Widok wskaźników instrukcji (IP) - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 9d3ad0bc9239c0cee9bdb425f2a475391654125a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964166"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Widok wskaźników instrukcji (IP) - dane próbkowania pamięci platformy .NET
Widok adresów IP dla platformy .NET dane alokacji pamięci profilowania zebrane przy użyciu metody próbkowania wymieniono instrukcje montażu, które pamięci przydzielonej podczas uruchomienia profilowania. Kolumny widoku Wyświetl listę, rozmiar i liczba przydziałów.  
  
 Tylko wartości wyłącznych są wyświetlane.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera instrukcję.|  
|**Nazwa funkcji**|Nazwa funkcji.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Adres funkcji**|Adres początkowy funkcji.|  
|**Początkowy wiersz w źródle**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła Alokacja.|  
|**Końcowy wiersz w źródle**|Końcowy numer wiersza w pliku źródłowym, w którym wystąpiła Alokacja.|  
|**Początkowy znak w źródle**|Przesunięcie początkowy znak w wierszu pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Końcowy znak w źródle**|Przesunięcie końcowy znak w wierszu pliku źródłowego, w którym wystąpiła Alokacja.|  
|**Adres instrukcji**|Adres instrukcji.|  
|**Przydziały wyłączne**|Całkowita liczba obiektów, które zostały utworzone przez instrukcję.|  
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone podczas uruchomienia profilowania, które zostały przydzielone przez instrukcję.|  
|**Bajty wyłączne**|Liczba bajtów pamięci, które zostały przydzielone w profilowania, została przydzielona przez instrukcję.|  
|**% Bajtów wyłącznych**|Procent przydzielonych przez instrukcję wszystkich bajtów pamięci, która została przydzielona podczas uruchomienia profilowania.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)