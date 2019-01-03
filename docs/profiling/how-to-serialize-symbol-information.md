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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ae49e4656bcbeb8e1048331b9fb0b61849e4099
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987602"
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