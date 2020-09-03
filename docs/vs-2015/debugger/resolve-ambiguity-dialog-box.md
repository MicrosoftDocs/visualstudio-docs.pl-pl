---
title: Okno dialogowe Rozwiązywanie niejednoznaczności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b35d305bbd011adc02692cd7c9c687ac0bfc7d45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148787"
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno `Resolve Ambiguity` dialogowe pojawia się, gdy debuger nie może wybrać lokalizacji do wyświetlenia. Na przykład jeśli używasz szablonów języka C++, możesz utworzyć wiele funkcji z jednego szablonu funkcji. Jeśli debuger zostanie zatrzymany w lokalizacji źródłowej w szablonie, a Ty wybierzesz `Go To Disassembly` , debuger będzie miał wiele opcji. Każda funkcja utworzona na podstawie szablonu ma swój własny kod demontażu, a debuger nie wie, który kod chcesz wyświetlić. Okno `Resolve Ambiguity` dialogowe umożliwia wybranie wybranej lokalizacji z listy wszystkich odpowiednich lokalizacji.  
  
 `Choose the specific location`  
 Wyświetla wszystkie lokalizacje odpowiadające podanemu poleceniu.  
  
 `Address`  
 Pokazuje adresy pamięci dla każdej funkcji.  
  
 `Function`  
 Pokazuje nazwę każdej funkcji.  
  
 `Module`  
 Pokazuje moduł (EXE lub DLL) zawierający kod obiektu dla funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)
