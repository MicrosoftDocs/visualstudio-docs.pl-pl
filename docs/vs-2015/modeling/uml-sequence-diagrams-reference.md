---
title: 'Diagramy sekwencji UML: Informacje ogólne | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661713"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramy sekwencji UML: Odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *Diagram sekwencji* przedstawia interakcję, która reprezentuje sekwencję komunikatów między wystąpieniami klas, składników, podsystemów lub aktorów. Czas przepływa w dół diagramu i pokazuje przepływ kontroli od jednego uczestnika do innego. Użyj diagramów sekwencji do wizualizacji wystąpień i zdarzeń zamiast klas i metod. Na diagramie może występować więcej niż jedno wystąpienie tego samego typu. Może również pojawić się więcej niż jedno wystąpienie tego samego komunikatu.

 Diagramy sekwencji UML są częścią modelu UML i istnieją tylko w projektach modelowania UML. Aby utworzyć diagram sekwencji UML, w menu **Architektura** kliknij **Nowy UML lub diagram warstwowy**. Dowiedz się więcej o tym, jak tworzyć i rysować [diagramy sekwencji UML](../modeling/uml-sequence-diagrams-guidelines.md) lub [diagramy modelowania UML](../modeling/edit-uml-models-and-diagrams.md) .

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Odczytywanie diagramów sekwencyjnych
 W poniższej tabeli opisano elementy, które można wyświetlić na diagramie sekwencji. Dowiedz się więcej o [właściwościach tych elementów](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).

 ![Części diagramu sekwencji](../modeling/media/uml-sequence.png "UML_Sequence")

|**Kształt**|**Element**|**Opis**|
|---------------|-----------------|---------------------|
|1|**Linii życia**|Linia pionowa, która reprezentuje sekwencję zdarzeń występujących w uczestniku podczas interakcji, podczas gdy czas postępuje w dół wiersza. Ten Uczestnik może być wystąpieniem klasy, składnika lub aktora.|
|2|**Aktor**|Uczestnik, który jest zewnętrzny względem opracowywanego systemu.<br /><br /> Aby umieścić symbol aktora w górnej części linii życia, należy ustawić jego właściwość **aktora** .|
|3|**Komunikat synchroniczny**|Nadawca czeka na odpowiedź na komunikat synchroniczny przed kontynuowaniem. Na diagramie przedstawiono wywołanie i zwrot. Komunikaty synchroniczne są używane do reprezentowania zwykłych wywołań funkcji w ramach programu, a także innych rodzajów komunikatów, które zachowują się w taki sam sposób.|
|4|**Komunikat asynchroniczny**|Komunikat, który nie wymaga odpowiedzi przed kontynuowaniem nadawcy. Komunikat asynchroniczny wyświetla tylko wywołanie od nadawcy. Służy do reprezentowania komunikacji między oddzielnymi wątkami lub tworzeniem nowego wątku.|
|5|**Wystąpienie wykonywania**|Pionowy prostokąt cieniowany, który pojawia się na linii życia uczestnika i reprezentuje okres, w którym Uczestnik wykonuje operację.<br /><br /> Wykonywanie rozpoczyna się, gdy uczestnik otrzymuje wiadomość. Jeśli komunikat inicjujący był komunikatem synchronicznym, wykonanie zostanie zakończone ze strzałką "return" z powrotem do nadawcy.|
|6|**Komunikat wywołania zwrotnego**|Komunikat, który zwraca z powrotem do uczestnika, który oczekuje na powrót z wcześniejszego wywołania. Utworzone wystąpienie wykonywania pojawia się na górze istniejącej.|
|7|**Wiadomość własna**|Wiadomość od uczestnika do siebie. Utworzone wystąpienie wykonywania pojawia się na wierzchu wykonywania operacji wysyłania.|
|8|**Utwórz komunikat**|Komunikat, który tworzy uczestnika. Jeśli uczestnik otrzymuje komunikat o utworzeniu, powinien to być pierwszy z nich.|
|9|**Znaleziono komunikat**|Komunikat asynchroniczny od nieznanego lub nieokreślonego uczestnika.|
|10|**Utracony komunikat**|Komunikat asynchroniczny do nieznanego lub nieokreślonego uczestnika.|
|11|**Komentarz**|Komentarz może być dołączany do dowolnego punktu w linii życia.|
|12|**Użycie interakcji**|Ujmuje sekwencję wiadomości, które są zdefiniowane w innym diagramie.<br /><br /> Aby utworzyć **użycie interakcji**, kliknij narzędzie, a następnie przeciągnij je między liniami życia, które chcesz dołączyć.|
|13|**Połączony fragment**|Kolekcja fragmentów. Każdy fragment może zawierać co najmniej jeden komunikat. Istnieją różne rodzaje łączonych fragmentów. Aby uzyskać więcej informacji, zobacz [opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Aby utworzyć fragment, kliknij prawym przyciskiem myszy komunikat, wskaż polecenie **Otocz**, a następnie kliknij typ fragmentu.|
|14|**Ochrona fragmentów**|Może służyć do wypełniania warunku związanego z tym, czy fragment wystąpi.<br /><br /> Aby ustawić ochronę, wybierz fragment, a następnie wybierz opcję Ochrona i wpisz wartość.|
|**Y**|**Zdarzenie zniszczenia**|Reprezentuje punkt, w którym obiekt został usunięty lub nie jest już dostępny. Pojawia się u dołu każdej linii życia.|
||**Interakcja**|Kolekcja komunikatów i linii życia, które są wyświetlane na diagramie sekwencji. Aby wyświetlić właściwości interakcji, należy wybrać ją w **Eksploratorze modelu UML**.|
||**Diagram sekwencji**|Diagram przedstawiający interakcję. Aby wyświetlić właściwości, kliknij pustą część diagramu. **Uwaga:**  Nazwy diagramu sekwencji, interakcja wyświetlana przez niego oraz plik zawierający diagram mogą być różne.|

## <a name="see-also"></a>Zobacz też
 [Diagramy sekwencji UML: wskazówki](../modeling/uml-sequence-diagrams-guidelines.md) [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [diagramów przypadków użycia UML: referencyjne](../modeling/uml-use-case-diagrams-reference.md) [diagramy klas UML:](../modeling/uml-class-diagrams-reference.md) referencyjne diagramy [składników](../modeling/uml-component-diagrams-reference.md) UML: referencyjne [diagramy składników UML: odwołanie](../modeling/uml-component-diagrams-reference.md)
