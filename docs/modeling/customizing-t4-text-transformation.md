---
title: Dopasowanie transformacji tekstu T4
description: Dowiedz się, jak rozszerzyć domyślny proces przekształcania szablonu przez dostosowanie procesora dyrektywy szablonu tekstu lub hosta szablonu tekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35942b5f87458d1ccaf4892d33b5bba1dcdbb8a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389361"
---
# <a name="customize-t4-text-transformation"></a>Dostosowywanie przekształcenia tekstu T4

Szablony tekstowe są funkcją Visual Studio które umożliwiają generowanie kodu programu lub innych plików tekstowych w procesie przekształcania. Za pomocą funkcji można rozszerzyć domyślny proces przekształcania szablonu przez dostosowanie procesora dyrektywy szablonu tekstu [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] lub hosta szablonu tekstu.

## <a name="in-this-section"></a>W tej sekcji

 [Proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md) Opisuje sposób działania przekształcania tekstu i wyjaśnia rolę hosta szablonu i procesorów dyrektyw.

 [Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor dyrektywy zajmuje się dyrektywami w szablonie, takimi jak Jest on uruchamiany podczas kompilacji szablonu i może ładować `<#@template#>.` zestawy i inne zasoby. Może również wstawić kod, który będzie ładować zasoby w czasie rzeczywistym. Dzięki zdefiniowaniu własnego procesora dyrektywy można zmniejszyć złożoność szablonów.

 [Wywołania przekształcenia tekstu w rozszerzeniu programu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) W przypadku pisania rozszerzenia Visual Studio, takiego jak polecenie menu lub program obsługi zdarzeń, rozszerzenie może użyć usługi szablonów tekstu do przekształcenia dowolnego szablonu tekstu. Dane parametrów można przekazać do szablonu przy użyciu obiektu Session i pobrać wartości z szablonu przy użyciu `<#@parameter#>` dyrektywy .

 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md) Po wykonaniu kodu szablonu tekstowego host zapewnia dostęp do plików zewnętrznych i stanu aplikacji. Na przykład host, który uruchamia przekształcenia tekstu w programie Visual Studio może zapewnić dostęp do **Eksplorator rozwiązań**. Błędy są również wyświetlane w oknie komunikatu o błędzie. Jeśli chcesz uruchamiać przekształcenia tekstu w innym kontekście, możesz zdefiniować własnego hosta, który zapewnia dostęp do usług dostępnych w tym kontekście.

 Jeśli piszesz rozszerzenie Visual Studio, rozważ użycie istniejącej usługi przekształcania tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [Temat Invoking Text Transformation in a VS Extension (Wywołania przekształcenia tekstu w rozszerzeniu programu VS).](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="reference"></a>Odwołanie

- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md) zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.
