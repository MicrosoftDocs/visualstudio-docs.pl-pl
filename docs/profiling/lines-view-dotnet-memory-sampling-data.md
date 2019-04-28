---
title: Widok linii — dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c654bbcc9db696d78e651414bfa89d6ad1e2f3e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000070"
---
# <a name="lines-view---net-memory-sampling-data"></a>Widok linii — dane próbkowania pamięci platformy .NET
Widok linii dla platformy .NET dane alokacji pamięci profilowania, która używa metody pobierania próbek Wyświetla listę instrukcji, które pamięci przydzielonej podczas uruchomienia profilowania. Kolumny także rozmiar i liczba przydziałów.

 W pliku źródłowym instrukcji może obejmować więcej niż jeden wiersz w pliku źródłowym, a jeden wiersz może zawierać więcej niż jedną instrukcję.

 Instrukcja jest identyfikowane przez następujące elementy:

- Plik źródłowy, który zawiera deklarację funkcji.

- Funkcja, która zawiera instrukcję.

- Wiersza źródłowego, w którym rozpoczyna się wykonywanie instrukcji.

- Znak w wierszu źródłowym, w którym rozpoczyna się wykonywanie instrukcji.

- Wiersza źródłowego, w którym kończy się instrukcji.

- Znak w wierszu źródłowym, w którym kończy się instrukcji.

  Kolumna Nazwa wiersza zawiera wzorzec sortowalnej łączenia danych identyfikator.

  Zgodnie z definicją instrukcja wywołuje inne funkcje. W związku z tym są wyświetlane tylko wyłączne wartości.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera deklarację.|
|**Nazwa funkcji**|Nazwa funkcji, która zawiera instrukcję.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres początkowy funkcji.|
|**Początkowy wiersz w źródle**|Numer wiersza początkowego w pliku źródłowym, w którym wystąpiła Alokacja.|
|**Końcowy wiersz w źródle**|Końcowy numer wiersza w pliku źródłowym, w którym wystąpiła Alokacja.|
|**Początkowy znak w źródle**|Przesunięcie początkowy znak w wierszu pliku źródłowego, w którym wystąpiła Alokacja.|
|**Końcowy znak w źródle**|Przesunięcie końcowy znak w wierszu pliku źródłowego, w którym wystąpiła Alokacja.|
|**Nazwa wiersza**|Generowane przez program profilujący identyfikator wiersza przy użyciu następującej składni:`Source File`**; [**  `Line Number Start` **,**`Character Start`**] ->; [** `Line Number Start,Character Start`**]**|
|**Przydziały wyłączne**|Całkowita liczba obiektów, które zostały utworzone w tym wierszu.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone podczas uruchomienia profilowania, przydzielonych w taki sposób, w tym wierszu.|
|**Bajty wyłączne**|Procent przydzielonych w taki sposób, w tym wierszu wszystkich bajtów pamięci, która została przydzielona podczas uruchomienia profilowania.|
|**% Bajtów wyłącznych**|Procent przydzielonych w taki sposób, w tym wierszu wszystkich bajtów pamięci, która została przydzielona podczas uruchomienia profilowania.|

## <a name="see-also"></a>Zobacz także
- [Widok linii](../profiling/lines-view-sampling-data.md)