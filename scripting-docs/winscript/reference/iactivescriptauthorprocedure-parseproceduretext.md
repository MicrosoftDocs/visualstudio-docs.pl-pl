---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149383"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizuje kod procedury, dodaje tekst procedury kodu do skryptu tworzenia aparatu i tworzy `IScriptEntry` obiekt, który odnosi się do procedury kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in] Tekst skryptu można przeanalizować.  
  
 `pszFormalParams`  
 [in] Adres nazwy parametrów formalnych w procedurze. Nazwy parametrów muszą być rozdzielone odpowiednie ograniczniki skryptu tworzenia aparatu. Nazwy nie powinna zostać ujęta w nawiasy.  
  
 `pszProcedureName`  
 [in] Adres nazwa procedury, która ma być analizowany.  
  
 `pszItemName`  
 [in] Skojarzony adres buforu, który zawiera nazwę elementu `IScriptEntry` obiektu.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Gdy `pszCode` jest analizowany ze strumienia tekstu, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), na końcu bloku skryptu do wykrywania. Ustaw ten parametr na wartość NULL, jeśli nie było ogranicznika do oznaczenia końca bloku skryptu.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartość skojarzoną z nowymi `IScriptEntry` obiektu.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
 `pdispFor`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Bieżący [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparat nie obsługuje tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptAuthorProcedure, interfejs](../../winscript/reference/iactivescriptauthorprocedure-interface.md)