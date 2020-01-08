---
title: Dopasowanie transformacji tekstu T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e35c279f397f1228c17fb6a41a18a2fe583ab88
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589737"
---
# <a name="customize-t4-text-transformation"></a>Dostosowywanie przekształcenia tekstu T4

Szablony tekstowe to funkcja programu Visual Studio, która umożliwia generowanie kodu programu lub innych plików tekstowych w procesie transformacji. Za pomocą [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]można rozłożyć proces transformacji szablonu domyślnego przez dostosowanie procesora dyrektywy tekstu lub hosta szablonu tekstu.

## <a name="in-this-section"></a>W tej sekcji

 [Proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md) Opisuje sposób działania transformacji tekstu oraz wyjaśnia rolę hosta szablonu i procesorów dyrektywy.

 [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor dyrektywy zajmuje się dyrektywami w szablonie, takimi jak `<#@template#>.` działa podczas kompilowania szablonu i może ładować zestawy i inne zasoby. Może również wstawić kod, który będzie ładować zasoby w czasie wykonywania. Definiując własny procesor dyrektywy, można zmniejszyć złożoność szablonów.

 [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Jeśli piszesz rozszerzenie programu Visual Studio, takie jak polecenie menu lub program obsługi zdarzeń, rozszerzenie może używać usługi Text tworzenia szablonów do przekształcania dowolnego szablonu tekstu. Można przekazać dane parametrów do szablonu przy użyciu obiektu Session i pobrać wartości z szablonu za pomocą dyrektywy `<#@parameter#>`.

 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md) Gdy kod szablonu tekstu jest wykonywany, Host zapewnia dostęp do zewnętrznych plików i stanu aplikacji. Na przykład host, na którym są uruchomione przekształcenia tekstu w programie Visual Studio, może zapewnić dostęp do **Eksplorator rozwiązań**. Wyświetla także błędy w oknie komunikatu o błędzie. Jeśli chcesz uruchomić przekształcenia tekstu w innym kontekście, możesz zdefiniować własnego hosta, który zapewnia dostęp do usług dostępnych w tym kontekście.

 Jeśli piszesz rozszerzenie programu Visual Studio, rozważ użycie istniejącej usługi transformacji tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Tematy pomocy

- [Napisz szablon tekstowy T4](../modeling/writing-a-t4-text-template.md) zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.
