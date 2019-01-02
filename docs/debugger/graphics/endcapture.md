---
title: EndCapture | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 320898ad028015085448b706e4962ae4050d8b2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950624"
---
# <a name="endcapture"></a>EndCapture
Kończy się interwał przechwytywania, który został uruchomiony z `BeginCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał przechwytywania zazwyczaj obejmuje to podzbiór jedną klatkę, takie jak kiedy chcesz przechwytywać informacje graficzne tylko o pewnego rodzaju wywołania rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do przedstawienia, dwóch ramek informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` , a następnie wywołać, aby przedstawić; drugi ramki obejmuje odstęp między pierwszym zdarzeniem Direct3D po wywołaniu metody do prezentowania i wywołania `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)