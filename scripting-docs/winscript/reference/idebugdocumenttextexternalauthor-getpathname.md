---
title: IDebugDocumentTextExternalAuthor::GetPathName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e17d27a320eac95445c083c718f5abcebbbc46cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088845"
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