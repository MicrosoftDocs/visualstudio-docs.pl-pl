---
title: Definiowanie pakietów i przestrzeni nazw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669901"
---
# <a name="define-packages-and-namespaces"></a>Definiowanie pakietów i przestrzeni nazw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *pakiet* jest kontenerem dla definicji elementów UML, takich jak klasy, przypadki użycia i składniki. Pakiet może również zawierać inne pakiety.

 W Eksploratorze modelu UML wszystkie definicje wewnątrz pakietu są zagnieżdżone pod pakietem. Model UML jest rodzajem pakietu i tworzy katalog główny drzewa.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>W tym temacie
 [Przestrzenie nazw](#Namespaces)

 [Tworzenie i wyświetlanie pakietów](#Packages)

 [Tworzenie elementów modelu wewnątrz pakietów](#Elements)

 [Przeniesienie elementów do lub z pakietu](#Moving)

 [Wklejanie elementów do pakietu](#Pasting)

 [Importuj relacje między pakietami](#Import)

 [Odwołania z jednej przestrzeni nazw do innej](#References)

 [Właściwości pakietów](#Properties)

## <a name="Namespaces"></a>Przestrzeni
 Pakiety są przydatne do rozdzielania pracy z różnymi obszarami. Każdy pakiet definiuje przestrzeń nazw, aby nazwy zdefiniowane w różnych pakietach nie powodowały konfliktów ze sobą.

 Właściwość kwalifikowana nazwa każdego elementu jest kwalifikowana nazwa pakietu, do którego należy, a następnie jego własna nazwa. Na przykład jeśli pakiet jest nazywany `MyPackage`, Klasa w pakiecie będzie miała kwalifikowaną nazwę, taką jak `MyPackage::MyClass`. Ponieważ każdy element jest zawarty w modelu, każda kwalifikowana nazwa zaczyna się od nazwy modelu.

 Model definiuje również przestrzeń nazw, dzięki czemu kwalifikowana nazwa każdego elementu w modelu zaczyna się od nazwy modelu.

 Inne elementy modelu również definiują przestrzenie nazw. Na przykład operacja należy do przestrzeni nazw zdefiniowanej przez jej klasę nadrzędną, tak aby jej kwalifikowana nazwa była taka sama jak `MyModel ::MyPackage ::MyClass ::MyOperation`. W ten sam sposób akcja należy do przestrzeni nazw zdefiniowanej przez działanie nadrzędne.

 Pakiety są kontenerami. Jeśli przeniesiesz lub usuniesz pakiet, klasy, pakiety i inne zawarte w nim elementy są również przenoszone lub usuwane. Ta sama wartość dotyczy innych elementów, które definiują przestrzenie nazw.

## <a name="Packages"></a>Tworzenie i wyświetlanie pakietów
 Pakiet można utworzyć na diagramie klas UML lub w Eksploratorze modelu UML.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Aby utworzyć pakiet na diagramie klas UML

1. Otwórz diagram klas UML lub Utwórz nowy.

2. Kliknij narzędzie **pakiet** .

3. Kliknij w dowolnym miejscu na diagramie. Zostanie wyświetlony nowy kształt pakietu.

     Możesz kliknąć wewnątrz istniejącego pakietu, aby zagnieździć jeden pakiet w innym.

4. Wpisz nową nazwę pakietu.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>Aby utworzyć pakiet w Eksploratorze modelu UML

1. Otwórz **Eksploratora modelu UML**. W menu **Architektura** wskaż polecenie **Windows**, a następnie kliknij **Eksplorator modelu UML**.

2. Kliknij prawym przyciskiem myszy pakiet lub model, do którego chcesz dodać nowy pakiet.

   > [!NOTE]
   > Pakiet można zagnieżdżać wewnątrz innego pakietu.

3. Wskaż polecenie **Dodaj** , a następnie kliknij pozycję **pakiet**.

    Nowy pakiet pojawi się w modelu.

4. Wpisz nową nazwę pakietu.

   Jeśli utworzono pakiet w Eksploratorze modelu UML, można go wyświetlić na diagramie klas UML. Możesz również wyświetlić pakiet na więcej niż jednym diagramie klas UML.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Aby wyświetlić istniejący pakiet na diagramie klas UML

- Przeciągnij pakiet z Eksploratora modelu UML na Diagram klas.

    > [!NOTE]
    > Spowoduje to utworzenie widoku pakietu na tym diagramie. Nie zawsze będzie pokazywać wszystkich elementów, które zawiera pakiet. Aby upewnić się, że zobaczysz całą zawartość pakietu, Wyświetl ją w Eksploratorze modelu UML.

## <a name="Elements"></a>Tworzenie elementów modelu wewnątrz pakietów
 Istnieją cztery sposoby umieszczania elementów modelu w pakiecie:

- Dodaj nowy element do pakietu w Eksploratorze modelu UML.

- Dodaj klasy i inne typy do pakietów na diagramie klas UML.

- Ustaw właściwość **LinkedPackage** diagramu tak, aby nowe elementy utworzone na diagramie były umieszczane w określonym pakiecie. Diagramy klas, diagramy składników i diagramy przypadków użycia mogą być połączone z pakietem w ten sposób.

- Przenieś elementy do lub z pakietu w Eksploratorze modelu UML.

  Element w pakiecie pojawia się pod pakietem w Eksploratorze modelu UML, a jego kwalifikowana nazwa rozpoczyna się od kwalifikowanej nazwy pakietu. Aby wyświetlić kwalifikowaną nazwę dowolnego elementu, kliknij prawym przyciskiem myszy element, a następnie kliknij polecenie **Właściwości**. Właściwość **kwalifikowana nazwa** pojawia się w oknie **Właściwości** .

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Aby utworzyć element w pakiecie w Eksploratorze modelu UML

1. Otwórz **Eksploratora modelu UML**. W menu **Widok** wskaż polecenie **inne okna**, a następnie kliknij pozycję **Eksplorator modelu UML**.

2. Kliknij prawym przyciskiem myszy pakiet lub model, do którego chcesz dodać nowy element.

3. Wskaż polecenie **Dodaj**, a następnie kliknij rodzaj elementu, który chcesz dodać.

     Nowy element zostanie wyświetlony pod pakietem.

4. Wpisz nazwę nowego elementu.

    > [!NOTE]
    > Nowy element nie jest wyświetlany na żadnym diagramie. Aby utworzyć widok nowego elementu, można go przeciągnąć z Eksploratora modelu UML na diagram. Diagram musi być typem, który będzie wyświetlał ten rodzaj elementu.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Aby utworzyć element w pakiecie na diagramie klas UML

1. Otwórz diagram klas, na którym jest wyświetlany pakiet.

    - Utwórz nowy pakiet, jeśli jeszcze tego nie zrobiono.

    - Aby istniejący pakiet pojawił się na diagramie klas, można przeciągnąć pakiet z **Eksploratora modelu UML** na Diagram klas.

2. Kliknij narzędzie dla klasy, interfejsu lub wyliczenia lub pakietu.

3. Kliknij pakiet, w którym chcesz umieścić nowy element.

     Nowy element pojawi się wewnątrz pakietu.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Aby utworzyć wszystkie elementy diagramu w określonym pakiecie

1. Utwórz pakiet, jeśli jeszcze tego nie zrobiono.

2. Otwórz diagram składników, diagram przypadków użycia lub Diagram klas UML.

3. Otwórz właściwości diagramu. Kliknij prawym przyciskiem myszy w pustej części diagramu, a następnie kliknij polecenie **Właściwości**.

4. W właściwości **pakiet połączony** wybierz pakiet, który ma zawierać zawartość diagramu.

5. Utwórz nowe elementy na diagramie. Zostaną one umieszczone w pakiecie.

    - **Kwalifikowana nazwa** każdego elementu zacznie się od kwalifikowanej nazwy pakietu.

    - W **Eksploratorze modelu UML**każdy element pojawi się w obszarze pakietu.

## <a name="Moving"></a>Przeniesienie elementów do i z pakietów
 Można przenieść jeden lub więcej elementów z lub z pakietu.

 Po przeniesieniu pakietu wszystkie elementy wewnątrz niego są przenoszone razem z nim.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Aby przenieść element do lub z pakietu

- W Eksploratorze modelu UML przeciągnij element do lub z drzewa, którego elementem głównym jest pakiet.

     Kwalifikowana nazwa elementu zmieni się w taki sposób, aby pokazywał nowy pakiet lub model będącego właścicielem.

     \- lub-

- W diagramie klas przeciągnij element do kształtu pakietu.

     Kwalifikowana nazwa elementu zmieni się, aby wyświetlić nowy pakiet będącego właścicielem.

    > [!NOTE]
    > Jeśli przeciągniesz element z pakietu do pustej części diagramu, jego pakiet będący właścicielem nie zmieni się. Dzięki temu można utworzyć diagram pokazujący elementy z kilku pakietów bez konieczności pokazywania samych pakietów.

## <a name="Pasting"></a>Wklejanie elementów do pakietu
 Element można wkleić do pakietu. W przypadku wklejenia grupy powiązanych elementów do pakietu zostaną również wklejone relacje między nimi.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Aby wkleić elementy do pakietu na diagramie klas UML

1. Na diagramie klasy UML zaznacz wszystkie elementy, które chcesz skopiować. Kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij polecenie **Kopiuj**.

2. Kliknij prawym przyciskiem myszy pakiet, a następnie kliknij przycisk **Wklej**.

    > [!NOTE]
    > Pakiet może znajdować się na innym diagramie.

## <a name="Import"></a>Importuj relacje między pakietami
 Można zdefiniować relację importu między pakietami za pomocą narzędzia do **importowania** .

 Import oznacza, że elementy zdefiniowane w zaimportowanym pakiecie, które są elementami na końcu strzałki relacji, są efektywnie definiowane również w pakiecie importowania. Wszystkie elementy, których widoczność jest zdefiniowana jako **pakiet** , będą widoczne także w pakiecie importowania.

 Unikaj tworzenia pętli w relacjach importu.

## <a name="References"></a>Odwołania z jednej przestrzeni nazw do innej
 Jeśli chcesz odwołać się do elementu jednego pakietu z innego, musisz użyć kwalifikowanej nazwy elementu.

 Załóżmy na przykład, że pakiet `SalesCommon` definiuje `CustomerAddress` typu. W innym `RestaurantSales` pakietu, chcesz zdefiniować `MealOrder` typu, który ma atrybut typu adres klienta. Dostępne są dwie opcje:

- Określ typ atrybutu przy użyciu w pełni kwalifikowanej nazwy `SalesCommon::CustomerAddress`. Należy to zrobić tylko wtedy, gdy `CustomerAddress` ma właściwość **widoczność** ustawioną na **publiczną**.

- Utwórz relację importu z pakietu `RestaurantSales` do pakietu `SalesCommon`. Następnie można użyć `CustomerAddress` bez użycia nazwy kwalifikowanej.

## <a name="Properties"></a>Właściwości pakietów
 Każdy pakiet ma następujące właściwości. Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy pakiet, na diagramie lub w Eksploratorze modelu UML, a następnie kliknij polecenie **Właściwości**.

|Właściwość|Wartość domyślna|Opis|
|--------------|-------------------|-----------------|
|**Nazwa**|(Nowa nazwa)|Nazwa pakietu. Można go zmienić na diagramie lub w okno Właściwości.|
|**Kwalifikowana nazwa**|*Container* :: *Package — nazwa pakietu*|Pełna nazwa, poprzedzona nazwą pakietu lub modelu, który zawiera ten pakiet. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](#Namespaces).|
|**Profil**|ciągiem|Lista profilów połączonych z tym pakietem. Te profile zapewniają stereotypy, które można zastosować do elementów wewnątrz pakietu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Propagowan**|**Public**|Widoczność pakietu poza jego pakietem nadrzędnym.|
|**Elementy robocze**|ciągiem|Lista połączonych elementów roboczych. Aby uzyskać więcej informacji, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|
|**Lokalizacja definicji**|(nazwa)|Nazwa pliku, w którym są przechowywane szczegóły pakietu. Pliki znajdują się w folderze projektu **ModelDefinition** . Te informacje mogą być przydatne do celów kontroli źródła.|
|**Opis**|ciągiem|Opis pakietu.|
|**Stereotypy**|ciągiem|Stereotypy, które są stosowane do tego pakietu. Lista stereotypów dostępnych jest określana na podstawie profilów wybranych dla tego pakietu i pakietów, które je zawierają. Aby uzyskać więcej informacji, zobacz [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Jak przechowywane są pakiety
 Podczas tworzenia nowego pakietu tworzony jest nowy plik **UML** w folderze projektu **ModelDefinition** . Główny model, który jest również pakietem, również jest przechowywany w pliku **. UML** .

 Ponadto każdy diagram jest przechowywany w dwóch plikach, jeden, który reprezentuje kształty diagramu, i plik **układu** , który rejestruje pozycje kształtów.

## <a name="see-also"></a>Zobacz też
 [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [diagramy klas UML: referencyjne](../modeling/uml-class-diagrams-reference.md) [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md) [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md)
