---
title: IActiveScriptAuthorProcedure::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572817"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analizuje procedurę kodu, dodaje tekst procedury kodu do aparatu tworzenia skryptów i tworzy obiekt `IScriptEntry`, który odnosi się do procedury kodu.  
  
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
 podczas Tekst skryptu do analizy.  
  
 `pszFormalParams`  
 podczas Adres formalnych nazw parametrów dla procedury. Nazwy parametrów muszą być oddzielone odpowiednimi ogranicznikami dla aparatu tworzenia skryptów. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pszProcedureName`  
 podczas Adres nazwy procedury, która ma zostać przeanalizowana.  
  
 `pszItemName`  
 podczas Adres buforu, który zawiera nazwę elementu skojarzoną z obiektem `IScriptEntry`.  
  
 `pszDelimiter`  
 podczas Adres ogranicznika bloku End-of-Script. Gdy `pszCode` jest analizowany ze strumienia tekstu, Host zwykle używa ogranicznika (takiego jak dwa znaki pojedynczego cudzysłowu) w celu wykrycia końca bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli nie ma ogranicznika, aby oznaczyć koniec bloku skryptu.  
  
 `dwCookie`  
 podczas Zdefiniowana przez aplikację wartość, która jest skojarzona z nowym obiektem `IScriptEntry`.  
  
 `dwFlags`  
 podczas Nieużywane.  
  
 `pdispFor`  
 podczas Nieużywane.  
  
## <a name="return-value"></a>Wartość zwracana  
 @No__t_0. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Bieżący aparat [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nie implementuje tej metody.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptAuthorProcedure, interfejs](../../winscript/reference/iactivescriptauthorprocedure-interface.md)