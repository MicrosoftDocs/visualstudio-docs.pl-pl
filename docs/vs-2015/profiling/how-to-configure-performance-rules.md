---
title: 'Porady: Konfigurowanie zasad wydajności | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b4750dcd245094d0ea116097c7e58b87065aa91
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765107"
---
# <a name="how-to-configure-performance-rules"></a>Porady: Konfigurowanie zasad wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżeń dotyczących wydajności o tym Visual Studio Profiling Tools wskazują na problemy w profilowanej aplikacji, która może spowolnić działanie programu. Ostrzeżenia może również oznaczać, że konieczne może być zmiana metody kolekcji, aby zebrać więcej przydatnych danych. Ostrzeżenia wydajności są automatycznie generowane w sesji profilowania i są wyświetlane w **lista błędów** okna po otwarciu pliku danych profilowania w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Niektórych ostrzeżeń może nie mieć zastosowania do scenariuszy, że jesteś zainteresowany i ostrzeżenia, które może zostać wywołane niepoprawnie. Można skonfigurować ostrzeżeń dotyczących wydajności, aby pokazać lub ukryć szczególne ostrzeżenia.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Aby skonfigurować ostrzeżeń dotyczących wydajności programu profilującego  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  Rozwiń **narzędzia do oceny wydajności**, a następnie kliknij przycisk **reguły**.  
  
3.  Aby włączyć lub wyłączyć ostrzeżenia, zaznacz lub wyczyść pole wyboru obok ostrzeżenie **identyfikator** i nazwę.  
  
4.  Aby określić poziom warring regułę, kliknij przycisk **akcji** komórki obok reguły, a następnie kliknij przycisk poziom ostrzeżeń.  
  
    -   **Wyłączone** — wyłącza regułę (jest to taka sama jak wyczyścić pole wyboru obok identyfikator reguły).  
  
    -   **Ostrzeżenie** -Wyświetla reguły jako ostrzeżenie.  
  
    -   **Błąd** — zatrzymuje wykonywanie profilowania i wyświetla reguł jako błąd.  
  
    -   **Informacje o** -Wyświetla reguły jako tylko informacje.



