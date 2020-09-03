---
title: m_children pole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149061"
---
# <a name="m_children-field"></a>m_children, pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lista zadań podrzędnych, które są zarejestrowane w tym zadaniu.  
  
 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).  
  
## <a name="syntax"></a>Składnia  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy zadanie jest uruchomione, tylko wątek, który wykonuje zadanie, powinien uzyskać dostęp do tej tablicy.  
  
 Jeśli zadanie zostanie ukończone, inne wątki mogą uzyskać dostęp do tego pola, o ile nie dodają do niego niczego lub nie usuwają niczego z nich.  
  
## <a name="see-also"></a>Zobacz też  
 [ContingentProperties, klasa](../../extensibility/debugger/contingentproperties-class-internal-members.md)
