---
title: IDebugCustomAttributeQuery | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea9c37dbb889a622d0b428d53144c27d0c04aef9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706460"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Reprezentuje zapytanie, w przypadku niestandardowych atrybutów na metody lub typu.

## <a name="syntax"></a>Składnia

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Metody
 Ten interfejs implementuje następujących metod:

|Metoda|Opis|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Pobiera atrybut niestandardowy nadać jej nazwę.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Określa, w określonym zdefiniowano atrybutu niestandardowego.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll