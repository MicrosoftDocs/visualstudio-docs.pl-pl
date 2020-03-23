---
title: Widok rywalizacji o zasoby — dane rywalizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1607e594b6456d4da4396069d589160230b39680
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778339"
---
# <a name="resource-contentions-view---contention-data"></a>Widok rywalizacji o zasoby — dane rywalizacji
Widok Rywalizacja o zasoby zawiera listę danych rywalizacji dla zasobów, które były źródłem zdarzeń rywalizacji. Zdarzenie rywalizacji występuje, gdy funkcja w wątku jest zmuszony czekać na dostęp do zasobu, ponieważ funkcja w innym wątku uzyskała wyłączny dostęp do zasobu. Każdy zasób jest węzłem głównym drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowało zdarzenia rywalizacji.

## <a name="data-values"></a>Wartości danych

### <a name="resource-values"></a>Wartości zasobów
 Dane w wierszu zasobu wyświetla całkowity czas, że dostęp do zasobu został zablokowany w danych profilowania i całkowita liczba zdarzeń rywalizacji, które wystąpiły z powodu konfliktu dostępu do tego zasobu. Wartości włączające i wyłączne dla zasobu są zawsze takie same.

### <a name="function-values"></a>Wartości funkcji
 Wartości funkcji są oparte na wystąpieniach funkcji, które wystąpiły w ścieżce wykonywania reprezentowanej w drzewie wywołań.

- Wartości wyłączne są oparte na zdarzeniach, które wystąpiły podczas wykonywania przez funkcję instrukcji w treści funkcji. Zdarzenia, które wystąpiły w funkcjach, które były wywoływane przez funkcję, nie są uwzględniane w wartościach wyłączności.

- Wartości włącznie są oparte na zdarzeniach, które wystąpiły podczas wykonywania funkcji lub funkcji wywoływanych przez funkcję.

### <a name="percentage-values"></a>Wartości procentowe
 Wartości procentowe są oparte na całkowitym czasie lub zdarzeniach rywalizacji w danych profilowania. Jeśli raport lub widok przebiegu profilowania jest filtrowany, jako wartość całkowitą jest używany tylko zablokowany czas i rywalizacje w filtrowanych danych.

## <a name="navigating-the-resource-allocation-view"></a>Poruszanie się po widoku alokacji zasobów

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa zasobu lub funkcji.|
|**Ekskluzywny zablokowany czas**|- Dla zasobu całkowity czas, że dostęp do zasobu został zablokowany i spowodował wątek czekać.<br />- Dla funkcji, czas, że te wystąpienia funkcji zostały zablokowane dostęp do zasobu nadrzędnego, gdy funkcja była wykonywanie kodu w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję nie jest uwzględniony.|
|**Ekskluzywny zablokowany czas %**|- W przypadku zasobu procent wszystkich zablokowanych czasów w danych profilowania, który został zablokowany przez czas tego zasobu<br />- Dla funkcji procent wszystkich zablokowany czas w danych profilowania, który był wyłączny zablokowany czas tych wystąpień funkcji.|
|**Ekskluzywne twierdzenia**|- Dla zasobu całkowita liczba razy, że dostęp do zasobu został zablokowany i spowodował wątek czekać.<br />- Dla funkcji, ile razy te wystąpienia funkcji zostały zablokowane dostęp do zasobu nadrzędnego, gdy funkcja była wykonywanie kodu w treści funkcji. Blokowanie zdarzeń w funkcjach, które były wywoływane przez funkcję nie są uwzględniane.|
|**Ekskluzywne rywalizacje %**|- Dla zasobu procent wszystkich zdarzeń rywalizacji w danych profilowania, które były zdarzenia rywalizacji o dostęp do tego zasobu.<br />- Dla funkcji procent wszystkich zdarzeń rywalizacji w danych profilowania, które były wyłączne zdarzenia rywalizacji tych wystąpień funkcji dla zasobu nadrzędnego.|
|**Włącznie zablokowany czas**|- Dla zasobu całkowity czas, że dostęp do zasobu został zablokowany i spowodował wątek czekać.<br />- Dla funkcji czas, że te wystąpienia funkcji lub żadnych funkcji wywoływanych przez wystąpienia zostały zablokowane dostęp do zasobu nadrzędnego, gdy funkcja była wykonywanie kodu w treści funkcji.|
|**Włącznie zablokowany czas %**|- W przypadku zasobu procent wszystkich zablokowanych czasów w danych profilowania, który został zablokowany przez czas tego zasobu<br />- Dla funkcji procent wszystkich zablokowany czas w przebiegu profilowania, który był włącznie zablokowany czas tych wystąpień funkcji.|
|**Rywalizacje włączające**|- Dla zasobu całkowita liczba razy, że dostęp do zasobu został zablokowany i spowodował wątek czekać.<br />- Dla funkcji procent wszystkich zdarzeń rywalizacji w przebiegu profilowania, które były zdarzeniami rywalizacji włączającej tych wystąpień funkcji dla zasobu nadrzędnego.|
|**Rywalizacja włączająca %**|- Dla zasobu procent wszystkich zdarzeń rywalizacji w przebiegu profilowania, które były zdarzeniami rywalizacji o dostęp do tego zasobu.<br />- Dla funkcji, ile razy te wystąpienia funkcji zostały zablokowane dostęp do zasobu nadrzędnego, gdy funkcja była wykonywanie kodu w treści funkcji. Blokowanie zdarzeń w funkcjach, które były wywoływane przez funkcję nie są uwzględniane.|
|**Poziom**|Głębokość tej funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md)|
|**Numer wiersza funkcyjnego**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym funkcja była wykonywana.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy zawierający definicję tej funkcji.|
