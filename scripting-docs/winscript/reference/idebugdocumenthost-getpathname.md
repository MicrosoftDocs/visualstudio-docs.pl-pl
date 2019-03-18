---
title: IDebugDocumentHost::GetPathName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09e36411cdd378e78ac3bc59df5330eb8ecb47b6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160579"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Zwraca pełną ścieżkę i nazwę pliku źródłowego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 [out] Ciąg zawierający długiej nazwy.  
  
 `pfIsOriginalFile`  
 [out] Flaga oznacza to wartość true, jeśli `pbstrLongName` odwołuje się do oryginalnego pliku w dokumencie, wartość false w przeciwnym razie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Brak pliku źródłowego, można utworzyć lub określić.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pełną ścieżkę i nazwę pliku źródłowego dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)