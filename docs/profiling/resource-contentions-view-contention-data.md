---
title: Widok rywalizacji o zasoby — dane rywalizacji | Microsoft Docs
description: Dowiedz się, w jaki sposób widok rywalizacji o zasoby wyświetla listę zawartości dla zasobów, które były źródłem zdarzeń rywalizacji.
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
ms.openlocfilehash: fc8e6c39efea24ac8a4a493099f3bcdb39dc4fe6
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720348"
---
# <a name="resource-contentions-view---contention-data"></a>Widok rywalizacji o zasoby — dane rywalizacji
Widok rywalizacji o zasoby zawiera listę danych dotyczących zawartości dla zasobów, które były źródłem zdarzeń rywalizacji. Zdarzenie rywalizacji występuje, gdy funkcja w wątku jest zmuszona do oczekiwania na dostęp do zasobu, ponieważ funkcja w innym wątku uzyskała wyłączny dostęp do zasobu. Każdy zasób jest węzłem głównym drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowały zdarzenia rywalizacji.

## <a name="data-values"></a>Wartości danych

### <a name="resource-values"></a>Wartości zasobów
 Dane w wierszu zasobu przedstawiają łączny czas dostępu do zasobu w danych profilowania oraz łączną liczbę zdarzeń rywalizacji, które wystąpiły z powodu konfliktu dostępu do tego zasobu. Wartości włączne i wyłączne dla zasobu są zawsze takie same.

### <a name="function-values"></a>Wartości funkcji
 Wartości funkcji są oparte na wystąpieniach funkcji, które wystąpiły w ścieżce wykonywania reprezentowanej w drzewie wywołań.

- Wartości wyłączne opierają się na zdarzeniach, które wystąpiły, gdy funkcja wykonywała instrukcje w jego treści funkcji. Zdarzenia, które wystąpiły w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane w wartościach wyłącznych.

- Wartości włączne bazują na zdarzeniach, które wystąpiły podczas wykonywania funkcji lub funkcji wywołanej przez funkcję.

### <a name="percentage-values"></a>Wartości procentowe
 Wartości procentowe są zależne od łącznego czasu lub zdarzeń rywalizacji w danych profilowania. Jeśli raport lub widok przebiegu profilowania jest filtrowany, jako łączną wartość są używane tylko zablokowane czas i rywalizacje w odniesieniu do danych.

## <a name="navigating-the-resource-allocation-view"></a>Nawigowanie w widoku alokacja zasobów

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa zasobu lub funkcji.|
|**Wyłączny czas blokowania**|-Dla zasobu łączny czas, w którym dostęp do zasobu został zablokowany i spowodował oczekiwanie wątku.<br />-Dla funkcji — czas, w którym te wystąpienia funkcji były blokowane dostęp do zasobu nadrzędnego, gdy funkcja wykonywała kod w treści funkcji. Zablokowany czas w funkcjach, które zostały wywołane przez funkcję, nie jest uwzględniany.|
|**% Wyłącznego czasu blokowania**|-Dla zasobu procent całego zablokowanego czasu w danych profilowania, który miał zablokowany czas tego zasobu<br />-Dla funkcji, procent całego zablokowanego czasu w danych profilowania, który miał wyłączny czas blokowania tych wystąpień funkcji.|
|**Rywalizacje wyłączne**|-Dla zasobu całkowita liczba przypadków, w których dostęp do zasobu został zablokowany i spowodował oczekiwanie wątku.<br />-Dla funkcji, liczba przypadków, w których te wystąpienia funkcji były blokowane dostęp do zasobu nadrzędnego, gdy funkcja wykonywała kod w treści funkcji. Blokowanie zdarzeń w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane.|
|**Zawartość wyłącznych%**|-Dla zasobu procent wszystkich zdarzeń rywalizacji w danych profilowania, które były zdarzeniami rywalizacji o dostęp do tego zasobu.<br />-Dla funkcji, procent wszystkich zdarzeń rywalizacji w danych profilowania, które były zdarzeniami wyłącznych rywalizacji o te wystąpienia funkcji dla zasobu nadrzędnego.|
|**Włączny czas blokowania**|-Dla zasobu łączny czas, w którym dostęp do zasobu został zablokowany i spowodował oczekiwanie wątku.<br />-Dla funkcji, czas, przez jaki wystąpienia funkcji lub wszelkich funkcji wywoływanych przez wystąpienia, miały zablokowany dostęp do zasobu nadrzędnego, gdy funkcja wykonywała kod w treści funkcji.|
|**% Włącznego czasu blokowania**|-Dla zasobu procent całego zablokowanego czasu w danych profilowania, który miał zablokowany czas tego zasobu<br />-Dla funkcji — wartość procentowa całego zablokowanego czasu w przebiegu profilowania, która została włącznie z zablokowanym czasem blokowania tych wystąpień funkcji.|
|**Rywalizacje włączne**|-Dla zasobu całkowita liczba przypadków, w których dostęp do zasobu został zablokowany i spowodował oczekiwanie wątku.<br />-Dla funkcji, procent wszystkich zdarzeń rywalizacji w przebiegu profilowania, które były włącznie zdarzenia rywalizacji o te wystąpienia funkcji dla zasobu nadrzędnego.|
|**% Rywalizacji włącznych**|-Dla zasobu procent wszystkich zdarzeń rywalizacji w przebiegu profilowania, który miał zdarzenia rywalizacji o dostęp do tego zasobu.<br />-Dla funkcji, liczba przypadków, w których te wystąpienia funkcji były blokowane dostęp do zasobu nadrzędnego, gdy funkcja wykonywała kod w treści funkcji. Blokowanie zdarzeń w funkcjach, które zostały wywołane przez funkcję, nie są uwzględniane.|
|**Poziomie**|Głębokość tej funkcji w drzewie wywołań. Tylko w raportach wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) .|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Nazwa modułu**|Nazwa modułu, który zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, który zawiera funkcję.|
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym uruchomiono funkcję.|
|**Nazwa procesu**|Nazwa procesu|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
