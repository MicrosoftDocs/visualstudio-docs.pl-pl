---
title: IDebugDocumentHelper::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576980"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Wskazuje pomocnikowi, że konkretny zakres znaków jest blokiem skryptu, który jest obsługiwany przez dany aparat skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulCharOffset`  
 podczas Lokalizacja początku bloku skryptu.  
  
 `cChars`  
 podczas Liczba znaków w bloku skryptu.  
  
 `pas`  
 podczas Aparat skryptów dla tego bloku skryptu.  
  
 `fScriptlet`  
 podczas Flaga wskazująca, czy blok skryptu jest obiektem Scriptlet.  
  
 `pdwSourceContext`  
 określoną Kontekst źródłowy bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Inteligentny host może użyć tej metody, gdy dokumenty zawierają osadzone bloki skryptu. Aparat języka może używać tej metody, gdy jej kod zawiera osadzone skrypty dla innych języków.  
  
 Aparat skryptów jest odpowiedzialny za wszystkie kolorowanie składni i wyszukiwania kontekstu kodu w bloku skryptu.  
  
 Metoda `DefineScriptBlock` powinna być wywoływana po dodaniu tekstu (na przykład przy użyciu metody `IDebugDocumentHelper::AddDBCSText`), ale przed przeanalizą bloku skryptu (na przykład przy użyciu metody `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper   interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)