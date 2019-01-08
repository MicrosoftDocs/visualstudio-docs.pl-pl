---
title: Wyliczenie DOCUMENTNAMETYPE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094773"
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