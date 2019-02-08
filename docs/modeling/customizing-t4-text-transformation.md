---
title: Dopasowanie przekształcenia tekstu T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33f7fd14ff62369de66e4934bf9bb2cf6fd83542
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951556"
---
# <a name="customize-t4-text-transformation"></a>Dostosowywanie przekształcenia tekstu T4

Szablony tekstowe są funkcją programu Visual Studio, dzięki czemu można generować kod programu lub innych plików tekstowych, proces przekształcenia. Za pomocą [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], można rozszerzyć proces przekształcania szablonu domyślnego, dostosowując procesora dyrektywy szablonu tekstu lub hosta szablonu tekstu.

## <a name="in-this-section"></a>W tej sekcji

 [Proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md) w tym artykule opisano, jak działa Transformacja tekstu i opisano rolę hosta szablonu i procesorów dyrektyw.

 [Tworzenie procesorów dyrektywy szablonu tekstowego T4 niestandardowe](../modeling/creating-custom-t4-text-template-directive-processors.md) procesora dyrektywy zajmuje się dyrektywy w szablonie, takich jak `<#@template#>.` jest uruchamiany podczas kompilacji szablonu i mogą ładować zestawy i innych zasobów. Można także wstawić kod, który załaduje zasobów w czasie wykonywania. Definiując procesor dyrektywy, można zmniejszyć złożoność szablonów.

 [Wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) Jeśli piszesz rozszerzenie programu Visual Studio, takich jak menu polecenie lub procedura obsługi zdarzeń Twojego rozszerzenia, można użyć usługi szablonów tekstowych do przekształcania dowolnego szablonu tekstu. Można przekazać danych parametru do szablonu, za pomocą obiektu sesji i uzyskać wartości z w ramach szablonu za pomocą `<#@parameter#>` dyrektywy.

 [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md) podczas wykonywania kodu szablonu tekstu, host zapewnia dostęp do plików zewnętrznych i stan aplikacji. Na przykład host, który uruchamia przekształcenia tekstu w programie Visual Studio można zapewnić dostęp do **Eksploratora rozwiązań**. Wyświetla również błędy w oknie komunikat o błędzie. Jeśli chcesz uruchomić przekształcenia tekstu w innym kontekście, można zdefiniować własnego hosta, który zapewnia dostęp do usług, które są dostępne w tym kontekście.

 Jeśli piszesz rozszerzenie programu Visual Studio, należy wziąć pod uwagę przy użyciu istniejącej usługi przekształcenia tekstu zamiast pisania własnego hosta. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Tematy pomocy

- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md) zapewnia składnia dyrektyw szablonu tekstu i bloki sterujące.