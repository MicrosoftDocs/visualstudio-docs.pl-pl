---
title: QueryCounters | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f5bedfd794dc7666240b1657cbdc4125b46708b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809286"
---
# <a name="querycounters"></a>QueryCounters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**QueryCounters** opcji Wyświetla liczniki wydajności procesora CPU (sprzęt), które są dostępne na komputerze.  
  
 **QueryCounters** musi być jedyną opcją, w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak  
  
## <a name="remarks"></a>Uwagi  
 Korzystając z metody instrumentacji, program profilujący może zbierać wartości co najmniej jeden liczniki wydajności procesora CPU w poszczególnych zdarzeń zbierania danych. Gdy używana jest metoda profilowania próbkowanie, można określić jedno zdarzenie licznika i liczbę wystąpień zdarzeń ma być używany jako interwał próbkowania.  
  
 Różnych procesorów ujawnić różne liczniki wydajności procesora CPU. Program profilujący definiuje zestaw ogólnych liczniki, które mogą być używane na prawie wszystkie procesory w systemie. **QueryCounters** opcja list zarówno nazwy liczników ogólny i nazwy liczników, które są specyficzne dla procesora.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



