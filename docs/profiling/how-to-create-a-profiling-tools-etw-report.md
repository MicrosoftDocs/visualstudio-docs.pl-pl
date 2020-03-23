---
title: 'Jak: Tworzenie raportu ETW narzędzi profilowania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776404"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Jak: Tworzenie raportu ETW narzędzi do profilowania
Raport Śledzenia zdarzeń dla systemu Windows (ETW) zawiera listę zdarzeń ETW, które są rejestrowane w sesji wydajności narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania. Dane ETW są zbierane w pliku binarnym (.* etl*). Aby uzyskać więcej informacji na temat tego raportu, zobacz [Śledzenie zdarzeń dla systemu Windows (ETW) raport](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Nie można wyświetlić raportów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ETW w interfejsie dla programu .

- Aby uzyskać informacje na temat zbierania danych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ETW za pomocą interfejsu , zobacz [Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW).](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Aby uzyskać informacje dotyczące sposobu zbierania danych ETW z wiersza polecenia, zobacz [VSPerfCmd](../profiling/vsperfcmd.md) i [Zdarzenia](../profiling/events-vsperfcmd.md).

  Raport ETW jest generowany przy użyciu polecenia **VSReport/summary:etw.** Tthe. *etl,* który zawiera dane ETW musi znajdować się w tym samym katalogu co dane profilowania (.* vsp* lub . *vsps*) Plik. Domyślnie raport jest generowany jako wartość oddzielona przecinkami (.* csv*). Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Aby wygenerować raport ETW

- W oknie **wiersza polecenia** wpisz następujący wiersz polecenia:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |||
    |-|-|
    |*Ścieżka narzędzi*|Ścieżka narzędzia Narzędzia profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*Plik VSP*|Dane profilowania (.* vsp* lub . *vsps*) Plik. Akceptowane są pełne i częściowe ścieżki.|
    |Xml|Generuje raport sformatowany w formacie XML.|
