---
title: Brak dostępnego źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697807"
---
# <a name="no-source-available"></a>Nie jest dostępne żadne źródło
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt nie zawiera kodu źródłowego dla kodu, który próbujesz wyświetlić. Typową przyczyną jest dwukrotne kliknięcie modułu, który nie ma kodu źródłowego w oknie **stosu wywołań** lub w **oknie wątków**. Można kontynuować debugowanie, ale nie może używać okna źródłowego do ustawiania punktów przerwania i wykonywania innych akcji w tej lokalizacji. Jeśli musisz ustawić punkt przerwania, Użyj zamiast niego **okna demontażu** .  
  
 Na stronach właściwości rozwiązania można zmienić katalogi, w których debuger szuka plików źródłowych, i powiadom debugera, aby ignorował wybrane pliki źródłowe. Zobacz [pliki źródłowe debugowania, wspólne właściwości, okno dialogowe strony właściwości rozwiązania](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Przeglądaj, aby znaleźć kod źródłowy**  
 Kliknij ten link, aby otworzyć okno dialogowe, w którym można przeglądać, aby znaleźć kod źródłowy.  
  
 **Pokaż demontaż**  
 Uruchamia **okno demontaż**.  
  
 **Zawsze pokazuj demontaż dla brakujących plików źródłowych**  
 Wybierz tę opcję, aby automatycznie wyświetlić **okno demontażu** , gdy nie jest dostępne żadne źródło. To ustawienie można także zmienić w oknie dialogowym **Opcje** , kategorii **debugowanie** , stronie **Ogólne** , zaznaczając lub czyszcząc polecenie **Pokaż demontaż, jeśli źródło jest niedostępne**.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki źródłowe debugowania, wspólne właściwości, okno dialogowe strony właściwości rozwiązania](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (rozszerzenie debugowania SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
