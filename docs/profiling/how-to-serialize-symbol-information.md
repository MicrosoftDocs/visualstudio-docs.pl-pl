---
title: 'Jak: Serialize Symbol Information | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 202c30b1786e7e3ddb27583ddaeda9180d680b53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774890"
---
# <a name="how-to-serialize-symbol-information"></a>Jak: Serialize informacje o symbolu
Można serializować symbole, które muszą być niezbędne do analizy aplikacji. Serializacja symboli dodaje symbole do pliku . *vsp.* Dodając informacje o symbolu do pliku . *vsp,* inni mogą analizować raport wydajności bez dostępu do oryginalnych symboli. Jeśli symbole nie są serializowane, musi być oryginalny instrumentowany . *exe* i . *pliki pdb* do analizy pliku . *vsp.*

### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializować informacje o symbolu

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

     Zostanie wyświetlone okno dialogowe **Opcje.**

2. Kliknij pozycję **Narzędzia wydajności**.

3. W obszarze **Ustawienie ogólne**wybierz pozycję **Automatycznie serizuj informacje o symbolu**.

## <a name="see-also"></a>Zobacz też
- [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Jak: Zapisywanie analizowanych plików raportu](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
