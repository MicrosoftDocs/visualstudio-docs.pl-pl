---
title: Włącz lub Wyłącz analizę kodu
ms.date: 10/25/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ec0a8a3f04830115d343fcef611cfbd338163395
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551033"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie automatycznej analizy kodu zarządzanego

Można skonfigurować (statyczny) analizę kodu do uruchomienia po każdej kompilacji projektu kodu zarządzanego. Można ustawić różne właściwości analizy kodu dla każdej konfiguracji kompilacji, na przykład debugowanie i wydanie.

Ten artykuł ma zastosowanie tylko do starszej analizy i nie analizy kodu na żywo przy użyciu [analizatorów kodu](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Aby włączyć lub wyłączyć automatyczną analizę kodu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym właściwości projektu wybierz kartę **Analiza kodu** .

   > [!TIP]
   > Nowsze typy projektów, takie jak .NET Core i aplikacje .NET Standard, nie mają karty **Analiza kodu** . Starsza analiza nie jest dostępna dla tych typów projektów, ale można uzyskać analizę kodu na żywo za pomocą [analizatorów kodu opartego na .NET compiler platform](roslyn-analyzers-overview.md). Aby pominąć ostrzeżenia z analizatorów kodu, zapoznaj się z uwagą na końcu tego artykułu.

1. Określ typ kompilacji w obszarze **Konfiguracja** i platforma docelowa na **platformie**.

1. Aby włączyć lub wyłączyć automatyczną analizę kodu, zaznacz lub wyczyść pole wyboru **Włącz analizę kodu podczas kompilacji** .

> [!NOTE]
> Pole wyboru **Włącz analizę kodu podczas kompilacji** ma wpływ tylko na starszą analizę. Nie ma to wpływu na [.NET compiler platform analizatorów kodu](roslyn-analyzers-overview.md), które są zawsze wykonywane w kompilacji, jeśli zostały zainstalowane jako pakiet NuGet. Jeśli chcesz wyczyścić błędy analizatora z **Lista błędów**, możesz pominąć wszystkie bieżące naruszenia, wybierając **Analizuj** > **Run Code Analysis i pomijając aktywne problemy** na pasku menu. Aby uzyskać więcej informacji, zobacz [pomijanie naruszeń](use-roslyn-analyzers.md#suppress-violations).
