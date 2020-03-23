---
title: 'Jak: Tworzenie raportu śledzenia połączeń narzędzi profilowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b184310d837193679a1a5eacf2fbae4ecf29caa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778989"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Instrukcje: tworzenie raportu śledzenia wywołań narzędzi profilowania
*Raport śledzenia wywołań* dla narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania zawiera listę informacji chronometrażu dla każdego punktu wejścia i wyjścia do funkcji aplikacji i każdego wywołania innych funkcji przez funkcję. Raporty śledzenia wywołania są dostępne dla profilowania danych tylko wtedy, gdy zostały zebrane za pomocą metody instrumentacji.

> [!NOTE]
> W pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby wygenerować wartość oddzieloną przecinkami, należy użyć narzędzia wiersza polecenia **VSPerfReport.** * csv)* lub . *xml.* Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raport śledzenia połączeń

1. Otwórz okno **wiersza polecenia.**

2. W wierszu polecenia wpisz następujące polecenie:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |||
    |-|-|
    |*Ścieżka narzędzi*|Ścieżka narzędzi wiersza polecenia Narzędzia profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*Plik VSP*|Dane profilowania (.* vsp* lub . *vsps*) Plik. Akceptowane są pełne i częściowe ścieżki.|
    |Xml|Generuje raport sformatowany w formacie XML.|

## <a name="see-also"></a>Zobacz też
- [Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
