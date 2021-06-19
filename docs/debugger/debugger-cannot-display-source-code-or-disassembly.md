---
title: Debuger nie może wyświetlać kodu źródłowego ani dezembować
description: Zapoznaj się z przyczynami komunikatu "Debuger nie może wyświetlić kodu źródłowego ani dezemblii dla bieżącej lokalizacji, w której zatrzymano wykonywanie".
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bac2f04ab77e34186a4f0ee202fa8d16f6e45e38
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387349"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
Ten błąd odczytuje:

 Debuger nie może wyświetlać kodu źródłowego ani desemblii dla bieżącej lokalizacji, w której zatrzymano wykonywanie.

 Ten komunikat o błędzie może wystąpić z kilku powodów:

- Być może trafisz punkt przerwania w lokalizacji, dla której nie ma kodu źródłowego, podczas debugowania języka, który nie obsługuje dekompełtowania. Otwórz **okno Punkty przerwania,** znajdź punkt przerwania i usuń go.

- Jeśli debugujesz skrypt, możesz trafić punkt przerwania, gdy w programie nie ma wątków. Wybierz **pozycję Krok** lub **Kontynuuj** z menu **Debugowanie,** aby wznowić debugowanie.

- Zagadnienia dotyczące zabezpieczeń mogą uniemożliwić debugerowi odczytywanie stosu, wątku, rejestru i innych informacji kontekstowych z debugego programu. Jest to najbardziej prawdopodobne, jeśli debugujesz aplikację internetową i nie masz odpowiednich uprawnień dostępu do katalogu wirtualnego. Ustaw zabezpieczenia katalogu wirtualnego na Anonimowe i spróbuj ponownie.

## <a name="see-also"></a>Zobacz też
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)