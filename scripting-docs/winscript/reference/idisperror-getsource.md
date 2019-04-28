---
title: IDispError::GetSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a84640f020a1ff255b8c7e5dd753752e0d310a7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446885"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Zwraca identyfikator programowy zależne od języka dla klasy lub aplikacji, który spowodował błąd.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrSource`  
 [out] Ciąg, który zawiera identyfikator programowy, w postaci `progname.objectname`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana do określenia klasy lub aplikacji, w którym wystąpił wyjątek. Identyfikator programowy mogą być zwracane w języku określonym przez podany w momencie wywołania identyfikator ustawień regionalnych (LCID).  
  
> [!NOTE]
> Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [IDispError, interfejs](../../winscript/reference/idisperror-interface.md)