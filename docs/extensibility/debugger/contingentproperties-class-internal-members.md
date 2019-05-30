---
title: ContingentProperties, klasa — składowe wewnętrzne | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7b9775ed74e7ae81768f180e596f171b2c99cba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344320"
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