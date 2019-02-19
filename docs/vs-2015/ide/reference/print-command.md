---
title: Print — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c72f6668e6babab6bd62cfb0e9a6ca8632df2a84
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763573"
---
# <a name="print-command"></a>Print — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Oblicza wyrażenie lub wyświetla określony tekst.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Wymagana. Wyrażenie do oceny lub tekst do wyświetlenia.  
  
## <a name="remarks"></a>Uwagi  
 Dla tego polecenia, można użyć znaku zapytania (?) jako alias. Tak na przykład polecenie  
  
```  
>Debug.Print expA  
```  
  
 można również zapisać  
  
```  
>? expA  
```  
  
 Obie wersje to polecenie zwraca bieżącą wartość wyrażenia `expA`.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Evaluate statement — polecenie](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
