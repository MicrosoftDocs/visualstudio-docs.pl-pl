---
title: DOCUMENTNAMETYPE, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575874"
---
# <a name="documentnametype-enumeration"></a>Wyliczenie DOCUMENTNAMETYPE
Wskazuje, który typ ma zostać pobrany dla dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Pobiera nazwę wyświetlaną w drzewie aplikacji.|  
|DOCUMENTNAMETYPE_TITLE|Pobiera nazwę, która pojawia się na pasku tytułu przeglądarki.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Pobiera nazwę pliku bez ścieżki.|  
|DOCUMENTNAMETYPE_URL|Pobiera adres URL dokumentu.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Pobiera tytuł dołączany z wyliczeniem do identyfikacji.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)