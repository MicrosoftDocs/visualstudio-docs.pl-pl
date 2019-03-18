---
title: IDispError::GetHelpInfo | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4087e77fdd87aaa012e4d09013bb92ae5835bb0d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160683"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Zwraca ścieżkę do pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli jest to możliwe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 [out] Ciąg zawierający w pełni kwalifikowaną ścieżkę pliku pomocy. Jeśli nie ma żadnego pliku pomocy lub wystąpi błąd, wartość zwracana jest wartość NULL.  
  
 `pdwContext`  
 [out] Identyfikator kontekstu pomocy dla błędu. Jeśli nie ma żadnego pliku pomocy (Jeśli `pbstrFileName` ma wartość NULL), ten parametr nie ma znaczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Wystąpił błąd specyficzny dla dostawcy.|  
|`E_INVALIDARG`|`pbstrFileName` lub `pdwContext` była równa NULL.|  
|`E_OUTOFMEMORY`|Dostawca nie może przydzielić wystarczającej ilości pamięci, w której ma zostać zwrócone ścieżkę pliku pomocy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca ścieżkę do pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli jest to możliwe.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDispError, interfejs](../../winscript/reference/idisperror-interface.md)