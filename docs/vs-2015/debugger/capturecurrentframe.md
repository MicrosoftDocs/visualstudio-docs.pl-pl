---
title: CaptureCurrentFrame | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161630"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przechwytuje resztę bieżącej ramki do pliku dziennika grafiki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli trwa wykonywanie innego przechwytywania, takiego jak przechwytywanie, które zostało uruchomione przez `BeginCapture` funkcję — to przechwycenie zostanie zakończone i zarejestrowane w dzienniku grafiki jako odrębna ramka. Natychmiast po wykonaniu tej czynności Diagnostyka grafiki rozpocznie przechwytywanie reszty bieżącej ramki, która jest również rejestrowana jako odrębna ramka. Zakończenie bieżącej ramki jest oznaczone przez wywołanie do prezentacji.  
  
 Aby przechwycić ramkę, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że przed wywołaniem należy wywołać [init](../debugger/init.md) za pomocą wystąpienia `VsgDbg` klasy `CaptureCurrentFrame` .  
  
## <a name="see-also"></a>Zobacz też  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
