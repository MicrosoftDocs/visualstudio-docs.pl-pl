---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6870f3b19c5727fdbea0418b8373b990cb671a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955085"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analizuje tekst skryptu, dodaje tekst do skryptu tworzenia aparatu i tworzy `IScriptEntry` obiekt, który odnosi się do bloku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in] Tekst skryptu można przeanalizować.  
  
 `pszItemName`  
 [in] Adres buforu, który zawiera nazwę elementu skojarzonego z blokiem skryptu.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Gdy `pszCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), na końcu bloku skryptu do wykrywania. Ustaw ten parametr na wartość NULL, jeśli nie było ogranicznika do identyfikowania koniec bloku skryptu.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartość skojarzoną z nowymi `IScriptEntry` obiektu.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptAuthor, interfejs](../../winscript/reference/iactivescriptauthor-interface.md)