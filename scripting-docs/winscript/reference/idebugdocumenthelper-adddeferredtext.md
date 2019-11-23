---
title: 'IDebugDocumentHelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577040"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Powiadamia pomocnika, że dany tekst jest dostępny, ale nie zawiera znaków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cChars`  
 podczas Liczba znaków (Unicode) do dodania.  
  
 `dwTextStartCookie`  
 podczas Plik cookie zdefiniowany przez hosta, który reprezentuje pozycję początkową tekstu.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia hostowi odroczenie podawania znaków do dodania do momentu, gdy jest to konieczne, przez co pomocnik może generować dokładne powiadomienia i informacje o rozmiarze. `dwTextStartCookie` parametr jest plikiem cookie zdefiniowanym przez hosta, który reprezentuje pozycję początkową tekstu. Kolejne wywołania `IDebugDocumentText::GetText` muszą dostarczyć ten plik cookie. Na przykład, na hoście, który reprezentuje tekst w DBCS, plik cookie może być przesunięciem bajtów.  
  
 Przyjęto założenie, że pojedyncze wywołanie `IDebugDocumentText::GetText` może uzyskać znaki z wielu wywołań do `AddDeferredText`. Klasy pomocników mogą również żądać tego samego zakresu znaków odroczonych więcej niż raz.  
  
> [!NOTE]
> Wywołania `AddDeferredText` nie powinny być mieszane z wywołaniami `AddUnicodeText` lub `AddDBCSText`. W takim przypadku `E_FAIL` jest zwracana.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHelper  interfejsu](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)