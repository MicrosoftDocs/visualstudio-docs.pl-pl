---
title: 'Instrukcje: Serializowanie informacji o symbolach | Microsoft Docs'
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
ms.openlocfilehash: c4ea056c48525014fffad0243dfeb4dd40a8daa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687014"
---
# <a name="how-to-serialize-symbol-information"></a>Porady: serializacja informacji o symbolach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz serializować symbole, które muszą być potrzebne do analizowania aplikacji. Serializacja symboli dodaje symbole do pliku. vsp. Po dodaniu informacji o symbolach do pliku. vsp inne osoby mogą analizować raport wydajności bez dostępu do oryginalnych symboli. Jeśli symbole nie są serializowane, musisz mieć oryginalne pliki z instrumentacją. exe i. pdb, aby przeanalizować plik VSP.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializować informacje o symbolach  
  
1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
     Zostanie wyświetlone okno dialogowe **Opcje** .  
  
2. Kliknij pozycję **Narzędzia wydajności**.  
  
3. W obszarze **Ustawienia ogólne**wybierz opcję **automatycznie serializować informacje o symbolach**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: odwołania do informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Instrukcje: zapisywanie przeanalizowanych plików raportów](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
