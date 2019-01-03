---
title: CaptureCurrentFrame | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c96a931593771e381d8f526919a5180da1eb919a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990165"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Rejestruje pozostałą część bieżącej ramki w pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli inny przechwytywania jest obecnie w toku — takich jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcji — tego przechwytywania jest zakończone i rejestrowane w dzienniku grafiki jako odrębne ramki. Natychmiast po tym dniu diagnostyki grafiki rozpoczyna się, przechwytywania w pozostałej części bieżącej ramki, który jest zarejestrowany jako odrębne ramki. Koniec bieżącej ramki jest oznaczona przez wywołanie do przedstawienia.  
  
 Aby przechwycić ramki, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Zobacz też  
 [Init](init.md)   
 [BeginCapture](begincapture.md)