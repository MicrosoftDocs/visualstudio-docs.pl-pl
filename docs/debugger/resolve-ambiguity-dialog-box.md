---
title: Okno dialogowe rozstrzyganie niejednoznaczności | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a31d217f8dc492468a894f78f10a4f7656677521
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945070"
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
`Resolve Ambiguity` Pojawi się okno dialogowe, gdy debuger nie można wybrać lokalizację, aby wyświetlić. Na przykład jeśli używasz szablonów języka C++, można utworzyć wiele funkcji z pojedynczego szablonu funkcji. Jeśli debuger zatrzymuje się w lokalizacji źródłowej, w szablonie, a Ty podejmiesz `Go To Disassembly`, debuger ma wiele opcji. Każda funkcja tworzone na podstawie szablonu ma swój własny kod dezasemblacji i debuger nie wie, kod, który chcesz wyświetlić. `Resolve Ambiguity` Okno dialogowe pozwala wybrać lokalizację z listy wszystkich odpowiedniej lokalizacji.  
  
 `Choose the specific location`  
 Wyświetla listę wszystkich lokalizacji odpowiadającego do swojej dyspozycji.  
  
 `Address`  
 Pokazuje adresów pamięci dla każdej funkcji.  
  
 `Function`  
 Zawiera nazwę każdej funkcji.  
  
 `Module`  
 Zawiera moduł (plik EXE lub DLL) zawierająca kod obiektowy dla tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)