---
title: ERRORRESUMEACTION, Wyliczenie | Microsoft Docs
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
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575867"
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
|ERRORRESUMEACTION_ReexecuteErrorStatement|Wykonuje ponowną instrukcję, która wygenerowała błąd.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Umożliwia aparatowi języka obsłużenie błędu.|  
|ERRORRESUMEACTION_SkipErrorStatement|Wznawia wykonywanie w kodzie następującym po instrukcji, która wygenerowała błąd.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)