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
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446911"
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
> Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDispError, interfejs](../../winscript/reference/idisperror-interface.md)