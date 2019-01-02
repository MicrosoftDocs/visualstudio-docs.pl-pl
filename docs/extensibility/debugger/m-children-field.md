---
title: Pole m_children | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d924e0439be2f8ab615d18a61f1303994b8dde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923695"
---
# <a name="mchildren-field"></a>pole m_children
Lista zadań podrzędnych, które zostały zarejestrowane przy użyciu tego zadania.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w *mscorlib.dll*)  
  
 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu zadania tylko wątku, który wykonuje zadania powinien uzyskać dostęp do tej tablicy.  
  
 Jeśli zadanie zostało ukończone, inne wątki mogą uzyskać dostęp do tego pola tak długo, jak one nie nic dodawać do niego lub usunąć elementy z niego.  
  
## <a name="see-also"></a>Zobacz także  
 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md)