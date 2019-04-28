---
title: Wyliczenie ERRORRESUMEACTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d92b4b2e00b25a509d29511008876d781c8a577a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955181"
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