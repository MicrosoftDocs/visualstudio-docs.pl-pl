---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754925"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli inny przechwytywania jest obecnie w toku — takich jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcji — tego przechwytywania jest zakończone i rejestrowane w dzienniku grafiki jako odrębne ramki. Natychmiast po tym dniu diagnostyki grafiki rozpoczyna się, przechwytywania w pozostałej części bieżącej ramki, który jest zarejestrowany jako odrębne ramki. Koniec bieżącej ramki jest oznaczona przez wywołanie do przedstawienia.  
  
 Aby przechwycić ramki, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](../debugger/init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
