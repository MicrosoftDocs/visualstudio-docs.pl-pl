---
title: IDebugDocumentHelper::AddDeferredText | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b2f2a7c134142668613cc38cee9357e42cb95096
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433939"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Powiadamia pomocnika, że dany tekst jest dostępna, ale nie zawiera znaków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cChars`  
 [in] Liczba znaków (Unicode), aby dodać.  
  
 `dwTextStartCookie`  
 [in] Zdefiniowane przez hosta pliku cookie, który reprezentuje pozycję początkową tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia hosta, które mają być odroczone, zapewniając znaków, które można dodać, dopóki nie są potrzebne, zapewniając pomocnika do generowania powiadomień dokładne i informacje o rozmiarze. `dwTextStartCookie` Parametr jest plik cookie, zdefiniowane przez hosta, który reprezentuje pozycję początkową tekstu. Kolejne wywołania `IDebugDocumentText::GetText` należy podać ten plik cookie. Na przykład na hoście, który reprezentuje tekst w znaków Dwubajtowych, plik cookie może być przesunięcie bajtu.  
  
 Zakłada się, że pojedyncze wywołanie `IDebugDocumentText::GetText` można uzyskać znaki z wielu wywołań `AddDeferredText`. Klasy pomocnika może również poprosić o tego samego zakresu znaków odroczonego więcej niż jeden raz.  
  
> [!NOTE]
> Wywołania `AddDeferredText` nie powinny się łączyć z wywołaniami dotyczącymi `AddUnicodeText` lub `AddDBCSText`. W takim przypadku `E_FAIL` jest zwracana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)