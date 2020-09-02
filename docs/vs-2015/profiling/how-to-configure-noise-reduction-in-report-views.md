---
title: 'Instrukcje: Konfigurowanie redukcji szumu w widokach raportu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5871473eaba749833714d6382beb487702ebe02d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64830991"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Porady: konfigurowanie redukcji szumu w widoku raportu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raporty wydajności można skonfigurować pod kątem obniżenia poziomu hałasu przez ograniczenie ilości danych prezentowanych w widoku drzewa wywołań i widoku alokacji. Dzięki zmniejszeniu szumu problemy z wydajnością są bardziej widoczne. Jest to przydatne podczas analizowania raportów wydajności.  
  
 Opcje konfiguracji zmniejszania szumu obejmują następujące ustawienia:  
  
- Trwa **przycinanie** Gdy raport jest analizowany, widok pominie funkcje, które następują ustawienia wartości i progu, które zostały skonfigurowane, zgodnie z opisem w dalszej procedurze przycinania. Domyślnie przycinanie jest włączone.  
  
- **Folding** Składanie Po włączeniu funkcji składania, kolejne funkcje w ścieżce, która spełnia skonfigurowane ustawienia, zostaną scalone zgodnie z opisem w poniższej procedurze składania. Domyślnie funkcja składania jest domyślnie włączona.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Aby skonfigurować przycinanie raportu wydajności  
  
1. Gdy w wygenerowanym raporcie zostanie wyświetlony widok drzewa wywołań lub Widok alokacji, w menu **deweloper** kliknij pozycję **Profiler** , a następnie kliknij pozycję **Opcje redukcji szumów**.  
  
     Zostanie wyświetlone okno dialogowe **redukcja szumów** .  
  
2. Aby włączyć przycinanie, wykonaj następujące kroki:  
  
    1. Wybierz pozycję **Włącz przycinanie**. Jest to ustawienie domyślne.  
  
        > [!NOTE]
        > W przypadku włączenia redukcji szumu w raporcie zostanie wyświetlony pasek informacji. Aby uzyskać więcej informacji, zobacz widok [drzewa wywołań](../profiling/call-tree-view.md) i [Widok przydziałów](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Skonfiguruj ustawienie wartości za pomocą listy rozwijanej **wartość** i wybierz odpowiednie ustawienie.  
  
    3. Skonfiguruj odpowiednie ustawienie progu, wpisując wartość procentową w polu tekstowym **próg** .  
  
    4. Aby włączyć ostrzeżenie o zmniejszeniu szumu w wygenerowanym raporcie, wybierz opcję **Wyświetl ostrzeżenie, gdy jest włączone zmniejszenie szumu**. Jest to ustawienie domyślne.  
  
3. Aby wyłączyć przycinanie, wyczyść pole wyboru **Włącz przycinanie**.  
  
4. Kliknij przycisk **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Aby skonfigurować składanie raportu wydajności  
  
1. W menu **deweloper** kliknij pozycję **Profiler** , a następnie kliknij pozycję **Opcje redukcji szumów**.  
  
     Zostanie wyświetlone okno dialogowe **redukcja szumów** .  
  
2. Aby włączyć składanie, wykonaj następujące kroki:  
  
    1. Wybierz pozycję **Włącz**składanie. Jest to ustawienie domyślne.  
  
        > [!NOTE]
        > W przypadku włączenia redukcji szumu w raporcie zostanie wyświetlony pasek informacji. Aby uzyskać więcej informacji, zobacz widok [drzewa wywołań](../profiling/call-tree-view.md) i [Widok przydziałów](../profiling/dotnet-memory-allocations-view.md).  
  
    2. Skonfiguruj ustawienie wartości za pomocą listy rozwijanej **wartość** i wybierz odpowiednie ustawienie.  
  
    3. Skonfiguruj odpowiednie ustawienie progu, wpisując wartość procentową w polu tekstowym **próg** .  
  
    4. Aby włączyć ostrzeżenie o zmniejszeniu szumu w wygenerowanym raporcie, wybierz opcję **Wyświetl ostrzeżenie, gdy jest włączone zmniejszenie szumu**. Jest to ustawienie domyślne.  
  
3. Aby wyłączyć składanie, wyczyść pole wyboru **Włącz**składanie.  
  
4. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie widoków raportów narzędzi wydajności](../profiling/customizing-performance-tools-report-views.md)   
 [Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view.md)   
 [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)
