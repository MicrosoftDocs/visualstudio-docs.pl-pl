---
title: Widok linii | Dokumentacja firmy Microsoft
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
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 829db9b1f8e4826ea9761a4433e6ee1adaab49e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749980"
---
# <a name="lines-view"></a>Widok linii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok linii jest dostępna tylko dla danych profilera, które zostały zebrane przy użyciu metody próbkowania. Widok nie jest dostępna dla danych, które zostały zebrane przy użyciu Instrumentacji.  
  
 Dla pobierania próbek danych profilowych, widok linii identyfikuje instrukcji w funkcji, która bezpośrednio był wykonywany, gdy zostały zebrane próbki. W przypadku danych pamięci .NET widok linii określa instrukcje, które przydzielić pamięci.  
  
 W pliku źródłowym instrukcji może obejmować więcej tego wiersza w pliku źródłowym, a jeden wiersz może zawierać więcej niż jedną instrukcję.  
  
 Instrukcja jest identyfikowane przez następujące elementy:  
  
-   Plik źródłowy, który zawiera deklarację funkcji.  
  
-   Funkcja, która zawiera instrukcję.  
  
-   Wiersza źródłowego, w którym rozpoczyna się wykonywanie instrukcji.  
  
-   Znak w wierszu źródłowym, w którym rozpoczyna się wykonywanie instrukcji.  
  
-   Wiersza źródłowego, w którym kończy się instrukcji.  
  
-   Znak w wierszu źródłowym, w którym kończy się instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok linii](../profiling/lines-view-sampling-data.md)   
 [Widok linii - próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Widok linii](../profiling/lines-view-contention-data.md)



