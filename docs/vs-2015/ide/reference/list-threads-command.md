---
title: Lista wątków polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 627e361fca63522f47a1d472655573c14a44035a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54804611"
---
# <a name="list-threads-command"></a>Lista wątków — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Wyświetla listę wątków w bieżącym programem.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Opcjonalna. Wybiera wątku za pomocą jego indeksu do bieżącego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zostanie określony, `index` argument oznacza wskazany wątek jako bieżącego wątku. Znak gwiazdki (*) jest wyświetlana na liście obok bieżącego wątku.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)   
 [Lista dezasemblacji — polecenie](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
