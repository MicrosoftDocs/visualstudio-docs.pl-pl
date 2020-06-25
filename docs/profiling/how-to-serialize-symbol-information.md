---
title: Jak serializować informacje o symbolach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d28df6d36b1b91974483ae793e6e57f064974183
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328529"
---
# <a name="how-to-serialize-symbol-information"></a>Instrukcje: Serializowanie informacji o symbolach
Możesz serializować symbole, które muszą być potrzebne do analizowania aplikacji. Serializacja symboli dodaje symbole do. plik *VSP* . Przez dodanie informacji o symbolach do. plik *VSP* , inne mogą analizować raport wydajności bez dostępu do oryginalnych symboli. Jeśli symbole nie są serializowane, musisz mieć oryginalny instrument. *exe* i. pliki *PDB* do przeanalizowania. plik *VSP* .

### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializować informacje o symbolach

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

     Zostanie wyświetlone okno dialogowe **Opcje** .

2. Kliknij pozycję **Narzędzia wydajności**.

3. W obszarze **Ustawienia ogólne**wybierz opcję **automatycznie serializować informacje o symbolach**.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Instrukcje: zapisywanie przeanalizowanych plików raportów](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
