---
title: 'IDebugDocumentHost:: getPathname | Microsoft Docs'
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
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569278"
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
 określoną Ciąg zawierający długą nazwę.  
  
 `pfIsOriginalFile`  
 określoną Flaga, która ma wartość true, jeśli `pbstrLongName` odwołuje się do oryginalnego pliku dla dokumentu, w przeciwnym razie false.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można utworzyć lub określić pliku źródłowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pełną ścieżkę i nazwę pliku źródłowego dokumentu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)