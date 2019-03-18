---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04a2c700d2cac4bcdc845ebf442de29863e87deb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159494"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

Wymusza debugera w trybie pojedynczego kroku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>Parametry

`pStepThread`

[in] Wątek procesu monitora debugowania do wykonania. Jeśli ma wartość null, menedżerów PDM wyczyści jego przechodzenia krok po kroku wątku.

## <a name="return-value"></a>Wartość zwracana

Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.

|Wartość|Opis|
|-----------|-----------------|
|`S_OK`|Wykonanie metody powiodło się.|

## <a name="see-also"></a>Zobacz także

- [IRemoteDebugApplicationEx, interfejs](iremotedebugapplicationex-interface.md)