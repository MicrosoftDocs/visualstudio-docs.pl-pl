---
title: Evaluate statement — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f774458eb63d9e56b99a635e7b32309375a903ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199364"
---
# <a name="evaluate-statement-command"></a>Evaluate Statement — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oblicza i wyświetla daną instrukcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Wymagane. Instrukcja do oceny.  
  
## <a name="remarks"></a>Uwagi  
 Okno służące do wprowadzania **EvaluateStatement** polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.  
  
 W **polecenia** okna, znak równości (=) jest interpretowany jako operator porównania. Na przykład, jeśli wartości zmiennych `a` i `b` są różne, a następnie polecenie  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 Zwraca wartość `false`.  
  
 W **bezpośrednie** okna, z drugiej strony, znak równości (=) jest interpretowany jako operator przypisania. Tak na przykład polecenie  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 przypiszą do zmiennej `a` wartość zmiennej `b`.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Print — polecenie](../../ide/reference/print-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
