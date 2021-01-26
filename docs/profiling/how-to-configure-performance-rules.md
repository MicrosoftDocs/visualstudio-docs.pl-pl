---
title: Konfigurowanie reguł wydajności | Microsoft Docs
description: Zwróć uwagę na ostrzeżenia z programu Visual Studio narzędzia profilowania — mogą one prowadzić do lepszych metod zbierania danych. Znajdziesz je w oknie Lista błędów.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 788cc8d8a0988740ae78e5b2b21368eb5658ec7a
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800335"
---
# <a name="how-to-configure-performance-rules"></a>Instrukcje: Konfigurowanie reguł wydajności
Ostrzeżenia dotyczące wydajności narzędzia profilowania programu Visual Studio wskazują problemy w profilowanej aplikacji, która może spowalniać wykonywanie programu. Ostrzeżenia mogą również wskazywać, że może zajść potrzeba zmiany metod zbierania danych w celu zebrania bardziej użytecznych informacji. Ostrzeżenia o wydajności są generowane automatycznie w sesji profilowania i pojawiają się w oknie **Lista błędów** , gdy plik danych profilowania zostanie otwarty w programie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . Niektóre ostrzeżenia mogą nie dotyczyć interesujących Cię scenariuszy, a niektóre ostrzeżenia mogą być nieprawidłowo zgłaszane. Można skonfigurować ostrzeżenia wydajności, aby pokazać lub ukryć określone ostrzeżenia.

### <a name="to-configure-profiler-performance-warnings"></a>Aby skonfigurować ostrzeżenia wydajności profilera

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Rozwiń węzeł **Narzędzia do oceny wydajności**, a następnie kliknij pozycję **reguły**.

3. Aby włączyć lub wyłączyć ostrzeżenie, zaznacz lub wyczyść pole wyboru obok **identyfikatora** ostrzeżenia i nazwy.

4. Aby określić poziom Warring reguły, kliknij komórkę **Akcja** obok reguły, a następnie kliknij poziom ostrzeżenia.

    - **Wyłączone** — wyłącza regułę (jest to takie samo jak wyczyszczenie pola wyboru obok identyfikatora reguły).

    - **Ostrzeżenie** — wyświetla regułę jako ostrzeżenie.

    - **Błąd** — zatrzymuje wykonywanie profilowania i wyświetla regułę jako błąd.

    - **Informacje** — wyświetla tylko regułę jako informacje.
