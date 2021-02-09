---
title: Informacje o symbolach serializacji | Microsoft Docs
description: Dowiedz się, jak można serializować symbole, które trzeba wykonać, aby analizować swoją aplikację oraz jak Serializacja symboli dodaje symbole do pliku. vsp.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb9e965fb1b863d7e5837fe45a5d832fadcbc5c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907047"
---
# <a name="how-to-serialize-symbol-information"></a>Instrukcje: Serializowanie informacji o symbolach
Możesz serializować symbole, które muszą być potrzebne do analizowania aplikacji. Serializacja symboli dodaje symbole do. plik *VSP* . Przez dodanie informacji o symbolach do. plik *VSP* , inne mogą analizować raport wydajności bez dostępu do oryginalnych symboli. Jeśli symbole nie są serializowane, musisz mieć oryginalny instrument. *exe* i. pliki *PDB* do przeanalizowania. plik *VSP* .

### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializować informacje o symbolach

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

     Zostanie wyświetlone okno dialogowe **Opcje** .

2. Kliknij pozycję **Narzędzia wydajności**.

3. W obszarze **Ustawienia ogólne** wybierz opcję **automatycznie serializować informacje o symbolach**.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Instrukcje: zapisywanie przeanalizowanych plików raportów](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
