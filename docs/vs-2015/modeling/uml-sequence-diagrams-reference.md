---
title: 'Diagramy sekwencji UML: Dokumentacja | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 3990d43ae11db3db8eb792883ba62a030cde3a2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755159"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramy sekwencji UML: Tematy pomocy
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
||**Diagram sekwencji**|Diagram, który wyświetla interakcji. Aby wyświetlić jego właściwości, kliknij pustą część diagramu. **Uwaga:**  Nazwy diagramu sekwencji, interakcji, wyświetla i pliku, który zawiera diagram może składać się z inną.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy sekwencji UML: Wytyczne dotyczące](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy przypadków użycia UML: Odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)
