---
title: Brak dostępnego źródła | Microsoft Docs
description: Dowiedz się, co możesz zrobić, gdy projekt nie ma kodu źródłowego dla kodu, który chcesz wyświetlić.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cf7bf067602586d90271eab1f9289a3b6b884ce
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975189"
---
# <a name="no-source-available"></a>Nie jest dostępne żadne źródło
Projekt nie zawiera kodu źródłowego dla kodu, który próbujesz wyświetlić. Typową przyczyną jest dwukrotne kliknięcie modułu, który nie ma kodu źródłowego w oknie **stosu wywołań** lub w **oknie wątków**. Można kontynuować debugowanie, ale nie może używać okna źródłowego do ustawiania punktów przerwania i wykonywania innych akcji w tej lokalizacji. Jeśli musisz ustawić punkt przerwania, Użyj zamiast niego **okna demontażu** .

 Na stronach właściwości rozwiązania można zmienić katalogi, w których debuger szuka plików źródłowych, i powiadom debugera, aby ignorował wybrane pliki źródłowe. Zobacz [pliki źródłowe debugowania, wspólne właściwości, okno dialogowe strony właściwości rozwiązania](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Przeglądaj, aby znaleźć kod źródłowy** Kliknij ten link, aby otworzyć okno dialogowe, w którym można przeglądać, aby znaleźć kod źródłowy.

 **Pokaż demontaż** Uruchamia **okno demontaż**.

 **Zawsze pokazuj demontaż dla brakujących plików źródłowych** Wybierz tę opcję, aby automatycznie wyświetlić **okno demontażu** , gdy nie jest dostępne żadne źródło. To ustawienie można także zmienić w oknie dialogowym **Opcje** , kategorii **debugowanie** , stronie **Ogólne** , zaznaczając lub czyszcząc polecenie **Pokaż demontaż, jeśli źródło jest niedostępne**.

## <a name="see-also"></a>Zobacz też
- [Pliki źródłowe debugowania, wspólne właściwości, okno dialogowe strony właściwości rozwiązania](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (rozszerzenie debugowania SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)