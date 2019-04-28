---
title: IScriptNode::GetLanguage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetLanguage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetLanguage
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36b7076bf7f261e462802174c6f9014403606ac8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786961"
---
# <a name="iscriptnodegetlanguage"></a>IScriptNode::GetLanguage
Zwraca język skryptów, używany przez bieżącego węzła skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 [out] Wraca "JScript", jeśli węzeł skrypt używa języka JScript lub "VBScript", jeśli węzeł skrypt używa Visual Basic Scripting Edition (VBScript).  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptNode, interfejs](../../winscript/reference/iscriptnode-interface.md)