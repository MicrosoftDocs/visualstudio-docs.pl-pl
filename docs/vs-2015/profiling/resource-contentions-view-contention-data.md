---
title: Widok Kontencji zasobów — dane rywalizacji o zasoby | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dddc9c85731137c6499e976b4b571396af297f7a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810354"
---
# <a name="resource-contentions-view---contention-data"></a>Widok rywalizacji o zasoby — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok rywalizacji o zasoby zawiera dane kontencji zasobów, które były źródłem zdarzeń rywalizacji o zasoby. Zdarzenia rywalizacji występuje, gdy funkcja w wątku musieli czekać na dostęp do zasobu, ponieważ funkcja w innym wątku uzyskał wyłączny dostęp do zasobu. Każdy zasób jest węzeł główny drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowały zdarzenia rywalizacji.  
  
## <a name="data-values"></a>Wartości danych  
  
### <a name="resource-values"></a>Wartości zasobów  
 Dane w wierszu zasobów wyświetla całkowity czas, który został zablokowany dostęp do zasobu w danych profilowania i łączna liczba zdarzeń rywalizacji o zasoby, które wystąpiły z powodu konfliktu dostępu do tego zasobu. Wartości włączne i wyłączne zasobu są zawsze takie same.  
  
### <a name="function-values"></a>Wartości funkcji  
 Wartości funkcji są oparte na wystąpieniach funkcji, które wystąpiły w ścieżce wykonywania reprezentowany w drzewie wywołań.  
  
-   Wyłączne wartości są oparte na zdarzeniach, które wystąpiły podczas wykonywania instrukcji funkcji w jego treści funkcji. Zdarzenia, które wystąpiły w funkcjach, które zostały wywołane przez funkcję nie są uwzględnione w wartości wyłączności.  
  
-   Wartości włączne opierają się na zdarzenia, które wystąpiły podczas wykonywania funkcji i funkcji wywoływanych przez funkcję.  
  
### <a name="percentage-values"></a>Wartości procentowe  
 Wartości procentowe są oparte na całkowita liczba zdarzeń w czasie lub rywalizacji o zasoby w danych profilowania. Jeśli zastosowano filtr raportu lub widoku uruchomienia profilowania, tylko czas blokowania i rywalizacji w odfiltrowane dane są używane jako wartość całkowita.  
  
## <a name="navigating-the-resource-allocation-view"></a>Nawigowanie w widoku alokacji zasobów  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa zasobu lub funkcji.|  
|**Wyłączny czas blokowania**|— Dla zasobu całkowity czas tego dostępu do zasobu został zablokowany i spowodowane wątku oczekiwania.<br />— Dla funkcji, czas, który te wystąpienia funkcji był zablokowany dostęp do zasobu nadrzędnego, podczas wykonywania kodu funkcji w treści funkcji. Czas blokowania w funkcjach, które zostały wywołane przez funkcję nie jest włączony.|  
|**% Własnego czasu blokowania**|— Dla zasobu, procent wszystkich czas blokowania w danych profilowania, która została zablokowana czas tego zasobu<br />— Dla funkcji, wartość procentowa cały czas blokowania w danych profilowania, która była wyłączny czas blokowania tych wystąpień funkcji.|  
|**Rywalizacje wyłączne**|— Dla zasobu całkowita liczba prób uzyskania dostępu do zasobu został zablokowany i spowodowała wątku oczekiwania.<br />— Dla funkcji, ile razy tych wystąpień funkcji był zablokowany dostęp do zasobu nadrzędnego, podczas wykonywania kodu funkcji w treści funkcji. Nie uwzględniono zdarzeń blokujących w funkcjach, które zostały wywołane przez funkcję.|  
|**% Rywalizacji wyłącznych**|— Dla zasobu, wartość procentowa wszystkie zdarzenia rywalizacji o zasoby w danych profilowania, które były zdarzenia rywalizacji w celu uzyskania dostępu do tego zasobu.<br />— Dla funkcji, wartość procentowa wszystkie zdarzenia rywalizacji o zasoby w danych profilowania, które były zdarzenia rywalizacji wyłącznych funkcji tych wystąpień zasobu nadrzędnego.|  
|**Całkowity czas blokowania**|— Dla zasobu całkowity czas tego dostępu do zasobu został zablokowany i spowodowane wątku oczekiwania.<br />— Dla funkcji czas, który te wystąpienia, funkcja lub wszystkie funkcje wywoływane przez wystąpienia zostały zablokowane podczas wykonywania kodu funkcji w treści funkcji, dostęp do zasobu nadrzędnego.|  
|**% Całkowitego czasu blokowania**|— Dla zasobu, procent wszystkich czas blokowania w danych profilowania, która została zablokowana czas tego zasobu<br />— W przypadku funkcji procent wszystkich czas blokowania w profilowania, był całkowity czas blokowania tych wystąpień funkcji.|  
|**Rywalizacje włączne**|— Dla zasobu całkowita liczba prób uzyskania dostępu do zasobu został zablokowany i spowodowała wątku oczekiwania.<br />— Dla funkcji wartość procentowa wszystkie zdarzenia rywalizacji o zasoby w profilowania, były zdarzenia rywalizacji (włącznie) funkcji tych wystąpień zasobu nadrzędnego.|  
|**% Rywalizacji włącznych**|— Dla zasobu wszystkie zdarzenia rywalizacji o zasoby w profilowania, wartość procentowa były zdarzenia rywalizacji w celu uzyskania dostępu do tego zasobu.<br />— Dla funkcji, ile razy tych wystąpień funkcji był zablokowany dostęp do zasobu nadrzędnego, podczas wykonywania kodu funkcji w treści funkcji. Nie uwzględniono zdarzeń blokujących w funkcjach, które zostały wywołane przez funkcję.|  
|**poziom**|Długość tej funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym wykonywania funkcji.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|



