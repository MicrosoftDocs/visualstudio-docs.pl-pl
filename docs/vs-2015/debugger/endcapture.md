---
title: EndCapture | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3547de40190a7a591b3781d982f34378c3354044
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817558"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał przechwytywania zazwyczaj obejmuje to podzbiór jedną klatkę, takie jak kiedy chcesz przechwytywać informacje graficzne tylko o pewnego rodzaju wywołania rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do przedstawienia, dwóch ramek informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` , a następnie wywołać, aby przedstawić; drugi ramki obejmuje odstęp między pierwszym zdarzeniem Direct3D po wywołaniu metody do prezentowania i wywołania `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](../debugger/init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



