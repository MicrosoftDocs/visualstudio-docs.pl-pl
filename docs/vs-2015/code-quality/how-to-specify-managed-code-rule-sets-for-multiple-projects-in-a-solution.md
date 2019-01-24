---
title: 'Instrukcje: Określanie zestawów reguł kodu zarządzanego dla wielu projektów w rozwiązaniu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2bf83c66f86d516d18221d01470e125979d39349
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757925"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Instrukcje: Określanie zestawów reguł kodu zarządzanego dla wielu projektów w rozwiązaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie, wszystkie projekty zarządzane rozwiązanie przypisanych reguł zalecanych Minimum Microsoft code analysis *zestaw reguł*. Można zmienić zestawów reguł, które są przypisane do projektów rozwiązania w oknie dialogowym właściwości rozwiązania.  
  
> [!NOTE]
>  Domyślnie analizę kodu projektu nie jest uruchamiane jako krok kompilacji. Aby włączyć analizę kodu krok kompilacji, zobacz [jak: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Aby określić zestaw reguł dla wielu projektów w rozwiązaniu do kodu zarządzanego  
  
1.  W [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], lub [!INCLUDE[vsPro](../includes/vspro-md.md)] Otwórz rozwiązanie.  
  
2.  Na **analizy** menu, kliknij przycisk **Konfigurowanie analizy kodu dla rozwiązania**.  
  
3.  Jeśli to konieczne, rozwiń węzeł **wspólne właściwości**, a następnie kliknij przycisk **ustawienia analizy kodu**.  
  
4.  Można określić zestaw reguł dla jednego lub więcej projektów.  
  
    -   Aby określić zestaw reguł dla pojedynczego projektu, kliknij nazwę projektu.  
  
    -   Aby określić zestaw reguł dla wielu projektów, przytrzymaj wciśnięty klawisz CTRL, a następnie kliknij przycisk nazwy projektu.  
  
    -   Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj wciśnięty klawisz SHIFT i kliknij na liście projektu.  
  
5.  Kliknij przycisk **zestaw reguł** pole projektu, a następnie kliknij przycisk, ustaw nazwę reguły, chcesz zastosować.
