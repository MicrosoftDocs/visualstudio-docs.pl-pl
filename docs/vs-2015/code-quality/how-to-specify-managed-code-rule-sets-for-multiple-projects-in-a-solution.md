---
title: 'Instrukcje: Określanie zestawów reguł kodu zarządzanego dla wielu projektów w rozwiązaniu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656422"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Porady: określanie zestawów reguł zarządzanego kodu dla wielu projektów w rozwiązaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie wszystkie zarządzane projekty rozwiązania są przypisane do *zestawu reguł*analizy kodów minimalnych zalecanych reguł firmy Microsoft. Zestawy reguł, które są przypisane do projektów rozwiązania, można zmienić w oknie dialogowym właściwości rozwiązania.

> [!NOTE]
> Domyślnie Analiza kodu projektu nie jest uruchamiana jako krok kompilacji. Aby włączyć analizę kodu jako krok kompilacji, zobacz [jak: Konfigurowanie analizy kodu dla projektu kodu zarządzanego](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Aby określić zestaw reguł dla wielu projektów w rozwiązaniu kodu zarządzanego

1. W [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] lub [!INCLUDE[vsPro](../includes/vspro-md.md)] otworzyć rozwiązanie.

2. W menu **Analizuj** kliknij polecenie **Konfiguruj analizę kodu dla rozwiązania**.

3. W razie potrzeby rozwiń węzeł **wspólne właściwości**, a następnie kliknij pozycję **Ustawienia analizy kodu**.

4. Można określić zestaw reguł dla jednego lub większej liczby projektów.

    - Aby określić zestaw reguł dla danego projektu, kliknij nazwę projektu.

    - Aby określić zestaw reguł dla wielu projektów, przytrzymaj wciśnięty klawisz CTRL i kliknij nazwy projektu.

    - Aby określić wszystkie projekty w rozwiązaniu, przytrzymaj wciśnięty klawisz SHIFT i kliknij na liście projektów.

5. Kliknij pole **zestaw reguł** w projekcie, a następnie kliknij nazwę zestawu reguł, który ma zostać zastosowany.
