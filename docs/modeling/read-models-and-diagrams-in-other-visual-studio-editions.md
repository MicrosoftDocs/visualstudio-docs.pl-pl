---
title: Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d8366c0f87830a77f550dabbce2e8f875171418
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087381"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio

Po otwarciu modelu w wersji programu Visual Studio, który nie obsługuje tworzenia modelu modelu zostanie otwarty w trybie tylko do odczytu. W tym trybie można zmienić układ diagramy, ale nie można zmienić modelu.

Aby dowiedzieć się, które wersje programu Visual Studio obsługują tworzenie modelu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Uzyskiwanie dostępu do modeli i diagramów

Do odczytywania diagram zależności, należy najpierw przy użyciu programu Visual Studio Otwórz projekt modelowania, a następnie Otwórz diagram znajdujący się w nim.

Z tego powodu jeśli chcesz odczytać diagram zależności, należy również masz dostęp do projektu modelowania, w której został utworzony. Można to zrobisz, uzyskując dostęp do projektu z kontroli źródła lub przez uzyskanie kopii plików projektu.

> [!NOTE]
> To nie ma zastosowania do kodu mapy i .NET klasy diagramy wygenerowane z kodu. Można wyświetlić tych diagramów, niezależnie od projektu modelowania.

Aby uzyskać diagram zależności, minimalny zestaw plików, które są potrzebne jest następująca:

- Dwa pliki dla diagramu, który chcesz, aby dowiedzieć się, na przykład diagramu **MyDiagram.classdiagram i MyDiagram.classdiagram.layout**.

    > [!NOTE]
    > Dla diagramów zależności powinien również mieć plik o nazwie _MyDiagram_**. layerdiagram.suppressions**.

- Pliku projektu modelowania (**MyModel.modelproj**)

- Plik modelu głównym (**ModelDefinition\MyModel.uml**)

- Pliki pakietu dla dowolnego pakietu, do którego odwołuje się na diagramie (**ModelDefinition\MyPackage.uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Zmiany wprowadzone w trybie tylko do odczytu

Jeśli otworzysz modelu i jego diagramy w wersjach programu Visual Studio, który nie obsługuje tworzenia modelu, nie można zmienić modelu. Oznacza to, że nie można zmienić elementów i relacji, które są wyświetlane na diagramach lub w Eksploratorze modelu. Można jednak wprowadzić pewne zmiany, układu tych diagramów:

- Rozmieszczanie kształtów i łączników na diagramie.

- Rozwijanie i zwijanie kształtów.

Możesz zapisać te zmiany. Jeśli chcesz zmiany były widoczne dla innych użytkowników, co najmniej trzeba wysłać zaktualizowany **.layout** plików.

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: informacje](../modeling/layer-diagrams-reference.md)
- [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)