---
title: ContingentProperties, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60129950c2311cc94b8573de4cd8ae3c46194e75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926001"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties, klasa — składowe wewnętrzne
Zawiera dodatkowe właściwości <xref:System.Threading.Tasks.Task> obiektu.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tych wewnętrznych składowych z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Elementy członkowskie

### <a name="fields"></a>Pola

|Nazwa|Opis|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista zadań podrzędnych, które zostały zarejestrowane przy użyciu tego zadania.|

## <a name="remarks"></a>Uwagi
 .NET Framework inicjuje pól tej klasy, tylko wtedy, gdy są potrzebne.

## <a name="see-also"></a>Zobacz także
- [Równoległe elementy wewnętrzne rozszerzeń dla programu .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)