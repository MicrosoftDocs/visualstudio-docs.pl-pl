---
title: BeginCapture | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d9ac50f2e1f5f92a16a7482a25c9054c2a36f68
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787312"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozpoczyna się interwał przechwytywania, które będą kończyć się znakiem `EndCapture`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Uwagi  
 Interwał przechwytywania zazwyczaj obejmuje to podzbiór jedną klatkę, takie jak kiedy chcesz przechwytywać informacje graficzne tylko o pewnego rodzaju wywołania rysowania. Jeśli interwał Przechwytywanie obejmuje wywołania do przedstawienia, dwóch ramek informacji graficznych są przechwytywane. Pierwsza ramka obejmuje odstęp między wywołanie `BeginCapture` , a następnie wywołać, aby przedstawić; drugi ramki obejmuje odstęp między pierwszym zdarzeniem Direct3D po wywołaniu metody do prezentowania i wywołania `EndCapture`.  
  
 Aby przechwycić interwał, należy przygotować aplikacji umożliwia przechwytywanie i rejestrowanie informacji graficznych — oznacza to, musi być wywołana [Init](../debugger/init.md) za pośrednictwem wystąpienia `VsgDbg` klasy przed wywołaniem `BeginCapture` lub `EndCapture`.  
  
## <a name="see-also"></a>Zobacz też  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



