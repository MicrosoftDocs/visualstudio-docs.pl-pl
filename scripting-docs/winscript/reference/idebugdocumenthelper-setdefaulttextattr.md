---
title: 'IDebugDocumentHelper:: SetDefaultTextAttr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574637"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Ustawia domyślne atrybuty do użycia dla tekstu, który nie znajduje się w bloku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `staTextAttr`  
 Domyślne atrybuty tekstu źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 O ile domyślne atrybuty nie są zmieniane przez tę metodę, atrybuty domyślne dla tekstu spoza bloku skryptu to SOURCETEXT_ATTR_NONSOURCE. Interfejs użytkownika może używać tych informacji do oznaczania tekstu poza blokami skryptów jako tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper   interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)