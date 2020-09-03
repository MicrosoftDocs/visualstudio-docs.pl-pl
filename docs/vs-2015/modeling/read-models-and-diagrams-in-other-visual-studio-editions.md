---
title: Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671278"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po otwarciu modelu w wersji programu Visual Studio, która nie obsługuje tworzenia modelu, model zostanie otwarty w trybie tylko do odczytu. W tym trybie można zmienić układ diagramów, ale nie można zmienić modelu.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tworzenie modelu, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Uzyskiwanie dostępu do modelu i diagramów
 Aby odczytać diagram UML lub diagram warstwowy, należy najpierw użyć programu Visual Studio, aby otworzyć projekt modelowania, a następnie otworzyć go w tym diagramie.

 Z tego powodu, jeśli chcesz odczytać diagram UML lub diagram warstwowy, musisz również mieć dostęp do projektu modelowania, w którym został utworzony. Można to zrobić przez uzyskanie dostępu do projektu z [!INCLUDE[esprscc](../includes/esprscc-md.md)] lub uzyskanie kopii plików projektu.

> [!NOTE]
> Nie dotyczy to map kodu i diagramów klas .NET generowanych na podstawie kodu. Te diagramy mogą być wyświetlane niezależnie od projektu modelowania.

 Aby można było odczytać diagram UML lub diagram warstwowy, minimalny zestaw wymaganych plików jest następujący:

- Dwa pliki diagramu dla diagramu, który ma zostać odczytany, na przykład, **Webdiagrams. classdiagram i webdiagram. classdiagram. layout**.

    > [!NOTE]
    > W przypadku diagramów warstwowych powinien istnieć również plik o nazwie Moje _Diagram_**. layerdiagram. pominięcia**.

- Plik projektu modelowania (**WebMode. modelproj**)

- Plik modelu głównego (**ModelDefinition\MyModel.UML**)

- Pliki pakietu dla dowolnego pakietu, do którego odwołuje się Diagram (**ModelDefinition\MyPackage.UML**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Zmiany, które można wprowadzić w trybie tylko do odczytu
 Jeśli otworzysz model i jego diagramy w wersji programu Visual Studio, która nie obsługuje tworzenia modelu, nie możesz zmienić modelu. Oznacza to, że nie można zmienić elementów i relacji, które są wyświetlane na diagramach lub w Eksploratorze modelu. Można jednak wprowadzić pewne zmiany w układzie diagramów:

- Zmień rozmieszczenie kształtów i łączników na diagramie.

- Rozwijanie i zwijanie kształtów.

  Można zapisać te zmiany. Jeśli chcesz, aby zmiany były widoczne dla innych użytkowników, musisz mieć co najmniej wysłanie zaktualizowanych plików **układu** .

## <a name="related-topics"></a><a name="RelatedTopics"></a> Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)|Diagram warstwowy pokazuje strukturę istniejącej lub proponowanej architektury. Po zapisaniu kodu można automatycznie sprawdzić jego poprawność na diagramie warstwowym.|
|[Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)|Diagram aktywności pokazuje przepływ pracy w procesie biznesowym lub w oprogramowaniu.|
|[Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)|Diagram klas zawiera typy i relacje używane w wielu kontekstach, takich jak kod, schematy bazy danych, Protokoły komunikacyjne lub słownik terminów używanych do opisywania domeny biznesowej.|
|[Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)|Diagram składnika pokazuje wyodrębnione części w projekcie oprogramowania i ich interfejsy.|
|[Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)|Diagram sekwencji pokazuje interakcje między elementami w projekcie oprogramowania.|
|[Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)|Diagram przypadków użycia pokazuje użytkowników systemu i działań, które mogą wykonać w celu osiągnięcia określonych celów.|

## <a name="see-also"></a>Zobacz też
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
