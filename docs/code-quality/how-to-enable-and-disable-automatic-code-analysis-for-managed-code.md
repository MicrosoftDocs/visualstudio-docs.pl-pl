---
title: Wyłącz analizę kodu starszej wersji
ms.date: 10/04/2019
description: Dowiedz się, jak włączać i wyłączać analizę kodu binarnego w programie Visual Studio. Zobacz jak skonfigurować tę funkcję w projektach kodu zarządzanego.
ms.custom: SEO-VS-2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 582d0e0d86909b266bbb18f83745b1b2261f0d10
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348752"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie analizy kodu binarnego dla kodu zarządzanego

Można skonfigurować starszą analizę kodu (analiza binarna) do uruchomienia po każdej kompilacji projektu kodu zarządzanego. Można również mieć różne ustawienia dla każdej konfiguracji kompilacji, na przykład debugowanie i wydanie.

> [!NOTE]
> Starsza analiza nie jest dostępna dla nowszych typów projektów, takich jak .NET Core i .NET Standard Apps. Te projekty używają [.NET compiler platform analizatorów kodu](roslyn-analyzers-overview.md) do analizowania kodu, zarówno na żywo, jak i w czasie kompilacji. Aby uzyskać informacje na temat wyłączania analizy kodu źródłowego w tych projektach, zobacz [Jak wyłączyć analizę kodu źródłowego](disable-code-analysis.md).

Aby włączyć lub wyłączyć analizę starszego kodu:

1. W **Eksplorator rozwiązań** wybierz i przytrzymaj (lub kliknij prawym przyciskiem myszy) projekt, a następnie wybierz pozycję **Właściwości**.

2. W oknie dialogowym właściwości projektu przejdź do karty **Analiza kodu** .

3. Określ typ kompilacji w obszarze **Konfiguracja** i platforma docelowa na **platformie**. (Tylko projekty Non-.NET Core/. NET standard).

::: moniker range="vs-2017"

4. Aby włączyć lub wyłączyć automatyczną analizę kodu, zaznacz lub wyczyść pole wyboru **Włącz analizę kodu podczas kompilacji** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Aby włączyć lub wyłączyć automatyczną analizę kodu, zaznacz lub wyczyść pole wyboru **Uruchom przy kompilacji** w sekcji **analizatory binarne** .

   ![Uruchom analizę kodu binarnego dla opcji kompilacji w programie Visual Studio](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> Wyłączenie analizy kodu binarnego na kompilowaniu nie ma wpływu na [.NET compiler platform analizatorów kodu](roslyn-analyzers-overview.md), które są zawsze wykonywane w kompilacji, jeśli zostały zainstalowane jako pakiet NuGet. Aby uzyskać informacje na temat wyłączania analizy z tych analizatorów, zobacz [Jak wyłączyć analizę kodu źródłowego](disable-code-analysis.md).
