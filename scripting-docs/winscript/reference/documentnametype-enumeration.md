---
title: Wyliczenie DOCUMENTNAMETYPE | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955220"
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
|DOCUMENTNAMETYPE_APPNODE|Pobiera nazwę, która jest wyświetlana w drzewie aplikacji.|  
|DOCUMENTNAMETYPE_TITLE|Pobiera nazwę wyświetlaną na pasku tytułu podglądu.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Pobiera nazwę pliku bez ścieżki.|  
|DOCUMENTNAMETYPE_URL|Pobiera adres URL dokumentu.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Pobiera tytuł dołączany wraz z wyliczenia do identyfikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)