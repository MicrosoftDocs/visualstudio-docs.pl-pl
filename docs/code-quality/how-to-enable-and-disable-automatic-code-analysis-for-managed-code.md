---
title: Włączanie lub wyłączanie analizy kodu
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1620999385eec0862b4ba2aceadba10bb21d239d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905601"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Instrukcje: Włączanie i wyłączanie automatycznej analizy kodu dla kodu zarządzanego

Można skonfigurować analizy kodu (statyczne), aby uruchomić po każdej kompilacji projektu kodu zarządzanego. Można ustawić właściwości analizy dla każdej konfiguracji kompilacji inny kod, na przykład debug i release.

Ten artykuł ma zastosowanie tylko do statycznej analizy kodu i za pomocą analizy kodu nie na żywo [analizatorów kodu Roslyn](roslyn-analyzers-overview.md).

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Włączanie lub wyłączanie automatycznej analizy kodu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie wybierz **właściwości**.

1. W oknie dialogowym właściwości projektu wybierz **analizy kodu** kartę.

   > [!TIP]
   > Typów projektu w nowszych, takie jak aplikacje platformy .NET Core i .NET Standard nie mają **analizy kodu** kartę. Statyczna analiza kodu nie jest dostępny dla tych typów projektów, ale nadal można uzyskać za pomocą analizy kodu na żywo [analizatorów kodu Roslyn](roslyn-analyzers-overview.md). Aby pominąć ostrzeżenia z Roslyn analizatorów kodu, zobacz uwagę na końcu tego artykułu.

1. Określ typ kompilacji w **konfiguracji** i platformy docelowej w **platformy**.

1. Aby włączyć lub wyłączyć automatycznej analizy kodu, zaznacz lub wyczyść **Włącz analizę kodu podczas kompilacji** pole wyboru.

> [!NOTE]
> **Włącz analizę kodu podczas kompilacji** pole wyboru ma wpływ tylko na statycznej analizy kodu. Nie wpływa na [analizatorów kodu Roslyn](roslyn-analyzers-overview.md), która zawsze wykonać na konferencji build, jeśli został zainstalowany jako pakiet NuGet. Jeśli chcesz wyczyścić błędy analizatora z **lista błędów**, można pominąć wszystkie bieżące naruszenia, wybierając **analizy** > **Uruchom analizę kodu i Pomiń aktywne Problemy z** na pasku menu. Aby uzyskać więcej informacji, zobacz [Pomiń naruszenia](use-roslyn-analyzers.md#suppress-violations).
