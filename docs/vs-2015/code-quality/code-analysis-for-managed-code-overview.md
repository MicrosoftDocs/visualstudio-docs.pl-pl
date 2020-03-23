---
title: Omówienie analizy kodu zarządzanego | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72610075"
---
# <a name="code-analysis-for-managed-code-overview"></a>Analiza kodu dla zarządzanego kodu — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analiza kodu dla kodu zarządzanego analizuje zarządzane zestawy i raportuje informacje o zestawach, takie jak naruszenia reguł programowania i projektowania określonych w wytycznych dotyczących projektowania programu Microsoft .NET Framework Design.

 Narzędzie analityczne reprezentuje kontrole, które wykonuje podczas analizy jako komunikaty ostrzegawcze. Komunikaty ostrzegawcze identyfikują wszelkie istotne problemy z programowaniem i projektowaniem, a gdy jest to możliwe, dostarczają informacji o tym, jak rozwiązać problem.

## <a name="ide-integrated-development-environment-integration"></a>Integracja IDE (zintegrowane środowisko programistyczne)
 Jako deweloper możesz automatycznie uruchamiać analizę kodu w projekcie lub uruchomić ją ręcznie.

 Aby uruchomić analizę kodu za każdym razem, gdy tworzysz projekt, wybierz **włącz analizę kodu na kompilacji (definiuje CODE_ANALYSIS stałą)** na stronie właściwości projektu. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Aby ręcznie uruchomić analizę kodu w projekcie, w menu **Analiza** kliknij polecenie **Uruchom analizę kodu w programie**_ProjectName_. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Zestawy reguł
 Reguły analizy kodu dla kodu zarządzanego są pogrupowane w *zestawy reguł*. Można użyć jednego z zestawów reguł standardowych firmy Microsoft lub utworzyć zestaw reguł niestandardowych, aby spełnić określone potrzeby. Aby uzyskać więcej informacji, zobacz [Używanie zestawów reguł do reguł analizy kodu grupy](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>W tłumieniu źródła
 Często warto wskazać, że ostrzeżenie nie ma zastosowania. Informuje to dewelopera i inne osoby, które mogą przejrzeć kod później, że ostrzeżenie zostało zbadane, a następnie pominięte lub zignorowane.

 W tłumieniu źródeł ostrzeżenia jest implementowana za pomocą atrybutów niestandardowych. Aby pominąć ostrzeżenie, dodaj `SuppressMessage` atrybut do kodu źródłowego, jak pokazano w poniższym przykładzie:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Aby uzyskać więcej informacji, zobacz [Pomijanie ostrzeżeń przy użyciu atrybutu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Uruchamianie analizy kodu w ramach zasad zaewidencjonowania
 Jako organizacja możesz wymagać, aby wszystkie zaewidencjonowania spełniały określone zasady. W szczególności chcesz upewnić się, że przestrzegasz następujących zasad:

- Nie było żadnych błędów kompilacji w kodzie zaewidencjonowany.

- Analiza kodu została przeprowadzona jako część najnowszej kompilacji.

  Można to osiągnąć, określając zasady zaewidencjonowania. Aby uzyskać więcej informacji, zobacz [Zwiększanie jakości kodu za pomocą zasad odprawy projektu zespołowego](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integracja budowania zespołu
 Można użyć zintegrowanych funkcji systemu kompilacji, aby uruchomić narzędzie analizy w ramach procesu kompilacji. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji](/azure/devops/pipelines/index).

## <a name="see-also"></a>Zobacz też
 [Używanie zestawów reguł do grupowania reguł analizy kodu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [Jak: Włączanie i wyłączanie automatycznej analizy kodu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
