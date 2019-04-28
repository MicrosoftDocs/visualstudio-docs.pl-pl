---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934586"
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