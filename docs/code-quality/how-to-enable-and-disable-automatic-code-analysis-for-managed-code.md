---
title: Wyłącz analizę kodu starszej wersji
ms.date: 10/04/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 656b36e6d0a90bb44eaa5745312f1a57e1ea3474
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448940"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie analizy kodu binarnego dla kodu zarządzanego

Można skonfigurować starszą analizę kodu (analiza binarna) do uruchomienia po każdej kompilacji projektu kodu zarządzanego. Można również mieć różne ustawienia dla każdej konfiguracji kompilacji, na przykład debugowanie i wydanie.

> [!NOTE]
> Starsza analiza nie jest dostępna dla nowszych typów projektów, takich jak .NET Core i .NET Standard Apps. Te projekty używają [.NET compiler platform analizatorów kodu](roslyn-analyzers-overview.md) do analizowania kodu, zarówno na żywo, jak i w czasie kompilacji. Aby uzyskać informacje na temat wyłączania analizy kodu źródłowego w tych projektach, zobacz [Jak wyłączyć analizę kodu źródłowego](disable-code-analysis.md).

Aby włączyć lub wyłączyć analizę starszego kodu:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

2. W oknie dialogowym właściwości projektu wybierz kartę **Analiza kodu** .

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
