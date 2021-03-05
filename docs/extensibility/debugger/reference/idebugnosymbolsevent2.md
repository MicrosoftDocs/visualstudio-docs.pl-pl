---
description: Informuje interfejs użytkownika debugera programu Visual Studio, aby ostrzec użytkownika, że nie można zlokalizować symboli dla uruchomionego pliku wykonywalnego.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149824"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Informuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika debugera, aby ostrzec użytkownika o tym, że nie można zlokalizować symboli dla uruchomionego pliku wykonywalnego.

## <a name="syntax"></a>Składnia

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementowane przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfejs użytkownika debugera.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll
