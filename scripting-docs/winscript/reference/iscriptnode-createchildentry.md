---
title: 'IScriptNode:: CreateChildEntry | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75369df719b0cd140ce621e916215eb18cf30a9e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58156661"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Dodaje wystąpienie podrzędnych `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartości używane do kojarzenia wpis podrzędnych za pomocą obiektu hosta.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Do analizowania, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), aby wykrywać koniec bloku skryptu.  
  
 Ogranicznik umożliwia skryptu tworzenia aparatu, aby zapewnić przetwarzania wstępnego. Na przykład aparat może zastąpić znak pojedynczego cudzysłowu dwa znaki pojedynczego cudzysłowu jako ogranicznika. Aparat określa sposób korzystania z ogranicznikiem.  
  
 Wartość NULL, jeśli ogranicznika nie są oznaczane koniec bloku skryptu.  
  
 `ppse`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptEntry` interfejsu, wystąpienia podrzędne.  
  
 Aby uzyskać `IScriptNode` obiektów, które reprezentują strony sieci Web, ten parametr zwraca `IScriptEntry` wystąpienia, która określa Blok skryptu.  
  
 Aby uzyskać `IScriptEntry` obiektów, które reprezentują blok skryptu, ten parametr zwraca `IScriptEntry` wystąpienia, która określa obiekt funkcyjny.  
  
 Aby uzyskać `IScriptEntry` obiektu obiektami, które reprezentują funkcję, ta metoda nie powiedzie się.  
  
 Aby uzyskać `IScriptScriptlet` obiektów, ta metoda nie powiedzie się.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `IScriptNode` Interfejs reprezentuje strony sieci Web lub jej elementów. `IScriptEntry` Interfejsu (który jest tworzony na podstawie `IScriptNode`) reprezentuje blok skryptu lub obiekt funkcyjny. `IScriptScriptlet` Interfejsu (który jest tworzony na podstawie `IScriptEntry`) reprezentuje program obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)