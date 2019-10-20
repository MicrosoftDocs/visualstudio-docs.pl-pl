---
title: Opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f48891107c2eb3250b6b050e00c3650812d386
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669813"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Opisywanie przepływu sterowania przy użyciu fragmentów w diagramach sekwencji UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W diagramie sekwencji UML *połączone fragmenty* pozwalają pokazać pętle, gałęzie i inne alternatywy.

 Połączony fragment składa się z co najmniej jednego *operandu interakcji*, a każda z nich zawiera co najmniej jeden komunikat, interakcja lub połączone fragmenty.

> [!NOTE]
> Ten temat dotyczy fragmentów w diagramach sekwencji. Aby uzyskać więcej informacji na temat odczytywania diagramów sekwencji UML, zobacz [diagramy sekwencji UML: odwołanie](../modeling/uml-sequence-diagrams-reference.md). Aby uzyskać więcej informacji na temat rysowania diagramów sekwencji UML, zobacz [diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md).

 ![Połączony fragment z dwoma operandami interakcji](../modeling/media/uml-seqfragments.png "UML_SeqFragments")

 Elementy wyświetlane na rysunku są następujące.

1. Połączony fragment. Istnieje kilka rodzajów połączonych fragmentów. Ten przykład to osadzony połączony fragment, którego można użyć, aby pokazać, że mogą wystąpić Alternatywne sekwencje komunikatów.

2. Operandy interakcji. Każdy połączony fragment zawiera co najmniej jeden operand interakcji, który może zawierać komunikaty, użycie interakcji i mniejsze połączone fragmenty. W tym przykładzie połączony fragment Alt ma dwie operacje interakcji, pokazując dwie alternatywne sekwencje komunikatów.

3. Każdy operand interakcji można wybrać osobno, klikając wewnątrz niego. W tym przykładzie wybrano operand top Interaction, aby można było zobaczyć jego granicę. Zazwyczaj widoczna jest tylko linia podziału między operandami interakcji.

    > [!NOTE]
    > Aby wybrać operand najwyższej interakcji, nie można kliknąć zbyt blisko górnej części połączonego fragmentu.

4. Chroni. Dla każdego operandu interakcji należy zapewnić ochronę. Opisano w nim warunek, pod którym będą wykonywane komunikaty wewnątrz operandu interakcji.

## <a name="creating-combined-fragments"></a>Tworzenie połączonych fragmentów
 Aby zapoznać się z listą rodzajów fragmentów, które można utworzyć, zobacz [rodzaje połączonego fragmentu](#KindsOfFragment).

#### <a name="to-create-a-combined-fragment"></a>Aby utworzyć połączony fragment

1. Wybierz jeden komunikat lub sekwencję komunikatów, które zaczynają się na tym samym wystąpieniu linii życia lub wykonania.

   > [!NOTE]
   > Jeśli wybierzesz więcej niż jeden komunikat, muszą one stanowić nieprzerwaną sekwencję.

2. Kliknij prawym przyciskiem myszy jeden z komunikatów, wskaż polecenie **Otocz**, a następnie kliknij odpowiedni rodzaj połączonego fragmentu, taki jak **Alt połączony fragment**.

    Zostanie wyświetlony nowy połączony fragment. Nagłówek wskazuje rodzaj wybranego fragmentu, na przykład **Alt**.

    W połączonym fragmencie znajduje się fragment zawierający wybrane wiadomości.

   Można dodać więcej argumentów operacji interakcji do niektórych rodzajów połączonego fragmentu.

   Po ponownym rozmieszczeniu komunikatów w połączonym fragmencie wybierz pozycję **Zmień układ układu** w menu skrótów, aby zmienić rozmiar połączonej ramki fragmentu.

#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Aby dodać nowy operand interakcji do połączonego fragmentu

1. Kliknij prawym przyciskiem myszy puste miejsce wewnątrz operandu interakcji (2) poza zawartym fragmentem i poniżej nagłówka połączonego fragmentu.

2. Wskaż polecenie **Dodaj**.

3. Kliknij przycisk **interakcji operand przed**lub z **argumentem operacji interakcji po**.

4. Można dodawać komunikaty wewnątrz nowego operandu interakcji przy użyciu narzędzi komunikatów lub kopiując i wklejając istniejące komunikaty.

   Właściwość **Guard** operandu interakcji można ustawić, aby opisać warunki, w których są wykonywane komunikaty. Na przykład w połączonym fragmencie **pętli** można użyć funkcji Guard, aby określić warunek, w którym pętla będzie kontynuowana. W **łącznym** połączonym fragmencie można określić oddzielny warunek dla każdego operandu interakcji.

#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Aby ustawić ochronę operandu interakcji

1. Kliknij puste miejsce wewnątrz operandu interakcji (2) poza zawartym fragmentem.

    Obramowanie zaznaczenia pojawia się wokół operandu interakcji i wokół warunku ochrony.

    W nagłówku okna **Właściwości** zostanie wyświetlony **operand interakcji**.

2. Wpisz warunek ochrony.

    Warunek pojawi się w górnej części fragmentu (4).

   Można ustawić właściwości niektórych rodzajów połączonych fragmentów.

#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Aby ustawić lub wyświetlić właściwości połączonego fragmentu

- Kliknij prawym przyciskiem myszy tytuł połączonego fragmentu, a następnie kliknij polecenie **Właściwości**.

    > [!NOTE]
    > Różne rodzaje połączonego fragmentu mają różne właściwości.

## <a name="KindsOfFragment"></a>Rodzaje połączonego fragmentu

### <a name="fragments-describing-control-flow"></a>Fragmenty opisujące przepływ sterowania
 Prosty diagram sekwencji pokazuje tylko jedną typową sekwencję. Możesz użyć następujących typów połączonych fragmentów, aby opisać różnice, które mogą wystąpić w różnych przypadkach.

|Typ fragmentu|Opis|
|-------------------|-----------------|
|**Uszlachetniania**|Opcjonalny. Obejmuje sekwencję, która może być lub może nie wystąpić. W strażniku można określić warunek, pod którym występuje.|
|**+**|Zawiera listę fragmentów zawierających Alternatywne sekwencje komunikatów. Tylko jedna sekwencja występuje w dowolnym momencie.<br /><br /> W każdym fragmencie można umieścić funkcję Guard, aby wskazać, w jaki sposób można jej uruchomić. Funkcja **else** wskazuje fragment, który powinien zostać uruchomiony, jeśli żadna inna ochrona nie ma wartości true. Jeśli wszystkie zabezpieczenia mają wartość false i nie ma żadnych **innych**, nie są wykonywane żadne fragmenty.|
|**For**|Fragment powtarza liczbę razy. W obszarze Ochrona można wskazać warunek, pod którym powinien on być powtarzany.<br /><br /> Połączone fragmenty pętli mają właściwości **min** i **Max**, które wskazują minimalną i maksymalną liczbę przypadków, w których fragment może być powtórzony. Wartość domyślna nie jest ograniczeniem.|
|**Przerwij**|W przypadku wykonania tego fragmentu pozostała część sekwencji zostanie porzucona. Możesz użyć funkcji Guard, aby wskazać stan, w którym nastąpi przerwanie.|
|**Cena**|Równoległ. Zdarzenia w fragmentach mogą być przeplatane.|
|**Najistotniejsz**|Używany w fragmencie par lub SEQ. Wskazuje, że komunikaty w tym fragmencie nie mogą być przeplotem z innymi komunikatami.|
|**Sekwencja**|Istnieją co najmniej dwa fragmenty operandu. Komunikaty dotyczące tej samej linii życia muszą wystąpić w kolejności fragmentów. W przypadku, gdy nie obejmują tych samych linii życia, komunikaty z różnych fragmentów mogą być przeplatane równolegle.|
|**Surowszych**|Istnieją co najmniej dwa fragmenty operandu. Fragmenty muszą wystąpić w określonej kolejności.|

### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmenty informacji o sposobie interpretowania sekwencji
 Domyślnie diagram sekwencji stanowi szereg komunikatów, które mogą być wykonywane. W uruchomionym systemie mogą wystąpić inne komunikaty, które nie zostały wybrane do wyświetlenia na diagramie.

 Aby zmienić tę interpretację, można użyć następujących typów fragmentów.

|Typ fragmentu|Opis|
|-------------------|-----------------|
|**Pod**|Określa listę komunikatów, które opisano w tym fragmencie. Inne komunikaty mogą wystąpić w uruchomionym systemie, ale nie są istotne do celów tego opisu.<br /><br /> Wpisz listę we właściwości **messages** .|
|**Ignoruj**|Lista komunikatów, które nie opisują ten fragment. Mogą występować w uruchomionym systemie, ale nie są istotne do celów tego opisu.<br /><br /> Wpisz listę we właściwości **messages** .|
|**Stanowcz**|Fragment operandu określa jedyne prawidłowe sekwencje. Zwykle używane w fragmencie rozważania lub ignorowania.|
|**Śledz**|Sekwencja pokazana w tym fragmencie nie może wystąpić. Zwykle używane w fragmencie rozważania lub ignorowania.|

## <a name="see-also"></a>Zobacz też
 [Diagramy sekwencji UML: wytyczne](../modeling/uml-sequence-diagrams-guidelines.md) [diagramy sekwencji UML: dokumentacja](../modeling/uml-sequence-diagrams-reference.md) [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md)
