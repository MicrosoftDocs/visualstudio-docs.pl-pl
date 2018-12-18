---
title: 'Diagramy sekwencji UML: Odwołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c92d9eb8ee7858a036fdbb8dfb621c269e3ed4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797029"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramy sekwencji UML: Odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *diagram sekwencji* pokazuje interakcji, która reprezentuje sekwencję wiadomości między wystąpieniami klasy, składników, podsystemów lub podmiotów. Czas przepływy w dół do diagramu, a następnie przedstawia przepływ sterowania od jednego uczestnika do innego. Użyj diagramów sekwencji do wizualizacji, wystąpienia i zdarzenia, a nie klasy i metody. Więcej niż jedno wystąpienie tego samego typu mogą być wyświetlane na diagramie. Więcej niż jedno wystąpienie tego samego komunikatu może również zostać wyświetlony.  
  
 Diagramy sekwencji UML są częścią modelu UML i istnieją tylko w projektach modelowania UML. Aby utworzyć diagram sekwencji UML, na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**. Dowiedz się więcej na temat sposobu tworzenia i narysuj [diagramy sekwencji UML](../modeling/uml-sequence-diagrams-guidelines.md) lub [diagramów modelowania UML](../modeling/edit-uml-models-and-diagrams.md) ogólnie rzecz biorąc.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Odczytywanie diagramów sekwencji  
 W poniższej tabeli opisano elementy, które są widoczne na diagramie sekwencji. Dowiedz się więcej na temat tych [właściwości elementów](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Części diagramu sekwencji](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Kształt**|**Element**|**Opis**|  
|---------------|-----------------|---------------------|  
|1|**Linia życia**|Pionowym wierszem, który reprezentuje sekwencję zdarzeń występujących w uczestnikiem podczas interakcji, podczas czasu trwania wiersz w dół. Ta uczestnika, który może być wystąpienia klasy, składnika lub aktora.|  
|2|**aktora**|Uczestnika, który jest zewnętrzne względem systemu, który tworzysz.<br /><br /> Można wprowadzić symbol aktora są wyświetlane w górnej części linii życia, ustawiając jego **aktora** właściwości.|  
|3|**Synchronicznego komunikatu**|Nadawcy czeka na odpowiedź na komunikat synchroniczne, przed kontynuowaniem. Na diagramie przedstawiono wywołanie i zwracana. Synchroniczne komunikaty są używane do reprezentowania wywołań zwykłej funkcji w ramach programu, a także inne rodzaje komunikatów, które zachowują się tak samo jak.|  
|4|**Komunikatów asynchronicznych**|Komunikat, który nie wymaga odpowiedzi przed kontynuacją nadawcy. Asynchroniczne komunikat zostanie wyświetlony tylko wywołania od nadawcy. Służy do reprezentowania komunikacji między oddzielnych wątkach lub tworzenia nowego wątku.|  
|5|**Wystąpienie wykonania**|Pionowa cieniowanie prostokąt, który pojawi się na linię życia dla uczestników i oznacza, że okres, gdy uczestnik jest wykonywania operacji.<br /><br /> Wykonanie rozpoczyna się, gdy uczestnik odbiera komunikat. Jeśli komunikat inicjujący synchronicznego komunikatu, wykonanie kończy się ze strzałką "Wróć" do nadawcy.|  
|6|**Wywołanie zwrotne komunikatu**|Komunikat, który zwraca uczestnika, który oczekuje na powrót z wcześniejszego wywołania funkcji. Wynikowy wystąpienie wykonywania pojawia się u góry istniejącą grupę.|  
|7|**Samodzielna wiadomości**|Komunikat z uczestnika, który do samego siebie. Wynikowy wystąpienie wykonywania pojawia się u góry wysyłania wykonywania.|  
|8|**Utwórz wiadomość**|Komunikat, który tworzy uczestnikiem. Uczestnika, który odbiera komunikat utworzenia, powinien być pierwszy z nich otrzymuje.|  
|9|**Znaleziona wiadomość**|Komunikatów asynchronicznych z nieznanej lub uczestnika nieokreślony.|  
|10|**Wiadomości utracone**|Komunikatów asynchronicznych do nieznanego lub uczestnika nieokreślony.|  
|11|**Komentarz**|Komentarz można dołączyć do dowolnego punktu w linii życia.|  
|12|**Wykorzystanie interakcji**|Otacza sekwencję wiadomości, które są zdefiniowane w innym diagramie.<br /><br /> Aby utworzyć **wykorzystanie interakcji**, kliknij pozycję Narzędzia, a następnie przeciągnij na linii życia, które chcesz dołączyć.|  
|13|**Połączony Fragment**|Kolekcja fragmentów. Każdy fragment może być częścią co najmniej jeden komunikat. Istnieją różne rodzaje połączonego fragmentu. Aby uzyskać więcej informacji, zobacz [opis przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Aby utworzyć fragmentu, kliknij prawym przyciskiem myszy komunikat, wskaż opcję **Otocz**, a następnie kliknij typ fragmentu.|  
|14|**Fragment Guard**|Może służyć do stanu dotyczą tego, czy zostanie przeprowadzona fragment warunku.<br /><br /> Aby ustawić osłony, wybierz fragment, a następnie wybierz osłony, a następnie wpisz wartość.|  
|**X**|**Zdarzenie niszczenia**|Reprezentuje punkt, w którym obiekt jest usunięty lub nie będą już dostępne. Pojawi się u dołu każdej linii życia.|  
||**Interakcji**|Kolekcja komunikatów i linie życia, która jest wyświetlana w diagramie sekwencji. Aby wyświetlić właściwości interakcji, należy wybrać w **Eksploratora modelu UML**.|  
||**Diagram sekwencji**|Diagram, który wyświetla interakcji. Aby wyświetlić jego właściwości, kliknij pustą część diagramu. **Uwaga:** nazwy diagramu sekwencji, interakcji, wyświetla i pliku, który zawiera diagram może składać się z inną.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)



