---
title: Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio
description: Dowiedz się więcej o odczytywaniu modeli i diagramów w Visual Studio, a także o zachowaniu tylko do odczytu w przypadku korzystania z wersji Visual Studio, która nie obsługuje tworzenia modelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 95fbf6451a3f07581ff2bdb098428f41904d4276
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389907"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio

Po otwarciu modelu w wersji programu Visual Studio, która nie obsługuje tworzenia modelu, model zostanie otwarty w trybie tylko do odczytu. W tym trybie można zmienić układ diagramów, ale nie można zmienić modelu.

Aby sprawdzić, które wersje aplikacji Visual Studio tworzenia modelu, zobacz Obsługa wersji dla architektury [i narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Uzyskiwanie dostępu do modelu i diagramów

Aby odczytać diagram zależności, należy najpierw użyć Visual Studio, aby otworzyć projekt modelowania, a następnie otworzyć diagram w nim.

Z tego powodu, jeśli chcesz odczytać diagram zależności, musisz również mieć dostęp do projektu modelowania, w którym został utworzony. W tym celu można uzyskać dostęp do projektu z kontroli źródła lub uzyskać kopię plików projektu.

> [!NOTE]
> Nie dotyczy to map kodu i diagramów klas .NET generowanych na podstawie kodu. Te diagramy można wyświetlać niezależnie od projektu modelowania.

Aby odczytać diagram zależności, minimalny zestaw potrzebnych plików jest następujący:

- Dwa pliki diagramu dla diagramu, który chcesz odczytać, na przykład **MyDiagram.classdiagram i MyDiagram.classdiagram.layout.**

    > [!NOTE]
    > W przypadku diagramów zależności powinien być również plik o nazwie _MyDiagram_**.layerdiagram.suppressions**.

- Plik projektu modelowania (**MyModel.modelproj**)

- Plik modelu głównego (**ModelDefinition\MyModel.uml**)

- Pliki pakietu dla dowolnego pakietu, do których odwołuje się diagram (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Zmiany, które można wprowadzić w trybie Read-Only offline

Jeśli otworzysz model i jego diagramy w wersji Visual Studio, która nie obsługuje tworzenia modelu, nie można zmienić modelu. Oznacza to, że nie można zmienić elementów i relacji, które są wyświetlane na diagramach lub w eksploratorze modeli. Można jednak wprowadzić pewne zmiany w układzie diagramów:

- Rozmieszczaj kształty i łączniki na diagramie.

- Rozwijanie i zwijanie kształtów.

Te zmiany można zapisać. Jeśli chcesz, aby zmiany były widoczne dla innych użytkowników, musisz co najmniej wysłać zaktualizowane **pliki układu.**

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
