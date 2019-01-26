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
ms.openlocfilehash: f7957917c999396f2e09bbb697474beb47ebcc47
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042442"
---
# <a name="how-to-serialize-symbol-information"></a>Instrukcje: Serializacja informacji o symbolach
Może wykonywać serializację symboli, które są niezbędne do analizowania aplikacji. Serializacja symbolu dodaje symbole. *vsp* pliku. Przez dodanie informacji o symbolach w celu. *vsp* pliku, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnej symboli. Symbole nie są serializowane, musisz mieć oryginalny instrumentacji. *exe* i. *plik PDB* plików do przeanalizowania. *Vsp* pliku.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij przycisk **narzędzia do oceny wydajności**.  
  
3.  W obszarze **ustawienia ogólne**, wybierz opcję **automatycznie serializuj informacje dotyczące symboli**.  
  
## <a name="see-also"></a>Zobacz także  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)   
 [Instrukcje: Zapisz przeanalizowany raport pliki](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))