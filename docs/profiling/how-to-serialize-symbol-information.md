---
title: 'Instrukcje: Serializacja informacji o symbolach | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b88268ba0ed8b1c324eda08ec3db969e088f279
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083149"
---
# <a name="how-to-serialize-symbol-information"></a>Instrukcje: Serializacja informacji o symbolach
Może wykonywać serializację symboli, które są niezbędne do analizowania aplikacji. Serializacja symbolu dodaje symbole. *vsp* pliku. Przez dodanie informacji o symbolach w celu. *vsp* pliku, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnej symboli. Symbole nie są serializowane, musisz mieć oryginalny instrumentacji. *exe* i. *plik PDB* plików do przeanalizowania. *Vsp* pliku.

### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli

1. Na **narzędzia** menu, kliknij przycisk **opcje**.

     **Opcje** zostanie wyświetlone okno dialogowe.

2. Kliknij przycisk **narzędzia do oceny wydajności**.

3. W obszarze **ustawienia ogólne**, wybierz opcję **automatycznie serializuj informacje dotyczące symboli**.

## <a name="see-also"></a>Zobacz także
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)
- [Instrukcje: Zapisz przeanalizowany raport pliki](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))