---
title: QueryCounters | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdd2707a6af2b9d03e73c696884dc12413437b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178270"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **QueryCounters** wyświetla listę liczników wydajności procesora CPU (sprzętu), które są dostępne na komputerze.  
  
 **QueryCounters** musi być jedyną opcją w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Gdy korzystasz z metody instrumentacji, profiler może zbierać wartości z co najmniej jednego licznika wydajności procesora CPU podczas każdego zdarzenia zbierania danych. W przypadku korzystania z metody profilowania próbkowania można określić jedno zdarzenie licznika oraz liczbę wystąpień zdarzeń, które mają być używane jako interwał próbkowania.  
  
 Różne procesory uwidaczniają różne liczniki wydajności procesora CPU. Profiler definiuje zestaw liczników ogólnych, które mogą być używane na prawie wszystkich procesorach. Opcja **QueryCounters** wyświetla nazwy ogólnych liczników i nazwy liczników, które są specyficzne dla procesora.  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
