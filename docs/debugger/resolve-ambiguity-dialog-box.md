---
title: Okno dialogowe Rozwiązywanie niejednoznaczności | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4257fd213d6401de381e25c74c126b8468b76057
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729841"
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
Okno dialogowe `Resolve Ambiguity` pojawia się, gdy debuger nie może wybrać lokalizacji do wyświetlenia. Na przykład jeśli używasz C++ szablonów, możesz utworzyć wiele funkcji z jednego szablonu funkcji. Jeśli debuger zatrzyma się w lokalizacji źródłowej w szablonie, a użytkownik wybierze `Go To Disassembly`, debuger będzie miał wiele opcji. Każda funkcja utworzona na podstawie szablonu ma swój własny kod demontażu, a debuger nie wie, który kod chcesz wyświetlić. Okno dialogowe `Resolve Ambiguity` umożliwia wybranie wybranej lokalizacji z listy wszystkich odpowiednich lokalizacji.

 `Choose the specific location` wyświetla wszystkie lokalizacje odpowiadające Twojemu poleceniu.

 `Address` pokazuje adresy pamięci dla każdej funkcji.

 `Function` wyświetla nazwę każdej funkcji.

 `Module` wyświetla moduł (EXE lub DLL) zawierający kod obiektu dla funkcji.

## <a name="see-also"></a>Zobacz także
- [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)