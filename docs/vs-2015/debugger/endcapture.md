---
title: EndCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a451746cae978f141b30fb7295a82310e04367c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197094"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zakończenie interwału przechwytywania, który został uruchomiony z `BeginCapture` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka rozciąga się między wywołaniem `BeginCapture` i wywołaniem metody. druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody i wywołaniem metody `EndCapture` .  
  
 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że [Init](../debugger/init.md) `VsgDbg` przed wywołaniem `BeginCapture` lub `EndCapture` .  
  
## <a name="see-also"></a>Zobacz też  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
