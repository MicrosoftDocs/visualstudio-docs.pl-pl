---
title: BeginCapture | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 536fac55c68a7736a37961ccab2741d6b8aedd41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993185"
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna się interwał przechwytywania, które będą kończyć się znakiem `EndCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał przechwytywania zazwyczaj obejmuje to podzbiór jedną klatkę, takie jak kiedy chcesz przechwytywać informacje graficzne tylko o pewnego rodzaju wywołania rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do przedstawienia, dwóch ramek informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` , a następnie wywołać, aby przedstawić; drugi ramki obejmuje odstęp między pierwszym zdarzeniem Direct3D po wywołaniu metody do prezentowania i wywołania `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)