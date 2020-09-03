---
title: Właściwości skojarzeń w diagramach klas UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652089"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Właściwości skojarzeń w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML można rysować *skojarzenia* między dowolną parą typów. Typ jest klasą, interfejsem lub wyliczeniem.

 Skojarzenie wskazuje, że opracowywany system przechowuje linki pewnego rodzaju między wystąpieniami skojarzonych typów. Ogólnie rzecz biorąc nie oznacza to żadnych elementów dotyczących implementacji linków. Na przykład mogą być wskaźnikami, wierszami w tabeli, nazwami odsyłaczy w formacie XML i tak dalej.

 Skojarzenie jest metodą diagramowy pokazującą atrybut lub parę atrybutów. Na przykład jeśli zdefiniowano restauracji klasy w celu posiadania atrybutu menu typu, można określić tę samą definicję przez rysowanie skojarzenia między restauracji i menu.

 Aby narysować skojarzenie, kliknij pozycję **skojarzenie** w przyborniku, kliknij pierwszy typ, a następnie drugi. Możesz kliknąć ten sam typ dwa razy, aby pokazać, że wystąpienia mogą być połączone z innymi wystąpieniami tego samego typu.

## <a name="properties"></a>Właściwości
 Są to właściwości skojarzenia na diagramie klas UML.

 Aby wyświetlić właściwości skojarzenia, kliknij prawym przyciskiem myszy skojarzenie, a następnie kliknij polecenie **Właściwości**. Właściwości zostaną wyświetlone w okno Właściwości.

 Niektóre właściwości są również widoczne na diagramie, jak pokazano na poniższej ilustracji.

 ![Właściwości w skojarzeniach](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Właściwość**|Opis|
|------------------|-----------------|
|**Nazwa (1)**|Identyfikuje skojarzenie. Pojawia się również na diagramie blisko punktu środkowego skojarzenia.|
|**Kwalifikowana nazwa**|Jednoznacznie identyfikuje skojarzenie. Poprzedzona nazwą kwalifikowaną pakietu zawierającego pierwszą rolę skojarzenia.|
|**Elementy robocze**|Liczba elementów roboczych połączonych z tym skojarzeniem. Aby połączyć elementy robocze, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Kolor**|Kolor łącznika. W przeciwieństwie do innych właściwości, jest to właściwość tego widoku skojarzenia, a nie właściwość podstawowej relacji w modelu.|
|**Pierwsza rola**<br /><br /> **Druga rola**|Każdy koniec skojarzenia nazywa się rolą. Każda rola opisuje właściwości równoważnego atrybutu klasy na odwrotnej końcu skojarzenia.<br /><br /> Na przykładowym diagramie skojarzenie między menu i elementem menu ma role o nazwie menu i zawartość.<br /><br /> Zawartość to nazwa atrybutu w klasie menu.|

### <a name="properties-of-each-role"></a>Właściwości każdej roli
 Aby wyświetlić właściwości każdej roli, rozwiń **pierwszą rolę** lub właściwość **drugiej roli** .

|     **Właściwość**     |          **Wartooć**          |                                                                                                                                                                                                                                                                                                                                        Opis                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nazwa roli (2)**   | Nazwa typu w tej roli |                                                                                                                                                                                                                                                                                                       Nazwa roli. Pojawia się blisko końca skojarzenia na diagramie.                                                                                                                                                                                                                                                                                                        |
|   **Agregacji**    |             Brak              |                                                                        **Brak** (4) — reprezentuje ogólną relację między wystąpieniami klas.<br /><br /> **Złożone** (5) — obiekt z tej roli zawiera obiekt w roli przeciwległej. Za pomocą narzędzia **złożonego** można utworzyć skojarzenie z agregacją złożoną.<br /><br /> **Shared** (6) — obiekt w tej roli zawiera odwołania do obiektu w innej roli. Za pomocą narzędzia **agregacji** można utworzyć skojarzenie z udostępnioną agregacją.<br /><br /> Dokładna interpretacja jest otwarta w Konwencji lokalnej.                                                                         |
|    **Jest pochodny**    |             Fałsz             |                                                                                                                                                                                                                          Jeśli wartość jest równa true, obiekt na tym końcu łącza jest obliczany na podstawie innych atrybutów i skojarzeń. Na przykład można obliczyć miejsce pracy w miejscu pracy. Szczegóły powinny zostać wpisane w opisie lub dołączonym komentarzu.                                                                                                                                                                                                                           |
| **Jest Unią pochodną** |             Fałsz             |                                                                                                                                                                                                                                                                                                             W przypadku wartości true rola jest złożeniem zestawu ról w typach pochodnych.                                                                                                                                                                                                                                                                                                             |
|   **Jest nawigować**   |             Prawda              |                                                 Skojarzenie może zostać odczytane w tym kierunku. W przypadku wystąpienia roli przeciwległej opisywane oprogramowanie może efektywnie określić skojarzone wystąpienie w tej roli.<br /><br /> Jeśli jedna z ról jest w trakcie nawigacji, a druga nie, pojawi się strzałka (7) na skojarzeniu w kierunku nawigacji.<br /><br /> Domyślnie narzędzie skojarzenia tworzy skojarzenie, które jest nawigować w jednym kierunku. Aby przekonwertować ją na skojarzenie dwukierunkowe, możesz wybrać skojarzenie, kliknąć tag akcji, który zostanie wyświetlony, a następnie kliknąć przycisk **Utwórz dwukierunkowe**.                                                 |
|   **Jest tylko do odczytu**   |             Fałsz             |                                                                                                                                                                                                                                                                                   W przypadku wartości true wystąpienia skojarzenia nie można zmienić po jego utworzeniu. Łącze jest zawsze do tego samego obiektu.                                                                                                                                                                                                                                                                                    |
| **Liczebność (3)** |               1               | **1** — ten koniec skojarzenia zawsze łączy się z jednym obiektem. Na rysunku każdy element menu ma jedno menu.<br /><br /> **0.. 1** — albo to koniec linków skojarzenia z jednym obiektem, albo nie ma łącza.<br /><br /> **\\**\* -Każdy obiekt na drugim końcu skojarzenia jest połączony z kolekcją obiektów na tym końcu, a kolekcja może być pusta.<br /><br /> **1.. \\ ** \* — każdy obiekt na drugim końcu skojarzenia jest połączony z co najmniej jednym obiektem na tym końcu. Na rysunku każde menu zawiera co najmniej jeden element menu.<br /><br /> *n* **..** *m* — każdy obiekt na drugim końcu ma kolekcję między *n* i *m* łącza do obiektów na tym końcu. |
|    **Jest uporządkowany**    |             Fałsz             |                                                                                                                                                                                                                                                                                                  W przypadku wartości true zwracana kolekcja tworzy listę sekwencyjną. Liczebność jest większa niż 1.                                                                                                                                                                                                                                                                                                   |
|    **Jest unikatowy**     |             Fałsz             |                                                                                                                                                                                                                                                                                              W przypadku opcji true nie ma zduplikowanych wartości w zwróconej kolekcji. Liczebność jest większa niż 1.                                                                                                                                                                                                                                                                                              |
|    **Widoczność**    |            Publiczne             |                                                                                                                                                                                                                                 Publiczne — widoczne globalnie<br /><br /> Prywatny — niewidoczny poza typem będącym właścicielem<br /><br /> Chronione — widoczne dla typów pochodzących od właściciela<br /><br /> Pakiet jest widoczny dla innych typów w tym samym pakiecie.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Zobacz też
 [Diagramy klas UML: właściwości odwołania](../modeling/uml-class-diagrams-reference.md) [typów na diagramach klas](../modeling/properties-of-types-on-uml-class-diagrams.md) UML [właściwości atrybutów w](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramach klas UML [właściwości operacji na](../modeling/properties-of-operations-on-uml-class-diagrams.md) [diagramach](../modeling/uml-class-diagrams-guidelines.md) klas UML
