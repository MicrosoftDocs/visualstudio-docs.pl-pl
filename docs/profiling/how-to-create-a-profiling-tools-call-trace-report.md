---
title: Utwórz raport śledzenia wywołań narzędzia profilowania | Microsoft Docs
description: Utwórz raport śledzenia wywołań narzędzi wydajności, aby wyświetlić informacje o chronometrażu dla funkcji i funkcjach wywoływanych przez funkcje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b9c979668cdf24fae7acddd259a82e5c62353084
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800416"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Instrukcje: tworzenie raportu śledzenia wywołań narzędzi profilowania
*Raport śledzenia wywołań* dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wyświetla informacje o chronometrażu dla każdego wpisu i punktu wyjścia do funkcji aplikacji oraz każde wywołanie funkcji przez funkcję. Raporty śledzenia wywołań są dostępne do profilowania danych tylko wtedy, gdy zostały zebrane przy użyciu metody instrumentacji.

> [!NOTE]
> Nie można wyświetlić raportów śledzenia wywołań w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Aby wygenerować wartość rozdzieloną przecinkami, należy użyć narzędzia wiersza polecenia **VSPerfReport** .*CSV*) lub. plik *XML* . Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raport śledzenia wywołań

1. Otwórz okno **wiersza polecenia** .

2. W wierszu polecenia wpisz następujące polecenie:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**

    |Element|Opis|
    |-|-|
    |*ToolsPath*|Ścieżka narzędzia profilowania narzędzi wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Dane profilowania (.*VSP* lub. *vsps*) rozszerzeniem. Akceptowane są pełne i częściowe ścieżki.|
    |Xml|Generuje raport w formacie XML.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
