---
title: Dostosowywanie modelu za pomocą profilów i stereotypów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301198"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Dostosowywanie modelu za pomocą profilów i stereotypów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można dostosować standardowe elementy modelu UML, takie jak klasy i składniki, w celu dostosowania ich do określonych celów. Można zastosować *stereotyp* do elementu modelu, który może zmienić listę właściwości elementu. Stereotypy są zdefiniowane w kolekcjach o nazwie *Profile*.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Aby użyć stereotypu, należy połączyć pakiet z profilem. Pozwala to zastosować stereotypy zdefiniowane w profilu do elementów w pakiecie. Niektóre profile są instalowane razem z programem Visual Studio. Ponadto można definiować własne profile.

 Stereotypy można ustawić na liście właściwości elementu. W przypadku głównych rodzajów kształtów na diagramie zastosowane Stereotypy są również wyświetlane w kształcie, jak pokazano w przykładzie.

 ![Klasa UML z stereotypem.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Jeśli tworzysz model przy użyciu profilu, a następnie udostępnisz go innym osobom, nie będą oni mogli zobaczyć stereotypów, chyba że zainstalowano na nim ten sam profil.

## <a name="related-topics"></a>Tematy pokrewne

|Stanowisko|Opis|
|-----------|-----------------|
|[Dodawanie stereotypów do elementów modelu UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Umieszczanie elementu modelu w pakiecie, łączenie pakietu z profilem i stosowanie stereotypu do elementu.|
|[Standardowe stereotypy dla modeli UML](../modeling/standard-stereotypes-for-uml-models.md)|Standardowe profile UML L2 i L3 są instalowane z programem Visual Studio, a każdy model jest domyślnie połączony z nimi. Zapewniają stereotypy, których można użyć do dodawania adnotacji do modeli.<br /><br /> Na przykład można zastosować stereotyp "Specyfikacja»" do klasy, aby wskazać, że jest on przeznaczony tylko do definiowania widocznego zewnętrznie zachowania jego wystąpień,|
|[Definiowanie profilu w celu rozszerzenia kodu UML](../modeling/define-a-profile-to-extend-uml.md)|Można definiować własne stereotypy i narzędzia, które są dostosowywane do Twojego obszaru aplikacji.<br /><br /> Na przykład w przypadku tworzenia oprogramowania bankowego można zdefiniować stereotyp «Account», który można zastosować do klas. Następnie można użyć diagramów klas do opisywania różnych typów kont i ich relacji.|
|[Instalowanie profilu UML](../modeling/install-a-uml-profile.md)|Jeśli ktoś udzielił Ci profilu UML, możesz go zainstalować na komputerze.|
|[Definiowanie niestandardowego elementu przybornika modelowania](../modeling/define-a-custom-modeling-toolbox-item.md)|Niestandardowy element przybornika zapisuje z wielokrotnego ustawiania stereotypu dla nowych elementów.|
