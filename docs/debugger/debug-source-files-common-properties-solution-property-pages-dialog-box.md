---
title: Okno dialogowe strony właściwości rozwiązania źródła plików, typowe właściwości, debugowanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 83bed0588a0959ab85906d949e1b0752396223ae
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609712"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Debugowanie plików źródłowych, typowe właściwości, strony właściwości rozwiązania — Okno dialogowe
Ta strona właściwości określa, gdzie debuger będzie szukać plików źródłowych, podczas debugowania rozwiązania.

 Aby uzyskać dostęp do **Debuguj pliki źródłowe** strony właściwości, kliknij prawym przyciskiem myszy w rozwiązaniu w **Eksploratora rozwiązań** i wybierz **właściwości** z menu skrótów. Rozwiń **wspólne właściwości** folder, a następnie kliknij przycisk **Debuguj pliki źródłowe** strony.

 **Katalogi zawierające kod źródłowy** zawiera listę katalogów, w których debuger wyszukuje pliki źródłowe podczas debugowania rozwiązania. Przeszukiwane są również podkatalogi w określonych katalogach.

 **Nie wyszukuj tych plików źródłowych** wprowadzić nazwy wszystkich plików, które nie chcesz, aby debuger do odczytu. Jeśli debuger wykryje jeden z tych plików w jednym z katalogów wymienione powyżej, zignoruje go. Jeśli **Znajdź źródło** okno dialogowe funkcjonuje podczas debugowania, a następnie kliknij **anulować**, plik wyszukiwany pobiera dodana do tej listy, aby debuger nie będzie kontynuowane wyszukiwanie dla tego pliku.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)