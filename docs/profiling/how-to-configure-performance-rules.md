---
title: 'Jak: Konfigurowanie reguł wydajności | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c9bb9b07a0ae1fa19ae48408aa34a9dfb6577b6e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779015"
---
# <a name="how-to-configure-performance-rules"></a>Jak: Konfigurowanie reguł wydajności
Ostrzeżenia dotyczące wydajności th Visual Studio Profilowanie Narzędzia wskazują problemy w profilowane aplikacji, które mogą spowolnić wykonywanie programu. Ostrzeżenia mogą również wskazywać, że może być konieczne zmienić metody zbierania, aby zebrać więcej przydatnych danych. Ostrzeżenia o wydajności są generowane automatycznie w sesji profilowania i pojawiają się w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]oknie **Lista błędów** po otwarciu pliku danych profilowania w programie . Niektóre ostrzeżenia mogą nie mieć zastosowania do scenariuszy, które Cię interesują, a niektóre ostrzeżenia mogą być wywoływane niedokładnie. Ostrzeżenia o wydajności można skonfigurować w celu pokazywalenia lub ukrywania określonych ostrzeżeń.

### <a name="to-configure-profiler-performance-warnings"></a>Aby skonfigurować ostrzeżenia o wydajności profilera

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Rozwiń węzeł **Narzędzia wydajności**, a następnie kliknij pozycję **Reguły**.

3. Aby włączyć lub wyłączyć ostrzeżenie, zaznacz lub wyczyść pole wyboru obok **identyfikatora** i nazwy ostrzeżenia.

4. Aby określić poziom walczącej reguły, kliknij komórkę **Akcja** obok reguły, a następnie kliknij poziom ostrzeżenia.

    - **Wyłączone** - wyłącza regułę (jest to takie samo jak wyczyszczenie pola wyboru obok identyfikatora reguły).

    - **Ostrzeżenie** - wyświetla regułę jako ostrzeżenie.

    - **Error** - zatrzymuje wykonywanie profilowania i wyświetla regułę jako błąd.

    - **Informacje** — wyświetla regułę tylko jako informacje.
