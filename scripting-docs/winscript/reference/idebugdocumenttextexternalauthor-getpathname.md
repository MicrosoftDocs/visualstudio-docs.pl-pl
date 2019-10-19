---
title: 'IDebugDocumentTextExternalAuthor:: getPathname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575967"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Zwraca pełną ścieżkę i nazwę pliku dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 określoną Ciąg zawierający pełną ścieżkę i nazwę pliku.  
  
 `pfIsOriginalFile`  
 określoną Wartość logiczna wskazująca, czy ścieżka i nazwa pliku odwołują się do oryginalnego dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Nie można utworzyć lub określić pliku źródłowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pełną ścieżkę i nazwę pliku dokumentu.  
  
 Jeśli `pfIsOriginalFile` ma wartość FALSE, ścieżka i nazwa pliku w `pbstrLongName` odnoszą się do nowo utworzonego pliku tymczasowego.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentTextExternalAuthor, interfejs](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)