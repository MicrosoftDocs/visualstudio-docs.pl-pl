---
title: 'Instrukcje: Serializacja informacji o symbolach | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f0359613586531a4cc7b80e25acc02be9ae37f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769186"
---
# <a name="how-to-serialize-symbol-information"></a>Instrukcje: Serializacja informacji o symbolach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Może wykonywać serializację symboli, które są niezbędne do analizowania aplikacji. Serializacja symbolu dodaje symboli do pliku Vsp. Przez dodawanie informacji o symbolach w pliku Vsp, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnej symboli. Jeżeli symbole są nie seryjny, konieczne jest posiadanie oryginalnego instrumentowanych .exe i pliki .pdb do analizowania pliku Vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij przycisk **narzędzia do oceny wydajności**.  
  
3.  W obszarze **ustawienia ogólne**, wybierz opcję **automatycznie serializuj informacje dotyczące symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)   
 [Instrukcje: Zapisz przeanalizowany raport pliki](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
