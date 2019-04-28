---
title: Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 21dc0cb7f02639ca6faa89ae4c067f21e083d6d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387501"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Odczytywanie modeli i diagramów w innych wersjach programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po otwarciu modelu w wersji programu Visual Studio, który nie obsługuje tworzenia modelu modelu zostanie otwarty w trybie tylko do odczytu. W tym trybie można zmienić układ diagramy, ale nie można zmienić modelu.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tworzenie modelu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Uzyskiwanie dostępu do modeli i diagramów  
 Aby przeczytać diagramu UML lub diagramu warstwowego, musi najpierw przy użyciu programu Visual Studio Otwórz projekt modelowania, a następnie Otwórz diagram znajdujący się w nim.  
  
 Z tego powodu jeśli chcesz odczytać diagramu UML lub diagramu warstwowego, musi również masz dostęp do projektu modelowania, w której został utworzony. Możesz to zrobić, uzyskując dostęp do projektu z [!INCLUDE[esprscc](../includes/esprscc-md.md)], lub przez uzyskanie kopii plików projektu.  
  
> [!NOTE]
> To nie ma zastosowania do kodu mapy i .NET klasy diagramy wygenerowane z kodu. Można wyświetlić tych diagramów, niezależnie od projektu modelowania.  
  
 Aby przeczytać diagramu UML lub diagramu warstwowego, minimalny zestaw plików, które są potrzebne jest następująca:  
  
- Dwa pliki dla diagramu, który chcesz, aby dowiedzieć się, na przykład diagramu **MyDiagram.classdiagram i MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    > Dla diagramów warstw powinien również mieć plik o nazwie _MyDiagram_**. layerdiagram.suppressions**.  
  
- Pliku projektu modelowania (**MyModel.modelproj**)  
  
- Plik modelu głównym (**ModelDefinition\MyModel.uml**)  
  
- Pliki pakietu dla dowolnego pakietu, do którego odwołuje się na diagramie (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Zmiany wprowadzone w trybie tylko do odczytu  
 Jeśli otworzysz modelu i jego diagramy w wersjach programu Visual Studio, który nie obsługuje tworzenia modelu, nie można zmienić modelu. Oznacza to, że nie można zmienić elementów i relacji, które są wyświetlane na diagramach lub w Eksploratorze modelu. Można jednak wprowadzić pewne zmiany, układu tych diagramów:  
  
- Rozmieszczanie kształtów i łączników na diagramie.  
  
- Rozwijanie i zwijanie kształtów.  
  
  Możesz zapisać te zmiany. Jeśli chcesz zmiany były widoczne dla innych użytkowników, co najmniej trzeba wysłać zaktualizowany **.layout** plików.  
  
## <a name="RelatedTopics"></a> Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)|Diagram warstwowy pokazuje strukturę ogólną architekturę. Gdy kod jest zapisywany, mogą być automatycznie sprawdzone podstawie diagramu warstwowego.|  
|[Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)|Diagram aktywności zawiera przepływ pracy, procesu biznesowego lub w oprogramowaniu.|  
|[Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)|Diagram klas zawiera typów i relacji używanych w wielu kontekstach, takich jak kod, schematy bazy danych, protokołów komunikacyjnych i słownikiem pojęć używanych do opisania domeny biznesowej.|  
|[Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)|Diagram składników zawiera osobnych części, w projekt oprogramowania oraz ich interfejsów.|  
|[Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)|Diagram sekwencji przedstawia interakcje między elementy projektu oprogramowania.|  
|[Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)|Diagram przypadków użycia zawiera użytkowników systemu i działań, które użytkownicy mogą wykonywać do osiągnięcia określonych celów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)
