---
title: 'IDebugDocumentHost:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569427"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Zwraca zakres znaków, które zostały dodane przy użyciu metody `IDebugDocumentHelper::AddDeferredText` w oryginalnym dokumencie hosta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwTextStartCookie`  
 podczas Plik cookie zdefiniowany przez hosta, który reprezentuje pozycję początkową tekstu.  
  
 `pcharText`  
 [in. out] Bufor tekstowy znaku. Ta metoda nie zwraca znaków, jeśli ten parametr jest `NULL`.  
  
 `pstaTextAttr`  
 [in. out] Bufor atrybutu znaku. Ta metoda nie zwraca atrybutów, jeśli ten parametr jest `NULL`.  
  
 `pcNumChars`  
 [in. out] Wskazuje rzeczywistą liczbę zwracanych znaków/atrybutów. Ten parametr musi być ustawiony na wartość zero przed wywołaniem tej metody.  
  
 `cMaxChars`  
 podczas Maksymalna liczba znaków do zwrócenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może zwracać `E_NOTIMPL`, Jeśli host nie wywoła `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Ta metoda zwraca tekst z oryginalnego dokumentu. Host nie śledzi edycji ani innych zmian w dokumencie.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHost   interfejsu](../../winscript/reference/idebugdocumenthost-interface.md)  
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)