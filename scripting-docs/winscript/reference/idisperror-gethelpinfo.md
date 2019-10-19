---
title: 'IDispError:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573134"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Zwraca ścieżkę pliku pomocy oraz identyfikator kontekstu tematu, który wyjaśnia błąd, jeśli jest to możliwe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 określoną Ciąg zawierający w pełni kwalifikowaną ścieżkę pliku pomocy. Jeśli nie ma pliku pomocy lub wystąpi błąd, zwracana wartość jest RÓWNa NULL.  
  
 `pdwContext`  
 określoną Identyfikator kontekstu pomocy dla błędu. Jeśli nie ma pliku pomocy (jeśli `pbstrFileName` ma wartość NULL), ten parametr nie ma znaczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Wystąpił błąd specyficzny dla dostawcy.|  
|`E_INVALIDARG`|`pbstrFileName` lub `pdwContext` mieć wartość NULL.|  
|`E_OUTOFMEMORY`|Dostawca nie może przydzielić wystarczającej ilości pamięci, w której ma zostać zwrócona ścieżka pliku pomocy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca ścieżkę pliku pomocy oraz identyfikator kontekstu tematu, który wyjaśnia błąd, jeśli jest to możliwe.  
  
> [!NOTE]
> Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz także  
 [IDispError, interfejs](../../winscript/reference/idisperror-interface.md)