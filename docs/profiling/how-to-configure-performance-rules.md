---
title: Jak skonfigurować reguły wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a1301161667d945fe4570eb8c7c9f0c2ce8bfffb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328454"
---
# <a name="how-to-configure-performance-rules"></a>Instrukcje: Konfigurowanie reguł wydajności
Ostrzeżenia dotyczące wydajności programu Visual Studio narzędzia profilowania wskazują problemy w profilowanej aplikacji, która może spowalniać wykonywanie programu. Ostrzeżenia mogą również wskazywać, że może zajść potrzeba zmiany metod zbierania danych w celu zebrania bardziej użytecznych informacji. Ostrzeżenia o wydajności są generowane automatycznie w sesji profilowania i pojawiają się w oknie **Lista błędów** , gdy plik danych profilowania zostanie otwarty w programie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . Niektóre ostrzeżenia mogą nie dotyczyć interesujących Cię scenariuszy, a niektóre ostrzeżenia mogą być nieprawidłowo zgłaszane. Można skonfigurować ostrzeżenia wydajności, aby pokazać lub ukryć określone ostrzeżenia.

### <a name="to-configure-profiler-performance-warnings"></a>Aby skonfigurować ostrzeżenia wydajności profilera

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Rozwiń węzeł **Narzędzia do oceny wydajności**, a następnie kliknij pozycję **reguły**.

3. Aby włączyć lub wyłączyć ostrzeżenie, zaznacz lub wyczyść pole wyboru obok **identyfikatora** ostrzeżenia i nazwy.

4. Aby określić poziom Warring reguły, kliknij komórkę **Akcja** obok reguły, a następnie kliknij poziom ostrzeżenia.

    - **Wyłączone** — wyłącza regułę (jest to takie samo jak wyczyszczenie pola wyboru obok identyfikatora reguły).

    - **Ostrzeżenie** — wyświetla regułę jako ostrzeżenie.

    - **Błąd** — zatrzymuje wykonywanie profilowania i wyświetla regułę jako błąd.

    - **Informacje** — wyświetla tylko regułę jako informacje.
