---
title: IDebugDocumentTextExternalAuthor::GetPathName | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5739e7cb0cb12661ee5683051fb7b687e62dfde4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58156297"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Zwraca pełną ścieżkę i nazwę dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 [out] Ciąg zawierający pełną ścieżkę i nazwę pliku.  
  
 `pfIsOriginalFile`  
 [out] Wartość logiczna wskazująca, jeśli ścieżka i nazwa pliku można znaleźć w oryginalnym dokumencie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Plik źródłowy nie można utworzyć ani określić.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca Pełna ścieżka i nazwa pliku dokumentu.  
  
 Jeśli `pfIsOriginalFile` jest wartość FALSE, ścieżkę i nazwę pliku w `pbstrLongName` odwołuje się do nowo utworzonego pliku tymczasowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentTextExternalAuthor, interfejs](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)