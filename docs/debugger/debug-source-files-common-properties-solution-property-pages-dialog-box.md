---
title: Debuguj pliki źródłowe/strony właściwości rozwiązania
description: Dostęp do strony właściwości pliki źródłowe debugowania w programie Visual Studio, klikając prawym przyciskiem myszy rozwiązanie w Eksplorator rozwiązań i wybierając właściwości > wspólnych właściwości.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10818f473dec392364832cdc2f5215197ef4627f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873174"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Debugowanie plików źródłowych, typowe właściwości, strony właściwości rozwiązania — Okno dialogowe
Ta strona właściwości określa, gdzie debuger ma szukać plików źródłowych podczas debugowania rozwiązania.

 Aby uzyskać dostęp do strony właściwości **pliki źródłowe debugowania** , kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości** z menu skrótów. Rozwiń folder **wspólne właściwości** , a następnie kliknij stronę **debugowanie plików źródłowych** .

 **Katalogi zawierające kod źródłowy** Zawiera listę katalogów, w których debuger wyszukuje pliki źródłowe podczas debugowania rozwiązania. Podkatalogi określonych katalogów są również przeszukiwane.

 **Nie wyszukuj tych plików źródłowych** Wprowadź nazwy wszystkich plików, które nie mają być odczytywane przez debuger. Jeśli debuger odnajdzie jeden z tych plików w jednym z katalogów określonych powyżej, zostanie on zignorowany. Jeśli okno dialogowe **Znajdowanie źródła** pojawia się w trakcie debugowania i klikniesz przycisk **Anuluj**, wyszukiwany plik zostanie dodany do tej listy, dzięki czemu debuger nie będzie kontynuował wyszukiwania tego pliku.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)