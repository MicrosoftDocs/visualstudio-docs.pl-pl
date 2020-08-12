---
title: 'IDispatchEx:: GetNextDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144432"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Wylicza elementy członkowskie obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parametry

`grfdex`\
Określa zestaw elementów, które mają zostać wyliczone. Może to być kombinacja następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|fdexEnumDefault|Żąda, aby obiekt wyliczał elementy domyślne. Obiekt może wyliczyć dowolny zestaw elementów.|
|fdexEnumAll|Żąda, aby obiekt wyliczał wszystkie elementy. Obiekt może wyliczyć dowolny zestaw elementów.|

`id`\
Identyfikuje bieżącego członka. GetNextDispID Pobiera element w wyliczeniu. W celu uzyskania tego identyfikatora używa metody getdispid lub Previous do GetNextDispID. Używa wartości DISPID_STARTENUM do uzyskania pierwszego identyfikatora pierwszego elementu.

`pid`\
Adres zmiennej DISPID, która odbiera identyfikator następnego elementu w wyliczeniu.

Jeśli element członkowski jest usuwany przez `DeleteMemberByName` lub `DeleteMemberByDispID` , `DISPID` musi pozostać prawidłowy dla `GetNextDispID` .

## <a name="return-value"></a>Wartość zwracana

Zwraca jedną z następujących wartości:

|Wartość|Znaczenie|
|-|-|
|`S_OK`|Powodzenie.|
|`S_FALSE`|Wyliczanie zostało wykonane.|

## <a name="example"></a>Przykład

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Zobacz także

- [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)