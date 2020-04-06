---
title: IDebugProgramNodeAttach2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721820"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umożliwia powiadamianie węzła programu o próbie dołączenia do skojarzonego programu.

## <a name="syntax"></a>Składnia

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany w tej samej klasie, która implementuje interfejs [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) w celu otrzymania powiadomienia o operacji dołączania i zapewnienia możliwości anulowania operacji dołączania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Uzyskaj ten interfejs, `QueryInterface` wywołując metodę w [obiekcie IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Metoda musi być wywołana przed [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody, aby dać węzłowi programu szansę, aby zatrzymać proces dołączania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Dołącza do skojarzonego programu lub odracza proces dołączania do [metody Dołącz.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest preferowaną alternatywą dla przestarzałej metody [Attach_V7.](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Wszystkie aparaty debugowania `CoCreateInstance` są zawsze ładowane z funkcją, oznacza to, że są tworzone poza przestrzenią adresową programu, który jest debugowany.

 Jeśli poprzednia implementacja `IDebugProgramNode2::Attach_V7` metody po `GUID` prostu ustawienie programu jest debugowane, a następnie tylko [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda musi być zaimplementowana.

 Jeśli poprzednia implementacja `IDebugProgramNode2::Attach_V7` metody używane wywołania zwrotnego interfejsu, który został dostarczony, a następnie tej funkcji musi zostać przeniesiony do implementacji [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody i `IDebugProgramNodeAttach2` interfejs nie musi być zaimplementowana.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
