---
title: IDebugDocumentHelper::DefineScriptBlock | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2a320e4e43a983ace4decbaa68de0b1a7df7d457
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58144566"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Wskazuje do elementu pomocniczego do określonego zakresu znaków blok skryptu, który jest obsługiwany przez aparat skryptu.  
  
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
 [in] Lokalizacja początku bloku skryptu.  
  
 `cChars`  
 [in] Liczba znaków w bloku skryptu.  
  
 `pas`  
 [in] Aparat skryptów dla tego bloku skryptu.  
  
 `fScriptlet`  
 [in] Flaga wskazująca, czy za pomocą bloku skryptu scriptlet.  
  
 `pdwSourceContext`  
 [out] Kontekst źródła dla bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Jest host inteligentny użyć tej metody podczas jego dokumenty zawierają bloki osadzonych skryptów. Aparat języka użyć tej metody, gdy jego kod zawiera skrypty osadzone w innych językach.  
  
 Aparat skryptów jest odpowiedzialny za wszystkie składni kolorowanie i kod kontekstu wyszukiwań w bloku skryptu.  
  
 `DefineScriptBlock` Metoda powinna być wywoływana po dodaniu tekstu (na przykład za pomocą `IDebugDocumentHelper::AddDBCSText` metoda), ale przed skrypt przeanalizowaniu bloku (na przykład za pomocą `IActiveScriptParse ::ParseScriptText` metody).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)