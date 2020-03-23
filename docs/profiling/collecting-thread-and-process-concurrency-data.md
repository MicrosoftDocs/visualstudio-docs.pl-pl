---
title: Zbieranie danych dotyczących współbieżności wątków i procesów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e8fda0300aad4a331366fac0a9ebd1b559cecc9d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779522"
---
# <a name="collect-thread-and-process-concurrency-data"></a>Zbieranie danych współbieżności dla wątku i procesu

Metoda profilowania współbieżności narzędzi programu Visual Studio umożliwia zbieranie danych rywalizacji o zasoby, które zawierają informacje o każdym zdarzeniu synchronizacji, które powoduje, że funkcja w profilizowanej aplikacji czeka na dostęp do zasobu.

Metodę profilowania współbieżności można określić przy użyciu jednej z następujących procedur:

- Na pierwszej stronie Kreatora profilowania kliknij pozycję **Współbieżność**
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij pozycję **Współbieżność**.
- Na pasku **narzędzi Eksploratora wydajności** na liście **Metoda** kliknij pozycję **Współbieżność**.

## <a name="common-tasks"></a>Typowe zadania

Dodatkowe opcje można określić w oknie dialogowym**Strony właściwości** _sesji_wydajności sesji wydajności. Aby otworzyć to okno dialogowe:

- W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**Strony właściwości sesji** _wydajności_podczas profilowania przy użyciu metody współbieżności.

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|Na stronie **Ogólne** określ szczegóły nazewnictwa wygenerowanego pliku danych profilowania (vsp).|- [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
|Na **launch** strony określ aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|- [Jak: Określ plik binarny, aby rozpocząć](../profiling/how-to-specify-the-binary-to-start.md)|
|Na stronie **Interakcja warstwy** dodaj ADO.NET dane wywołania do uruchomienia profilowania.|- [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)|
|Na stronie **Liczniki systemu Windows** określ jeden lub więcej liczników wydajności systemu operacyjnego, które mają być dodawanye do danych profilowania jako znaczników.|- [Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|
|Na stronie **Zaawansowane** określ wersję czasu wykonywania programu .NET Framework do profilu, jeśli moduły aplikacji używają wielu wersji. Domyślnie pierwsza załadowana wersja jest profilowana.|- [Jak: Określ środowisko uruchomieniowe programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
