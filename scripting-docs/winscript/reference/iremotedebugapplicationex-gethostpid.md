---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62033169e10585015b5f1439067aa0cbc42447a4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754643"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Zwraca identyfikator procesu aplikacji hosta.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Parametry

`dwHostPid`

[out] Identyfikator procesu hosta.

## <a name="return-value"></a>Wartość zwracana

Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.

|Wartość|Opis|
|-----------|-----------------|
|`S_OK`|Wykonanie metody powiodło się.|

## <a name="remarks"></a>Uwagi

Używane przez środowisko IDE.

## <a name="see-also"></a>Zobacz także

- [IRemoteDebugApplicationEx, interfejs](iremotedebugapplicationex-interface.md)