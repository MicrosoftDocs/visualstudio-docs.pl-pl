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
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666549"
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
