---
title: Okno dialogowe Rozwiązywanie niejednoznaczności | Microsoft Docs
description: Przejrzyj okno dialogowe Rozwiązywanie niejednoznaczności programu Visual Studio, które jest wyświetlane, gdy debuger nie może wybrać lokalizacji do wyświetlenia.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee7b83630935b948d29150763e0ad5b9c435175f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891322"
---
# <a name="resolve-ambiguity-dialog-box"></a>Rozwiązywania niejednoznaczności — Okno dialogowe
Okno `Resolve Ambiguity` dialogowe pojawia się, gdy debuger nie może wybrać lokalizacji do wyświetlenia. Na przykład jeśli używasz szablonów języka C++, możesz utworzyć wiele funkcji z jednego szablonu funkcji. Jeśli debuger zostanie zatrzymany w lokalizacji źródłowej w szablonie, a Ty wybierzesz `Go To Disassembly` , debuger będzie miał wiele opcji. Każda funkcja utworzona na podstawie szablonu ma swój własny kod demontażu, a debuger nie wie, który kod chcesz wyświetlić. Okno `Resolve Ambiguity` dialogowe umożliwia wybranie wybranej lokalizacji z listy wszystkich odpowiednich lokalizacji.

 `Choose the specific location` Wyświetla wszystkie lokalizacje odpowiadające podanemu poleceniu.

 `Address` Pokazuje adresy pamięci dla każdej funkcji.

 `Function` Pokazuje nazwę każdej funkcji.

 `Module` Pokazuje moduł (EXE lub DLL) zawierający kod obiektu dla funkcji.

## <a name="see-also"></a>Zobacz też
- [Wyrażenia w debugerze](../debugger/expressions-in-the-debugger.md)