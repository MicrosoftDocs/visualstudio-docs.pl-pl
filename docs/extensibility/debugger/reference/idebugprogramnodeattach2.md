---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721820"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Zezwala na powiadamianie węzła programu o próbie dołączenia do skojarzonego programu.

## <a name="syntax"></a>Składnia

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany w tej samej klasie, która implementuje interfejs [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , aby można było odbierać powiadomienia o operacji Attach i zapewnić możliwość anulowania operacji Attach.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskaj ten interfejs, wywołując `QueryInterface` metodę w obiekcie [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Metoda [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) musi być wywoływana przed metodą [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , aby umożliwić programowi węzłowi zatrzymywanie procesu dołączania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Dołącza do skojarzonego programu lub przypisuje proces Attach do metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest preferowaną alternatywą dla przestarzałej metody [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) . Wszystkie aparaty debugowania są zawsze ładowane przy użyciu `CoCreateInstance` funkcji, to oznacza, że są one tworzone poza przestrzenią adresową debugowanego programu.

 Jeśli wcześniejsza implementacja `IDebugProgramNode2::Attach_V7` metody była po prostu ustawiona dla `GUID` debugowanego programu, należy zaimplementować tylko metodę [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Jeśli poprzednia implementacja `IDebugProgramNode2::Attach_V7` metody użył interfejsu wywołania zwrotnego, który został dostarczony, ta funkcja musi zostać przeniesiona do implementacji metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , a `IDebugProgramNodeAttach2` interfejs nie musi być zaimplementowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
