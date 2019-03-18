---
title: IScriptNode::CreateChildHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149250"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Dodaje scriptlet jako wystąpienie podrzędnych `IScriptNode`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 [in] Adres nazwy domyślnej, aby skojarzyć ze scriptlet.  
  
 `prgpszNames`  
 [w size_is (`cpszNames`)] identyfikatorów w pełni kwalifikowana nazwa hosta.  
  
 `cpszNames`  
 [in] Liczba identyfikatorów w `prgpszNames` parametru.  
  
 `pszEvent`  
 [in] Adres buforu, który identyfikuje nazwę zdarzenia, skojarzone ze scriptlet.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika końcowego elementu skrypt bloku. Do analizowania, host zazwyczaj używa rozdzielnika (takie jak dwa pojedyncze cudzysłowy), aby wykrywać koniec bloku skryptu.  
  
 Ogranicznik umożliwia przetwarzanie wstępne za pomocą skryptu tworzenia aparatu. Na przykład aparat może zastąpić znak pojedynczego cudzysłowu dwa znaki pojedynczego cudzysłowu jako ogranicznika. Aparat określa sposób korzystania z ogranicznikiem.  
  
 Wartość NULL, jeśli nie było ogranicznika używany do identyfikowania koniec bloku skryptu.  
  
 `ptiSignature`  
 [in] Informacje o typie dla obiektu funkcji.  
  
 `iMethodSignature`  
 [in] Indeks funkcji w `ITypeInfo``ptiSignature` parametru.  
  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `dwCookie`  
 [in] Wartość zdefiniowanych przez aplikację, która jest używana do kojarzenia wpis z obiektu hosta.  
  
 `ppse`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptEntry` interfejsu, wystąpienia podrzędne.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Scriptlet określa procedurę obsługi zdarzeń. Ta metoda tworzy scriptlet, jeśli jest wywoływany przez `IScriptNode` obiekt, który reprezentuje strony sieci Web. Ta metoda nie powiedzie się, jeśli jest ona wywoływana przez inne interfejsy.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry, interfejs](../../winscript/reference/iscriptentry-interface.md)