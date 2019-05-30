---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dadd4547d5b0f691b454a98ba714abea9bf6f058
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323716"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Sygnały [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera interfejsu użytkownika, aby ostrzec użytkownika, że symbole nie można zlokalizować dla uruchomionego pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Implementowany przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera interfejsu użytkownika.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll