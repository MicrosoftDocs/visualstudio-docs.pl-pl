---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570923"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Umożliwia aparatowi obsługi skryptów uzyskiwanie informacji o elemencie dodanym przy użyciu metody [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 podczas Nazwa skojarzona z elementem, jak określono w metodzie [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 podczas Maska bitów określająca, jakie informacje o elemencie powinny być zwracane. Aparat obsługi skryptów powinien zażądać minimalnej ilości informacji, ponieważ niektóre parametry powrotne (na przykład `ITypeInfo`) mogą zająć dużo czasu w celu załadowania lub wygenerowania. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Zwraca interfejs `IUnknown` dla tego elementu.|  
|SCRIPTINFO_ITYPEINFO|Zwraca interfejs `ITypeInfo` dla tego elementu.|  
  
 `ppunkItem`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `IUnknown` skojarzonego z danym elementem. Aparat skryptów może użyć metody `IUnknown::QueryInterface`, aby uzyskać interfejs `IDispatch` dla elementu. Ten parametr otrzymuje wartość NULL, jeśli `dwReturnMask` nie zawiera wartości SCRIPTINFO_IUNKNOWN. Ponadto otrzymuje wartość NULL, jeśli nie ma obiektu skojarzonego z nazwą elementu; Ten mechanizm służy do tworzenia prostej klasy, gdy nazwany element został dodany z flagą SCRIPTITEM_CODEONLY ustawioną w metodzie [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 określoną Adres zmiennej, która otrzymuje wskaźnik do interfejsu `ITypeInfo` skojarzonego z elementem. Ten parametr otrzymuje wartość NULL, jeśli `dwReturnMask` nie zawiera wartości SCRIPTINFO_ITYPEINFO lub jeśli informacje o typie nie są dostępne dla tego elementu. Jeśli informacje o typie nie są dostępne, obiekt nie może ze zdarzeniami źródłowymi, a powiązanie nazwy musi być zrealizowane przy użyciu metody `IDispatch::GetIDsOfNames`. Należy zauważyć, że pobrano interfejs `ITypeInfo` (TKIND_COCLASS), ponieważ obiekt może obsługiwać wiele interfejsów i interfejsów zdarzeń. Jeśli element obsługuje interfejs `IProvideMultipleTypeInfo`, pobrany interfejs `ITypeInfo` jest taki sam jak indeks zerowe `ITypeInfo`, który zostanie uzyskany przy użyciu metody `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Prawnego.|  
|`E_INVALIDARG`|Nieprawidłowy argument.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`TYPE_E_ELEMENTNOTFOUND`|Nie znaleziono elementu o określonej nazwie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera tylko informacje wskazane przez parametr `dwReturnMask`; zwiększa to wydajność. Na przykład jeśli interfejs `ITypeInfo` nie jest wymagany dla elementu, to po prostu nie jest określony w `dwReturnMask`.  
  
## <a name="see-also"></a>Zobacz także  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)