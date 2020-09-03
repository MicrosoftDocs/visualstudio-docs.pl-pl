---
title: Dostosowywanie przekształcenia tekstu T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654968"
---
# <a name="customizing-t4-text-transformation"></a>Dopasowanie transformacji tekstu T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony tekstowe to funkcja [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , która umożliwia generowanie kodu programu lub innych plików tekstowych w procesie transformacji. Korzystając z programu [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] , można rozłożyć proces transformacji szablonu domyślnego przez dostosowanie procesora dyrektywy tekstu lub hosta szablonu tekstu.

## <a name="in-this-section"></a>W tej sekcji
 [Proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md) Opisuje sposób działania transformacji tekstu oraz wyjaśnia rolę hosta szablonu i procesorów dyrektywy.

 [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor dyrektywy zajmuje się dyrektywami w szablonie, na przykład `<#@template#>.` podczas kompilowania szablonu i może ładować zestawy i inne zasoby. Może również wstawić kod, który będzie ładować zasoby w czasie wykonywania. Definiując własny procesor dyrektywy, można zmniejszyć złożoność szablonów.

 [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Jeśli piszesz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie takie jak polecenie menu lub program obsługi zdarzeń, rozszerzenie może użyć usługi Text tworzenia szablonów do przekształcenia dowolnego szablonu tekstu. Dane parametrów można przekazać do szablonu przy użyciu obiektu Session i pobrać wartości z szablonu za pomocą `<#@parameter#>` dyrektywy.

 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md) Gdy kod szablonu tekstu jest wykonywany, Host zapewnia dostęp do zewnętrznych plików i stanu aplikacji. Na przykład host, na którym są uruchomione przekształcenia tekstu w programie, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może zapewnić dostęp do Eksploratora rozwiązań. Wyświetla także błędy w oknie komunikatu o błędzie. Jeśli chcesz uruchomić przekształcenia tekstu w innym kontekście, możesz zdefiniować własnego hosta, który zapewnia dostęp do usług dostępnych w tym kontekście.

 Jeśli piszesz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie, rozważ użycie istniejącej usługi transformacji tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Tematy pomocy
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)

 Zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.
