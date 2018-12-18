---
title: Widok wskaźników instrukcji (IP) - dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 884e8a75b555d0cee59a708aea91f6fc83557df1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730309"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Widok wskaźników instrukcji (IP) — dane próbkowania pamięci platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok adresów IP dla platformy .NET dane alokacji pamięci profilowania zebrane przy użyciu metody próbkowania wymieniono instrukcje montażu, które pamięci przydzielonej podczas uruchomienia profilowania. Kolumny widoku Wyświetl listę, rozmiar i liczba przydziałów.  
  
 Tylko wartości wyłącznych są wyświetlane.  
  
|Kolumny|Opis|  
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
  
## <a name="see-also"></a>Zobacz też  
 [Widok wskaźników instrukcji (IP)](../profiling/instruction-pointers-ips-view-sampling-data.md)



