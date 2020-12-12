---
title: Dopasowanie transformacji tekstu T4
description: Dowiedz się, jak można zwiększyć domyślny proces transformacji szablonu, dostosowując procesor dyrektywy tekstu lub hosta szablonu tekstu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9b168e0e66b7704c3e78a241f76ee4122278c9ed
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362915"
---
# <a name="customize-t4-text-transformation"></a>Dostosowywanie przekształcenia tekstu T4

Szablony tekstowe to funkcja programu Visual Studio, która umożliwia generowanie kodu programu lub innych plików tekstowych w procesie transformacji. Korzystając z programu [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] , można rozłożyć proces transformacji szablonu domyślnego przez dostosowanie procesora dyrektywy tekstu lub hosta szablonu tekstu.

## <a name="in-this-section"></a>W tej sekcji

 [Proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md) Opisuje sposób działania transformacji tekstu oraz wyjaśnia rolę hosta szablonu i procesorów dyrektywy.

 [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor dyrektywy zajmuje się dyrektywami w szablonie, na przykład `<#@template#>.` podczas kompilowania szablonu i może ładować zestawy i inne zasoby. Może również wstawić kod, który będzie ładować zasoby w czasie wykonywania. Definiując własny procesor dyrektywy, można zmniejszyć złożoność szablonów.

 [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Jeśli piszesz rozszerzenie programu Visual Studio, takie jak polecenie menu lub program obsługi zdarzeń, rozszerzenie może używać usługi Text tworzenia szablonów do przekształcania dowolnego szablonu tekstu. Dane parametrów można przekazać do szablonu przy użyciu obiektu Session i pobrać wartości z szablonu za pomocą `<#@parameter#>` dyrektywy.

 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md) Gdy kod szablonu tekstu jest wykonywany, Host zapewnia dostęp do zewnętrznych plików i stanu aplikacji. Na przykład host, na którym są uruchomione przekształcenia tekstu w programie Visual Studio, może zapewnić dostęp do **Eksplorator rozwiązań**. Wyświetla także błędy w oknie komunikatu o błędzie. Jeśli chcesz uruchomić przekształcenia tekstu w innym kontekście, możesz zdefiniować własnego hosta, który zapewnia dostęp do usług dostępnych w tym kontekście.

 Jeśli piszesz rozszerzenie programu Visual Studio, rozważ użycie istniejącej usługi transformacji tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Dokumentacja

- [Napisz szablon tekstowy T4](../modeling/writing-a-t4-text-template.md) zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.
