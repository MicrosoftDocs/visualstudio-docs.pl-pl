---
title: IDebugDocumentHost::GetDeferredText | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446570"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Zwraca szeroką gamę znaków, które zostały dodane za pomocą `IDebugDocumentHelper::AddDeferredText` metody w oryginalnym dokumencie hosta.  
  
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
 [in] Zdefiniowane przez hosta pliku cookie, który reprezentuje pozycję początkową tekstu.  
  
 `pcharText`  
 [out w] Bufor tekstowy znaków. Ta metoda nie zwraca znaki, jeśli ten parametr jest `NULL`.  
  
 `pstaTextAttr`  
 [out w] Buforu atrybut znaków. Ta metoda nie zwraca atrybuty, jeśli ten parametr jest `NULL`.  
  
 `pcNumChars`  
 [out w] Wskazuje rzeczywistą liczbę znaków i atrybuty zwracane. Ten parametr musi być równa zero przed wywołaniem tej metody.  
  
 `cMaxChars`  
 [in] Maksymalna liczba znaków do zwrócenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może zwrócić `E_NOTIMPL`, jeśli host nie mogą wywoływać `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Ta metoda zwraca tekst z oryginalnego dokumentu. Host nie zachować informacje o edycji lub innych zmian w dokumencie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR, wyliczenie](../../winscript/reference/source-text-attr-enumeration.md)