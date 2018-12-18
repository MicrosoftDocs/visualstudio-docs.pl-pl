---
title: Stackframetypeenum — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de80fd054459556e273427b666175751ced203fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740372"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa typ ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Elementy  
 `FrameTypeFPO`  
 Wskaźnik ramki pominięta; FPO informacji.  
  
 `FrameTypeTrap`  
 Ramka pułapki jądra.  
  
 `FrameTypeTSS`  
 Ramka pułapki jądra.  
  
 `FrameTypeStandard`  
 Standardowa EBP ramki stosu.  
  
 `FrameTypeFrameData`  
 Wskaźnik ramki pominięta; Ramka danych informacji.  
  
 `FrameTypeUnknown`  
 Ramki, który nie ma żadnych informacji o debugowaniu.  
  
## <a name="remarks"></a>Uwagi  
 Wartości w tym wyliczeniu są zwracane przez wywołanie [idiastackframe::get_type —](../../debugger/debug-interface-access/idiastackframe-get-type.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: cvconst.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia i struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



