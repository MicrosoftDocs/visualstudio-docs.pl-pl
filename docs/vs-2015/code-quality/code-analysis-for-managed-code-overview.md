---
title: Analiza kodu dla zarządzanego kodu — Omówienie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610075"
---
# <a name="code-analysis-for-managed-code-overview"></a>Analiza kodu dla zarządzanego kodu — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiza kodu dla kodu zarządzanego analizuje zestawy zarządzane i raportuje informacje o zestawach, takie jak naruszenia reguł programowania i projektowania, które zostały określone w wytycznych dotyczących projektowania Microsoft .NET Framework.

 Narzędzie do analizy reprezentuje kontrole wykonywane podczas analizy jako komunikaty ostrzegawcze. Komunikaty ostrzegawcze identyfikują wszelkie istotne problemy związane z programowaniem i projektowaniem oraz, gdy jest to możliwe, dostarczają informacji na temat sposobu rozwiązania problemu.

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)
 Jako deweloper możesz automatycznie uruchomić analizę kodu w projekcie lub uruchomić ją ręcznie.

 Aby uruchomić analizę kodu przy każdej kompilacji projektu, zaznacz opcję **Włącz analizę kodu podczas kompilacji (definiuje stałą CODE_ANALYSIS)** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Aby ręcznie uruchomić analizę kodu w projekcie, w menu **Analizuj** kliknij polecenie **Uruchom analizę kodu na**_ProjectName_. Aby uzyskać więcej informacji, zobacz [jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Zestawy reguł
 Reguły analizy kodu dla kodu zarządzanego są pogrupowane w *zestawy reguł*. Można użyć jednego z standardowych zestawów reguł firmy Microsoft lub można utworzyć niestandardowy zestaw reguł, aby spełnić konkretne potrzeby. Aby uzyskać więcej informacji, zobacz [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>W pominięciu źródła
 Często warto wskazać, że ostrzeżenie nie ma zastosowania. Informuje dewelopera i inne osoby, które mogą później przejrzeć kod, że ostrzeżenie zostało zbadane, a następnie pominięte lub zignorowane.

 W przypadku pominięcia źródła ostrzeżeń jest implementowana za poorednictwem atrybutów niestandardowych. Aby pominąć ostrzeżenie, należy dodać atrybut `SuppressMessage` do kodu źródłowego, jak pokazano w następującym przykładzie:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Aby uzyskać więcej informacji, zobacz [pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchom analizę kodu w ramach zasad ewidencjonowania
 Jako organizacja można wymagać, aby wszystkie zaewidencjonowania spełniały określone zasady. W szczególności chcesz upewnić się, że przestrzegasz następujących zasad:

- Brak błędów kompilacji w kodzie, który został zaewidencjonowany.

- Analiza kodu została uruchomiona jako część najnowszej kompilacji.

  Można to osiągnąć przez określenie zasad ewidencjonowania. Aby uzyskać więcej informacji, zobacz [rozszerzanie jakości kodu za pomocą zasad ewidencjonowania projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integracja kompilacji zespołowej
 Możesz użyć zintegrowanych funkcji systemu kompilacji, aby uruchomić Narzędzie analizy jako część procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji](/azure/devops/pipelines/index).

## <a name="see-also"></a>Zobacz też
 [Korzystanie z zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [instrukcje: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
