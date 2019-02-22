---
title: Brak dostępnego źródła | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703698"
---
# <a name="no-source-available"></a>Nie jest dostępne żadne źródło
Projekt nie zawiera kodu źródłowego dla kodu, który chcesz wyświetlić. Najczęstszą przyczyną jest dwukrotne kliknięcie modułu, który nie ma kodu źródłowego w **okna stosu wywołań** lub **okno wątków**. Można kontynuować debugowania, ale nie można użyć okna źródła do ustawiania punktów przerwania i wykonywać inne działania w tej lokalizacji. Jeśli potrzebujesz ustawić punkt przerwania, użyj **okna dezasemblacji** zamiast tego.

 Na stronach właściwości rozwiązania można zmienić katalogi, gdzie debuger wyszukuje pliki źródłowe i polecić debugerowi, aby zignorować wybrane źródło plików. Zobacz [debugowania okno dialogowe strony właściwości rozwiązania źródła plików, typowe właściwości,](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Przeglądaj, aby znaleźć kod źródłowy** kliknij ten link, aby otworzyć okno dialogowe, w którym możesz przejść do znalezienia kodu źródłowego.

 **Pokaż Dezasemblację** uruchamia **okna dezasemblacji**.

 **Zawsze pokazuj dezasemblację dla brakujących plików źródłowych** wybierz tę opcję, aby wyświetlić **okna dezasemblacji** automatycznie, gdy jest dostępne żadne źródło. To ustawienie można zmienić w **opcje** okno dialogowe **debugowanie** kategorii **ogólne** strony, zaznaczając lub usuwając **Pokaż dezasemblację Jeśli źródło jest niedostępne**.

## <a name="see-also"></a>Zobacz też
- [Debugowanie plików źródłowych, Typowe właściwości, Strony właściwości rozwiązania, okno dialogowe](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (rozszerzenie do debugowania SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)