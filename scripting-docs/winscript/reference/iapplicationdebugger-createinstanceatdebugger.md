---
title: 'IApplicationDebugger:: CreateInstanceAtDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.CreateInstanceAtDebugger
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::CreateInstanceAtDebugger
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c15dc5d9b36a718ed41813bac46bc4b9415eb853
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577888"
---
# <a name="iapplicationdebuggercreateinstanceatdebugger"></a>IApplicationDebugger::CreateInstanceAtDebugger
Umożliwia tworzenie obiektów w procesie debugera przez kod, który jest poza procesem do debugera.  
  
> [!IMPORTANT]
> Ta metoda nie powinna być zaimplementowana, ponieważ umożliwia niezaufanego kodu tworzenie dowolnych obiektów w zaufanym wątku debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 podczas Identyfikator klasy (CLSID) obiektu do utworzenia.  
  
 `pUnkOuter`  
 podczas Jeśli `NULL`, obiekt nie jest tworzony w ramach agregacji. W przeciwnym razie `pUnkOuter` jest wskaźnikiem do interfejsu `IUnknown` obiektu agregacji (kontrolka `IUnknown`).  
  
 `dwClsContext`  
 podczas Kontekst do uruchamiania kodu wykonywalnego. Wartości są pobierane z `CLSCTX` wyliczenia.  
  
 `riid`  
 podczas Identyfikator interfejsu używany do komunikacji z obiektem.  
  
 `ppvObject`  
 określoną Adres zmiennej wskaźnika, która odbiera wskaźnik interfejsu żądany w `riid`. Po pomyślnym powrocie, * `ppvObject` zawiera żądany wskaźnik interfejsu. W przypadku niepowodzenia `ppvObject` \* zawiera `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda deleguje do `CoCreateInstance`.  
  
 Metoda nie jest obecnie zaimplementowana.  
  
## <a name="see-also"></a>Zobacz także  
 [IApplicationDebugger, interfejs](../../winscript/reference/iapplicationdebugger-interface.md)