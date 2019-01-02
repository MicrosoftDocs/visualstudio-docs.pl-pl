---
title: QueryCounters | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9a4e3c9f80ed437eb4476833776c5c19689c69a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866923"
---
# <a name="querycounters"></a>QueryCounters
**QueryCounters** opcji Wyświetla liczniki wydajności procesora CPU (sprzęt), które są dostępne na komputerze.  
  
 **QueryCounters** musi być jedyną opcją, w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z metody instrumentacji, program profilujący może zbierać wartości co najmniej jeden liczniki wydajności procesora CPU w poszczególnych zdarzeń zbierania danych. Gdy używana jest metoda profilowania próbkowanie, można określić jedno zdarzenie licznika i liczbę wystąpień zdarzeń ma być używany jako interwał próbkowania.  
  
 Różnych procesorów ujawnić różne liczniki wydajności procesora CPU. Program profilujący definiuje zestaw ogólnych liczniki, które mogą być używane na prawie wszystkie procesory w systemie. **QueryCounters** opcja list zarówno nazwy liczników ogólny i nazwy liczników, które są specyficzne dla procesora.  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)