---
title: Pliki źródłowe debugowania/typowe właściwości/strony właściwości rozwiązania
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 735432db485277e2265479e625f5e8acaa2cc2e3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738400"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Debugowanie plików źródłowych, typowe właściwości, strony właściwości rozwiązania — Okno dialogowe
Ta strona właściwości określa, gdzie debuger ma szukać plików źródłowych podczas debugowania rozwiązania.

 Aby uzyskać dostęp do strony właściwości **pliki źródłowe debugowania** , kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu skrótów. Rozwiń folder **wspólne właściwości** , a następnie kliknij stronę **debugowanie plików źródłowych** .

 **Katalogi zawierające kod źródłowy** Zawiera listę katalogów, w których debuger wyszukuje pliki źródłowe podczas debugowania rozwiązania. Podkatalogi określonych katalogów są również przeszukiwane.

 **Nie wyszukuj tych plików źródłowych** Wprowadź nazwy wszystkich plików, które nie mają być odczytywane przez debuger. Jeśli debuger odnajdzie jeden z tych plików w jednym z katalogów określonych powyżej, zostanie on zignorowany. Jeśli okno dialogowe **Znajdowanie źródła** pojawia się w trakcie debugowania i klikniesz przycisk **Anuluj**, wyszukiwany plik zostanie dodany do tej listy, dzięki czemu debuger nie będzie kontynuował wyszukiwania tego pliku.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)