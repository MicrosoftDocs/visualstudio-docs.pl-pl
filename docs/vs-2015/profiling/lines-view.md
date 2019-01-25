---
title: Widok linii | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e27194d830e880fd9ae28065e69fa140d9201dc2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54762016"
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
