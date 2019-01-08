---
title: IActiveScriptSite::GetItemInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f4dc6515d64406870ca10f003d7cea515c49b7d8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095891"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Umożliwia silnik wykonywania skryptów uzyskać informacje na temat elementu, który został dodany z [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
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
 [in] Nazwa skojarzona z elementu, jak to określono w [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
 `dwReturnMask`  
 [in] Maska bitów, określania, jakie informacje o elemencie ma zostać zwrócony. Silnik wykonywania skryptów należy zażądać minimalną ilość informacji możliwe, ponieważ niektóre zwracane parametry (na przykład `ITypeInfo`) może zająć znaczną ilość czasu do załadowania lub wygenerować. Może być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Zwraca `IUnknown` interfejsu dla tego elementu.|  
|SCRIPTINFO_ITYPEINFO|Zwraca `ITypeInfo` interfejsu dla tego elementu.|  
  
 `ppunkItem`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IUnknown` interfejsu skojarzonego z danym elementem. Aparat skryptów można użyć `IUnknown::QueryInterface` metodę, aby uzyskać `IDispatch` interfejs dla elementu. Ten parametr otrzymuje wartość NULL, jeśli `dwReturnMask` nie zawiera wartości SCRIPTINFO_IUNKNOWN. Ponadto otrzymuje wartość NULL Jeśli nie ma obiektu skojarzone z nazwą elementu; Ten mechanizm jest używany do tworzenia klasą prostą, gdy element o nazwie została dodana z flagą SCRIPTITEM_CODEONLY w [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.  
  
 `ppTypeInfo`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `ITypeInfo` interfejsu skojarzonego z elementem. Ten parametr otrzymuje wartość NULL, jeśli `dwReturnMask` nie zawiera wartości SCRIPTINFO_ITYPEINFO, lub jeśli informacje o typie nie jest dostępna dla tego elementu. Jeśli nie ma informacji o typie, obiekt nie źródeł zdarzeń i powiązania nazwy musi być realizowany przy użyciu `IDispatch::GetIDsOfNames` metody. Należy pamiętać, że `ITypeInfo` interfejsu, pobrać w tym artykule opisano coclass elementu (TKIND_COCLASS), ponieważ obiekt może obsługiwać wielu interfejsach i zdarzeń. Jeśli element obsługuje `IProvideMultipleTypeInfo` interfejsu, `ITypeInfo` interfejsu pobierana jest taka sama jak indeks zero `ITypeInfo` , będzie można uzyskać przy użyciu `IProvideMultipleTypeInfo::GetInfoOfIndex` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument ten był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`TYPE_E_ELEMENTNOTFOUND`|Nie można odnaleźć elementu o określonej nazwie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera tylko te informacje, które są wskazywane przez `dwReturnMask` parameter; poprawia to wydajność. Na przykład jeśli `ITypeInfo` interfejsu nie jest wymagany dla elementu, po prostu nie określono w `dwReturnMask`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)