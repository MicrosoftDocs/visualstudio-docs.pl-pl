---
title: Czujka — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 537b3f45dcf22dcc766b9902d20bf97af24b3c9d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675508"
---
# <a name="watch-command"></a>Czujka — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzy i otwiera określone wystąpienie **Obejrzyj** okna. Możesz użyć **Obejrzyj** okna do obliczania wartości zmiennych, wyrażenia i rejestry, aby edytować te wartości i zapisać wyniki.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Wymagana. Liczba wystąpień okna czujki.  
  
## <a name="remarks"></a>Uwagi  
 `index` Musi być liczbą całkowitą. Prawidłowe wartości to 1, 2, 3 lub 4.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiennych automatycznych i zmiennych lokalnych Windows](../../debugger/autos-and-locals-windows.md)   
 [Instrukcje: Edytowanie wartości w oknie zmiennych](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Instrukcje: Użyj okna dialogowego QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
