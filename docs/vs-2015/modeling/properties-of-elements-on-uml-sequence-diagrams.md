---
title: Właściwości elementów w diagramach sekwencji UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671427"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Właściwości elementów w diagramach sekwencji UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W diagramie sekwencji UML każdy element na diagramie ma właściwości. Aby wyświetlić właściwości elementu, kliknij prawym przyciskiem myszy element na diagramie lub w **Eksploratorze modelu UML** , a następnie kliknij polecenie **Właściwości**. Właściwości są wyświetlane w oknie **Właściwości** .

> [!NOTE]
> Ten temat zawiera informacje o właściwościach elementów w diagramach sekwencji UML. Aby uzyskać więcej informacji na temat odczytywania diagramów sekwencji UML, zobacz [diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md). Aby uzyskać więcej informacji na temat rysowania diagramów sekwencji UML, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Właściwości elementów

|Właściwość|Domyślny|Element|Opis|
|--------------|-------------|-------------|-----------------|
|**Nazwa**|Nazwa domyślna|Wszystkie|Identyfikuje element.|
|**Kwalifikowana nazwa**|Pakiet:: Nazwa|Wszystkie|Jednoznacznie identyfikuje element. Poprzedzona nazwą kwalifikowaną pakietu, która go zawiera.|
|**Elementy robocze**|0 skojarzone|Wszystkie|Liczba elementów roboczych skojarzonych z tym elementem. Aby skojarzyć elementy robocze, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Opis**|puste|Wszystkie|Tutaj możesz tworzyć ogólne uwagi na temat tego elementu.|
|**Kolor**|(domyślnie dla typu elementu)|Linia życia, komunikat|Kolor kształtu. Jest to właściwość kształtu, a nie elementu, który jest wyświetlany.|
|**Wprowadź**|puste|Linii życia|Typ wystąpienia reprezentowanego przez linię życia.<br /><br /> Jeśli w nagłówku linii życia jest wyświetlany symbol odwołania, ta klasa lub interfejs istnieje oddzielnie w Eksploratorze modelu UML i może być wyświetlany na diagramie klas.|
|**Zewnętrzny**|False|Linii życia|Wskazuje, czy linia życia reprezentuje składnik użytkownika, urządzenia lub oprogramowania, który jest zewnętrzny względem składnika, na którym znajduje się diagram.|
|**Natur**|**Ukończono** — komunikat z nadawcą i odbiornikiem.<br /><br /> **Znaleziono** — komunikat, który ma nieokreślony nadawcę.<br /><br /> **Utracono** komunikat z nieokreślonym odbiornikiem.|Komunikat|Wskazuje, które zakończenia komunikatu są dołączone do linii życia.<br /><br /> Nie można zmienić tej właściwości. Jest ona ustawiana podczas tworzenia wiadomości.|
|**Porządku**|**AsynchCall** — komunikat asynchroniczny.<br /><br /> **SynchCall** — komunikat synchroniczny.<br /><br /> **Odpowiedź** — zwracanie części komunikatu synchronicznego.<br /><br /> **OnMessage** — komunikat tworzenia wystąpienia.|Komunikat|Typ komunikatu. Nie można zmienić tej właściwości. Jest ona określana przez narzędzie, którego można użyć do utworzenia wiadomości.|
|**Operacje**|ciągiem|Komunikat|Metoda wywoływana przez komunikat w linii życia otrzymującej.<br /><br /> Widoczne tylko wtedy, gdy linia życia jest połączona z interfejsem lub klasą.|
|**Odwołuje się do**|Diagram sekwencji|Użycie interakcji|Diagram sekwencji wywoływany przez to użycie interakcji.|
|**Operator interakcji**|Ustaw, gdy użyto polecenia **przestrzenny with**|Połączony fragment|Operator reprezentowany przez ten fragment lub zbiór fragmentów.|
|**Chroni**|ciągiem|Argument operacji interakcji w połączonym fragmencie|Sekwencja w fragmencie nie zostanie wykonana, chyba że funkcja Guard ma wartość true.<br /><br /> Aby wybrać górny fragment dowolnego połączonego fragmentu, kliknij poniżej tytuł fragmentu.|
|**Minimum, maksimum**|(bez ograniczeń)|Połączony fragment pętli|Minimalna i Maksymalna liczba uruchomień pętli.|
|**Komunikaty**|ciągiem|Weź pod uwagę i<br /><br /> Ignoruj połączone fragmenty|Komunikaty, które są uwzględniane lub ignorowane w tym fragmencie.|

## <a name="see-also"></a>Zobacz też
 [Diagramy sekwencji UML: odniesienia](../modeling/uml-sequence-diagrams-reference.md) [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md) [opisują przepływ sterowania za pomocą fragmentów w diagramach sekwencji UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
