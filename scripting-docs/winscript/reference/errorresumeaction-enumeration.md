---
title: Wyliczenie ERRORRESUMEACTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d78852a05226f5112447dd142c06a2ba55ddba5a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090938"
---
# <a name="errorresumeaction-enumeration"></a>Wyliczenie ERRORRESUMEACTION
Opisuje sposób kontynuowania pracy po błędzie czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Ponownie wykonuje instrukcja, która wygenerowała błąd.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Umożliwia aparat języka obsłużyć błąd.|  
|ERRORRESUMEACTION_SkipErrorStatement|Wznawia działanie w kodzie następującej po instrukcji, które spowodowało błąd.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)