---
title: Widok wierszy | Microsoft Docs
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
ms.openlocfilehash: ccdb211312a6f53e7f519b7fac0e3ac28aab2429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145628"
---
# <a name="lines-view"></a>Widok linii
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok linie jest dostępny tylko dla danych profilera, które zostały zebrane przy użyciu metody próbkowania. Widok nie jest dostępny dla danych, które zostały zebrane przy użyciu instrumentacji.  
  
 W przypadku danych profilu próbkowania widok wierszy identyfikuje instrukcję w funkcji, która była wykonywana bezpośrednio podczas zbierania próbki. W przypadku danych pamięci .NET Widok wiersze identyfikuje instrukcje, które przydzielą pamięć.  
  
 W pliku źródłowym instrukcja może obejmować więcej niż jeden wiersz w pliku źródłowym, a pojedynczy wiersz może zawierać więcej niż jedną instrukcję.  
  
 Instrukcja jest identyfikowana przez następujące elementy:  
  
- Plik źródłowy, który zawiera instrukcję Function.  
  
- Funkcja, która zawiera instrukcję.  
  
- Wiersz źródłowy, w którym rozpocznie się wykonywanie instrukcji.  
  
- Znak w wierszu źródłowym, w którym rozpocznie się wykonywanie instrukcji.  
  
- Wiersz źródłowy, w którym zostanie zakończona instrukcja.  
  
- Znak w wierszu źródłowym, w którym następuje zakończenie instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok linii](../profiling/lines-view-sampling-data.md)   
 [Widok linii — próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Widok linii](../profiling/lines-view-contention-data.md)
