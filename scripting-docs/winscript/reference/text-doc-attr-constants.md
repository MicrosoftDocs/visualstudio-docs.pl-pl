---
title: Stałe TEXT_DOC_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572984"
---
# <a name="text_doc_attr-constants"></a>Stała TEXT_DOC_ATTR
Opisuje atrybuty dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Stałe  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Dokument jest tylko do odczytu.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Dokument jest plikiem podstawowym tego drzewa dokumentu.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Dokument jest procesem roboczym.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Dokument jest plikiem skryptu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)