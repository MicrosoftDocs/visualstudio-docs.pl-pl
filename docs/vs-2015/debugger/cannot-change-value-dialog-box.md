---
title: Nie można zmienić wartości, okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19ef7640939ba1ad9a22dcf519636c64df011394
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782404"
---
# <a name="cannot-change-value-dialog-box"></a>Nie można zmienić wartości — okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Błąd  
 `The value of this variable cannot be changed` &#124;`The name` *nazwa* `does not exist in the current context` &#124; *różne inne komunikaty*  
  
 To okno komunikatu pojawia się podczas próby zmiany zawartości zmiennej na niedozwoloną wartość okna debugera (windows automatyczne, wyrażenie kontrolne lub lokalne) lub okna dialogowego QuickWatch. Na przykład Jeśli spróbujesz ustawić wartość zmiennej liczby całkowitej na ciąg znaków, pojawi się to okno komunikatu.  
  
## <a name="solution"></a>Rozwiązanie  
 Upewnij się, dane wejściowe, można wpisać w oknie debugera lub okno dialogowe QuickWatch reprezentuje dozwoloną wartością dla zmiennej, którą chcesz ustawić.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)



