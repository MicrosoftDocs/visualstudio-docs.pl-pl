---
title: Debuger nie może wyświetlić kodu źródłowego lub demontażu
description: Zobacz przyczyny dotyczące komunikatu "debuger nie może wyświetlić kodu źródłowego lub odasemblowania dla bieżącej lokalizacji, w której wykonywanie zostało zatrzymane".
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 2966405378d2a6144c921c442e7412a41c454c52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873070"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debuger nie może wyświetlić kodu źródłowego lub dezasemblacji
Ten błąd odczytuje:

 Debuger nie może wyświetlić kodu źródłowego lub odasemblowania dla bieżącej lokalizacji, w której wykonywanie zostało zatrzymane.

 Ten komunikat o błędzie może wystąpić z kilku powodów:

- Być może osiągnięto punkt przerwania w lokalizacji, dla której nie ma kodu źródłowego, podczas debugowania języka, który nie obsługuje demontażu. Otwórz okno **punkty przerwania** , Znajdź punkt przerwania i usuń go.

- Jeśli debugujesz skrypt, być może osiągnięto punkt przerwania, gdy w programie nie było wątków. Wybierz pozycję **krok** lub **Kontynuuj** z menu **Debuguj** , aby wznowić debugowanie.

- Zagadnienia dotyczące zabezpieczeń mogły uniemożliwić odczytywanie informacji o stosie, wątkach, rejestrowaniu i innych kontekstach z debugowanego programu. Najprawdopodobniej dzieje się tak, jeśli debugujesz aplikację sieci Web i nie masz odpowiednich uprawnień, aby uzyskać dostęp do katalogu wirtualnego. Ustaw dla katalogu wirtualnego zabezpieczenia anonimowe i spróbuj ponownie.

## <a name="see-also"></a>Zobacz też
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)